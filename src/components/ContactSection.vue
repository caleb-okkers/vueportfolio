<template>
    <div class="container">
        <div class="row pt-5">
            <h2 class="contact-heading headings">Contact</h2>
            <p class="pt-5">"Awaiting first contact..."</p>
        </div>

        <div class="row">
            <div class="col">
                <div class="spline-contact">

                    
                    <iframe src='https://my.spline.design/cybermannequin-013efb57449009f300fec795056b9482/' frameborder='0' width='100%' height='100%'></iframe>
                </div>
            </div>
            <div class="col">
                <div class="form-div container pb-5">
                            <form class="mt-5" action="https://formspree.io/f/mzzpbkpy" method="POST">
                                <div class="contact-label-div mb-3">
                                    <label for="name" class="form-label contact-label">Name</label>
                                    <input type="text" class="form-control" id="name" placeholder="Enter your name"
                                        name="name" required>
                                </div>
                                <div class="contact-label-div mb-3">
                                    <label for="email" class="form-label contact-label">Email address</label>
                                    <input type="email" class="form-control contact-form" id="email" placeholder="name@example.com"
                                        name="email" required>
                                </div>
                                <div class="contact-label-div mb-3">
                                    <label for="message" class="form-label contact-label">Message</label>
                                    <textarea class="form-control" id="message" rows="5"
                                        placeholder="Enter your message" name="message" required></textarea>
                                </div>
                                <button type="submit" class="btn custom-submit-button btn-outline-success"><span>Submit</span></button>
                            </form>
                        </div>
                        <div class="more">
                    <p>Reach out via...</p>
                </div>

                <div class="socials">
                    <a id="profile-link" href="https://github.com/caleb-okkers" target="_blank" class="btn contact-details">
                        <i class="fab fa-github fa-2xl"></i>
                         GitHub
                    </a>

                    <a id="profile-link" href="https://www.linkedin.com/in/caleb-okkers-43b100287" target="_blank" class="btn contact-details">
                        <i class="fab fa-linkedin fa-2xl"></i>
                         LinkedIn
                    </a>
                </div>
            </div>
        </div>

        
        <div class="content">
            
            
        </div>
    </div>
</template>

<script>
export default {
    name: "ContactSection"

}


</script>

<style scoped>
  .contact-heading {
  color: #fff;
  text-shadow: 2px 2px 4px #000, 5px 5px 70px cyan;
}

.contact-video {
    position: fixed;
    width: 30%;
    height: 30%;
    object-fit: cover;
    z-index: -1;
    transform: translateZ(-1px) scale(2);
}

iframe {
    width: 600px;
    height: 600px;
}

.form-div {
    width: 600px;
    height: 450px;
}

@media (max-width:475px) {

    iframe {
        width: 300px;
        height: 300px
    }

    .form-div {
        width: 100% !important;
        margin: 0 12px;
        padding-left: 0px ;
    }

    .spline-contact {
        width: 100% !important;
        padding-right: 12px;
        
    }

    .socials {
        padding-bottom: 1rem;
    }
}

</style>