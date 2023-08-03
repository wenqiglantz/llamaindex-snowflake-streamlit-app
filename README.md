# llamaindex-snowflake-streamlit-app

Integrating LlamaIndex into Snowflake and Streamlit app.

Refer to my blog [Exploring Snowflake and Streamlit With LlamaIndex Text-to-SQL](https://betterprogramming.pub/exploring-snowflake-and-streamlit-with-llamaindex-text-to-sql-f66fec6e321b?sk=97360acceef5ee331b5ac8a9663ce590) for details.

## Application Setup

```
conda create --name py38_env
conda activate py38_env
pip install -r requirements.txt
```
Please note, the version incompatibility error is expected.  There is a [known issue](https://github.com/snowflakedb/snowflake-sqlalchemy/issues/380) with ```snowflake-sqlalchem``` library.  Until that issue is resolved, we continue with our [workaround](https://github.com/snowflakedb/snowflake-sqlalchemy/issues/380#issuecomment-1470762025) from the ```utils.py``` file.  When we trigger the following ```streamlit run``` command to start our app, the workaround will take effect, thus allowing us to run our app in Streamlit to query Snowflake data using text-to-SQL.


Add `.env` file at the project root and replace placeholder with your API key:
```
OPENAI_API_KEY=<YOUR-API-KEY>
```

Add `credentials.json` at the project root, replace placeholders with your Snowflake connection details:
```
{
  "account": "<YOUR-ORG>-<YOUR-ACCOUNT>",
  "user": "<YOUR-USER-NAME>",
  "role": "ACCOUNTADMIN",
  "password": "*******",
  "warehouse": "COMPUTE_WH",
  "database": "ORGANIZATIONS",
  "schema": "PUBLIC"
}
```

Run the app by kicking off this command:
```
streamlit run orgs.py
```
