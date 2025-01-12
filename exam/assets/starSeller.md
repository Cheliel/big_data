## Star model on sales :

```mermaid
erDiagram

    D_time          ||--|| H_time                    : Hierarchie
    D_delivery_time ||--|| H_time                    : Hierarchie
    D_customer      ||--|| H_customer                : Hierarchie
    D_product       ||--|| H_product_categorie_name  : Hierarchie
    D_seller        ||--|| H_seller                  : Hierarchie
    D_reviews       ||--|| H_creation                : Hierarchie
    D_reviews       ||--|| H_comment                 : Hierarchie
    D_reviews       ||--|| H_answer                  : Hierarchie
    D_reviews       ||--|| H_score                   : Hierarchie


    
    F_Sales           ||--|| D_time                    : Dimension
    F_Sales           ||--|| D_delivery_time           : Dimension
    F_Sales           ||--|| D_customer                : Dimension
    F_Sales           ||--|| D_product                 : Dimension
    F_Sales           ||--|| D_seller                  : Dimension
    F_Sales           ||--|| D_reviews                 : Dimension


    F_Sales {
 
        string order_id PK    
        string customer_id FK
        string customer_unique_id FK


        float64 approuvee            
        float64 envoyee             
        float64 livree               
        float64 estimee             

        float64 int_boleto          
        float64 int_credit_card     
        float64 int_debit_card      
        float64 int_voucher         
        float64 value_boleto        
        float64 value_credit_card   
        float64 value_debit_card    
        float64 value_voucher       


        int64 score               
        int32 answer              
        int32 creation            
        int16 comment             
    }

    D_time { 
        datetime purchase_timestamp
    }


    D_delivery_time {
        datetime approved_at
        datetime estimated_delivery
        datetime delivered_carrier
        datetime delivered_customer
    }

    D_customer {
        string customer_id
    }

    D_seller {
        string seller_id
    }

    D_product {
        string product_id
    }

    D_reviews {
        string order_id
    }

    H_seller {
        string stage
        string city
        string zip_code
    }

    H_customer {
        string stage
        string city
        string zip_code
        string customer_unique_id
    }

    H_score {
        int64 score_1
        int64 score_2
        int64 score_3
        int64 score_4
        int64 score_5
    }

    H_answer {
        int32 answer_1
        int32 answer_2
        int32 answer_3
        int32 answer_4
        int32 answer_5
    }

    H_comment {
        int16 comment_1
        int16 comment_2
        int16 comment_3
        int16 comment_4
        int16 comment_5
    }

    H_creation {
        int32 creation_1
        int32 creation_2
        int32 creation_3
        int32 creation_4
        int32 creation_5
    }



    H_product_categorie_name {
        string category_name
    }

    H_time {
        int32 annee
        int32 mois
        int32 semaine
        int32 jour
        int32 jour_semaine
        int32 heure
    }
