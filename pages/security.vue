<template>
  <div>
    <form @submit.prevent="addSetting">
      <nav class="navbar">
        <div class="container-fluid">
          <a class="navbar-brand">
            <button type="reset" class="btn btn-warning">Reset</button></a>
          <a class="navbar-brand">
            <input type="submit" class="btn btn-warning" value="Save Setting" /></a>
        </div>
      </nav>
      <br>
      <div class="row">
        <div class="col-3">
          <!-- Tab navs -->
          <div id="v-tabs-tab" class="nav flex-column nav-tabs text-center" role="tablist" aria-orientation="vertical">
            <a id="v-tabs-home-tab" class="nav-link active" data-mdb-toggle="tab" href="#v-tabs-home" role="tab"
              aria-controls="v-tabs-home" aria-selected="true">Security Dashboard</a>
          </div>
          <!-- Tab navs -->
        </div>

        <div class="col-9">
          <div id="v-tabs-tabContent" class="tab-scope">
            <div id="v-tabs-home" class="tab-pane fade show active" role="tabpanel" aria-labelledby="v-tabs-home-tab">
              <div class="table table-responsive">
                <table class="table">
                  <tbody class="row">
                    <tr class="col-lg-6">
                      <td>
                        <label for="type">Site Name</label><br>
                        <input v-model="name" type="text" required value="Setting Name" />
                      </td>
                    </tr>
                    <tr class="col-lg-6">
                      <td>
                        <label for="type">Site Email</label><br>
                        <input v-model="email" type="email" value="Setting email" required />
                      </td>
                    </tr>
                    <tr class="col-lg-6">
                      <td>
                        <label for="type">Company</label><br>
                        <input v-model="company" name="SettingTax" value="Tax Class" type="text" />
                      </td>
                    </tr>
                    <tr class="col-lg-6">
                      <td>
                        <label for="type">Security Status</label><br>
                        <select name="securityStatus" id="securityStatus" v-model="status">
                          <option value="Active">Active</option>
                          <option value="Deactivated">Deactivated</option>
                          <option value="Pending">Pending</option>
                        </select>
                      </td>
                    </tr>
                    <tr class="col-lg-6">
                      <td>
                        <label for="type">Website URL</label><br>
                        <input v-model="website" type="url" value="Setting Website" />
                      </td>
                    </tr>
                    <tr class="col-lg-6">
                      <td>
                        <label for="type">Change Master Password</label><br>
                        <input v-model="password" type="text" value="Setting password" />
                      </td>
                    </tr>
                    <tr class="col-lg-6">
                      <td>
                        <label for="Permissions">Permissions</label><br>
                        <select id="category" v-model="permissions">
                          <option v-for="Permissions in Permissions" :key="Permissions.id" :value="Permissions">
                            {{ Permissions.name }}</option>
                        </select>
                      </td>
                    </tr>
                    <tr class="col-lg-6">
                      <td>
                        <label for="Permissions">Allowed Users</label><br>
                        <select id="category" v-model="user">
                          <option v-for="user in user" :key="user.id" :value="user">
                            {{ user.name }}</option>
                        </select>
                      </td>
                    </tr>
                  </tbody>
                </table>
              </div>
              <div class="accordion-item">
                <h2 id="headingThree" class="accordion-header">
                  <button class="accordion-button" type="button" data-mdb-toggle="collapse"
                    data-mdb-target="#collapseThree" aria-expanded="false" aria-controls="collapseThree">
                    Site Image
                  </button>
                </h2>
                <div id="collapseThree" class="accordion-collapse collapse" aria-labelledby="headingThree"
                  data-mdb-parent="#accordionExample">
                  <div class="accordion-body">
                    <td>
                      <div class="file-upload-wrapper">
                        <input type="image" id="input-file-now" class="file-upload-input"
                          data-mdb-file-upload="file-upload" data-mdb-accepted-extensions="image/*" />
                      </div>
                    </td>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
  /*  import gql from "graphql-tag";

  import findManySettings from "~/graphql/query/findManySettings"
  import findManyCategories from "~/graphql/query/findManyCategories"
  import findManyCountries from "~/graphql/query/findManyCountries"
  import attributes from "~/graphql/query/findManyAttributes"
  import findManySetting_types from "~/graphql/query/findManySetting_types"
  import findManyBrands from "~/graphql/query/findManyBrands"
  import findManydefaultTray from "~/graphql/query/findManydefaultTray"
  import findManyEvents from "~/graphql/query/findManyEvents"
  import manufacturerss from "~/graphql/query/manufacturers"
  import findManyUser from "~/graphql/query/findManyUser"
  import findManypassword from "~/graphql/query/findManypassword"

  const ADD_SettingS = gql`
    mutation ($attributes: String!, $brand: String!, $categories: String!, $content: String!, $contract: String!, $cost_string: String!, $country: String!, $created_at: String!, $customer_type: String!, $family: String!, $file: String!, $colorOption: String!, $status: String!, $id: String!, $image: String!, $manufacture: String!, $manufacturer_part_number: String!, $occassions: String!, $name: String!, $meta_url: String!, $meta_title: String!, $meta_keywords: String!, $meta_description: String!, $part_number: String!, $email: String!, $Setting: String!, $Setting: String!, $related_Setting: String!, $salable_quantity: String!, $short_description: String!, $defaultPaperSize: String!, $sku: String!, $status: String!, $SettingFunction: String!, $Permissions: String!, $company: String!, $thumbnail: String!, $types: String!, $variants: String!, $visibility: String!, $websites: String!, $whid: String!, $zone: String!){
    createOneSettings(data: {attributes: $attributes, brand: $brand, categories: $categories, content: $content, contract: $contract, cost_string: $cost_string, country: $country, created_at: $created_at, customer_type: $customer_type, family: $family, file: $file, colorOption: $colorOption, status: $status, id: $id, image: $image, manufacture: $manufacture, manufacturer_part_number: $manufacturer_part_number, occassions: $occassions, name: $name, meta_url: $meta_url, meta_title: $meta_title, meta_keywords: $meta_keywords, meta_description: $meta_description, part_number: $part_number, email: $email, Setting: $Setting, Setting: $Setting, related_Setting: $related_Setting, salable_quantity: $salable_quantity, short_description: $short_description, defaultPaperSize: $defaultPaperSize, sku: $sku, status: $status, SettingFunction: $SettingFunction, Permissions: $Permissions, company: $company, thumbnail: $thumbnail, types: $types, variants: $variants, visibility: $visibility, websites: $websites, whid: $whid, zone: $zone}) {
        attributes
        brand
        categories
        content
        contract
        cost_string
        country
        created_at
        customer_type
        family
        file
        colorOption
        status
        id
        image
        manufacture
        manufacturer_part_number
        occassions
        name
        meta_url
        meta_title
        meta_keywords
        meta_description
        part_number
        email
        Setting
        Setting
        related_Setting
        salable_quantity
        short_description
        defaultPaperSize
        sku
        status
        SettingFunction
        Permissions
        company
        thumbnail
        types
        variants
        visibility
        websites
        whid
        zone
  }
}`; */


  export default {
    /*   data() {
         return {
           attributes: [],
           brand: [],
           categories: [],
           content: " ",
           contract: [],
           cost_string: " ",
           country: [],
           created_at: " ",
           customer_type: " ",
           family: " ",
           file: " ",
           colorOption: " ",
           status: " ",
           id: " ",
           image: " ",
           manufacture: [],
           manufacturer_part_number: " ",
           occassions: [],
           name: " ",
           meta_url: " ",
           meta_title: " ",
           meta_keywords: " ",
           meta_description: " ",
           part_number: " ",
           email: " ",
           Setting: [],
           Setting: " ",
           related_Setting: " ",
           salable_quantity: " ",
           short_description: " ",
           defaultPaperSize: " ",
           sku: " ",
           status: " ",
           SettingFunction: " ",
           Permissions: [],
           company: " ",
           thumbnail: " ",
           types: [],
           variants: " ",
           visibility: " ",
           websites: " ",
           whid: " ",
           zone: [],
           show: true
         }
       },
       

       methods: {
         async addSetting() {
           const attributes = this.attributes;
           const brand = this.brand;
           const categories = this.categories;
           const content = this.content;
           const contract = this.contract;
           const cost_string = this.cost_string;
           const country = this.country;
           const created_at = this.created_at;
           const customer_type = this.customer_type;
           const family = this.family;
           const file = this.file;
           const colorOption = this.colorOption;
           const status = this.status;
           const id = this.id;
           const image = this.image;
           const manufacture = this.manufacture;
           const manufacturer_part_number = this.manufacturer_part_number;
           const occassions = this.occassions;
           const name = this.name;
           const meta_url = this.meta_url;
           const meta_title = this.meta_title;
           const meta_keywords = this.meta_keywords;
           const meta_description = this.meta_description;
           const part_number = this.part_number;
           const email = this.email;
           const Setting = this.Setting;
           const Setting = this.Setting;
           const related_Setting = this.related_Setting;
           const salable_quantity = this.salable_quantity;
           const short_description = this.short_description;
           const defaultPaperSize = this.defaultPaperSize;
           const sku = this.sku;
           const status = this.status;
           const SettingFunction = this.SettingFunction;
           const Permissions = this.Permissions;
           const company = this.company;
           const thumbnail = this.thumbnail;
           const types = this.types;
           const variants = this.variants;
           const visibility = this.visibility;
           const websites = this.websites;
           const whid = this.whid;
           const zone = this.zone;


           await this.$apollo.mutate({
             mutation: ADD_SettingS,
             variables: {
               attributes,
               brand,
               categories,
               content,
               contract,
               cost_string,
               country,
               created_at,
               customer_type,
               family,
               file,
               colorOption,
               status,
               id,
               image: target.files[0],
               manufacture,
               manufacturer_part_number,
               occassions,
               name,
               meta_url,
               meta_title,
               meta_keywords,
               meta_description,
               part_number,
               email,
               Setting,
               Setting,
               related_Setting,
               salable_quantity,
               short_description,
               defaultPaperSize,
               sku,
               status,
               SettingFunction,
               Permissions,
               company,
               thumbnail,
               types,
               variants,
               visibility,
               websites,
               whid,
               zone,
             },
             update: (cache, {
               data: {
                 insertCategories,
                 insertCountries,
                 insertAttributes,
                 insertSetting_types,
                 insertBrands,
                 insertOccassions,
                 insertpassword,
                 insertPermissions,
                 insertmanufacturer,
                 insertSettings,
                 insertdefaultTray
               }
             }) => {
               // Read data from cache for this query
               try {
                 const insertedCategory = insertCategories.returning;
                 const insertedCountries = insertCountries.returning;
                 const insertedAttributes = insertAttributes.returning;
                 const insertedSetting_types = insertSetting_types.returning;
                 const insertedBrands = insertBrands.returning;
                 const insertedOccassions = insertOccassions.returning;
                 const insertedpassword = insertpassword.returning;
                 const insertedPermissions = insertPermissions.returning;
                 const insertedmanufacturer = insertmanufacturer.returning;
                 const insertedSettings = insertSettings.returning;
                 const inserteddefaultTray = insertdefaultTray.returning;
                 console.log(insertedCategory, insertedCountries, insertedAttributes, insertedSetting_types,
                   insertedBrands, insertedOccassions, insertedpassword, insertedPermissions, insertedmanufacturer,
                   insertedSettings, inserteddefaultTray)
                 cache.writeQuery({
                   query: findManySettings
                 })
               } catch (err) {
                 console.error(err)
               }
             }
           }).then(() => {
             this.$router.push({
               path: '../../shop/Settings'
             })
           }).catch(err => console.log(err));
           this.attributes = ' ';
           this.brand = ' ';
           this.categories = ' ';
           this.content = ' ';
           this.contract = ' ';
           this.cost_string = ' ';
           this.country = ' ';
           this.created_at = ' ';
           this.customer_type = ' ';
           this.family = ' ';
           this.file = ' ';
           this.colorOption = ' ';
           this.status = ' ';
           this.id = ' ';
           this.image = ' ';
           this.manufacture = ' ';
           this.manufacturer_part_number = ' ';
           this.occassions = ' ';
           this.name = ' ';
           this.meta_url = ' ';
           this.meta_title = ' ';
           this.meta_keywords = ' ';
           this.meta_description = ' ';
           this.part_number = ' ';
           this.email = ' ';
           this.Setting = ' ';
           this.Setting = ' ';
           this.related_Setting = ' ';
           this.salable_quantity = ' ';
           this.short_description = ' ';
           this.defaultPaperSize = ' ';
           this.sku = ' ';
           this.status = ' ';
           this.SettingFunction = ' ';
           this.Permissions = ' ';
           this.company = ' ';
           this.thumbnail = ' ';
           this.types = ' ';
           this.variants = ' ';
           this.visibility = ' ';
           this.websites = ' ';
           this.whid = ' ';
           this.zone = ' ';
         },
       },
       apollo: {
         findManyCategories: {
           prefetch: true,
           query: findManyCategories
         },
         findManyCountries: {
           prefetch: true,
           query: findManyCountries
         },
         attributes: {
           prefetch: true,
           query: attributes
         },
         findManySetting_types: {
           prefetch: true,
           query: findManySetting_types
         },
         findManyBrands: {
           prefetch: true,
           query: findManyBrands
         },
         findManydefaultTray: {
           prefetch: true,
           query: findManydefaultTray
         },
         manufacturerss: {
           prefetch: true,
           query: manufacturerss
         },
         findManyEvents: {
           prefetch: true,
           query: findManyEvents
         },
         findManyPermissions: {
           prefetch: true,
           query: findManyPermissions
         },
         findManypassword: {
           prefetch: true,
           query: findManypassword
         },
         findManySettings: {
           prefetch: true,
           query: findManySettings
         }
       }*/

    head: {
      title: 'Security Dashboard'
    },
  }

</script>

<style>
  input,
  select,
  option {
    padding: 5px;
  }

</style>
