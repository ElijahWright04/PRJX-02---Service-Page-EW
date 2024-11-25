// Function to load and display the services from the XML file
function loadServices() {
    const xhr = new XMLHttpRequest();
    xhr.open("GET", "services.xml", true);  // The path to the XML file

    xhr.onload = function() {
        if (xhr.status == 200) {
            const xmlDoc = xhr.responseXML;  // Parse the XML response
            const services = xmlDoc.getElementsByTagName("service"); // Get all service elements
            const servicesContainer = document.getElementById("services-container");

            // Clear any existing content in the container
            servicesContainer.innerHTML = "";

            // Loop through each service and create the formatted string
            for (let i = 0; i < services.length; i++) {
                const name = services[i].getElementsByTagName("name")[0].textContent;
                const description = services[i].getElementsByTagName("description")[0].textContent;
                const price = services[i].getElementsByTagName("price")[0].textContent;
                const duration = services[i].getElementsByTagName("duration")[0].textContent;

                // Create the formatted service string
                const serviceText = `${name}: ${description} $${price} for ${duration}`;

                // Create a new HTML element to display the service
                const serviceHTML = `
                    <div class="service">
                        <p>${serviceText}</p>
                    </div>
                `;

                // Add the formatted service string to the container
                servicesContainer.innerHTML += serviceHTML;
            }
        }
    };

    xhr.send();  // Send the request to load the XML
}

// Call the function to load services when the page is loaded
window.onload = loadServices;
