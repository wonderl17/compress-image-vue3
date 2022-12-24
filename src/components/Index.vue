<template>
  <div>
    <header class="navbar navbar-light navbar-expand-md">
      <div class="container">
        <a class="navbar-brand" href="./">Compressor.js</a>
        <button
          class="navbar-toggler"
          type="button"
          data-toggle="collapse"
          data-target="#navbar-collapse"
          aria-controls="navbar-collapse"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div
          class="collapse navbar-collapse justify-content-end"
          id="navbar-collapse"
          role="navigation"
        >
          <ul class="nav navbar-nav">
            <li class="nav-item">
              <a
                class="nav-link"
                href="https://github.com/fengyuanchen/compressorjs/blob/main/README.md"
                >Docs</a
              >
            </li>
            <li class="nav-item dropdown">
              <a
                class="nav-link dropdown-toggle"
                href="#"
                id="navbarDropdownMenuLink"
                role="button"
                data-toggle="dropdown"
                aria-haspopup="true"
                aria-expanded="false"
              >
                Examples
              </a>
              <div
                class="dropdown-menu"
                aria-labelledby="navbarDropdownMenuLink"
              >
                <a class="dropdown-item" href="examples/grayscale.html"
                  >Grayscale</a
                >
                <a class="dropdown-item" href="examples/watermark.html"
                  >Watermark</a
                >
                <a class="dropdown-item" href="examples/work-with-promise.html"
                  >Work with promise</a
                >
              </div>
            </li>
            <li class="nav-item dropdown">
              <a
                class="nav-link"
                href="https://github.com/fengyuanchen/compressorjs"
                title="View the GitHub project"
                >GitHub</a
              >
            </li>
            <li class="nav-item dropdown">
              <a
                class="nav-link"
                href="https://fengyuanchen.github.io/"
                title="Explore more projects"
                >Explore</a
              >
            </li>
            <li class="nav-item dropdown">
              <a
                class="nav-link"
                href="https://chenfengyuan.com/"
                title="About the author"
                >About</a
              >
            </li>
          </ul>
        </div>
      </div>
    </header>

    <div class="jumbotron bg-primary text-white rounded-0">
      <div class="container"></div>
    </div>

    <div class="container">
      <h3>Playground</h3>
      <hr />
      <div id="app" v-cloak>
        <div
          class="card bg-light mb-4"
          @change="change"
          @dragover="dragover"
          @drop="drop"
        >
          <div class="card-body">
            <div class="p-5 text-center">
              Drop image here or
              <label class="text-primary"
                >browse...
                <input
                  type="file"
                  class="sr-only"
                  id="file"
                  accept="image/*"
                  ref="inputRef"
              /></label>
            </div>
          </div>
        </div>
        <div class="row">
          <div class="col-lg-4 mb-4">
            <div class="card h-100">
              <h4 class="card-header">Options</h4>
              <div class="card-body">
                <fieldset class="form-group">
                  <div class="form-check form-check-inline">
                    <input
                      type="checkbox"
                      name="strict"
                      class="form-check-input"
                      id="inputStrict"
                      v-model="options.strict"
                    />
                    <label class="form-check-label" for="inputStrict"
                      >strict</label
                    >
                  </div>
                </fieldset>
                <fieldset class="form-group">
                  <div class="form-check form-check-inline">
                    <input
                      type="checkbox"
                      name="checkOrientation"
                      class="form-check-input"
                      id="inputCheckOrientation"
                      v-model="options.checkOrientation"
                    />
                    <label class="form-check-label" for="inputCheckOrientation"
                      >checkOrientation</label
                    >
                  </div>
                </fieldset>
                <div class="form-group row">
                  <label for="inputMaxWidth" class="col-5 col-form-label"
                    >maxWidth</label
                  >
                  <div class="col-7">
                    <input
                      type="number"
                      name="maxWidth"
                      class="form-control"
                      id="inputMaxWidth"
                      placeholder="Infinity"
                      v-model.number="options.maxWidth"
                    />
                  </div>
                </div>
                <div class="form-group row">
                  <label for="inputMaxHeight" class="col-5 col-form-label"
                    >maxHeight</label
                  >
                  <div class="col-7">
                    <input
                      type="number"
                      name="maxHeight"
                      class="form-control"
                      id="inputMaxHeight"
                      placeholder="Infinity"
                      v-model.number="options.maxHeight"
                    />
                  </div>
                </div>
                <div class="form-group row">
                  <label for="inputMinWidth" class="col-5 col-form-label"
                    >minWidth</label
                  >
                  <div class="col-7">
                    <input
                      type="number"
                      name="minWidth"
                      class="form-control"
                      id="inputMinWidth"
                      placeholder="0"
                      v-model.number="options.minWidth"
                    />
                  </div>
                </div>
                <div class="form-group row">
                  <label for="inputMinHeight" class="col-5 col-form-label"
                    >minHeight</label
                  >
                  <div class="col-7">
                    <input
                      type="number"
                      name="minHeight"
                      class="form-control"
                      id="inputMinHeight"
                      placeholder="0"
                      v-model.number="options.minHeight"
                    />
                  </div>
                </div>
                <div class="form-group row">
                  <label for="inputWidth" class="col-5 col-form-label"
                    >width</label
                  >
                  <div class="col-7">
                    <input
                      type="number"
                      name="width"
                      class="form-control"
                      id="inputWidth"
                      placeholder="undefined"
                      v-model.number="options.width"
                    />
                  </div>
                </div>
                <div class="form-group row">
                  <label for="inputHeight" class="col-5 col-form-label"
                    >height</label
                  >
                  <div class="col-7">
                    <input
                      type="number"
                      name="height"
                      class="form-control"
                      id="inputHeight"
                      placeholder="undefined"
                      v-model.number="options.height"
                    />
                  </div>
                </div>
                <div class="form-group row">
                  <label for="inputResize" class="col-5 col-form-label"
                    >resize</label
                  >
                  <div class="col-7">
                    <select
                      class="form-control"
                      name="resize"
                      id="inputResize"
                      v-model.number="options.resize"
                    >
                      <option value="none">none</option>
                      <option value="contain">contain</option>
                      <option value="cover">cover</option>
                    </select>
                  </div>
                </div>
                <div class="form-group row">
                  <label for="inputQuality" class="col-5 col-form-label"
                    >quality</label
                  >
                  <div class="col-7">
                    <select
                      class="form-control"
                      name="quality"
                      id="inputQuality"
                      v-model.number="options.quality"
                    >
                      <option value="0">0</option>
                      <option value="0.1">0.1</option>
                      <option value="0.2">0.2</option>
                      <option value="0.3">0.3</option>
                      <option value="0.4">0.4</option>
                      <option value="0.5">0.5</option>
                      <option value="0.6">0.6</option>
                      <option value="0.7">0.7</option>
                      <option value="0.8">0.8</option>
                      <option value="0.9">0.9</option>
                      <option value="1">1</option>
                      <option value="">NaN</option>
                    </select>
                  </div>
                </div>
                <div class="form-group row">
                  <label for="inputMimeType" class="col-5 col-form-label"
                    >mimeType</label
                  >
                  <div class="col-7">
                    <input
                      type="text"
                      name="mimeType"
                      class="form-control"
                      id="inputMimeType"
                      placeholder="auto"
                      v-model.number="options.mimeType"
                    />
                  </div>
                </div>
                <div class="form-group row">
                  <label for="inputConvertTypes" class="col-5 col-form-label"
                    >convertTypes</label
                  >
                  <div class="col-7">
                    <input
                      type="text"
                      name="convertTypes"
                      class="form-control"
                      id="inputConvertTypes"
                      placeholder="image/png"
                      v-model="options.convertTypes"
                    />
                  </div>
                </div>
                <div class="form-group row mb-0">
                  <label for="inputConvertSize" class="col-5 col-form-label"
                    >convertSize</label
                  >
                  <div class="col-7">
                    <input
                      type="number"
                      name="convertSize"
                      class="form-control"
                      id="inputConvertSize"
                      placeholder="5000000"
                      v-model.number="options.convertSize"
                    />
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="col-lg-8 mb-4">
            <div class="card mb-4">
              <h5
                class="card-header d-flex align-items-center justify-content-between"
              >
                <span
                  >Input image
                  <small class="text-secondary">(original image)</small></span
                >
                <a
                  class="btn btn-sm btn-blocks btn-outline-primary"
                  :download="input.name"
                  :href="inputURL"
                  title="Download the compressed image"
                  >Download</a
                >
              </h5>
              <div class="card-body">
                <div class="row">
                  <div class="col-md-4 d-flex mb-3">
                    <div class="w-100 text-center" v-if="inputURL">
                      <img class="mw-100" :src="inputURL" :alt="input.name" />
                    </div>
                    <div v-else class="w-100 bg-light"></div>
                  </div>
                  <div class="col-md-8">
                    <dl class="row">
                      <dt class="col-5">lastModified:</dt>
                      <dd class="col-7">{{ input.lastModified || "N/A" }}</dd>
                      <dt class="col-5">lastModifiedDate:</dt>
                      <dd class="col-7">
                        {{ input.lastModifiedDate || "N/A" }}
                      </dd>
                      <dt class="col-5">name:</dt>
                      <dd class="col-7">{{ input.name || "N/A" }}</dd>
                      <dt class="col-5">type:</dt>
                      <dd class="col-7">{{ input.type || "N/A" }}</dd>
                      <dt class="col-5">size:</dt>
                      <dd class="col-7">
                        {{ prettySize(input.size) }}
                      </dd>
                    </dl>
                  </div>
                </div>
              </div>
            </div>
            <div class="card">
              <h5
                class="card-header d-flex align-items-center justify-content-between"
              >
                <span
                  >Output image
                  <small class="text-secondary">(compressed image)</small></span
                >
                <a
                  class="btn btn-sm btn-blocks btn-outline-primary"
                  :download="output.name"
                  :href="outputURL"
                  title="Download the compressed image"
                  >Download</a
                >
              </h5>
              <div class="card-body">
                <div class="row">
                  <div class="col-md-4 d-flex mb-3">
                    <div class="w-100 text-center" v-if="outputURL">
                      <img class="mw-100" :src="outputURL" :alt="output.name" />
                    </div>
                    <div v-else class="w-100 bg-light"></div>
                  </div>
                  <div class="col-md-8">
                    <dl class="row">
                      <dt class="col-5">lastModified:</dt>
                      <dd class="col-7">{{ output.lastModified || "N/A" }}</dd>
                      <dt class="col-5">lastModifiedDate:</dt>
                      <dd class="col-7">
                        {{ output.lastModifiedDate || "N/A" }}
                      </dd>
                      <dt class="col-5">name:</dt>
                      <dd class="col-7">{{ output.name || "N/A" }}</dd>
                      <dt class="col-5">type:</dt>
                      <dd class="col-7">{{ output.type || "N/A" }}</dd>
                      <dt class="col-5">size:</dt>
                      <dd class="col-7">
                        {{ prettySize(output.size) }}
                        <span v-if="output.size && input.size"
                          >({{
                            ((1 - output.size / input.size) * 100).toFixed(2)
                          }}% off)</span
                        >
                      </dd>
                    </dl>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="card" v-if="inputURL && outputURL">
          <h4 class="card-header">Comparing images</h4>
          <div class="card-body">
            <vue-compare-image
              v-if="inputURL && outputURL"
              :left-image="inputURL"
              :left-image-alt="input.name"
              left-label="Input image"
              :right-image="outputURL"
              :right-image-alt="output.name"
              right-label="Output image"
            ></vue-compare-image>
          </div>
        </div>
      </div>
    </div>

    <footer class="footer">
      <div class="container">
        <p class="heart"></p>
        <nav class="nav flex-wrap justify-content-center mb-3">
          <a class="nav-link">GitHub</a>
          <a class="nav-link">Releases</a>
          <a class="nav-link">License</a>
        </nav>
      </div>
    </footer>
  </div>
