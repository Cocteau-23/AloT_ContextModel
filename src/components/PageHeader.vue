<!-- <template>
  <header>
    <nav>
      <ul>
        <button @click="handleNewModel">新建模型</button>
        <button @click="handleDeleteModel">删除模型</button>
        <button @click="handleImportModel">导入模型</button>
        <button @click="handleExportModel">导出模型</button>
      </ul>
    </nav>
  </header>
  <div class="ModelName" v-if="showInputModelName">
    <input type="text" v-model="text" />
    <button @click="addDevice">添加设备</button>
    <table>
      <tr v-for="(dev, index) in devList" :key="index">
        <td>
          <button @click="deleteDevice(index)">删除</button>
        </td>
        <td>{{ `设备 ${index + 1}` }}</td>
        <td>
          <select v-model="dev.selectedOption1">
            <option v-for="option in options1" :key="option" :value="option">{{ option }}</option>
          </select>
        </td>
        <td>
          <select v-model="dev.selectedOption2">
            <option v-for="option in options2" :key="option" :value="option">{{ option }}</option>
          </select>
        </td>
        <td>
          <select v-model="dev.selectedOption3">
            <option v-for="option in options3" :key="option" :value="option">{{ option }}</option>
          </select>
        </td>
        <td>
          <select v-model="dev.selectedOption4">
            <option v-for="option in options4" :key="option" :value="option">{{ option }}</option>
          </select>
        </td>
        <td>
          <select v-model="dev.selectedOption5">
            <option v-for="option in options5" :key="option" :value="option">{{ option }}</option>
          </select>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  name: 'PageHeader',
  setup() {
    const text = ref('新建模型');
    const showInputModelName = ref(false);
    const devList = ref([]);

    const optionTextMap1 = {
      option1: 'Humidity',
      option2: 'Weather',
      option3: 'Temperature',
    };

    const optionTextMap2 = {
      option1: 'Collected',
      option2: 'Cosine',
      option3: 'Discrete',
      option4: 'Polynomial',
      option5: 'Sine',
    };

    const optionTextMap3 = {
      option1: '选项1',
      option2: '选项2',
      option3: '选项3',
      option4: '选项4',
    };

    const optionTextMap4 = {
      option1: '选项1',
      option2: '选项2',
      option3: '选项3',
      option4: '选项4',
    };

    const optionTextMap5 = {
      option1: '选项1',
      option2: '选项2',
      option3: '选项3',
      option4: '选项4',
    };

    const options1 = Object.values(optionTextMap1);
    const options2 = Object.values(optionTextMap2);
    const options3 = Object.values(optionTextMap3);
    const options4 = Object.values(optionTextMap4);
    const options5 = Object.values(optionTextMap5);

    function handleNewModel() {
      showInputModelName.value = true;
    }

    function handleDeleteModel() {
      showInputModelName.value = false;
      text.value = '新建模型';
      devList.value = [];
    }

    function handleExportModel() {
      const data = devList.value.map(dev => {
        const options = [];
          options.push(dev.selectedOption1);

          options.push(dev.selectedOption2);

          options.push(dev.selectedOption3);

          options.push(dev.selectedOption4);

          options.push(dev.selectedOption5);
        return options.join(', ');
      }).join('\n');

      const element = document.createElement('a');
      const file = new Blob([data], { type: 'application/owl+xml' });
      element.href = URL.createObjectURL(file);
      element.download = 'model_data.owl';
      document.body.appendChild(element);
      element.click();
      document.body.removeChild(element);
    }

    const addDevice = () => {
      devList.value.push({
        selectedOption1: '',
        selectedOption2: '',
        selectedOption3: '',
        selectedOption4: '',
        selectedOption5: '',
        showAdditionalOptions: false,
      });
    };

    function deleteDevice(index) {
      devList.value.splice(index, 1);
    }

    return {
      text,
      showInputModelName,
      devList,
      options1,
      options2,
      options3,
      options4,
      options5,
      handleNewModel,
      handleDeleteModel,
      handleExportModel,
      addDevice,
      deleteDevice,
    };
  },
};
</script>

<style>
header {
  background-color: #f0f0f0;
  padding: 10px;
}

