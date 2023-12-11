<script lang="ts">
  const keywords = ['키워드1', '키워드2', '키워드3'];
  const emotions = ['감정1', '감정2', '감정3'];
  const selected = {
    keyword: '',
    content: '',
    emotion: ''
  };

  function selectKeyword(keyword: string) {
    selected.keyword = keyword;
  }

  function updateContent(event: Event) {
    const input = event.target as HTMLTextAreaElement;
    selected.content = input.value;
  }

  function selectEmotion(emotion: string) {
    selected.emotion = emotion;
  }

  function handlePhotoUpload() {
    console.log("사진!");
  }
  
  function handleBackToAppBtn() {
    console.log("앱으로 돌아가라 뿅!");
  }

  $: if (selected) {
    console.log('선택된 상태:', selected);
  }
</script>

<main>
  <!-- 키워드 파트 -->
  <section>
    <h2>키워드</h2>
    <div>
      {#each keywords as keyword}
        <button class:selected={keyword === selected.keyword} on:click={() => selectKeyword(keyword)}>{keyword}</button>
      {/each}
    </div>
  </section>

  <!-- 내용 파트 -->
  <section>
    <h2>내용</h2>
    <textarea on:input={updateContent} placeholder="여기에 내용을 입력하세요"></textarea>
  </section>

  <!-- 사진 파트 -->
  <section>
    <h2>사진</h2>
    <button on:click={handlePhotoUpload}>사진 업로드</button>
  </section>

  <!-- 감정 파트 -->
  <section>
    <h2>감정</h2>
    <div>
      {#each emotions as emotion}
        <button class:selected={emotion === selected.emotion} on:click={() => selectEmotion(emotion)}>{emotion}</button>
      {/each}
    </div>
  </section>

  <!-- 버튼 파트 -->
  <section>
    <button on:click={handleBackToAppBtn}>앱으로 돌아가라 뿅!</button>
  </section>
</main>

<style>
  section {
    margin-bottom: 20px;
  }
  button {
    margin-right: 10px;
  }
  textarea {
    width: 100%;
    height: 100px;
  }

  .selected {
    border: 2px solid blue; /* 선택된 항목을 표시하기 위한 스타일 */
    background-color: lightblue;
  }
</style>
