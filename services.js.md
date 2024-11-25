// Function to load and display the services from the XML file  
function loadServices() {  
    // Create a new XMLHttpRequest to load the XML file  
    const xhr \= new XMLHttpRequest();  
    xhr.open("GET", "services.xml", true); // The XML file location (must be on the server or in the same directory)

    xhr.onload \= function() {  
        if (xhr.status \== 200\) {  
            const xmlDoc \= xhr.responseXML; // Get the XML document  
            const services \= xmlDoc.getElementsByTagName("service"); // Get all service elements  
            const servicesContainer \= document.getElementById("services-container");

            // Clear any existing content in the services container  
            servicesContainer.innerHTML \= "";

            // Loop through each service and create HTML content  
            for (let i \= 0; i \< services.length; i++) {  
                const name \= services\[i\].getElementsByTagName("name")\[0\].textContent;  
                const description \= services\[i\].getElementsByTagName("description")\[0\].textContent;  
                const price \= services\[i\].getElementsByTagName("price")\[0\].textContent;  
                const duration \= services\[i\].getElementsByTagName("duration")\[0\].textContent;

                // Create an HTML element for each service  
                const serviceHTML \= \`  
                    \<div class="service"\>  
                        \<h3\>${name}\</h3\>  
                        \<p\>${description}\</p\>  
                        \<p\>\<strong\>Price:\</strong\> $${price}\</p\>  
                        \<p\>\<strong\>Duration:\</strong\> ${duration}\</p\>  
                    \</div\>  
                \`;

                // Add the service HTML to the container  
                servicesContainer.innerHTML \+= serviceHTML;  
            }  
        }  
    };

    xhr.send(); // Send the request  
}

// Call the function to load services when the page is loaded  
window.onload \= loadServices;