<template>
    <div class="usercard">
        <figure class="usercard__photo">
            <img :src="user.photo" :alt="user.name" />
        </figure>
    </div>
</template>

<script>
export default {
    name: 'User',
    props: ['user'],
};
</script>

<style>
.usercard {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    padding: 10px 30px 10px 10px;
}
.usercard__photo {
    flex-shrink: 0;
    width: 65px;
    height: 65px;
    border-radius: 50%;
    overflow: hidden;
}
</style>
