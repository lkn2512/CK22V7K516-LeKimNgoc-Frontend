<template>
    <div>
        <h1>Thêm liên hệ</h1>
        <ContactForm :contact="newContact" @submit:contact="createContact" />
    </div>
</template>

<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";

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
                favorite: false
            }
        };
    },
    methods: {
        async createContact(data) {
            try {
                await ContactService.create(data);
                alert("Thêm thành công!");
                this.$router.push({ name: "contactbook" });
            } catch (error) {
                console.error(error);
            }
        }
    }
};
</script>
