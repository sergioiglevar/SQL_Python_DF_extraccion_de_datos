# Orders Data Extraction and Analysis

## Table of Contents
- [Introduction](#introduction)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Database Connection](#database-connection)
- [Usage](#usage)
- [Exercises Overview](#exercises-overview)
- [License](#license)
- [Contact](#contact)

## Introduction

Welcome to the **Orders Data Extraction and Analysis** project! This project involves extracting data from the "pedidos" (orders) MySQL database, processing it using Python and Pandas, and presenting it in well-structured DataFrames for insightful analysis. Whether you're a data analyst, a developer, or a project manager, this project demonstrates effective data handling and visualization techniques.

## Features

- **Database Interaction**: Connects to a MySQL database to fetch and manipulate order-related data.
- **Data Processing**: Utilizes Python and Pandas to create and manage DataFrames for better data representation.
- **Comprehensive Analysis**: Includes 15 detailed exercises that cover various aspects of data querying and analysis.
- **Structured Reporting**: Outputs are organized for clarity, facilitating easy interpretation and decision-making.

## Technologies Used

- **Programming Language**: Python
- **Database**: MySQL
- **Libraries**:
  - `mysql-connector-python`
  - `pandas`
- **Development Environment**: Visual Studio Code

## Prerequisites

Before you begin, ensure you have met the following requirements:

- **Python** installed on your machine. You can download it from [here](https://www.python.org/downloads/).
- **MySQL Server** set up with access credentials. If you don't have one, you can download MySQL [here](https://dev.mysql.com/downloads/).
- **Visual Studio Code** installed. Download it from [here](https://code.visualstudio.com/).
- Basic knowledge of SQL and Python.

## Installation

1. **Clone the Repository**

   ```bash
   git clone https://github.com/yourusername/orders-data-extraction.git
   cd orders-data-extraction
   ```

2. **Install Required Python Libraries**

   Open your terminal in the project directory and run:

   ```bash
   pip install mysql-connector-python pandas
   ```

   *Note: You may need to restart your development environment or terminal to recognize the newly installed packages.*

   To update `pip` to the latest version, execute:

   ```bash
   python -m pip install --upgrade pip
   ```

## Database Connection

To establish a connection between Python and your MySQL database, follow these steps:

1. **Import Required Libraries**

   ```python
   import mysql.connector
   from mysql.connector import Error
   import pandas as pd
   ```

2. **Database Connection Script**

   Replace the placeholders with your actual database credentials:

   ```python
   try:
       connection = mysql.connector.connect(
           host='your_host',
           database='pedidos',
           user='your_username',
           password='your_password',
           connection_timeout=180
       )

       if connection.is_connected():
           db_info = connection.get_server_info()
           print(f"Connected to MySQL database... MySQL Server version on {db_info}")

           cursor = connection.cursor()
           connection.commit()

   except Error as e:
       print(f"Error while connecting to MySQL: {e}")
   finally:
       if connection.is_connected():
           cursor.close()
           connection.close()
           print("MySQL connection is closed")
   ```

   **Sample Output:**
   ```
   Connected to MySQL database... MySQL Server version on 8.0.36-28
   MySQL connection is closed
   ```

## Usage

This project comprises a series of exercises that demonstrate various data extraction and analysis techniques using SQL queries and Python's Pandas library. Below is an overview of each exercise, including the objectives and sample outputs.

### Exercise 1: Retrieve and Display Product Data

- **Objective**: Fetch all records from the `PRODUCTO` table and display them as a Pandas DataFrame.
- **Sample Output**:
  
  | Codigo | Nombre                           | Precio |
  |--------|----------------------------------|--------|
  | 01     | Hamburguesa                      | 2.6    |
  | 02     | Patatas                          | 2.0    |
  | ...    | ...                              | ...    |
  
- **Export to CSV**:

  ```python
  df1.to_csv('producto.csv', index=False)
  ```

### Exercise 2: Employees with Salaries Between €900 and €1000

- **Objective**: Retrieve employees earning between €900 and €1000 and display them sorted by salary in descending order.
  
  | DNI        | Nombre               | Nss         | Turno  | Salario |
  |------------|----------------------|-------------|--------|---------|
  | 14111155T  | Sergio Lérida Campos | 55577700089 | tarde  | 1000.0  |
  | ...        | ...                  | ...         | ...    | ...     |

### Exercise 3: Orders Taken After 7 PM

- **Objective**: Fetch order numbers, delivery person DNI, and delivery time for orders noted after 7 PM.
  
  | numero_pedido | dni_repartidor | hora_reparto       |
  |---------------|-----------------|--------------------|
  | 0005          | 14188151T       | 0 days 19:45:00    |
  | ...           | ...             | ...                |

### Exercise 4: Orders in November 2020 with Importe > €15

- **Objective**: Retrieve order numbers and amounts for orders placed in November 2020 with an importe greater than €15.
  
  | numero_pedido | importe |
  |---------------|---------|
  | 0006          | 23.0    |
  | ...           | ...     |

### Exercise 5: Total Orders Delivered by Each Repartidor

- **Objective**: List each delivery person's DNI along with the total number of orders they have delivered.
  
  | DNI_R      | TOTAL_PEDIDOS_REPARTIDOS |
  |------------|--------------------------|
  | 04477744T  | 2                        |
  | ...        | ...                      |

### Exercise 6: Monthly Order Counts

- **Objective**: Display the number of orders made each month using month names.
  
  | Mes       | numero de pedidos |
  |-----------|-------------------|
  | October   | 2                 |
  | ...       | ...               |

### Exercise 7: Employees Working 'tarde' or 'noche' Shifts

- **Objective**: List employees' DNI and names who work in the 'tarde' or 'noche' shifts, sorted by DNI.
  
  | empleado_dni_nombre           | Turno  |
  |-------------------------------|--------|
  | 03232323P, María Luisa Galdón Ter | noche |
  | ...                           | ...    |

### Exercise 8: Products Priced Above or Equal to the Average

- **Objective**: Retrieve product names, codes, and prices that are above or equal to the average price, sorted by price descending.
  
  | Nombre                         | Codigo | Precio |
  |--------------------------------|--------|--------|
  | Menú de Hamburguesa con queso  | 12     | 6.0    |
  | ...                            | ...    | ...    |

### Exercise 9: Employees Who Have Never Prepared an Order

- **Objective**: List names and DNIs of employees who have never prepared any orders.
  
  | Nombre               | DNI          |
  |----------------------|--------------|
  | Luis Ramírez Pardo   | 11111111Q    |
  | ...                  | ...          |

### Exercise 10: Products in Orders Taken by Specific Employees

- **Objective**: Fetch product codes, combined names and prices for products included in orders taken by "Luis" or "María Luisa", sorted by order date descending.
  
  | Codigo | Nombre_Precio                 | fecha      |
  |--------|-------------------------------|------------|
  | 02     | Patatas - 2.00                 | 2020-09-05 |
  | ...    | ...                           | ...        |

### Exercise 11: Delivery Person Performance

- **Objective**: For each delivery person, display their name, number of orders delivered, and average delivery time in minutes, sorted by average time.
  
  | Repartidor               | Cantidad_Pedidos | Tiempo_Medio_Minutos |
  |--------------------------|-------------------|----------------------|
  | Carmen Capel Pío         | 0                 | NaN                  |
  | ...                      | ...               | ...                  |

### Exercise 12: Cheapest and Most Expensive Products

- **Objective**: List products with the minimum and maximum prices.
  
  | Codigo | Nombre   | Precio |
  |--------|----------|--------|
  | 03     | tomate   | 0.5    |
  | ...    | ...      | ...    |

### Exercise 13: Products in Multiple Orders

- **Objective**: For each product, show the number of orders it appears in, provided it is included in two or more orders, sorted by the number of orders descending.
  
  | Codigo | Nombre                           | Total_Pedidos |
  |--------|----------------------------------|---------------|
  | 12     | Menú de Hamburguesa con queso    | 6             |
  | ...    | ...                              | ...           |

### Exercise 14: Employees Who Handled Specific Products with Specific Repartidors

- **Objective**: List employees (code and NSS) who have handled orders containing product code 13 and were delivered by 'Laura'.
  
  | Codigo_NSS          |
  |---------------------|
  | 77777777M - 23456785432 |
  | ...                 |

### Exercise 15: Menu Products in September 2020 Orders

- **Objective**: Display menu product names along with their component product codes for orders placed in September 2020.
  
  | Nombre_Menu                   | Codigo_Producto |
  |-------------------------------|------------------|
  | Menú de Hamburguesa con queso | 01               |
  | ...                           | ...              |

## Exercises Overview

The project includes 15 exercises that demonstrate how to perform various data extraction and analysis tasks using SQL and Python. Each exercise includes:

- **Objective**: What the exercise aims to achieve.
- **SQL Query**: The SQL statement used to retrieve the data.
- **Python Code**: How to execute the query and process the results using Pandas.
- **Sample Output**: An example of the DataFrame output for clarity.

These exercises cover a range of topics, including data retrieval, aggregation, joins, subqueries, and data transformation.

## License

This project is licensed under the [MIT License](LICENSE). You are free to use, modify, and distribute this project as per the license terms.

## Contact

For any inquiries or suggestions, please reach out to:

- **Name**: Your Name
- **Email**: your.email@example.com
- **LinkedIn**: [Your LinkedIn Profile](https://www.linkedin.com/in/yourprofile/)
- **GitHub**: [yourusername](https://github.com/yourusername)

---

*Happy Data Analyzing!*