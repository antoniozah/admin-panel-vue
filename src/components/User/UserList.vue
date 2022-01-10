<template>
    <nav class="usernav">
        <ul class="usernav__list">
            <li
                class="usernav__user"
                v-for="user in users"
                :key="user.id"
                @click="
                    setActiveUser(user.id);
                    this.handleCurrentUser(user);
                "
                :class="{ active: activeBar == user.id }"
            >
                <User :user="user" />
            </li>

            <li></li>
        </ul>
    </nav>
</template>

<script>
import User from './User';
export default {
    name: 'UserList',
    props: ['users'],
    components: {
        User,
    },
    data() {
        return {
            activeBar: '',
            currentUser: {},
        };
    },
    methods: {
        setActiveUser(id) {
            this.activeBar = id;
            console.log(this.activeBar);
        },
        handleCurrentUser(user) {
            this.currentUser = {
                id: user.id,
                photo: user.photo,
                name: user.name,
                company: user.company,
                email: user.email,
                phone: user.phone,
                address: user.address,
            };
            console.log(this.currentUser);
            this.$emit('currentUserData', this.currentUser);
        },
    },
};
</script>

<style>
.usernav {
    width: 95px;
    height: 100vh;
    overflow: hidden;
    position: relative;
    flex-shrink: 0;
}
.usernav__list {
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    bottom: -20px;
    right: -20px;
    overflow-x: hidden;
    overflow-y: auto;
}

.usernav__user {
    cursor: pointer;
}

.usernav__user.active {
    background-color: var(--user-selected-bg);
}
</style>
