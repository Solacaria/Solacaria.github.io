   <template>
    <section id="contact" class="py-16 md:py-24 bg-gray-900">
      <div class="container mx-auto px-4">
        <h2 class="text-3xl font-bold text-center mb-12 text-gray-100">Get In Touch</h2>
  
        <div class="max-w-3xl mx-auto bg-gray-800 rounded-lg shadow-md p-8">
          <div class="flex flex-col md:flex-row md:space-x-8">
            
            <!-- Left column -->
            <div class="md:w-1/2 flex flex-col justify-between">
              <div>
                <h3 class="text-xl font-semibold mb-4 text-gray-100">Contact Information</h3>
                <div class="space-y-4">
                  <div class="flex items-center">
                    <Mail class="h-5 w-5 text-emerald-600 mr-3" />
                    <a href="mailto:jonny.ahslund@live.se" class="text-gray-400 hover:text-emerald-600">
                      E-mail: Jonny.ahslund@live.se
                    </a>
                  </div>
                  <div class="flex items-center">
                    <Linkedin class="h-5 w-5 text-emerald-600 mr-3" />
                    <a
                      href="https://www.linkedin.com/in/jonny-%C3%A5hslund-b3823a283/"
                      target="_blank"
                      rel="noopener noreferrer"
                      class="text-gray-400 hover:text-emerald-600"
                    >
                      Jonny Åhslund @ LinkedIn
                    </a>
                  </div>
                  <div class="flex items-center">
                    <Github class="h-5 w-5 text-emerald-600 mr-3" />
                    <a
                      href="https://github.com/Solacaria"
                      target="_blank"
                      rel="noopener noreferrer"
                      class="text-gray-400 hover:text-emerald-600"
                    >
                      Solacaria @ Github
                    </a>
                  </div>
                  <!-- <div class="flex items-center">
                    <MapPin class="h-5 w-5 text-emerald-600 mr-3" />
                    <span class="text-gray-200">Tierp, Sweden</span>
                  </div> -->
                  <a
                    href="https://www.google.com/maps/search/?api=1&query=Tierp,+Sweden"
                    target="_blank"
                    rel="noopener noreferrer"
                    class="flex items-center"
                  >
                    <MapPin class="h-5 w-5 text-emerald-600 mr-3" />
                    Tierp, Sweden
                  </a>

                </div>
              </div>
  
              <div class="pt-6 mt-8 mb-8 md:mb-0">
                <GetPDF />
              </div>
            </div>
  
            <!-- Right column -->
            <div class="md:w-1/2 flex flex-col">
              <h3 class="text-xl font-semibold mb-4 text-gray-100">Send Me a Message</h3>
              <form @submit.prevent="submitForm" class="space-y-4 flex-grow">
                <div>
                  <label for="name" class="block text-sm font-medium text-gray-300 mb-1">Name</label>
                  <input
                    id="name"
                    v-model="contactForm.name"
                    type="text"
                    class="w-full px-3 py-2 border border-gray-400 rounded-md focus:outline-none focus:ring-2 focus:ring-emerald-500 focus:border-transparent text-gray-200 bg-gray-900"
                    required
                  />
                </div>
                <div>
                  <label for="subject" class="block text-sm font-medium text-gray-300 mb-1">Subject</label>
                  <input
                    id="subject"
                    v-model="contactForm.subject"
                    type="text"
                    class="w-full px-3 py-2 border border-gray-400 rounded-md focus:outline-none focus:ring-2 focus:ring-emerald-500 focus:border-transparent text-gray-200 bg-gray-900"
                    required
                  />
                </div>
                <div>
                  <label for="email" class="block text-sm font-medium text-gray-300 mb-1">Email</label>
                  <input
                    id="email"
                    v-model="contactForm.email"
                    type="email"
                    class="w-full px-3 py-2 border border-gray-400 rounded-md focus:outline-none focus:ring-2 focus:ring-emerald-500 focus:border-transparent text-gray-200 bg-gray-900"
                    required
                  />
                </div>
                <div>
                  <label for="message" class="block text-sm font-medium text-gray-300 mb-1">Message</label>
                  <textarea
                    id="message"
                    v-model="contactForm.message"
                    rows="4"
                    class="w-full px-3 py-2 border border-gray-400 rounded-md focus:outline-none focus:ring-2 focus:ring-emerald-500 focus:border-transparent text-gray-200 bg-gray-900"
                    required
                  ></textarea>
                </div>
                <button
                  type="submit"
                  class="w-full px-4 py-2 bg-emerald-600 text-gray-200 rounded-md hover:bg-emerald-700 transition-colors focus:outline-none focus:ring-2 focus:ring-emerald-500 focus:ring-offset-2"
                >
                  Send Message
                </button>
              </form>
            </div>
  
          </div>
        </div>
      </div>
    </section>
  </template>
  
  

<script setup>
import { ref } from 'vue';
import {Github, Mail, Linkedin, MapPin, } from 'lucide-vue-next';
import GetPDF from './GetPDF.vue';


const contactForm = ref({
  name: '',
  subject: '',
  email: '',
  message: '',
  time: '',
});
//Outlook service - service_bbd0s0d
//Google service - service_pjibhv6
const getCurrentTime = () => {
  const now = new Date();
  const formattedTime = `${now.getFullYear()}/${String(now.getMonth() + 1).padStart(2, '0')}/${String(now.getDate()).padStart(2, '0')} - ${String(now.getHours()).padStart(2, '0')}:${String(now.getMinutes()).padStart(2, '0')}`;
  contactForm.value.time = formattedTime;
};

const submitForm = async () => {
    getCurrentTime();

    const data = {
        service_id: 'service_bbd0s0d',
        template_id: 'template_qu8ubio',
        user_id: 'WTedodCc_3s28HeUh',
        template_params: {
            name: contactForm.value.name,
            email: contactForm.value.email,
            subject: contactForm.value.subject,
            message: contactForm.value.message,
            time: contactForm.value.time
        }
    }
    const resp = await fetch('https://api.emailjs.com/api/v1.0/email/send', {
        method: 'POST',
        headers: {'Content-Type': 'application/json'},
        body: JSON.stringify(data)
    });

    if (!resp.ok){
        const error = await resp.json();
        console.error('Error sending email:', error);
        alert('Failed to send email.');
        return;
    }
    alert('Email sent successfully!');
    contactForm.value = { name: '', subject: '', email: '', message: '', time: '' };
};

</script>