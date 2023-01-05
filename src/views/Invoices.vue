<template>
    <div>
        <h1>My pictures</h1>

        <!-- `greet` is the name of the method defined above -->
<button @click="getPictures">getPictures</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            username: '',
            password: ''
        }
    },
    methods: {
        getPictures() {
            // Auth user against the API -> TODO
            // POST request using fetch with error handling
            const requestOptions = {
                method: 'GET',

                //the following line triggers a CORS preflight in the browser - we do not want that when testing from localhost to localhost
               // headers: { 'Content-Type': 'application/json' },

               headers: { 'Authorization': 'Bearer c87671824aeca236a41bc5a9ea50aaeab51d4f34854532e945f82a3bcece1ad1'},
                
            };
            fetch('http://localhost:8080/pictures', requestOptions)
                .then(async response => {
                    const data = await response.json();

                    // check for error response
                    if (!response.ok) {
                        // get error message from body or default to response status
                        const error = (data && data.message) || response.status;
                        return Promise.reject(error);
                    }

                    console.log(data)
                })
                .catch(error => {
                    this.errorMessage = error;
                    console.error('There was an error!', error);
                });


        }
    },
  
}

</script>