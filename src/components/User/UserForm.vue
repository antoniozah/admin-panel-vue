<template>
    <div class="userform">
        <form>
            <div class="form-group">
                <label>Name</label>
                <input
                    type="text"
                    placeholder="Enter Name"
                    v-model="currentUser.name"
                />
            </div>
            <div class="form-group">
                <label>Email address</label>
                <input
                    type="email"
                    placeholder="Enter Email"
                    v-model="currentUser.email"
                />
            </div>
            <div class="form-group">
                <label>Phone</label>
                <input
                    type="text"
                    placeholder="Enter Phone"
                    v-model="currentUser.phone"
                />
            </div>
            <div class="form-group">
                <label>Address</label>
                <input
                    type="text"
                    placeholder="Enter Address"
                    v-model="currentUser.address"
                />
            </div>
            <div class="form-group">
                <label>Company</label>
                <input
                    type="text"
                    placeholder="Enter Company"
                    v-model="currentUser.company"
                />
            </div>
            <div class="button-group">
                <button v-if="cancelIsActive" class="btn btn--cancel">
                    Cancel
                </button>
                <button
                    class="btn btn--save"
                    :class="{ disabled: saveIsDisabled }"
                >
                    Save
                </button>
            </div>
        </form>
    </div>
</template>

<script>
export default {
    name: 'UserForm',
    props: ['currentUserData'],
    data() {
        return {
            cancelIsActive: false,
            saveIsDisabled: true,
            currentUser: {
                name: '',
                email: '',
                phone: '',
                address: '',
                company: '',
            },
        };
    },
    methods() {},
    beforeUpdate() {
        this.currentUser = {
            ...this.currentUserData,
        };
    },
};
</script>

<style>
.userform {
    flex: 1;
    width: 100%;
    padding: 10px 20px 10px 10px;
}
.form-group:not(:last-of-type) {
    margin-bottom: 23px;
}

.form-group label,
.form-group input {
    display: flex;
    width: 100%;
}

.form-group label {
    color: var(--label-color);
    font-size: 14px;
    margin-bottom: 5px;
}
.form-group input {
    padding: 9px 6px;
    font-size: 16px;
    color: #4e5561;
    border: 1px solid var(--input-border-color);
    background-color: transparent;
}
.button-group {
    display: flex;
    justify-content: flex-end;
    margin-top: 47px;
}
.btn {
    padding: 10px 14px;
    border: 0;
    border-radius: 4px;
    outline: none;
    font-size: 16px;
    cursor: pointer;
}

.btn:not(:last-of-type) {
    margin-right: 6px;
}

.btn--cancel {
    background-color: var(--cancel-btn-bg);
}

.btn--save {
    color: white;
    background-color: var(--save-btn-bg);
    transition: opacity 0.4s ease-in-out;
}

.btn--save.disabled {
    opacity: 0.7;
}
</style>
