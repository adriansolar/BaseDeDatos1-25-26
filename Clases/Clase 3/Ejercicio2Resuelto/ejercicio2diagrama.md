erDiagram
    %% ==== USUARIOS ====
    Usuario ||--o{ Cliente : "puede ser"
    Usuario ||--o{ Vendedor : "puede ser"

    %% ==== CATALOGO ====
    Vendedor ||--o{ Producto : "publica"
    Producto ||--o{ Variante : "tiene"
    Categoria ||--o{ Producto : "clasifica"
    Variante ||--o{ HistorialPrecio : "registra"

    %% ==== INVENTARIO ====
    Vendedor ||--o{ Almacen : "gestiona"
    Almacen ||--o{ Stock : "mantiene"
    Variante ||--o{ Stock : "pertenece"

    %% ==== PEDIDOS ====
    Cliente ||--o{ Pedido : "crea"
    Pedido ||--o{ LineaPedido : "contiene"
    LineaPedido ||--o{ Variante : "refiere"
    Pedido ||--o{ Envio : "puede dividirse en"
    Envio ||--o{ EnvioItem : "incluye"
    EnvioItem }o--|| LineaPedido : "asocia"

    %% ==== PAGOS ====
    Pedido ||--o{ Pago : "tiene"
    Pago ||--o{ IntentoPago : "puede tener"
    Pago ||--o{ Reembolso : "genera"

    %% ==== DEVOLUCIONES ====
    LineaPedido ||--o{ Devolucion : "puede tener"
    Devolucion }o--|| Reembolso : "genera"

    %% ==== PROMOCIONES ====
    Promocion ||--o{ LineaPedido : "aplica a"
    Promocion ||--o{ Producto : "puede aplicar"
    Promocion ||--o{ Categoria : "puede aplicar"
    Promocion ||--o{ Vendedor : "puede aplicar"

    %% ==== RESEÑAS ====
    Cliente ||--o{ Reseña : "escribe"
    Reseña }o--|| Producto : "sobre"
    Vendedor ||--o{ Reputacion : "acumula"

    %% ==== AUDITORIA ====
    Usuario ||--o{ LogAuditoria : "genera"
    LogAuditoria }o--|| Pedido : "sobre"
    LogAuditoria }o--|| Stock : "sobre"
