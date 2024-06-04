Here's the SQL code to accomplish the tasks:

### 1. Create the CRICKETERS table:
```sql
CREATE TABLE CRICKETERS (
    Country VARCHAR2(50) NOT NULL,
    Name VARCHAR2(20) NOT NULL,
    Runs NUMBER,
    Wickets NUMBER,
    Catches NUMBER,
    "Date-of-birth" DATE,
    CONSTRAINT CRICKETERS_PK PRIMARY KEY (Country, Name)
);
```

### 2. Modify the CRICKETERS table:
#### (a) Add a field centuries:
```sql
ALTER TABLE CRICKETERS
ADD centuries NUMBER;
```

#### (b) Add a field fives:
```sql
ALTER TABLE CRICKETERS
ADD fives NUMBER;
```

#### (c) Add a field caption:
```sql
ALTER TABLE CRICKETERS
ADD caption VARCHAR2(3);
```

### 3. Create the Transaction table:
```sql
CREATE TABLE Transaction (
    Acc_no NUMBER(4),
    T_date DATE DEFAULT SYSDATE,
    T_type CHAR(1) CHECK (T_type IN ('D', 'W')),
    T_mode VARCHAR2(6) CHECK (T_mode IN ('Cheque', 'Cash')),
    Cheque_no VARCHAR2(7),
    Operator VARCHAR2(20),
    Drawn_bank VARCHAR2(30),
    T_amount NUMBER(7,2),
    Clear CHAR(1) CHECK (Clear IN ('Y', 'N')),
    CONSTRAINT Transaction_PK PRIMARY KEY (Acc_no, T_date),
    CONSTRAINT Transaction_FK FOREIGN KEY (Acc_no) REFERENCES Account(Acc_no)
);
```

### 4. Insert data into the tables:
```sql
-- Insert data into CRICKETERS table
INSERT INTO CRICKETERS (Country, Name, Runs, Wickets, Catches, "Date-of-birth", centuries, fives, caption)
VALUES ('India', 'Virat Kohli', 12000, 10, 50, TO_DATE('1988-11-05', 'YYYY-MM-DD'), 27, 2, 'Y');

-- Insert data into Transaction table
INSERT INTO Transaction (Acc_no, T_type, T_mode, Cheque_no, Operator, Drawn_bank, T_amount, Clear)
VALUES (1001, 'D', 'Cheque', '1234567', 'John Doe', 'ABC Bank', 5000, 'Y');
```

These SQL commands create the required tables, modify the CRICKETERS table to add new fields, and insert some sample data into the tables. Adjust the data according to your specific requirements.