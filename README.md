# paytabs-assessment
 Paytabs Assessment


----

# PayTabs Shop - E-commerce Application

## Overview

This project is a simple e-commerce application that integrates with PayTabs' iFrame Payment Mode to process online payments. The application allows guest users to browse products, add them to a cart (represented through order items), and proceed to a checkout page where they can enter their information and make a payment using PayTabs.

## Features

*   **Product Listing:** Displays a list of products stored in the database (images not required).
*   **Add to Cart:** Allows guest users to add products (with quantity) to an active order.
*   **Checkout:** Collects customer information (name, email, shipping address) and integrates with PayTabs iFrame Payment Mode.
*   **PayTabs iFrame Integration:** Displays the PayTabs payment form within the checkout page using iFrame mode.
*   **Payment Processing:** Processes payments using the PayTabs API and redirects the user to a success or error page based on the payment status.
*   **Order Management:** Displays a list of past orders with details and status.
*   **Order Details:** Shows the payment request and response payloads for each order, as well as refund history for refunded orders.

## Technologies Used

*   **Backend:**
    *   Java
    *   Spring Boot
    *   JPA/Hibernate (for database interaction)
    *   MySQL (or SQLite for development)
    *   RestTemplate (for making HTTP requests to PayTabs API)
    *   Lombok (for reducing boilerplate code)
*   **Frontend:**
    *   Thymeleaf (for server-side rendering of HTML templates)
    *   Bootstrap (for basic styling)
    *   JavaScript (for AJAX and dynamic iFrame loading)
    *   jQuery (for simplifying AJAX requests and DOM manipulation)
*   **Build Tool:**
    *   Maven

## Setup Instructions

1.  **Clone the Repository:**

    ```bash
    git clone https://github.com/your-username/MyPayTabsShop.git
    cd MyPayTabsShop
    ```

2.  **Install Java:**

    *   Ensure you have Java 21 (or a compatible version) installed.

3.  **Install Maven:**

    *   Download and install Apache Maven from [https://maven.apache.org/download.cgi](https://maven.apache.org/download.cgi).
    *   Set the `JAVA_HOME` environment variable to your JDK installation directory.
    *   Add the Maven `bin` directory to your `PATH` environment variable.

4.  **Configure Database:**

    *   **MySQL:**
        *   Create a MySQL database named `paytabsshop`.
        *   Update the `application.properties` file with your MySQL connection details:

            ```properties
            spring.datasource.url=jdbc:mysql://localhost:3306/paytabsshop?createDatabaseIfNotExist=true&useSSL=false&serverTimezone=UTC
            spring.datasource.username=your_mysql_username
            spring.datasource.password=your_mysql_password
            spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
            spring.jpa.database-platform=org.hibernate.dialect.MySQLDialect
            spring.jpa.hibernate.ddl-auto=update
            ```

    *   **SQLite:**
        *   The application will automatically create an SQLite database file named `shop.db` in the project directory.
        *   Update the `application.properties` file to use SQLite:

            ```properties
            spring.datasource.url=jdbc:sqlite:./shop.db
            spring.datasource.driver-class-name=org.sqlite.JDBC
            spring.jpa.database-platform=org.hibernate.dialect.SQLiteDialect
            spring.jpa.hibernate.ddl-auto=update
            ```

5.  **Configure PayTabs Credentials:**

    *   Update the `application.properties` file with your PayTabs credentials:

        ```properties
        paytabs.profile-id=YOUR_PROFILE_ID
        paytabs.integration-key=YOUR_INTEGRATION_KEY
        paytabs.base-url=YOUR_PAYTABS_BASE_URL
        ```

        *   Replace `YOUR_PROFILE_ID`, `YOUR_INTEGRATION_KEY`, and `YOUR_PAYTABS_BASE_URL` with your actual PayTabs credentials and base URL (for your environment and region).

6.  **Build the Application:**

    ```bash
    mvn clean install
    ```

7.  **Run the Application:**

    ```bash
    java -jar target/paytabsshop-0.0.1-SNAPSHOT.jar
    ```

    *   The application will start on port 8080.

## Testing

1.  **Access the Application:**

    *   Open your web browser and go to `http://localhost:8080`.

2.  **Create a New Order:**

    *   Browse the products and add one to the cart.
    *   Proceed to the checkout page.
    *   Enter your customer information and select a payment option.
    *   Submit the form.
    *   You should see the PayTabs iFrame payment form.

3.  **Test PayTabs Integration:**

    *   Use the PayTabs test card details (available in the PayTabs documentation or support portal) to simulate a successful or failed transaction.
    *   Verify that your application correctly handles the PayTabs response and redirects you to the appropriate success or error page.

4.  **View My Orders:**

    *   Go to `http://localhost:8080/my_orders` to view your past orders.
    *   Click on an order to view its details, including the payment request and response payloads.

## Important Considerations

*   **Security:**
    *   Never commit sensitive information (passwords, API keys, etc.) directly into your Git repository. Use environment variables or configuration files that are not tracked by Git to store sensitive data.
    *   Use HTTPS in production.
    *   Implement proper input validation and output encoding to prevent security vulnerabilities.
*   **Error Handling:**
    *   Implement robust error handling throughout the application.
    *   Use logging to track errors and other important events.
*   **PayTabs API Documentation:**
    *   Consult the PayTabs API documentation for the most up-to-date information on their API and required parameters.
*   **Database Configuration:**
    *   The application is configured to use MySQL (or SQLite for development). You can change the database configuration in the `application.properties` file.
*   **Production Deployment:**
    *   For production deployment, you will need to deploy the application to a hosting platform like Heroku, AWS, or Google Cloud Platform.
* **Running on different profile:**
 The Spring Boot application uses the `SPRING_PROFILES_ACTIVE` System Environment Variable to configure the profile. You can change this parameter on you environment properties.

## Contact

If you have any questions or issues, please contact [your name] at [your email address].