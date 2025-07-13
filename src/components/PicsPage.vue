<template>
  <div class="pics-page">
    <div class="years-bar">
      <div
        v-for="year in years"
        :key="year"
        :class="{ active: year === selectedYear }"
        class="year"
        @click="selectYear(year)"
      >
        {{ year }}
      </div>
      <div class="bar-highlight" :style="highlightStyle"></div>
    </div>

    <div class="pics-gallery">
      <div v-for="photo in getPhotosForYear(selectedYear)" :key="photo.url" class="photo-item">
        <div class="photo-wrapper">
          <div class="photo-card" :style="{ backgroundImage: 'url(' + photo.url + ')' }" @click="openPhotoDetails(photo)">
            <div class="photo-overlay">
              <div class="photo-details" v-if="photo.showDetails">
                <div class="description">{{ photo.description }}</div>
                <div class="actions">
                  <button class="like-button" @click="likePhoto(photo)">
                    Like <span class="like-count">{{ photo.likes }}</span>
                  </button>
                  <button class="open-button" @click="openPhoto(photo)">
                    Open
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      years: ["Projects"],
      selectedYear: "Projects",
      images: [
        
        {
          year: "Projects",
          photos: [
            {
              url: "https://media.discordapp.net/attachments/971299427715272734/1393974907175567501/Screenshot_2025-07-13_203935.png?ex=68751fcc&is=6873ce4c&hm=5fe5f242bd6830c1bfdb959d9159b955488d510cc2281182b2e1751665fd3af5&=&format=webp&quality=lossless&width=762&height=678",
              description: "Automatic luminance based solar tracker for equatorial solar energy. 2019 Summer of Arduino Project.",
              showDetails: false,
              likes: 0,
              link: "https://drive.google.com/file/d/1ptoib5G9sd63z1UmxJmcXGFMj4IkVrQQ/view?usp=drive_link"
            },
            {
              url: "https://media.discordapp.net/attachments/971299427715272734/1116384004371927201/Screenshot_from_2023-06-08_20-40-11.png?width=430&height=341",
              description: "",
              showDetails: false,
              likes: 30,
              link: "https://drive.google.com/file/d/1ptoib5G9sd63z1UmxJmcXGFMj4IkVrQQ/view?usp=sharing"
            },
            
            {
              url: "https://media.discordapp.net/attachments/971299427715272734/1393974907443871825/Screenshot_2025-07-13_204032.png?ex=68751fcc&is=6873ce4c&hm=0a7845fa2f91f78cbca09b0ebf587e162f2d66cca170dc8726fcd114d2cc0358&=&format=webp&quality=lossless&width=845&height=689",
              description: "SOAR Config, 2019 Noktoberfest Hackathon",
              showDetails: false,
              likes: 0,
              link: "https://drive.google.com/file/d/11NLwSjfZLaE2gRKfj_wzKSX_5V37oeOu/view?usp=sharing"
            },
            {
              url: "https://media.discordapp.net/attachments/971299427715272734/1393974907712569526/Screenshot_2025-07-13_204055.png?ex=68751fcc&is=6873ce4c&hm=b0dd51b6acfdf7a112ab1105a4448c02be2dfbc55c96210d6cca6724e3432276&=&format=webp&quality=lossless&width=987&height=590",
              description: "My attempt to simulate the working of an avionics compt. The JFHET part failed misrable but the IRNK part worked well.",
              showDetails: false,
              likes: 0,
              link: "https://drive.google.com/file/d/1p6Us2HnEsUKvkRXTM8k_7UWY56LR43sL/view?usp=sharing"
            },
            {
              url: "https://media.discordapp.net/attachments/971299427715272734/1393974908500836482/Screenshot_2025-07-13_204736.png?ex=68751fcc&is=6873ce4c&hm=c22cbe831417b1ab8b014fcd002fb86582a4d0ccaa1bda811cc64a93ebddc529&=&format=webp&quality=lossless&width=1227&height=689",
              description: "A nueral network built by me before chatgpt was made pulbic using a variety of APIs.",
              showDetails: false,
              likes: 0,
              link: "https://drive.google.com/file/d/18Th6fXLP8RckZ1gkVicsZmGMzbakKMob/view?usp=sharing"
            },
            {
              url: "https://media.discordapp.net/attachments/971299427715272734/1393978486795931699/1719080973957.jpg?ex=68752322&is=6873d1a2&hm=2fbce1815dbdebc570ca3fa2a5d4971bcea98b42ad689eacabdc6da240f2fba4&=&format=webp&width=1224&height=689",
              description: "Me after Cascade EMR Prototype got selected in T hub one day before maths board exam",
              showDetails: false,
              likes: 0,
              link: "https://drive.google.com/file/d/1wYnnbtpc7E_nhoiSmxCAInAkBI6neLz7/view?usp=sharing"
            },            
          ]
        },
          ]
        },
      ],
      highlightPosition: 0,
    };
  },
  computed: {
    highlightStyle() {
      return {
        transform: `translateX(${this.highlightPosition}px)`,
      };
    },
  },
  methods: {
    selectYear(year) {
      this.selectedYear = year;
      this.highlightPosition = this.getYearOffset(year);
    },
    getPhotosForYear(year) {
      const yearData = this.images.find((image) => image.year === year);
      return yearData ? yearData.photos : [];
    },
    openPhotoDetails(photo) {
      photo.showDetails = !photo.showDetails;
    },
    likePhoto(photo) {
      photo.likes += 1;
    },
    openPhoto(photo) {
      window.open(photo.link, "_blank");
    },
    getYearOffset(year) {
      const index = this.years.indexOf(year);
      if (index !== -1) {
        const yearWidth = 60; // Adjust the width of each year item
        const yearSpacing = 10; // Adjust the spacing between each year item
        return index * (yearWidth + yearSpacing);
      }
      return 0;
    },
  },
};
</script>

