<template>
  <div id="app">
    <div class="container mx-auto">
      <div class="bg-white p-12 my-10 relative">
        <div
          class="icon bg-blue-600 text-white w-6 h-6 absolute flex items-center justify-center p-5"
          style="left:-40px"
        >
          <i
            class="fal fa-phone-volume fa-fw text-2xl transform -rotate-45"
          ></i>
        </div>
        <h3 class="text-2xl text-gray-900 font-semibold">
          CURL Command Builder
        </h3>
        <p class="text-gray-600">Simple thing, but this we always forget :p</p>

        <div class="grid grid-cols-1 py-4">
          <div class="flex flex-wrap -mx-3">
            <div class="w-full md:w-3/4 px-3 md:mb-0">
              <div class="md:flex md:items-center">
                <input
                  type="text"
                  name=""
                  id=""
                  placeholder="URL"
                  v-model="url"
                  @change="buildCommand"
                  class="border p-2 w-full mt-3"
                />
              </div>
            </div>
            <div class="w-full md:w-1/4 px-3 md:mb-0">
              <div class="md:flex md:items-center">
                <select
                  class="block appearance-none w-full bg-white border p-2 w-full mt-3"
                  v-model="http_method"
                  @change="buildCommand"
                >
                  <option value="">-- HTTP METHOD --</option>
                  <option value="GET">GET</option>
                  <option value="POST">POST</option>
                  <option value="PUT">PUT</option>
                  <option value="DELETE">DELETE</option>
                  <option value="PATCH">PATCH</option>
                </select>
              </div>
            </div>
          </div>
        </div>

        <div class="grid border p-4 grid-cols-1 py-4">
          <div class="flex flex-wrap -mx-3">
            <div class="w-full md:w-1/4 px-3 mb-6 md:mb-0">
              <div class="md:flex md:items-center mb-6">
                <label class="custom-label flex block font-bold">
                  <div
                    class="bg-white shadow w-6 h-6 p-1 flex justify-center items-center mr-2"
                  >
                    <input
                      type="checkbox"
                      class="hidden"
                      v-model="is_application_json"
                      @change="buildCommand"
                    />
                    <svg
                      class="hidden w-4 h-4 text-green-600 pointer-events-none"
                      viewBox="0 0 172 172"
                    >
                      <g
                        fill="none"
                        stroke-width="none"
                        stroke-miterlimit="10"
                        font-family="none"
                        font-weight="none"
                        font-size="none"
                        text-anchor="none"
                        style="mix-blend-mode:normal"
                      >
                        <path d="M0 172V0h172v172z" />
                        <path
                          d="M145.433 37.933L64.5 118.8658 33.7337 88.0996l-10.134 10.1341L64.5 139.1341l91.067-91.067z"
                          fill="currentColor"
                          stroke-width="1"
                        />
                      </g>
                    </svg>
                  </div>
                  <span class="select-none"> application/json</span>
                </label>
              </div>
            </div>
            <div class="w-full md:w-1/4 px-3 mb-6 md:mb-0">
              <div class="md:flex md:items-center mb-6">
                <label class="custom-label flex block font-bold">
                  <div
                    class="bg-white shadow w-6 h-6 p-1 flex justify-center items-center mr-2"
                  >
                    <input
                      type="checkbox"
                      class="hidden"
                      v-model="is_accept_self_signed_certs"
                      @change="buildCommand"
                    />
                    <svg
                      class="hidden w-4 h-4 text-green-600 pointer-events-none"
                      viewBox="0 0 172 172"
                    >
                      <g
                        fill="none"
                        stroke-width="none"
                        stroke-miterlimit="10"
                        font-family="none"
                        font-weight="none"
                        font-size="none"
                        text-anchor="none"
                        style="mix-blend-mode:normal"
                      >
                        <path d="M0 172V0h172v172z" />
                        <path
                          d="M145.433 37.933L64.5 118.8658 33.7337 88.0996l-10.134 10.1341L64.5 139.1341l91.067-91.067z"
                          fill="currentColor"
                          stroke-width="1"
                        />
                      </g>
                    </svg>
                  </div>
                  <span class="select-none"> accept self-signed certs</span>
                </label>
              </div>
            </div>
            <div class="w-full md:w-1/4 px-3 mb-6 md:mb-0">
              <div class="md:flex md:items-center mb-6">
                <label class="custom-label flex block font-bold">
                  <div
                    class="bg-white shadow w-6 h-6 p-1 flex justify-center items-center mr-2"
                  >
                    <input
                      type="checkbox"
                      class="hidden"
                      v-model="is_verbose"
                      @change="buildCommand"
                    />
                    <svg
                      class="hidden w-4 h-4 text-green-600 pointer-events-none"
                      viewBox="0 0 172 172"
                    >
                      <g
                        fill="none"
                        stroke-width="none"
                        stroke-miterlimit="10"
                        font-family="none"
                        font-weight="none"
                        font-size="none"
                        text-anchor="none"
                        style="mix-blend-mode:normal"
                      >
                        <path d="M0 172V0h172v172z" />
                        <path
                          d="M145.433 37.933L64.5 118.8658 33.7337 88.0996l-10.134 10.1341L64.5 139.1341l91.067-91.067z"
                          fill="currentColor"
                          stroke-width="1"
                        />
                      </g>
                    </svg>
                  </div>
                  <span class="select-none"> verbose</span>
                </label>
              </div>
            </div>
            <div class="w-full md:w-1/4 px-3 mb-6 md:mb-0">
              <div class="md:flex md:items-center mb-6">
                <button
                  @click="addCustomHeader"
                  class="bg-transparent small hover:bg-blue-500 text-blue-700 font-semibold hover:text-white py-2 px-4 border border-blue-500 hover:border-transparent rounded"
                >
                  + Add Custom Header
                </button>
              </div>
            </div>
          </div>
          <div>
            <div v-for="(header, i) in custom_headers" :key="i">
              <div class="flex flex-wrap -mx-3 mb-6">
                <div class="w-full md:w-2/6 px-3 mb-6 md:mb-0">
                  <input
                    class="border p-2 w-full"
                    id="grid-first-name"
                    type="text"
                    placeholder="Key"
                    v-model="header.key"
                    @change="buildCommand"
                  />
                </div>
                <div class="w-full md:w-3/6 px-3">
                  <input
                    class="border p-2 w-full"
                    id="grid-last-name"
                    type="text"
                    placeholder="Value"
                    v-model="header.value"
                    @change="buildCommand"
                  />
                </div>
                <div class="w-full md:w-1/6 px-3">
                  <button
                    @click="removeCustomHeader(i)"
                    class="bg-transparent hover:bg-red-500 text-red-700 font-semibold hover:text-white py-2 px-4 border border-red-500 hover:border-transparent rounded"
                  >
                    X
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="grid border p-4 grid-cols-1 mt-4">
          <div class="flex flex-wrap">
            <div class="w-full md:w-1/4">
              <div class="md:flex md:items-center">
                <select
                  class="block appearance-none w-full bg-white border p-2 w-full"
                  v-model="body_type"
                  @change="resetCustomFields"
                >
                  <option value="">-- BODY --</option>
                  <option value="json">JSON</option>
                  <option value="form_data">FORM DATA</option>
                  <option value="form_urlencoded">FORM URLENCODED</option>
                </select>
              </div>
            </div>
            <div
              class="w-full md:w-1/4 px-3"
              v-if="body_type != 'json' && body_type != ''"
            >
              <div class="md:flex md:items-center">
                <button
                  @click="addCustomField"
                  class="bg-transparent small hover:bg-blue-500 text-blue-700 font-semibold hover:text-white py-2 px-4 border border-blue-500 hover:border-transparent rounded"
                >
                  + Add Custom Field
                </button>
              </div>
            </div>
          </div>
          <div v-if="body_type != 'json' && body_type != ''">
            <div v-for="(header, i) in custom_fields" :key="i">
              <div class="flex flex-wrap -mx-3 mb-6 mt-6">
                <div class="w-full md:w-2/6 px-3 mb-6 md:mb-0">
                  <input
                    class="border p-2 w-full"
                    id="grid-first-name"
                    type="text"
                    placeholder="Key"
                    v-model="header.key"
                    @change="buildCommand"
                  />
                </div>
                <div class="w-full md:w-3/6 px-3">
                  <input
                    class="border p-2 w-full"
                    id="grid-last-name"
                    type="text"
                    placeholder="Value"
                    v-model="header.value"
                    @change="buildCommand"
                  />
                </div>
                <div class="w-full md:w-1/6 px-3">
                  <button
                    @click="removeCustomField(i)"
                    class="bg-transparent hover:bg-red-500 text-red-700 font-semibold hover:text-white py-2 px-4 border border-red-500 hover:border-transparent rounded"
                  >
                    X
                  </button>
                </div>
              </div>
            </div>
          </div>
          <div v-if="body_type == 'json' && body_type != ''">
            <textarea
              name=""
              id=""
              cols="10"
              rows="10"
              placeholder="JSON body here"
              class="border p-2 mt-3 w-full"
              v-model="json_body"
              @change="syntaxHighlight"
            ></textarea>
            <div
              class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded relative"
              role="alert"
              v-if="!is_json_valid"
            >
              <strong class="font-bold">Ooopss! Invalid json format.</strong>
            </div>
          </div>
        </div>
        <textarea
          name=""
          cols="10"
          rows="3"
          readonly="true"
          placeholder="Your curl command here"
          class="border p-2 mt-3 w-full"
          v-model="curl_command_text"
          id="curl_command_text"
        ></textarea>
        <button
          @click="copyCurlCommand"
          class="bg-transparent w-full small hover:bg-blue-500 text-blue-700 font-semibold hover:text-white py-2 px-4 border border-blue-500 hover:border-transparent rounded"
        >
          Copy Curl Command
        </button>
      </div>
    </div>
    <footer
      class="w-full text-center p-4 pin-b"
      style="vertical-align: middle; display: inline-block;"
    >
      Made with
      <span style="vertical-align: middle; display: inline-block;"
        ><svg
          xmlns="http://www.w3.org/2000/svg"
          width="24"
          height="24"
          viewBox="0 0 24 24"
        >
          <path
            d="M12 4.435c-1.989-5.399-12-4.597-12 3.568 0 4.068 3.06 9.481 12 14.997 8.94-5.516 12-10.929 12-14.997 0-8.118-10-8.999-12-3.568z"
          /></svg
      ></span>
      from Bali -
      <a href="https://github.com/gedelumbung" target="_blank">@gedelumbung</a>
    </footer>
  </div>
