<template>
  <div>
    <form  @submit.prevent="addPassword">
      <nav class="navbar navbar-dark bg-dark">
        <div class="container-fluid">
          <a class="navbar-brand">
            <button type="reset" class="btn btn-warning">Reset</button></a>
          <a class="navbar-brand">
            <input type="submit" class="btn btn-warning" value="Save Password" /></a>
        </div>
      </nav>
      <br>
      <div class="row">
        <div class="col-3">
          <!-- Tab navs -->
          <div id="v-tabs-tab" class="nav flex-column nav-tabs text-center" role="tablist" aria-orientation="vertical">
            <a id="v-tabs-home-tab" class="nav-link active" data-mdb-toggle="tab" href="#v-tabs-home" role="tab"
              aria-controls="v-tabs-home" aria-selected="true">Create A New Password</a>
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
                        <label for="type">Password Type</label><br>
                        <select id="PasswordType" v-model="types" name="template" class="form-attribute">
                          <option v-for="types in findManyPassword_types" :key="types.id" :value="Password_types">{{ types.name }}
                          </option>
                        </select>
                      </td>
                    </tr>
                    <tr class="col-lg-6">
                      <td>
                        <label for="type">Password Name</label><br>
                        <input v-model="name" type="text" required value="Password Name" />
                      </td>
                    </tr>
                    <tr class="col-lg-6">
                      <td>
                        <label for="type">Password Email</label><br>
                        <input v-model="email" type="email" value="Password email" required />
                      </td>
                    </tr>
                    <tr class="col-lg-6">
                      <td>
                        <label for="type">Password Company</label><br>
                        <input v-model="company" name="PasswordTax" value="Tax Class" type="text" />
                      </td>
                    </tr>
                    <tr class="col-lg-6">
                      <td>
                        <label for="type">Password</label><br>
                        <input v-model="password" type="number" value="Quantity" />
                      </td>
                    </tr>
                    <tr class="col-lg-6">
                      <td>
                        <label for="type">Password Name</label><br>
                        <select id="stockStatus" v-model="PasswordFunction">
                          <option value="inStock">In Stock</option>
                          <option value="outStock">Out of Stock</option>
                          <option value="backorder">Backorder</option>
                          <option value="clearance">Clearance</option>
                        </select>
                      </td>
                    </tr>
                    <tr class="col-lg-6">
                      <td>
                        <label for="type">Password Status</label><br>
                        <input v-model="status" type="number" value="Password status" />
                      </td>
                    </tr>
                    <tr class="col-lg-6">
                      <td>
                        <label for="type">Password for Location</label><br>
                        <input v-model="whid" type="text" value="Password Location" />
                      </td>
                    </tr>
                    <tr class="col-lg-6">
                      <td>
                        <label for="type">Password for Website</label><br>
                        <input v-model="website" type="url" value="Password Website" />
                      </td>
                    </tr>
                    <tr class="col-lg-6">
                      <td>
                        <label for="type">Password for Vendor</label><br>
                        <input v-model="vendor" type="text" value="Password Vendor" />
                      </td>
                    </tr>
                    <tr class="col-lg-6">
                      <td>
                        <label for="tags">Tags</label><br>
                        <select id="category" v-model="tags">
                          <option v-for="tags in tags" :key="tags.id" :value="tags">
                            {{ tags.name }}</option>
                        </select>
                      </td>
                    </tr>
                    <tr class="col-lg-6">
                      <td>
                        <label for="tags">User</label><br>
                        <select id="category" v-model="user">
                          <option v-for="user in user" :key="user.id" :value="user">
                            {{ user.name }}</option>
                        </select>
                      </td>
                    </tr>
                    <tr class="col-lg-12">
                      <td>
                        <label for="Password">Related Passwords</label><br>
                        <select id="Password" v-model="Password">
                          <option v-for="Password in findManyPasswords" :key="Password.id" :value="Password">
                            {{ Password.name }}</option>
                        </select>
                      </td>
                    </tr>
                  </tbody>
                </table>
              </div>
              <br><br>
              <div id="accordionExample" class="accordion">
                <div class="accordion-item">
                  <h2 id="headingOne" class="accordion-header">
                    <button class="accordion-button" type="button" data-mdb-toggle="collapse"
                      data-mdb-target="#collapseOne" aria-expanded="true" aria-controls="collapseOne">
                      Password Description
                    </button>
                  </h2>
                  <div id="collapseOne" class="accordion-collapse collapse" aria-labelledby="headingOne"
                    data-mdb-parent="#accordionExample">
                    <div class="accordion-body">
                      <div class="table table-responsive">
                        <table class="table">
                          <tbody>
                            <tr>
                              <td style="text-align: right;">Description</td>
                              <td>
                                <div class="form-check form-switch">
                                  <textarea v-model="description" cols="50" rows="10" value="Add a longer Description"></textarea>
                                </div>
                              </td>
                            </tr>
                          </tbody>
                        </table>
                      </div>
                    </div>
                  </div>
                </div>
                <div class="accordion-item">
                  <h2 id="headingThree" class="accordion-header">
                    <button class="accordion-button" type="button" data-mdb-toggle="collapse"
                      data-mdb-target="#collapseThree" aria-expanded="false" aria-controls="collapseThree">
                      Password Images
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
      </div>
    </form>
  </div>
</template>