nav ul {
  display: flex;
  justify-content: space-around;
}

nav ul button {
  border: none;
  background-color: transparent;
  cursor: pointer;
  font-size: larger;
  font-weight: bolder;
}

.ModelName {
  width: auto;
  margin-top: 30px;
}

.ModelName input {
  border: none;
  font-size: larger;
  text-align: center;
  padding: 10px;
}

.ModelName input:focus {
  border: 2px, solid;
}

.generated-div {
  display: inline-block;
  margin: 5px;
  padding: 10px;
  background-color: #f0f0f0;
}
</style> -->


<template>
  <header>
    <nav>
      <ul>
        <button @click="handleNewModel">新建模型</button>
        <button @click="handleDeleteModel">删除模型</button>
        <button @click="handleImportModel">导入模型</button>
        <button @click="handleExportModel">导出模型</button>
      </ul>
    </nav>
  </header>
  <div class="ModelName" v-if="showInputModelName">
    <input type="text" v-model="text" />
    <button @click="addDevice">添加设备</button>
    <table>
      <tr v-for="(dev, index) in devList" :key="index">
        <td>
          <button @click="deleteDevice(index)">删除</button>
        </td>
        <td>{{ `设备 ${index + 1}` }}</td>
        <td>
          <select v-model="dev.selectedOption1">
            <option v-for="(optionText, optionValue) in optionTextMap1" :key="optionValue" :value="optionValue">{{ optionText }}</option>
          </select>
        </td>
        <td>
          <select v-model="dev.selectedOption2">
            <option v-for="(optionText, optionValue) in optionTextMap2" :key="optionValue" :value="optionValue">{{ optionText }}</option>
          </select>
        </td>
        <td>
          <select v-model="dev.selectedOption3">
            <option v-for="(optionText, optionValue) in optionTextMap3" :key="optionValue" :value="optionValue">{{ optionText }}</option>
          </select>
        </td>
        <td>
          <select v-model="dev.selectedOption4">
            <option v-for="(optionText, optionValue) in optionTextMap4" :key="optionValue" :value="optionValue">{{ optionText }}</option>
          </select>
        </td>
        <td>
          <select v-model="dev.selectedOption5">
            <option v-for="(optionText, optionValue) in optionTextMap5" :key="optionValue" :value="optionValue">{{ optionText }}</option>
          </select>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  name: 'PageHeader',
  setup() {
    const text = ref('新建模型');
    const showInputModelName = ref(false);
    const devList = ref([]);

    const optionTextMap1 = {
      option1: 'Humidity',
      option2: 'Weather',
      option3: 'Temperature',
    };

    const optionTextMap2 = {
      option1: 'Class1',
      option2: 'Class2',
      option3: 'Class3',
      option4: 'Class4',
      option5: 'Class5',
    };

    const optionTextMap3 = {
      option1: 'Individual1',
      option2: 'Individual2',
      option3: 'Individual3',
      option4: 'Individual4',
    };

    const optionTextMap4 = {
      option1: 'Individual5',
      option2: 'Individual6',
      option3: 'Individual7',
      option4: 'Individual8',
    };

    const optionTextMap5 = {
      option1: 'Individual9',
      option2: 'Individual10',
      option3: 'Individual11',
      option4: 'Individual12',
    };

    const options1 = Object.keys(optionTextMap1);
    const options2 = Object.keys(optionTextMap2);
    const options3 = Object.keys(optionTextMap3);
    const options4 = Object.keys(optionTextMap4);
    const options5 = Object.keys(optionTextMap5);

    function handleNewModel() {
      showInputModelName.value = true;
    }

    function handleDeleteModel() {
      showInputModelName.value = false;
      text.value = '新建模型';
      devList.value = [];
    }

    function handleExportModel() {
      let owlContent = '<?xml version="1.0"?>\n';
      owlContent += '<!DOCTYPE rdf:RDF [\n';
      owlContent += '    <!ENTITY xsd "http://www.w3.org/2001/XMLSchema#">\n';
      owlContent += '    <!ENTITY owl "http://www.w3.org/2002/07/owl#">\n';
      owlContent += '    <!ENTITY rdf "http://www.w3.org/1999/02/22-rdf-syntax-ns#">\n';
      owlContent += '    <!ENTITY rdfs "http://www.w3.org/2000/01/rdf-schema#">\n';
      owlContent += '    <!ENTITY my-ontology "http://www.example.com/my-ontology#">\n';
      owlContent += ']>\n';
      owlContent += '<rdf:RDF xmlns="http://www.example.com/my-ontology#"\n';
      owlContent += '         xml:base="http://www.example.com/my-ontology"\n';
      owlContent += '         xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"\n';
      owlContent += '         xmlns:owl="http://www.w3.org/2002/07/owl#"\n';
      owlContent += '         xmlns:xsd="http://www.w3.org/2001/XMLSchema#"\n';
      owlContent += '         xmlns:rdfs="http://www.w3.org/2000/01/rdf-schema#">\n';
      owlContent += '    <owl:Ontology rdf:about="">\n';
      owlContent += '        <owl:imports rdf:resource="http://www.w3.org/2002/07/owl"/>\n';
      owlContent += '    </owl:Ontology>\n';

      devList.value.forEach((dev, index) => {
        const deviceName = `Device${index + 1}`;
        owlContent += `    <owl:Class rdf:about="${deviceName}">\n`;
        owlContent += `        <rdfs:label>${deviceName}</rdfs:label>\n`;
        owlContent += '    </owl:Class>\n';

        const selectedOption1Text = optionTextMap1[dev.selectedOption1];
        const selectedOption2Text = optionTextMap2[dev.selectedOption2];
        const selectedOption3Text = optionTextMap3[dev.selectedOption3];
        const selectedOption4Text = optionTextMap4[dev.selectedOption4];
        const selectedOption5Text = optionTextMap5[dev.selectedOption5];

        owlContent += `    <owl:NamedIndividual rdf:about="${deviceName}">\n`;
        owlContent += `        <rdf:type rdf:resource="${selectedOption1Text}"/>\n`;
        owlContent += `        <rdf:type rdf:resource="${selectedOption2Text}"/>\n`;
        owlContent += `        <my-ontology:hasIndividualProperty1 rdf:resource="${selectedOption3Text}"/>\n`;
        owlContent

 += `        <my-ontology:hasIndividualProperty2 rdf:resource="${selectedOption4Text}"/>\n`;
        owlContent += `        <my-ontology:hasIndividualProperty3 rdf:resource="${selectedOption5Text}"/>\n`;
        owlContent += '    </owl:NamedIndividual>\n';
      });

      owlContent += '</rdf:RDF>';

      const element = document.createElement('a');
      const file = new Blob([owlContent], { type: 'application/rdf+xml' });
      element.href = URL.createObjectURL(file);
      element.download = 'model_data.owl';
      document.body.appendChild(element);
      element.click();
      document.body.removeChild(element);
    }

    const addDevice = () => {
      devList.value.push({
        selectedOption1: '',
        selectedOption2: '',
        selectedOption3: '',
        selectedOption4: '',
        selectedOption5: '',
        showAdditionalOptions: false,
      });
    };

    function deleteDevice(index) {
      devList.value.splice(index, 1);
    }

    return {
      text,
      showInputModelName,
      devList,
      optionTextMap1,
      optionTextMap2,
      optionTextMap3,
      optionTextMap4,
      optionTextMap5,
      options1,
      options2,
      options3,
      options4,
      options5,
      handleNewModel,
      handleDeleteModel,
      handleExportModel,
      addDevice,
      deleteDevice,
    };
  },
};
</script>

<style>
header {
  background-color: #f0f0f0;
  padding: 10px;
}

nav ul {
  display: flex;
  justify-content: space-around;
}

nav ul button {
  border: none;
  background-color: transparent;
  cursor: pointer;
  font-size: larger;
  font-weight: bolder;
}

.ModelName {
  width: auto;
  margin-top: 30px;
}

.ModelName input {
  border: none;
  font-size: larger;
  text-align: center;
  padding: 10px;
}

.ModelName input:focus {
  border: 2px, solid;
}

.generated-div {
  display: inline-block;
  margin: 5px;
  padding: 10px;
  background-color: #f0f0f0;
}
</style>