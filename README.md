#  PEDIDOS - RESTAURANTE

# Matriz del menú:
# [Nombre del Producto, Categoría, Precio Base]

menu = [
    ["Hamburguesa BBQ", "Comida Rápida", 28000],
    ["Pizza Hawaiana", "Comida Rápida", 35000],
    ["Ensalada César", "Saludable", 18000],
    ["Salmón a la Plancha", "Mariscos", 52000],
    ["Lasaña Mixta", "Pastas", 30000],
    ["Camarones al Ajillo", "Mariscos", 45000]
]

# Categoría objetivo para promoción
categoria_objetivo = "Mariscos"

# Umbral mínimo para aplicar descuento
umbral_precio = 40000



# FUNCIÓN PARA CALCULAR PRECIO FINAL

def calcular_precio_final(categoria, precio_base):

    if categoria == categoria_objetivo and precio_base > umbral_precio:
        descuento = precio_base * 0.15
        precio_final = precio_base - descuento
    else:
        precio_final = precio_base

    return precio_final



# MOSTRAR MENÚ

print("-------- MENÚ DEL RESTAURANTE --------\n")

for i, producto in enumerate(menu):
    print(f"{i + 1}. {producto[0]} - ${producto[2]:,.0f}")

print("\n--------------------------")



# VALIDACIÓN DE DATOS


while True:

    opcion = input("\nIngrese el número del producto que desea pedir: ")

    # Validar que el dato sea numérico
    if not opcion.isdigit():
        print("ERROR: Debe ingresar solo números.")
        continue

    opcion = int(opcion)

    # Validar rango válido
    if opcion < 1 or opcion > len(menu):
        print("ERROR: Debe seleccionar un producto válido del menú.")
        continue

    # Si todo está correcto, salir del ciclo
    break



# OBTENER PRODUCTO


producto = menu[opcion - 1]

nombre = producto[0]
categoria = producto[1]
precio_base = producto[2]

# Calcular precio final
precio_final = calcular_precio_final(categoria, precio_base)


# MOSTRAR FACTURA


print("\n----- FACTURA ---------")
print(f"Producto: {nombre}")
print(f"Categoría: {categoria}")
print(f"Precio Base: ${precio_base:,.0f}")
print(f"Precio Final: ${precio_final:,.0f}")

# Mostrar promoción
if precio_final < precio_base:
    print("Promoción aplicada: 15% de descuento")
else:
    print("Este producto no tiene promoción")

print("--------------------")
