# ------------------------------
# MENÚ DE RESTAURANTE
# ------------------------------

# Matriz del menú:
# [Nombre del Producto, Categoría, Precio Base]

menu = [
    ["Hamburguesa", "Comida Rápida", 25000],
    ["Pizza Napolitana", "Comida Rápida", 20000],
    ["Ensalada César", "Saludable", 25000],
    ["Salmón Grillado", "Mariscos", 48000],
    ["Limonada de coco", "Bebidas", 15000],
    ["Pasta Alfredo", "Italiana", 35000]
]

# Categoría objetivo para aplicar promoción
categoria_objetivo = "Comida Rápida"

# Umbral mínimo del precio base
umbral_precio = 20000

# ------------------------------------
# MÓDULO PARA CALCULAR PRECIO FINAL
# ------------------------------------
def calcular_precio_final(categoria, precio_base):
    
    # Verifica si cumple condiciones
    if categoria == categoria_objetivo and precio_base > umbral_precio:
        
        descuento = precio_base * 0.15
        precio_final = precio_base - descuento
        
    else:
        precio_final = precio_base

    return precio_final

# ------------------------------------------
# MOSTRAR RESULTADOS
# ------------------------------------------
print("----- MENÚ DEL RESTAURANTE -----\n")

for producto in menu:
    
    nombre = producto[0]
    categoria = producto[1]
    precio_base = producto[2]

    # Llamado al módulo
    precio_final = calcular_precio_final(categoria, precio_base)

    # Mostrar información
    print(f"Producto: {nombre}")
    print(f"Categoría: {categoria}")
    print(f"Precio Base: ${precio_base:,.0f}")
    print(f"Precio Final: ${precio_final:,.0f}")
    print("-" * 40)
