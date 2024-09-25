SERVERLESS WEB APPLICATION DEPLOYMENT ON AWS
Abstract:
	In this project I have deployed a simple web application using serverless architecture on AWS. I have used different AWS services through out this project like AWS Amplify, AWS lambda, AWS API Gateway and AWS DynamoDB. This serverless architecture a software design model that lets developers build and manage applications without having to manage the underlying infrastructure, and it reduces the cost.
Process of Deploying:
Step-1: Create an app on AWS Amplify and deploy the sample web application on it. 
Step-2: Now create the lambda function to process the request, which will take the base and exponent values, calculates the power and stores on DynamoDB and return to application. 
Step-3: If we want to execute the lambda function, we need to add trigger (API Gateway). Which will trigger the lambda function.      
Step-4: Then create DynamoDB table for storing those data and give appropriate IAM permissions that lambda function access the DynamoDB. 
Step-5: Finally, we setup all the services on cloud now we need to change the web application JavaScript code for appropriate result.
<script>
        // callAPI function that takes the base and exponent numbers as parameters
        var callAPI = (base,exponent)=>{
            // instantiate a headers object
            var myHeaders = new Headers();
            // add content type header to object
            myHeaders.append("Content-Type", "application/json");
            // using built in JSON utility package turn object to string and store in a variable
            var raw = JSON.stringify({"base":base,"exponent":exponent});
            // create a JSON object with parameters for API call and store in a variable
            var requestOptions = {
                method: 'POST',
                headers: myHeaders,
                body: raw,
                redirect: 'follow'
            };
            // make API call with parameters and use promises to get response
            fetch("YOUR API GATEWAY ENDPOINT", requestOptions)
            .then(response => response.text())
            .then(result => alert(JSON.parse(result).body))
            .catch(error => console.log('error', error));
        }
    </script>
API CALL:
<button type="button" onclick="callAPI(document.getElementById('base').value,document.getElementById('exponent').value)">CALCULATE</button>
