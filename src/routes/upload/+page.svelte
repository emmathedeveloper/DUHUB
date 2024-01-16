<script lang="ts">

    function handleSubmit(e: any){

        const data = new FormData(e.target)

        data.forEach((v , k) => console.log(k , v))
    }
</script>

<section>
    <form on:submit|preventDefault={handleSubmit}>
        <label for="pdf_file_input">Upload PDF or DOCX file</label>
        <input name="pdf_file_input" type="file"/>
        <input name="title" type="text" placeholder="title" />
        <input name="description" type="text" placeholder="description" />
        <button>Upload</button>
    </form>
</section>