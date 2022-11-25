<template>
  <div>
    <form @submit.prevent="addNote()">
      <nav class="navbar navbar-dark bg-dark">
        <div class="container-fluid">
          <a class="navbar-brand">
            <button type="reset" class="btn btn-warning" @click="deleteNote(note.id)">Delete</button></a>
          <a class="navbar-brand">
            <input type="submit" class="btn btn-warning" value="Save Note" /></a>
        </div>
      </nav>
      <br>
      <div class="row">
        <div class="col-3">
          <!-- Tab navs -->
          <div id="v-tabs-tab" class="nav flex-column nav-tabs text-center" role="tablist" aria-orientation="vertical">
            <a id="v-tabs-home-tab" class="nav-link active" data-mdb-toggle="tab" href="#v-tabs-home" role="tab"
              aria-controls="v-tabs-home" aria-selected="true">Edit Note</a>
          </div>
          <!-- Tab navs -->
        </div>

        <div class="col-9">
          <div id="v-tabs-tabContent" class="tab-scope">
            <div id="v-tabs-home" class="tab-pane fade show active" role="tabpanel" aria-labelledby="v-tabs-home-tab">
              <div class="table table-responsive">
                <table class="table">
                  <tbody v-for="note in findManyNotes" :key="note.id">
                    <tr>
                      <td style="text-align: right;">Note Name</td>
                      <td>
                        <input :value="note.name" type="text" required />
                      </td>
                    </tr>
                    <tr>
                      <td style="text-align: right;">Categories</td>
                      <td>
                        <select id="category" :value="note.categories" name="template" class="form-category">
                          <option v-for="categories in findManyCategories" :key="categories.id"
                            :value="categories.name">
                            {{ categories.name }}
                          </option>
                        </select>
                      </td>
                    </tr>
                    <tr>
                      <td style="text-align: right;">Tags</td>
                      <td>
                        <select id="category" :value="note.tags" name="template" class="form-category">
                          <option v-for="tags in findManyTags" :key="tags.id" :value="tags.name">{{ tags.name }}
                          </option>
                        </select>
                      </td>
                    </tr>
                    <tr>
                      <td style="text-align: right;">Note Availibility</td>
                      <td>
                        <select name="noteType" id="noteType" :value="note.isPublic">
                          <option value="public">Public</option>
                          <option value="private">Private</option>
                          <option value="draft">Draft</option>
                        </select>
                      </td>
                    </tr>
                    <tr>
                      <td style="text-align: right;">Published Date</td>
                      <td>
                        <input :value="note.published" type="datetime-local"
                          placeholder="Default is published immediately" />
                      </td>
                    </tr>
                    <tr>
                      <td>
                        <select id="noteType" :value="note.type">
                          <option value="course">Blog Post</option>
                          <option value="material">Note</option>
                          <option value="school">Knowledgebase note</option>
                        </select>
                      </td>
                    </tr>
                    <tr>
                      <td style="text-align: right;">Author(s)</td>
                      <td>
                        <select id="category" :value="note.customers" name="template" class="form-category">
                          <option v-for="customers in findManyCustomers" :key="customers.id" :value="customers.name">
                            {{ customers.name }}</option>
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
                      Content
                    </button>
                  </h2>
                  <div id="collapseOne" class="accordion-collapse collapse" aria-labelledby="headingOne"
                    data-mdb-parent="#accordionExample">
                    <div class="accordion-body">
                      <div class="table table-responsive">
                        <table class="table">
                          <tbody>
                            <tr>
                              <td style="text-align: right;">Excerpt</td>
                              <td>
                                <textarea id="excerpt" :value="note.excerpt" cols="50" rows="10"
                                  placeholder="Add a short Description"></textarea>
                              </td>
                            </tr>
                            <tr>
                              <td style="text-align: right;">Description</td>
                              <td>
                                <client-only>
                                  <textarea :value="note.content" rows="10" cols="50"></textarea>
                                </client-only>
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
                      Images and Videos
                    </button>
                  </h2>
                  <div id="collapseThree" class="accordion-collapse collapse" aria-labelledby="headingThree"
                    data-mdb-parent="#accordionExample">
                    <div class="accordion-body">
                      <td>
                        <input :value="note.image" type="image" />
                      </td>
                    </div>
                  </div>
                </div>
                <div class="accordion-item">
                  <h2 id="headingFour" class="accordion-header">
                    <button class="accordion-button" type="button" data-mdb-toggle="collapse"
                      data-mdb-target="#collapseFour" aria-expanded="false" aria-controls="collapseFour">
                      Search Engine Optimization
                    </button>
                  </h2>
                  <div id="collapseFour" class="accordion-collapse collapse" aria-labelledby="headingFour"
                    data-mdb-parent="#accordionExample">
                    <div class="accordion-body">
                      <table class="table">
                        <tbody>
                          <tr>
                            <td></td>
                            <td>Meta Title, Meta Keywords, and Meta Description are used to describe your products to
                              potential customers using search engine like Google, Bing, etc.</td>
                          </tr>
                          <tr>
                            <td style="text-align: right;">Meta Title</td>
                            <td>
                              <input :value="note.meta_name" type="text" />
                            </td>
                          </tr>
                          <tr>
                            <td style="text-align: right;">Meta Description</td>
                            <td>
                              <textarea :value="note.meta_description" rows="10" cols="50"></textarea>
                            </td>
                          </tr>
                          <tr>
                            <td style="text-align: right;">Meta Url</td>
                            <td>
                              <input :value="note.meta_url" type="url" />
                            </td>
                          </tr>
                        </tbody>
                      </table>
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
  // eslint-disable-next-line camelcase
 // import gql from 'graphql-tag'
 // import findManyNotes from '~/graphql/query/findManyNotes'
 // import Editor from '~/components/Editor.vue'