<script>
/*  import gql from "graphql-tag";

  import findManyPasswords from "~/graphql/query/findManyPasswords"
  import findManyCategories from "~/graphql/query/findManyCategories"
  import findManyCountries from "~/graphql/query/findManyCountries"
  import attributes from "~/graphql/query/findManyAttributes"
  import findManyPassword_types from "~/graphql/query/findManyPassword_types"
  import findManyBrands from "~/graphql/query/findManyBrands"
  import findManydefaultTray from "~/graphql/query/findManydefaultTray"
  import findManyEvents from "~/graphql/query/findManyEvents"
  import manufacturerss from "~/graphql/query/manufacturers"
  import findManyUser from "~/graphql/query/findManyUser"
  import findManyvendor from "~/graphql/query/findManyvendor"

  const ADD_PasswordS = gql`
    mutation ($attributes: String!, $brand: String!, $categories: String!, $content: String!, $contract: String!, $cost_string: String!, $country: String!, $created_at: String!, $customer_type: String!, $family: String!, $file: String!, $colorOption: String!, $status: String!, $id: String!, $image: String!, $manufacture: String!, $manufacturer_part_number: String!, $occassions: String!, $name: String!, $meta_url: String!, $meta_title: String!, $meta_keywords: String!, $meta_description: String!, $part_number: String!, $email: String!, $Password: String!, $password: String!, $related_Password: String!, $salable_quantity: String!, $short_description: String!, $defaultPaperSize: String!, $sku: String!, $status: String!, $PasswordFunction: String!, $tags: String!, $company: String!, $thumbnail: String!, $types: String!, $variants: String!, $visibility: String!, $websites: String!, $whid: String!, $zone: String!){
    createOnePasswords(data: {attributes: $attributes, brand: $brand, categories: $categories, content: $content, contract: $contract, cost_string: $cost_string, country: $country, created_at: $created_at, customer_type: $customer_type, family: $family, file: $file, colorOption: $colorOption, status: $status, id: $id, image: $image, manufacture: $manufacture, manufacturer_part_number: $manufacturer_part_number, occassions: $occassions, name: $name, meta_url: $meta_url, meta_title: $meta_title, meta_keywords: $meta_keywords, meta_description: $meta_description, part_number: $part_number, email: $email, Password: $Password, password: $password, related_Password: $related_Password, salable_quantity: $salable_quantity, short_description: $short_description, defaultPaperSize: $defaultPaperSize, sku: $sku, status: $status, PasswordFunction: $PasswordFunction, tags: $tags, company: $company, thumbnail: $thumbnail, types: $types, variants: $variants, visibility: $visibility, websites: $websites, whid: $whid, zone: $zone}) {
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
        Password
        password
        related_Password
        salable_quantity
        short_description
        defaultPaperSize
        sku
        status
        PasswordFunction
        tags
        company
        thumbnail
        types
        variants
        visibility
        websites
        whid
        zone
  }
}`;


  export default {
    data() {
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
        Password: [],
        password: " ",
        related_Password: " ",
        salable_quantity: " ",
        short_description: " ",
        defaultPaperSize: " ",
        sku: " ",
        status: " ",
        PasswordFunction: " ",
        tags: [],
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
    head: {
      title: 'Add New Password'
    },

    methods: {
      async addPassword() {
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
        const Password = this.Password;
        const password = this.password;
        const related_Password = this.related_Password;
        const salable_quantity = this.salable_quantity;
        const short_description = this.short_description;
        const defaultPaperSize = this.defaultPaperSize;
        const sku = this.sku;
        const status = this.status;
        const PasswordFunction = this.PasswordFunction;
        const tags = this.tags;
        const company = this.company;
        const thumbnail = this.thumbnail;
        const types = this.types;
        const variants = this.variants;
        const visibility = this.visibility;
        const websites = this.websites;
        const whid = this.whid;
        const zone = this.zone;


        await this.$apollo.mutate({
          mutation: ADD_PasswordS,
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
            Password,
            password,
            related_Password,
            salable_quantity,
            short_description,
            defaultPaperSize,
            sku,
            status,
            PasswordFunction,
            tags,
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
              insertPassword_types,
              insertBrands,
              insertOccassions,
              insertvendor,
              insertTags,
              insertmanufacturer,
              insertPasswords,
              insertdefaultTray
            }
          }) => {
            // Read data from cache for this query
            try {
              const insertedCategory = insertCategories.returning;
              const insertedCountries = insertCountries.returning;
              const insertedAttributes = insertAttributes.returning;
              const insertedPassword_types = insertPassword_types.returning;
              const insertedBrands = insertBrands.returning;
              const insertedOccassions = insertOccassions.returning;
              const insertedvendor = insertvendor.returning;
              const insertedTags = insertTags.returning;
              const insertedmanufacturer = insertmanufacturer.returning;
              const insertedPasswords = insertPasswords.returning;
              const inserteddefaultTray = insertdefaultTray.returning;
              console.log(insertedCategory, insertedCountries, insertedAttributes, insertedPassword_types,
                insertedBrands, insertedOccassions, insertedvendor, insertedTags, insertedmanufacturer,
                insertedPasswords, inserteddefaultTray)
              cache.writeQuery({
                query: findManyPasswords
              })
            } catch (err) {
              console.error(err)
            }
          }
        }).then(() => {
          this.$router.push({
            path: '../../shop/Passwords'
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
        this.Password = ' ';
        this.password = ' ';
        this.related_Password = ' ';
        this.salable_quantity = ' ';
        this.short_description = ' ';
        this.defaultPaperSize = ' ';
        this.sku = ' ';
        this.status = ' ';
        this.PasswordFunction = ' ';
        this.tags = ' ';
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
      findManyPassword_types: {
        prefetch: true,
        query: findManyPassword_types
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
      findManyTags: {
        prefetch: true,
        query: findManyTags
      },
      findManyvendor: {
        prefetch: true,
        query: findManyvendor
      },
      findManyPasswords: {
        prefetch: true,
        query: findManyPasswords
      }
    }
  } */

</script>

<style>
  input,
  select,
  option {
    padding: 5px;
  }

</style>
