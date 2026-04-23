```mermaid
classDiagram
    %% 연관관계 및 다중성 설정
    Account "1..*" --> "1" User : 사용자 조회
    
    %% BankUI에서 Account로의 의존관계 설정
    BankUI ..> Account : 의존 (Dependency)

    class BankUI {
        <<Boundary>>
    }

    class User {
        - id: String
        - pw: String
        - name: String
        - phone: String
        - address: String
        + registerUser(id: String, pw: String, name: String, phone: String, address: String) boolean
        + updateUser(id: String, pw: String, name: String, phone: String, address: String) boolean
        + deleteUser(id: String) boolean
        + searchUser(id: String) boolean
    }

    class Account {
        - number: String
        - balance: long
        + deposit(userId: String, amount: long) boolean
        + withdraw(userId: String, amount: long) boolean
        + transfer(userId: String, toAccount: String, amount: long) boolean
        + computeBalance() long
    }
