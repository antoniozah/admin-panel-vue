<template>
    <div class="userpanel">
        <UserList :users="userData" @currentUserData="getCurrentUser" />
        <UserForm :currentUserData="currentUserData" />
    </div>
</template>

<script>
import UserList from './UserList.vue';
import UserForm from './UserForm.vue';
export default {
    name: 'UserPanel',
    components: { UserList, UserForm },
    data() {
        return {
            userData: [],
            currentUserData: {},
        };
    },
    methods: {
        getCurrentUser(currentUser) {
            this.currentUserData = currentUser;
        },
    },
    created() {
        fetch('https://api.jsonbin.io/b/61cb21cac277c467cb379571', {
            method: 'GET',
            headers: { Accept: 'application/json' },
        })
            .then((res) => res.json())
            .then((data) => {
                this.userData = data.users;
                console.log(this.userData);
            })
            .catch((err) => console.log(err.message));
    },
};
</script>

<style>
.userpanel {
    display: flex;
    background-color: #fff;
}
</style>
