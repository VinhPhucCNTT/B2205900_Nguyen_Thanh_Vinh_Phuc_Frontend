<template>
    <div class="page">
        <h4>Thêm liên hệ</h4>
        <ContactForm :contact="contact" @submit:contact="addContact" />
    </div>
</template>
<script>
import ContactForm from "@/components/ContactForm.vue"
import contactService from "@/services/contact.service";
export default {
    components: {
        ContactForm,
    },
    data() {
        return {
            contact: {},
        };
    },
    methods: {
        async addContact(data) {
            try {
                await contactService.create(data);
                alert('Liên hệ được thêm thành công.');
                this.$router.push({ name: "contactbook" });
            } catch (error) {
                console.log(error);
            }
        }
    }
}
</script>