<template>
    <div>
        <h1>Thêm liên hệ</h1>
        <contact-form @submit:contact="submitContact" :contact="newContact" />
    </div>
</template>

<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";

export default {
    components: {
        ContactForm
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
        async submitContact(contactData) {
            try {
                await ContactService.create(contactData);
                alert("Thêm thành công!.");
                this.$router.push({ name: "contactbook" });
            } catch (error) {
                console.error(error);
            }
        }
    }
};
</script>