</template>

<script>
export default {
  name: "App",
  data: () => ({
    curl_command_text: "curl",
    url: "https://jsonplaceholder.typicode.com/todos/1",
    http_method: "",
    body_type: "",
    custom_headers: [],
    custom_fields: [],
    is_application_json: false,
    is_accept_self_signed_certs: false,
    is_verbose: false,
    json_body: "",
    is_json_valid: true,
  }),
  mounted() {
    this.buildCommand();
  },
  methods: {
    addCustomField() {
      this.custom_fields.push({
        key: "",
        value: "",
      });
    },
    addCustomHeader() {
      this.custom_headers.push({
        key: "",
        value: "",
      });
    },
    removeCustomHeader(index) {
      this.$delete(this.custom_headers, index);
    },
    removeCustomField(index) {
      this.$delete(this.custom_fields, index);
    },
    resetCustomFields() {
      this.json_body = "";
      this.is_json_valid = true;
      if (this.body_type == "json") {
        this.custom_fields = [];
      }
      this.buildCommand();
    },
    syntaxHighlight() {
      this.is_json_valid = true;
      try {
        let json_body = JSON.stringify(JSON.parse(this.json_body), null, 2);
        this.json_body = json_body;
        this.buildCommand();
      } catch (e) {
        this.is_json_valid = false;
      }
    },
    buildCommand() {
      let curl_command_string = "curl";

      if (this.is_verbose) {
        curl_command_string = curl_command_string + " -v";
      }

      if (this.is_accept_self_signed_certs) {
        curl_command_string = curl_command_string + " --insecure";
      }

      if (this.http_method != "") {
        curl_command_string =
          curl_command_string + " --location --request " + this.http_method;
      }

      if (this.is_application_json) {
        if (this.body_type == "json") {
          curl_command_string =
            curl_command_string + ' --header "Content-type: application/json"';
        }
      }

      if (this.custom_headers.length > 0) {
        let custom_headers = this.custom_headers;
        for (let index = 0; index < custom_headers.length; index++) {
          if (
            custom_headers[index].key != "" &&
            custom_headers[index].value != ""
          ) {
            curl_command_string =
              curl_command_string +
              ' --header "' +
              custom_headers[index].key +
              ": " +
              custom_headers[index].value +
              '" ';
          }
        }
      }

      if (this.body_type == "json" && this.json_body != "") {
        let json_body = JSON.stringify(JSON.parse(this.json_body));
        curl_command_string =
          curl_command_string + " --data-raw '" + json_body + "'";
      }

      if (this.body_type == "form_urlencoded" && this.custom_fields != "") {
        let str = "";
        for (let index = 0; index < this.custom_fields.length; index++) {
          if (
            this.custom_fields[index].key != "" &&
            this.custom_fields[index].value != ""
          ) {
            if (str != "") {
              str += "&";
            }
            str +=
              this.custom_fields[index].key +
              "=" +
              this.custom_fields[index].value;
          }
        }

        curl_command_string =
          curl_command_string + " --data-urlencode '" + str + "'";
        curl_command_string =
          curl_command_string +
          ' --header "Content-Type: application/x-www-form-urlencoded"';
      }

      if (this.body_type == "form_data" && this.custom_fields != "") {
        for (let index = 0; index < this.custom_fields.length; index++) {
          if (
            this.custom_fields[index].key != "" &&
            this.custom_fields[index].value != ""
          ) {
            let str =
              " --form '" +
              this.custom_fields[index].key +
              "=" +
              this.custom_fields[index].value +
              "' ";

            curl_command_string = curl_command_string + str;
            curl_command_string =
              curl_command_string +
              ' --header "Content-Type: multipart/form-data"';
          }
        }
      }

      if (this.url != "") {
        curl_command_string = curl_command_string + " '" + this.url + "'";
      }

      this.curl_command_text = curl_command_string;
    },
    copyCurlCommand() {
      let final_curl_command = document.getElementById("curl_command_text");

      final_curl_command.select();
      final_curl_command.setSelectionRange(0, 99999);

      document.execCommand("copy");

      alert("Copied the text: " + final_curl_command.value);
    },
  },
};
</script>