/*  const DELETE_note = gql `
  mutation deleteOnenotes($id: Int!){
  deleteOnenotes(where: {id: $id}){
    id
        }
}
`;

  const UPDATE_note = gql `
  mutation updateOnenotes($id: Int!){
  updateOnenotes(data: {categories: $categories, content: $content, customers: $customers, excerpt: $excerpt, image: $image, isPublic: $isPublic, meta_description: $meta_description, meta_name: $meta_name, meta_url: $meta_url, name: $name, published: $published, tags: $tags, users: $users, type: $type}, (where: {id: $id})){
    categories
        content
        customers
        excerpt
        image
        isPublic
        meta_description
        meta_name
        meta_url
        name
        published
        tags
        users
        type
        }
}
`;

  export default {
    components: {
      Editor
    },
    head: {
      name: 'Edit note'
    },
    mounted() {
      this.forceRerender();
    },
    // eslint-disable-next-line vue/order-in-components
    data() {
      return {
        componentKey: 0
      }
    },
    methods: {
      async deletenote(note) {
        await this.$apollo.mutate({
          mutation: DELETE_note,
          variables: {
            id: note.id
          },
          refetchQueries: [{
              query: findManyNotes
            }

          ]
        }).then(() => {
          this.$router.push({
            path: '../../admin/content/blog'
          })
        }).catch(err => console.log(err));
      },
      async updatenote(note) {
        await this.$apollo.mutate({
          mutation: UPDATE_note,
          variables: {
            id: note.id
          },
          refetchQueries: [{
              query: findManyNotes
            }

          ]
        })
      },
      forceRerender() {
        this.componentKey += 1;
      }
    },
    apollo: {
      findManyNotes: {
        query: findManyNotes,
        prefetch: ({
          route
        }) => ({
          id: route.params.id
        }),
        variables() {
          return {
            id: this.$route.params.id
          }
        }
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

  li {
    display: inline-block;
  }

</style>
