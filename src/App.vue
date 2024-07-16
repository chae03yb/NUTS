<template> <!-- HTML -->
  <div id="app">
    <h1>오성고 시간표</h1>

    <table style="width: 45%; height: 85px; margin:auto"> <!-- 너비 -->
      <caption style="text-align: center;"><input type="text" size="3">의 2024년도 1학기의 시간표 입니다.</caption>
      <tr>
        <th></th>
        <th>월</th>
        <th>화</th>
        <th>수</th>
        <th>목</th>
        <th>금</th>
      </tr>
      <!-- 테이블의 내용 -->
      <tr>
        <th>1교시</th>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
      </tr>
      <tr>
        <th>2교시</th>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
      </tr>
      <tr>
        <th>3교시</th>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
      </tr>
      <tr>
        <th>4교시</th>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
      </tr>
      <tr>
        <th>5교시</th>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
      </tr>
      <tr>
        <th>6교시</th>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
      </tr>
      <tr>
        <th>7교시</th>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
      </tr>
      <tr>
        <th>8교시</th>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
        <td> <input type="text" size="3"> </td>
      </tr>
    </table>
  </div>
</template>

<script> //script

export default {
  name: 'App'
}
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

}

input[type="text"] {
  border-top: none;
  border-left: none;
  border-right: none;
  border-bottom: 1px solid black;
}

table, th, td {
  border: 1px solid black;
  border-collapse: collapse;
  text-align: center;
  width: 100px;
  height: 40px;
}

th, td {
  padding: 20px;
}

th {
  text-align: center;
}


</style>
