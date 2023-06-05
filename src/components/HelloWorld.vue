<template>
  <div >
 
   <div v-html=" this.htmlinside ">

   </div>

  </div>
</template>

<script>
export default {
  props : {
    html : { required : true , type : String}
  },
  watch : {
    html : {
      handler(newValue){
// Parse the HTML string and create a DOM document
const parser = new DOMParser();
const htmlDoc = parser.parseFromString(newValue, 'text/html');

// Find all table elements
const tables = htmlDoc.getElementsByTagName('table');

// Iterate over the tables and remove the one with "designedwithbee" text
for (let i = 0; i < tables.length; i++) {
  const table = tables[i];
  console.log(table.textContent)
  if (table.textContent.includes('Designed with BEE')) {
    const nestedTables = table.getElementsByTagName('table');
    if (nestedTables.length === 0) {
      table.parentNode.removeChild(table);
      break; // Remove the first matching table and exit the loop
    }}
}

// Get the modified HTML string
const modifiedHtmlString = htmlDoc.documentElement.innerHTML;
  this.htmlinside = modifiedHtmlString

      }
    }
  },
  name: 'HelloWorld',
  data(){
    return {
      htmlinside : this.html
    }
  },
  methods : {
   removeNestedTables(element) {
  const nestedTables = element.getElementsByTagName('table');

  for (let i = nestedTables.length - 1; i >= 0; i--) {
    const nestedTable = nestedTables[i];
    this.removeNestedTables(nestedTable); // Recursively remove nested tables

    // Check if the nested table's content matches the regex pattern
    const content = nestedTable.innerHTML;
    const regex = /designedwithbee/; // Replace with your desired regex pattern
    if (regex.test(content)) {
      nestedTable.parentNode.removeChild(nestedTable); // Remove the nested table
    }
  }
}


  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
table {
  border : none
}
</style>