</template>

<script lang="ts" setup>
import { onMounted, ref, watch } from "vue";
import Compressor from "compressorjs";
import VueCompareImage from "./CompareImage.vue";

const options = ref<Compressor.Options>({
  strict: true,
  checkOrientation: true,
  maxWidth: undefined,
  maxHeight: undefined,
  minWidth: 0,
  minHeight: 0,
  width: undefined,
  height: undefined,
  resize: "none",
  quality: 0.8,
  mimeType: "",
  convertTypes: "image/png",
  convertSize: 5000000,
  success: function (result: any) {
    console.log("Output: ", result);

    if (URL) {
      outputURL.value = URL.createObjectURL(result);
    }

    output.value = result;
    inputRef.value && (inputRef.value.value = "");
  },
  error: function (err: any) {
    window.alert(err.message);
  },
});

const inputURL = ref("");
const outputURL = ref("");
const inputRef = ref<HTMLInputElement>();
const input = ref<{
  size?: number;
  lastModified?: any;
  lastModifiedDate?: any;
  name?: string;
  type?: any;
}>({});
const output = ref<{
  size?: number;
  lastModified?: any;
  lastModifiedDate?: any;
  name?: string;
  type?: any;
}>({});

const prettySize = function (size?: number) {
  if (size == undefined) return "N/A";

  var kilobyte = 1024;
  var megabyte = kilobyte * kilobyte;

  if (size > megabyte) {
    return (size / megabyte).toFixed(2) + " MB";
  } else if (size > kilobyte) {
    return (size / kilobyte).toFixed(2) + " KB";
  } else if (size >= 0) {
    return size + " B";
  }

  return "N/A";
};

const compress = function (file: any) {
  if (!file) {
    return;
  }

  console.log("Input: ", file);

  if (URL) {
    inputURL.value = URL.createObjectURL(file);
  }

  input.value = file;
  new Compressor(file, options.value);
};

const change = function (e: any) {
  compress(e.target.files ? e.target.files[0] : null);
};

const dragover = function (e: any) {
  e.preventDefault();
};

const drop = function (e: any) {
  e.preventDefault();
  compress(e.dataTransfer.files ? e.dataTransfer.files[0] : null);
};

watch(
  options,
  () => {
    compress(input.value);
  },
  { deep: true }
);

onMounted(() => {
  if (!XMLHttpRequest) {
    return;
  }

  var xhr = new XMLHttpRequest();

  xhr.onload = function () {
    var blob = xhr.response;
    var date = new Date();

    blob.lastModified = date.getTime();
    blob.lastModifiedDate = date;
    blob.name = "picture.jpg";
    compress(blob);
  };
  xhr.open("GET", "images/picture.jpg");
  xhr.responseType = "blob";
  xhr.send();
});
</script>

<style lang="scss" scoped>
@import "../assets/main.css";
</style>
