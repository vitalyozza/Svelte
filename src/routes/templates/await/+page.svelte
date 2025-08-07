<script lang="ts">
    // Интерфейс для типизации репозитория
    interface RepoInfo {
        url: string;
        stars: number | null;
    }

    // Функция для получения звезд
    async function fetchGithubStars(repoUrl: string): Promise<number | null> {
        try {
            const [owner, repo] = repoUrl.split('github.com/')[1].split('/');
            const response = await fetch(`https://api.github.com/repos/${owner}/${repo}`);
            
            if (!response.ok) {
                return null;
            }
            
            const data = await response.json();
            return data.stargazers_count;
        } catch (error) {
            console.error('Error fetching stars:', error);
            return null;
        }
    }

    // Массив репозиториев
    const repositories: string[] = [
        'https://github.com/sveltejs/svelte',
        'https://github.com/facebook/react',
        'https://github.com/angular/angular'
    ];

    // Прямая инициализация Promise
    const repoPromise = (async () => {
        const repoInfoPromises = repositories.map(async (url) => {
            const stars = await fetchGithubStars(url);
            return { url, stars };
        });

        return Promise.all(repoInfoPromises);
    })();
</script>

<!-- Отображение списка репозиториев с количеством звезд -->
{#await repoPromise}
    <!-- Состояние загрузки -->
    <div>Загрузка репозиториев...</div>
{:then repos}
    <!-- Успешная загрузка -->
    <ul>
        {#each repos as repo}
            <li>
                <a href={repo.url} target="_blank">
                    {repo.url.split('github.com/')[1]}
                </a>
                {#if repo.stars !== null}
                    - ⭐ {repo.stars} звезд
                {:else}
                    - Не удалось получить количество звезд
                {/if}
            </li>
        {/each}
    </ul>
{:catch error}
    <!-- Обработка ошибки -->
    <div>Ошибка загрузки: {error.message}</div>
{/await}

<style>
    ul {
        list-style-type: none;
        padding: 0;
    }
    
    li {
        margin-bottom: 10px;
    }
    
    a {
        color: blue;
        text-decoration: none;
    }
</style>
