<template>
  <div class="live-downloader py-5 mb-5 sm:mb-10 px-3">
    <form class="sm:flex justify-center">
      <!-- Select: OS -->
      <div class="select-wrapper md:mr-10 mb-4 sm:mb-0">
        <label for="inputOS" class="mr-3 mb-2 sm:mb-0 text-uppercase font-bold"
          >OS</label
        >
        <select id="inputOS" class="form-control" v-model="os">
          <option selected>Choose...</option>
          <option value="mac">macOS</option>
          <option value="win">Windows</option>
        </select>
      </div>

      <!-- Select: Version -->
      <div class="select-wrapper md:mr-10 mb-4 sm:mb-0">
        <label
          for="inputVersion"
          class="mr-3 mb-2 sm:mb-0 text-uppercase font-bold"
          >Version</label
        >
        <select id="inputVersion" class="form-control" v-model="version">
          <option selected>Choose...</option>
          <option v-for="version in versions" :key="version.id">{{
            version
          }}</option>
        </select>
      </div>

      <!-- Select: Edition -->
      <div class="select-wrapper md:mr-10 mb-5 sm:mb-0">
        <label
          for="inputEdition"
          class="mr-3 mb-2 sm:mb-0 text-uppercase font-bold"
          >Edition</label
        >
        <select id="inputEdition" class="form-control" v-model="edition">
          <option selected>Choose...</option>
          <option value="suite">Suite</option>
          <option value="standard">Standard</option>
          <option value="intro">Intro</option>
          <option value="trial">Trial</option>
        </select>
      </div>

      <button
        type="submit"
        class="btn bg-white text-black hover:opacity-75 transition-color duration-200 uppercase px-3 py-3 sm:py-0 font-bold mt-3 md:mt-0"
        @click.prevent="download"
      >
        Download
      </button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // Example path:
      // https://cdn-downloads.ableton.com/channels/10.0.6/ableton_live_suite_10.0.6_64.dmg

      cdn_path: "https://cdn-downloads.ableton.com/channels/",
      versions: [
        // Future version numbers for when they release

        // "11.1.1",
        "11.1",
        "11.0.12",
        "11.0.11",
        "11.0.10",
        "11.0.6",
        "11.0.5",
        "11.0.2",
        "11.0.1",
        "11.0",
        "10.1.30",
        "10.1.25",
        "10.1.18",
        "10.1.17",
        "10.1.15",
        "10.1.14",
        "10.1.13",
        "10.1.9",
        "10.1.7",
        "10.1.6",
        "10.1.5",
        "10.1.4",
        "10.1.3",
        "10.1.2",
        "10.1.1",
        "10.1",
        "10.0.6",
        "10.0.5",
        "10.0.4",
        "10.0.3",
        "10.0.2",
        "10.0.1",
        "10.0",
        "9.7.7",
        "9.7.6",
        "9.7.5",
        "9.7.4",
        "9.7.3",
        "9.7.2",
        "9.7.1",
        "9.7",
        "9.6.2",
        "9.6.1",
        "9.6",
        "9.5",
        "9.2.3",
        "9.2.2",
        "9.2.1",
        "9.2",
        "9.1.10",
        "9.1.9",
        "9.1.8",
        "9.1.7",
        "9.1.6",
        "9.1.5",
        "9.1.4",
        "9.1.3",
        "9.1.2",
        "9.1",
        "9.0.6",
        "9.0.5",
        "9.0.4",
        "9.0.3",
        "9.0.2",
        "9.0.1"
      ],
      os: "Choose...",
      edition: "Choose...",
      version: "Choose..."
    };
  },

  methods: {
    download: function() {
      let url = this.cdn_path;

      if (
        this.os == "Choose..." ||
        this.edition == "Choose..." ||
        this.version == "Choose..."
      ) {
        alert("Please choose an option from each dropdown menu.");
      } else {
        url += this.version + "/ableton_live_suite_" + this.version;

        if (this.os === "mac") {
          url += "_64.dmg";
        } else {
          url += "_64.zip";
        }

        window.open(url);
      }
    }
  }
};
</script>

<style>
.select-wrapper {
  position: relative;
  display: flex;
  align-items: center;
}

.select-wrapper::after {
  content: "";
  position: absolute;
  right: 10px;
  width: 12px;
  height: 8px;
  border-style: solid;
  border-width: 8px 6px 0 6px;
  border-color: #ffffff transparent transparent transparent;
  pointer-events: none;
}

select {
  padding: 5px;
}

.form-control,
.form-control:focus {
  outline: 0;
  border: 2px solid white;
  background: black;
  color: white;
  border-radius: 0;
  font-weight: bold;
  -webkit-appearance: none;
  text-align: left;
  min-width: 130px;
}

@media screen and (max-width: 575px) {
  .select-wrapper {
    flex-direction: column;
  }
  .select-wrapper:after {
    bottom: 17px;
  }
  .btn,
  .form-control {
    width: 100%;
  }
  form .select-wrapper {
    width: 100%;
  }
}

@media screen and (max-width: 768px) {
  .form-inline {
    display: block;
  }
  .form-group:after {
    right: 13px;
  }
  .select-wrapper {
    /* background: red; */
    width: 280px;
  }
  .select-wrapper label {
    width: 100px;
  }
  .form-control {
    min-width: 160px;
  }
}
</style>
