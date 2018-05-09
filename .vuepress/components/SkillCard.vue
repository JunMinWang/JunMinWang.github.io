<template>
    <div class="card.mb-3">
        <h5 class="card-header bg-secondary text-white">
            <span class="fa fa-fw" :class="'fa-' + skill.icon">
            </span>
            {{ skill.title }}
        </h5>
        <div class="card-body">
            <div class="row mb-1" v-for="proficiency, name in sortedItems" :key="name">
                <div class="col-3 pl-0 pr-1 text-nowrap text-right" :title="name" data-placement="right">
                    {{ name }}
                </div>
                <div class="col-9 pl-1">
                    <div class="progress">
                        <div class="progress-bar progress-bar-success progress-bar-striped bg-success" :class="`proficiency-${proficiency}`"></div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['skill'],
    computed: {
        sortedItems() {
            return _.fromPairs(_.orderBy(_.toPairs(this.skill.items), [1], ['desc']))
        }
    }
}
</script>

<style>
.progress {
    height: 1rem;
    margin: 0.25rem 0;
}

.proficiency-1 {
    width: 35%;
    background-color: #ffc107 !important;
}

.proficiency-1:before {
    content: '略懂';
}

.proficiency-2 {
    width: 60%;
    background-color: #17a2b8 !important;
}

.proficiency-2:before {
    content: '中等';
}

.proficiency-3 {
    width: 85%;
    background-color: #28a745 !important;
}

.proficiency-3:before {
    content: '精通';
}

.card-body {
    height: 14rem;
}
</style>