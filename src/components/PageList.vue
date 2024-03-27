<template>
    <div class="cmp-page-list">
        <h2>Latest Updates</h2>
        <div class="cmp-page-list__content">
            <div class="checkbox">
                <div>
                    <input type="checkbox" id="news" v-model="newsCheckbox" @click="newsDisplay">
                    <label for="news">News</label>
                </div>
                <div>
                    <input type="checkbox" id="essays" v-model="essayCheckbox" @click="essayDisplay">
                    <label for="essays">Essays</label>
                </div>
            </div>
            <div class="entry">
                <div v-if="selectedCategory === '' || displayAll === true" :class="getCategoryClass(article.category)" v-for="(article, index) in sortedArticles" :key="index">
                    <a class="item" :href="article.url">
                        <p class="title">{{article.title}}</p>
                        <p>{{ formatDate(article.publishDate) }}</p>
                    </a>
                </div>
                <div v-if="selectedCategory !== ''" :class="getCategoryClass(article.category)" v-for="(article, index) in filteredArticles" :key="index">
                    <a class="item" :href="article.url">
                        <p class="title">{{article.title}}</p>
                        <p>{{ formatDate(article.publishDate) }}</p>
                    </a>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
            newsCheckbox: false,
            essayCheckbox: false,
            selectedCategory: "",
            displayAll: this.selectedCategory === 'news' && this.selectedCategory === 'essay',
            latestArticle: [
                    {
                        "title": "Find new ways to travel north",
                        "publishDate": "2023-06-03T13:51:50.417Z",
                        "category": "news",
                        "url": "/articles/4738.html"
                    },
                    {
                        "title": "When will it become possible to use time travel in order to fix your earlier mistakes?",
                        "publishDate": "2023-06-01T12:18:10.317Z",
                        "category": "essay",
                        "url": "/articles/7256.html"
                    },
                    {
                        "title": "10 ways to write better text",
                        "publishDate": "2023-06-03T09:00:32.200Z",
                        "category": "news",
                        "url": "/articles/7247.html"
                    },
                    {
                        "title": "Announcement: we have a new website category",
                        "publishDate": "2023-05-30T17:12:13.102Z",
                        "category": "news",
                        "url": "/articles/1749.html"
                    },
                    {
                        "title": "Weekly news",
                        "publishDate": "2023-05-29T00:23:15.276Z",
                        "category": "news",
                        "url": "/articles/1538.html"
                    },
                    {
                        "title": "In-depth travel guide for Tanzania",
                        "publishDate": "2023-05-31T11:12:43.003Z",
                        "category": "essay",
                        "url": "/articles/2594.html"
                    }
                ]
            };
        },
        methods: {
            getCategoryClass(category) {
            return `category-${category}`;
            },
            formatDate(dateString) {
                const date = new Date(dateString);
                return date.toLocaleDateString('en-US', { month: 'short', day: '2-digit' });
            },
            newsDisplay() {
                this.selectedCategory = "news";
            },
            essayDisplay() {
                this.selectedCategory = "essay";
            }
        },
        computed: {
            sortedArticles() {
                const articles = [...this.latestArticle];

                articles.sort((a, b) => {
                    return new Date(b.publishDate) - new Date(a.publishDate);
                });

                return articles;
            },
            filteredArticles() {
                return this.latestArticle.filter(article => article.category === this.selectedCategory);
            },
            displayAll() {
                return this.essayCheckbox && this.newsCheckbox;
            }
        }
    }
</script>

<style>
.cmp-page-list {
    h2 {
        text-align: center;
    }
    .cmp-page-list__content {
        width: 500px;
        border-style: solid;
        border-color: darkgray;
        padding: 10px;
    }

    .title {
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
        width: 400px;
    }

    .checkbox {
        display: flex;
        gap: 50px;
        justify-content: center;
        margin: 20px 20px;

        input {
            margin-right: 10px;
        }
    }

    .entry {
        .category-news {
            padding: 10px;
            background-color: aliceblue;
            margin-bottom: 20px;
            .item {
                color: cornflowerblue;
                display: flex;
            }
            .item:hover {
                background-color: azure;
            }
        }
        .category-essay {
            padding: 10px;
            background-color: blanchedalmond;
            margin-bottom: 20px;
            .item {
                color: cornflowerblue;
                display: flex;
            }
            .item:hover {
                background-color: peachpuff;
            }
        }
    }
}
</style>
