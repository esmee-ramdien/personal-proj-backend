<script lang="ts" setup>
import { ref, onMounted } from 'vue';
import { findUser } from '../../api';
import { useStore } from 'vuex';
import { useRouter } from 'vue-router';


const router = useRouter();
const firstName = ref("");
const lastName = ref("");


onMounted(async () => {
    const { username } = router.currentRoute.value.params;
    const userData = await findUser(username);

    firstName.value = userData.firstName;
    lastName.value = userData.lastName;
});

</script>

<template>
    <div>
        <h1>Welcome {{ firstName }} {{ lastName }} </h1>
    </div>
</template>