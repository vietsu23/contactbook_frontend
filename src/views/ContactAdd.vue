<template>
    <div>
        <h1>Tạo liên hệ mới</h1>
        <ContactForm :contact="newContact" @submit:contact="addContact" />
    </div>
</template>

<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service.js"; 
export default {
    components: {
        ContactForm,
    },
    data() {
        return {
            newContact: {
                name: "",
                email: "",
                address: "",
                phone: "",
                favorite: false,
            },
        };
    },
    methods: {
        async addContact(contact) {
            try {
                await ContactService.create(contact);
                this.$router.push({ name: "contactbook" }); 
            } catch (error) {
                console.log("Có lỗi xảy ra:", error);
            }
        },
    },
};
</script>
