# BigQuery MCP Server Showcase

## Project Overview

This project demonstrates the setup and configuration of a BigQuery MCP (Model Context Protocol) Server, enabling a Large Language Model (LLM) like Claude to interact directly with Google BigQuery. This allows for natural language querying of BigQuery data, streamlining data analysis and removing the need for manual SQL query writing.

This repository documents my personal journey in setting up this server, the challenges I faced, and the knowledge I gained.

## My Project Journey

### Motivation

*I was motivated to undertake this project to explore the intersection of Large Language Models and data analytics. The ability to query vast datasets using natural language is a powerful concept, and I wanted to gain hands-on experience with the technologies that make it possible.*

### Key Learnings

*   **BigQuery:** I gained practical experience with Google BigQuery, including setting up projects, managing datasets, and understanding the necessary permissions for data access.
*   **MCP Server:** I learned about the Model Context Protocol (MCP) and its role as a bridge between LLMs and data sources. I successfully configured and ran the `mcp-bigquery-server`.
*   **Authentication:** I learned how to authenticate with Google Cloud using both the gcloud CLI and service account keys, and I understand the security implications of each method.
*   **LLM Integration:** I successfully connected the MCP server to Claude, enabling it to query my BigQuery data.

### Challenges

*One of the challenges I faced was ensuring the correct IAM permissions were in place for the service account. I troubleshooted this by carefully reviewing the BigQuery documentation and the error messages from the MCP server, eventually granting the correct roles (`roles/bigquery.user`) to the service account.*

### Custom Modifications

*(This is a great place to mention any custom modifications you made. For example, did you write any scripts to automate the setup? Did you experiment with different query types?)*

## Setup and Configuration

These are the steps I followed to set up the BigQuery MCP Server:

1.  **Prerequisites:**
    *   Node.js (v14 or higher)
    *   Google Cloud project with BigQuery enabled
    *   Google Cloud CLI or a service account key file
    *   Claude Desktop

2.  **Authentication:** I authenticated with Google Cloud using a service account key. I created a service account, granted it the `roles/bigquery.user` role, and downloaded the key file.

3.  **Configuration:** I configured Claude Desktop to use the MCP server by adding the following to my `claude_desktop_config.json`:

    ```json
    {
      "mcpServers": {
        "bigquery": {
          "command": "npx",
          "args": [
            "-y",
            "@ergut/mcp-bigquery-server",
            "--project-id",
            "your-project-id",
            "--location",
            "us-central1",
            "--key-file",
            "/path/to/your/service-account-key.json"
          ]
        }
      }
    }
    ```

    **Note:** I have added my service account key file to the `.gitignore` file to prevent it from being committed to this repository.

## Original Project

This project is based on the [ergut/mcp-bigquery-server](https://github.com/ergut/mcp-bigquery-server) repository.
