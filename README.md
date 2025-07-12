# QuantumWatch: Real-time Crypto Price Alert System

A robust and scalable system that provides real-time crypto price alerts through Websocket streams, triggering serverless function execution and user notifications based on configurable thresholds.

QuantumWatch is designed to provide immediate notifications when cryptocurrency prices reach predefined levels. This is achieved by establishing persistent Websocket connections to cryptocurrency exchanges, continuously monitoring price feeds, and comparing them against user-defined thresholds. When a threshold is breached, a serverless function is triggered, allowing for flexible and customizable actions, such as sending email or SMS notifications, logging the event, or initiating automated trading strategies. This eliminates the need for constant polling and ensures near-instantaneous alerts, crucial for time-sensitive trading and investment decisions. The system is built with scalability and reliability in mind, leveraging serverless architecture to handle fluctuating workloads and ensure high availability.

The core benefit of QuantumWatch is its ability to provide proactive alerts without requiring constant manual monitoring. Users can define multiple alert rules for different cryptocurrencies and thresholds, allowing them to focus on other tasks while being assured that they will be notified instantly of significant price movements. Furthermore, the serverless architecture makes the system cost-effective, as users only pay for the resources consumed when alerts are triggered. The system's modular design allows for easy integration with other services and platforms, such as trading bots, portfolio management tools, and analytics dashboards. By offering real-time alerts and flexible customization options, QuantumWatch empowers users to react quickly to market changes and optimize their cryptocurrency investments.

QuantumWatch is built using Typescript, leveraging its strong typing and object-oriented features to ensure code maintainability and scalability. The system supports multiple cryptocurrency exchanges, with a flexible architecture that allows for easy addition of new exchange integrations. The configuration is handled through environment variables, providing a simple and secure way to manage sensitive information such as API keys and notification settings. The serverless functions are designed to be idempotent and fault-tolerant, ensuring that alerts are delivered reliably even in the face of transient errors. The system also includes comprehensive logging and monitoring capabilities, allowing developers to track performance, diagnose issues, and optimize the system over time.

## Key Features

*   **Real-time Price Monitoring:** Establishes persistent Websocket connections to cryptocurrency exchanges for continuous price updates. Uses libraries like `ws` or equivalent to manage websocket connections.
*   **Configurable Alert Thresholds:** Allows users to define multiple alert rules with custom thresholds (e.g., price above, price below, percentage change). Stored in a database like DynamoDB or Firestore.
*   **Serverless Function Execution:** Triggers serverless functions (e.g., AWS Lambda, Google Cloud Functions) when a threshold is breached. The serverless function payload includes the cryptocurrency symbol, the breached threshold, and the current price.
*   **Multi-Exchange Support:** Supports multiple cryptocurrency exchanges (e.g., Binance, Coinbase, Kraken) through modular exchange adapters. Each adapter handles authentication and data formatting specific to the exchange.
*   **User Notification System:** Integrates with notification services (e.g., Twilio, SendGrid) to send SMS or email alerts to users. Uses API keys stored securely in environment variables.
*   **Event Logging:** Logs all triggered alerts and system events to a persistent storage for auditing and analysis. Logs are formatted in JSON and include timestamps and relevant data.
*   **Typescript Implementation:** Uses Typescript for code maintainability, scalability, and type safety. Enforces strict typing and linting rules.

## Technology Stack

*   **Typescript:** The primary programming language, providing strong typing and object-oriented features for robust and maintainable code.
*   **Node.js:** The runtime environment for executing the Typescript code.
*   **Websockets (ws/socket.io):** Used for establishing real-time connections to cryptocurrency exchange APIs.
*   **Serverless Functions (AWS Lambda/Google Cloud Functions):** Provides a scalable and cost-effective platform for executing alert logic.
*   **Database (DynamoDB/Firestore):** Used for storing alert rules, user profiles, and event logs.
*   **Notification Service (Twilio/SendGrid):** Used for sending SMS and email notifications to users.
*   **dotenv:** To manage environment variables for local development.

## Installation

1.  Clone the repository:
    git clone https://github.com/uhsr/QuantumWatch.git
2.  Navigate to the project directory:
    cd QuantumWatch
3.  Install dependencies:
    npm install
4.  Configure environment variables (see Configuration section).
5.  Compile Typescript code:
    npm run build
6.  Deploy the serverless functions to your chosen platform (AWS Lambda, Google Cloud Functions). Follow the platform's documentation for deployment.
7.  Set up the database (DynamoDB, Firestore) and configure connection details in the environment variables.

## Configuration

The following environment variables are required for running QuantumWatch:

*   `EXCHANGE_API_KEY`: API key for accessing the cryptocurrency exchange.
*   `EXCHANGE_API_SECRET`: API secret for accessing the cryptocurrency exchange.
*   `NOTIFICATION_SERVICE_API_KEY`: API key for the notification service (Twilio, SendGrid).
*   `NOTIFICATION_SERVICE_SENDER_EMAIL` (or `NOTIFICATION_SERVICE_SENDER_PHONE`): Sender email address or phone number for sending notifications.
*   `DATABASE_URL`: URL for connecting to the database (DynamoDB, Firestore).
*   `LAMBDA_FUNCTION_ARN`: ARN of the serverless function triggered by alerts.
*   `LOG_LEVEL`: Sets the log level (e.g., INFO, DEBUG, ERROR).
*   `COIN_LIST`: Comma separated list of coins you wish to monitor.
    Example: BTC-USD,ETH-USD
 These variables can be set in a `.env` file in the root of the project for local development, and configured through the serverless platform's console for production deployments.

## Usage

1.  Define alert rules in the database, specifying the cryptocurrency symbol, threshold type (e.g., price above, price below), and threshold value.
2.  Start the QuantumWatch application. It will establish Websocket connections to the specified exchanges and begin monitoring prices.
    npm start
3.  When a threshold is breached, the serverless function will be triggered, sending a notification to the user.

Example alert rule (JSON):

{
"userId": "user123",
"coinPair": "BTC-USD",
"thresholdType": "priceAbove",
"thresholdValue": 60000,
"notificationChannel": "email"
}

Example serverless function payload (JSON):

{
"coinPair": "BTC-USD",
"thresholdType": "priceAbove",
"thresholdValue": 60000,
"currentPrice": 60500,
"userId": "user123"
}

## Contributing

We welcome contributions to QuantumWatch! Please follow these guidelines:

1.  Fork the repository.
2.  Create a new branch for your feature or bug fix.
3.  Write clear, concise, and well-documented code.
4.  Submit a pull request with a detailed description of your changes.
5.  Ensure all tests pass and that the code adheres to the project's coding style.

## License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/uhsr/QuantumWatch/blob/main/LICENSE) file for details.

## Acknowledgements

We would like to acknowledge the contributions of the open-source community and the developers of the libraries and tools used in this project.