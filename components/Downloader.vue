<template>
  <div class="live-downloader py-5">
    <form class="form-inline justify-content-center">
      <div class="form-group mr-md-5 mb-4 mb-sm-2">
        <label for="inputOS" class="mr-3 text-uppercase font-weight-bold">OS</label>
        <select id="inputOS" class="form-control" v-model="os">
          <option selected>Choose...</option>
          <option value="mac">macOS</option>
          <option value="win">Windows</option>
        </select>
      </div>
      <div class="form-group mr-md-5 mb-4 mb-sm-2">
        <label for="inputVersion" class="mr-3 text-uppercase font-weight-bold">Version</label>
        <select id="inputVersion" class="form-control" v-model="version">
          <option selected>Choose...</option>
          <option v-for="version in versions" :key="version.id">{{ version }}</option>
        </select>
      </div>
      <div class="form-group mr-md-5 mb-3 mb-sm-2">
        <label for="inputEdition" class="mr-3 text-uppercase font-weight-bold">Edition</label>
        <select id="inputEdition" class="form-control" v-model="edition">
          <option selected>Choose...</option>
          <option value="suite">Suite</option>
          <option value="standard">Standard</option>
          <option value="intro">Intro</option>
          <option value="trial">Trial</option>
        </select>
      </div>
      <button type="submit" class="btn btn-light text-uppercase font-weight-bold mt-3 mt-md-0 mb-2" v-on:click="download">Download</button>
    </form>
  </div>
</template>

<script>
import VersionDropdown from '~/components/VersionDropdown.vue'

export default {
  components: {
    VersionDropdown
  },
  data() {
    return {
      // Example path:
      // https://cdn-downloads.ableton.com/channels/10.0.6/ableton_live_suite_10.0.6_64.dmg

      cdn_path: 'https://cdn-downloads.ableton.com/channels/',
      versions: [
        // Future version numbers for when they release
        // '10.2',
        // '10.1.5',
        // '10.1.4',
        // '10.1.3',
        // '10.1.2',
        // '10.1.1',
        '10.1',
        '10.0.6',
        '10.0.5',
        '10.0.4',
        '10.0.3',
        '10.0.2',
        '10.0.1',
        '10.0',
        '9.7.7',
        '9.7.6',
        '9.7.5',
        '9.7.4',
        '9.7.3',
        '9.7.2',
        '9.7.1',
        '9.7',
        '9.6.2',
        '9.6.1',
        '9.6',
        '9.5',
        '9.2.3',
        '9.2.2',
        '9.2.1',
        '9.2',
        '9.1.10',
        '9.1.9',
        '9.1.8',
        '9.1.7',
        '9.1.6',
        '9.1.5',
        '9.1.4',
        '9.1.3',
        '9.1.2',
        '9.1',
        '9.0.6',
        '9.0.5',
        '9.0.4',
        '9.0.3',
        '9.0.2',
        '9.0.1',
      ],
      os: 'Choose...',
      edition: 'Choose...',
      version: 'Choose...',
    }
  },
  methods: {
    download: function (event) {
      event.preventDefault();
      let url = this.cdn_path;

      if(this.os == 'Choose...' || this.edition == 'Choose...' || this.version == 'Choose...') {
        alert('Please choose an option from each dropdown menu.');
      } else {
        url += this.version + '/ableton_live_suite_' + this.version;

        if (this.os === 'mac') {
          url += '_64.dmg';
        } else {
          url += '_64.zip';
        }
        window.open(url);
        console.log('Download Path' + url);
      }
    }
  }
}
</script>


<style>
.form-group {
  position: relative;
}

.form-group::after {
  content: '';
  position: absolute;
  right: 10px;
  width: 12px;
  height: 8px;
  border-style: solid;
  border-width: 8px 6px 0 6px;
  border-color: #ffffff transparent transparent transparent;
  pointer-events: none;
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
  .form-group:after {
    bottom: 17px;
  }
  .btn {
    width: 100%;
  }
  .form-inline .form-group {
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
  .form-group {
    /* background: red; */
    width: 280px;
    margin: 0 auto;

  }
  .form-group label {
    width: 100px;
  }
  .form-control {
    min-width: 160px;
  }
}
</style>

