<template>
    <section class="work-card">
        <div class="card bg-light text-center">
            <img class="img card-img-top" :src="$withBase(work.img)"/>
            <div class="card-body">
                <h5 class="card-title">{{ work.title }}</h5>
                <p class="card-text" v-html="work.desc"></p>
                <button class="btn btn-primary mr-1" type="button" data-toggle="modal" :data-target="'#' + modalId">
                    <span class="fa fa-picture-o">詳細</span>
                </button>
            </div>
        </div>
        <div class="modal fade" tabindex="-1" role="dialog" :id="modalId" :aria-labelledby="`${modalId}-title`" aria-hidden="true">
            <div class="modal-dialog modal-dialog-centered modal-lg" role="document">
                <div class="modal-content">
                    <div class="modal-header">
                        <h5 class="modal-title" :id="`${modalId}-title`">作品集: {{ work.title }}</h5>
                        <button class="close" type="button" data-dismiss="modal" aria-label="Close">
                            <span aria-hidden="true"> &times; </span>
                        </button>
                    </div>
                    <div class="modal-body">
                        <div class="carousel slide" v-if="_.get(work, 'album.length', 0)" :id="albumId" data-ride="carousel" data-interval="false" data-wrap="false">
                            <ol class="carousl-indicators" v-show="caption">
                                <li v-for="item, index in work.album" :key="item.img" :data-target="'#' + albumId" :data-slide-to="index" :class="{active: index===0}"></li>
                                <div class="carousel-inner">
                                    <div class="carousel-item" v-for="item, index in work.album" :key="item.img" :class="{active: index===0}">
                                        <img class="d-block w-100" :src="$withBase(item.img)" :alt="item.alt || ''"/>
                                        <div class="carousel-caption rounded" v-show="caption">
                                            <p v-html="item.caption"></p>
                                        </div>
                                    </div>
                                </div>
                                <a class="carousel-control-prev" :href="'#' + albumId" role="button" data-slide="prev">
                                    <span class="carousel-control-prev-icon" aria-hidden="true"></span>
                                    <span class="sr-only">Previous</span>
                                </a>
                                <a class="carousel-control-next" :href="'#' + albumId" role="button" data-slide="next">
                                    <span class="carousel-control-next-icon" aria-hidden="true"></span>
                                    <span class="sr-only">Next</span>
                                </a>
                            </ol>
                        </div>
                    </div>
                    <div class="modal-footer">
                        <button class="btn btn-info" type="button" @click="caption=!caption">開關圖片說明</button>
                        <a class="btn btn-primary" v-if="work.url" :href="$withBase(work.url)" target="_blank">
                            <span class="fa fa-external-link">網站</span>
                        </a>
                        <button class="btn btn-secondary" type="button" data-dismiss="modal">關閉</button>
                    </div>
                </div>
            
            </div>
        </div>
    </section>
</template>

<script>
export default {
    props: ['work'],
    computed: {
        modalId() {
            return 'workmodal-' + this._uid
        },
        albumId() {
            return 'workalbum-' + this.uid
        }
    },
    data: () => ({
        caption: true
    })
}
</script>