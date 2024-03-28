The LOANS table stores information about loans taken by customers. It includes fields like loan ID, account number, loan type, amount, interest rate, start date, and end date. The account number is a foreign key referencing the ACCOUNT_INFO table.
The PAYMENTS table records payments made towards loans. It includes fields like payment ID, loan ID, payment date, and amount. The loan ID is a foreign key referencing the LOANS table.
The BILL_PAYMENTS table stores information about payments made for bills. It includes fields like bill payment ID, account number, biller name, amount, and payment date. The account number is a foreign key referencing the ACCOUNT_INFO table.
The BENEFICIARIES table maintains a list of beneficiaries for fund transfers. It includes fields like beneficiary ID, account number, beneficiary name, and beneficiary account number. The account number is a foreign key referencing the ACCOUNT_INFO table.
The MESSAGES table stores messages sent between customers. It includes fields like message ID, sender ID, receiver ID, message text, and send date. Sender ID and receiver ID are foreign keys referencing the CUSTOMER_PERSONAL_INFO table.
With these additional tables, the database design now includes a broader range of functionalities for an online bank management system, such as handling loans, bill payments, beneficiaries, and messaging between customers.

ER DIAGRAM
This diagram represents the entities (tables), their attributes (columns), and the relationships between them. 
Relationships are depicted using lines connecting the related entities, with notation indicating the cardinality and participation
 constraints where applicable (e.g., 1:N, 1:1, etc.). Primary keys (PK) are indicated for each entity. Foreign keys (FK) are indicated 
 where there are relationships between entities.

 
   +------------------+           +-----------------+           +------------------+
   |   CUSTOMER       |           |   BANK_INFO     |           |   LOANS          |
   +------------------+           +-----------------+           +------------------+
   | CUSTOMER_ID (PK) |           | IFSC_CODE (PK)  |           | LOAN_ID (PK)     |
   | CUSTOMER_NAME    |           | BANK_NAME       |           | ACCOUNT_NO (FK)  |
   | DATE_OF_BIRTH    |           | BRANCH_NAME     |           | LOAN_TYPE        |
   | GUARDIAN_NAME    |           |                 |           | AMOUNT           |
   | ADDRESS          |           |                 |           | INTEREST_RATE    |
   | CONTACT_NO       |           |                 |           | START_DATE       |
   | MAIL_ID          |           |                 |           | END_DATE         |
   | GENDER           |           |                 |           +------------------+
   | MARITIAL_STATUS  |           +-----------------+
   | IDENTIFICATION_  |
   | DOC_TYPE         |
   | ID_DOC_NO        |
   | CITIZENSHIP      |
   +------------------+


    +-----------------------+           +-------------------+
    |   CUSTOMER_REFERENCE |           |   ACCOUNT_INFO    |
    +-----------------------+           +-------------------+
    | CUSTOMER_ID (PK, FK) |           | ACCOUNT_NO (PK)   |
    | REFERENCE_ACC_NAME   |           | CUSTOMER_ID (FK)  |
    | REFERENCE_ACC_NO     |           | ACCOUNT_TYPE      |
    | REFERENCE_ACC_ADDRESS|           | REGISTRATION_DATE |
    | RELATION             |           | ACTIVATION_DATE   |
    +-----------------------+           | IFSC_CODE (FK)    |
                                         | INTEREST          |
                                         | INITIAL_DEPOSIT   |
                                         +-------------------+


   +------------------+           +---------------+
   |   TRANSACTIONS   |           | LOGIN_CRED    |
   +------------------+           +---------------+
   | TRANSACTION_ID   |           | USERNAME (PK) |
   | ACCOUNT_NO (FK)  |           | PASSWORD      |
   | TRANSACTION_DATE |           | ACCOUNT_NO(FK)|
   | TRANSACTION_TYPE |           +---------------+
   | AMOUNT           |
   | DESCRIPTION      |
   +------------------+

    +------------------+           +---------------+
    |   PAYMENTS       |           | SESSIONS      |
    +------------------+           +---------------+
    | PAYMENT_ID (PK)  |           | SESSION_ID (PK) |
    | LOAN_ID (FK)     |           | USERNAME (FK)   |
    | PAYMENT_DATE     |           | TOKEN           |
    | AMOUNT           |           | EXPIRY_DATETIME |
    +------------------+           +---------------+

    +------------------+           +-------------------+
    |   BILL_PAYMENTS  |           | BENEFICIARIES     |
    +------------------+           +-------------------+
    | BILL_PAYMENT_ID  |           | BENEFICIARY_ID (PK)|
    | ACCOUNT_NO (FK)  |           | ACCOUNT_NO (FK)    |
    | BILLER_NAME      |           | BENEFICIARY_NAME   |
    | AMOUNT           |           | BENEFICIARY_ACC_NO |
    | PAYMENT_DATE     |           +-------------------+
    +------------------+


    +------------------+           +-------------------+
    |   MESSAGES       |           |                   |
    +------------------+           +-------------------+
    | MESSAGE_ID (PK)  |           |                   |
    | SENDER_ID (FK)   |           |                   |
    | RECEIVER_ID (FK) |           |                   |
    | MESSAGE_TEXT     |           |                   |
    | SEND_DATE        |           |                   |
    +------------------+           +-------------------+
