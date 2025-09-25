# 🛒 Marketplace + Logística

Plataforma de e-commerce donde **Vendedores** ponen a la venta **Productos** y **Clientes** realizan compras.  
Un **Usuario** puede ser Cliente, Vendedor o ambos.

---

## 👤 Usuarios
- **Usuario** (base)  
  - id_usuario, nombre, email, roles, fecha_registro  
- **Cliente**  
  - direcciones de envío, historial de pedidos  
- **Vendedor**  
  - tiendas, almacenes, reputación, catálogo  

---

## 📦 Catálogo de Productos
- **Categoría** (jerárquica: categoría → subcategoría → …)  
- **Producto**  
  - id_producto, vendedor, categoría, descripción  
- **Variante**  
  - id_variante, atributos (ej.: talla, color)  
- **Historial de precios**  
  - variante, fecha_inicio, fecha_fin, precio, motivo  

---

## 🏬 Inventario y Almacenes
- **Almacén**  
  - id_almacén, vendedor, ubicación, tipo (propio / proveedor)  
- **Stock**  
  - variante, almacén, cantidad_disponible, cantidad_reservada  

---

## 📑 Pedidos
- **Pedido**  
  - id_pedido, cliente, fecha_creación, estado, dirección_envío  
- **Línea de pedido (Order Item)**  
  - pedido, variante, cantidad, precio_unitario, promo_aplicada  
- **Envío (Shipment)**  
  - pedido, almacén/proveedor, estado_envío, fecha_envío  
- **Items en Envío**  
  - vínculo entre shipment ↔ líneas de pedido  

---

## 💳 Pagos
- **Pago**  
  - pedido, método, monto, estado, fecha  
- **Intento de pago**  
  - referencia pasarela, resultado, timestamp  
- **Reembolso / Nota de crédito**  
  - parcial o total, vinculado a pagos/líneas  

---

## 🔄 Devoluciones
- **Devolución**  
  - id_devolución, pedido, línea, motivo, estado, fecha, reembolso_asociado  

---

## 🎟️ Promociones y Cupones
- **Promoción / Cupón**  
  - id_promoción, tipo (producto, categoría, vendedor, pedido)  
  - condiciones (mínimo compra, fecha_inicio/fin)  
  - beneficio: descuento %, monto fijo, envío gratis  

---

## ⭐ Reseñas y Reputación
- **Reseña de Producto**  
  - cliente, producto, calificación, comentario, fecha  
- **Reputación de Vendedor**  
  - métrica agregada (reseñas, tiempos de entrega, cancelaciones)  

---

## 📝 Auditoría
- **Log de Auditoría**  
  - usuario, acción, entidad, fecha, cambios críticos  

---

## 📏 Reglas de Negocio
1. **Reserva de stock** cuando se crea pedido.  
2. **Cancelación automática** si no hay pago en ventana de X minutos.  
3. **Bloqueo de envío** si stock insuficiente en almacén correspondiente.  
4. **Máximos de compra** por cliente por producto (ej.: 5 unidades).  
5. **Registro de logs** en cambios de stock y pedidos.  

---

## 📊 Reportes Frecuentes
- Ventas por día / región / vendedor  
- Productos sin stock  
- Pedidos pendientes de pago  
- Rendimiento de promociones  
- Reputación de vendedores  

---