<style scoped>
.pics-page {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%;
  background-color: transparent;
}

.years-bar {
  display: flex;
  align-items: center;
  position: relative;
  margin-bottom: 20px;
}

.year {
  cursor: pointer;
  font-size: 16px;
  margin: 0 5px;
  padding: 5px 10px;
  color: #ffffff;
  background-color: rgba(255, 255, 255, 0.1);
  border-radius: 20px;
  transition: all 0.3s ease;
}

.year.active {
  background-color: #ffffff;
  color: #111111;
}

.bar-highlight {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 60px; /* Adjust the width of each year item */
  height: 3px;
  background-color: transparent; /* Update this line to match the background color of the years bar */
  border-radius: 5px;
  transition: transform 0.3s ease;
}

.pics-gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  grid-gap: 30px;
  max-width: 800px;
  margin-top: 20px;
}

@media (max-width: 600px) {
  .pics-gallery {
    grid-template-columns: 1fr; /* Display a single column in mobile mode */
    grid-gap: 20px; /* Adjust the gap value as desired */
  }
}


.photo-item {
  position: relative;
}

.photo-wrapper {
  overflow: hidden;
  border-radius: 20px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
  transition: transform 0.3s ease;
  width: 240px; /* Adjust the width as desired */
  height: 240px; /* Adjust the height as desired */
}

.photo-wrapper:hover {
  transform: translateY(-5px);
}

.photo-card {
  position: relative;
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  border-radius: 20px;
  overflow: hidden;
}

.photo-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  opacity: 0;
  transition: opacity 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
}

.photo-overlay:hover {
  opacity: 1;
}

.photo-details {
  text-align: center;
}

.description {
  margin-bottom: 10px;
}

.actions {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin-top: 10px;
}

.like-button,
.open-button {
  padding: 5px 10px;
  background-color: rgba(255, 255, 255, 0.2);
  color: #ffffff;
  border: none;
  border-radius: 20px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.like-button:hover,
.open-button:hover {
  background-color: rgba(255, 255, 255, 0.3);
}

.like-count {
  font-weight: bold;
  margin-left: 5px;
}
</style>
