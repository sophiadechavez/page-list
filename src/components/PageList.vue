<template>
    <div class="cmp-page-list">
        <h2>Latest Updates</h2>
        <div class="cmp-page-list__content">
            <div class="checkbox">
                <div>
                    <input type="checkbox" id="news" v-model="isChecked">
                    <label for="news">News</label>
                </div>
                <div>
                    <input type="checkbox" id="essays" v-model="isChecked">
                    <label for="essays">Essays</label>
                </div>
            </div>
            <div class="entry">
                 <div v-for="(page, index) in latestArticle" :key="index">
                    <h3 class="title">{{page.title}}</h3>
                    <p>{{page.publishDate}}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
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
        }
    }
</script>

<style>
.cmp-page-list {
    .cmp-page-list__content {
        border-style: solid;
        border-color: darkgray;
        padding: 10px;
    }

    .checkbox {
        display: flex;
        gap: 50px;

        input {
            margin-right: 10px;
        }
    }

    .entry {
        div {
            padding: 10px;
            background-color: aliceblue;
            margin-bottom: 20px;
        }
    }
}
</style>
