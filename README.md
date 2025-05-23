# rede-social-pets
Modelo de dados para uma rede social de pets (cachorros e gatos)
erDiagram
    DONO ||--o{ PET : possui
    DONO ||--o{ POSTAGEM : cria
    DONO ||--o{ EVENTO : organiza
    DONO ||--o{ PARTICIPACAO_EVENTO : participa
    DONO ||--o{ CURTIDA : curte
    PET ||--o{ AMIZADE : conecta
    DONO ||--o{ AMIZADE : conecta
    POSTAGEM ||--o{ CURTIDA : recebe
    EVENTO ||--o{ PARTICIPACAO_EVENTO : possui

    DONO {
        int dono_id PK
        string nome
        string email
        string senha
        date data_cadastro
    }

    PET {
        int pet_id PK
        int dono_id FK
        string nome
        string tipo
        string raca
        date data_nascimento
    }

    AMIZADE {
        int amizade_id PK
        int origem_id FK
        int destino_id FK
        string tipo
        date data_amizade
    }

    POSTAGEM {
        int postagem_id PK
        int dono_id FK
        string conteudo
        datetime data_postagem
    }

    CURTIDA {
        int curtida_id PK
        int postagem_id FK
        int dono_id FK
        datetime data_curtida
    }

    EVENTO {
        int evento_id PK
        int dono_id FK
        string nome
        string descricao
        datetime data_evento
        string local
    }

    PARTICIPACAO_EVENTO {
        int participacao_id PK
        int evento_id FK
        int dono_id FK
        datetime data_inscricao
    }
