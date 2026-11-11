<template>
  <!-- Landing Section START -->
  <section class="container-fluid" id="landing">
    <div
      class="row py-5 px-5 justify-content-between flex-md-row-reverse align-items-center g-3 position">
      <!-- img div -->
      <div
        class="col-12 col-md-6 col-lg-6 col-xl-4 p-3 bg-white rounded-3 shadow position-relative">
        <img class="img-fluid rounded-3" src="/images/my_pic.jpg" />

        <!-- Floating Div -->
        <div
          class="position-absolute bottom-0 start-50 translate-middle-x mb-5 w-75 bg-white rounded-3 shadow-sm border d-flex justify-content-between align-items-center px-3 py-2"
          id="floating-div-img">
          <span>Malolos, Bulacan &bull; Remote Available</span>

          <!-- Green Icon Badge -->
          <div
            class="rounded-circle d-flex justify-content-center align-items-center">
            <span><i class="fa-solid fa-map-pin"></i></span>
          </div>
        </div>
        <!-- Floating Div END -->
      </div>
      <!-- content -->
      <div class="col-12 col-md-6 col-lg-6">
        <div
          class="available p-2 d-inline-flex justify-content-center align-items-center">
          <span class="bullet-p"></span>
          <p>AVAILABLE FOR NEW ROLES & PROJECTS</p>
        </div>
        <h1 class="mt-3 hero-name">Matthew Antonio B. Bulaong</h1>
        <h2 class="mt-3">Full Stack Web Developer</h2>
        <p class="mt-4">
          Hey! Computer Engineering graduate here hoping to be an IT
          professional. Check out my latest projects below.
        </p>
        <p>I try to do my best to create things with love. &#x2764;&#xfe0f;</p>

        <div class="d-flex align-items-center gap-2 mb-3">
          <div
            class="d-flex flex-column gap-1 align-items-center card-landing p-2 p-lg-3">
            <span><i class="fa-solid fa-code"></i></span>
            <p>Frontend</p>
          </div>

          <div
            class="d-flex flex-column gap-1 align-items-center card-landing p-2 p-lg-3">
            <span>{ }</span>
            <p>Backend</p>
          </div>

          <div
            class="d-flex flex-column gap-1 align-items-center card-landing p-2 p-lg-3">
            <span><i class="fa-solid fa-database"></i></span>
            <p>Database</p>
          </div>
        </div>

        <a
          href="#projects"
          id="btn-landing"
          class="text-decoration-none d-inline-flex justify-content-center align-items-center py-auto"
          >VIEW PROJECTS ↓</a
        >
      </div>
    </div>
  </section>
  <!-- Landing section END -->
</template>
