<template>
  <div>
    <h3 style="text-align: center; margin: 10px;">Sites</h3>
    <div class="input-group mb-4">
      <input type="text" class="form-control" id="advanced-search-input" placeholder="phrase in:column1,column2" />
      <button class="btn btn-primary" id="advanced-search-button" type="button">
        <i class="fa fa-search"></i>
      </button>
    </div>
    <div id="datatable"></div>
  </div>
</template>

<script>
  export default {

    mounted() {
      const data = {
        columns: [{
            label: 'Site Name',
            field: 'name'
          },
          '# of Passwords',
          'Created On',
          'Access'
        ],
        rows: [
          ["Tiger Nixon", "System Architect", "Edinburgh", "61", "2011/04/25", "$320,800"],
          ["Garrett Winters", "Accountant", "Tokyo", "63", "2011/07/25", "$170,750"],
          ["Ashton Cox", "Junior Technical Author", "San Francisco", "66", "2009/01/12", "$86,000"],
        ],
      };

      const instance = new mdb.Datatable(document.getElementById('datatable'), data)
      const advancedSearchInput = document.getElementById('advanced-search-input');

      const search = (value) => {
        let [phrase, columns] = value.split(' in:').map((str) => str.trim());

        if (columns) {
          columns = columns.split(',').map((str) => str.toLowerCase().trim());
        }

        instance.search(phrase, columns);
      }

      document.getElementById('advanced-search-button').addEventListener('click', (e) => {
        search(advancedSearchInput.value)
      });

      advancedSearchInput.addEventListener('keydown', (e) => {
        if (e.keyCode === 13) {
          search(e.target.value);
        }
      })
    },
    head: {
      title: 'Sites'
    }
  }

</script>
