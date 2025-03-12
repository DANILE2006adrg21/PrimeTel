# PrimeTel

## 📱 Proyecto PrimeTel
PrimeTel es una aplicación para la venta y gestión de celulares. El proyecto incluye:
- **Frontend** - Interfaz de usuario para la compra y gestión de celulares.  
- **Backend** - API para manejar la lógica de negocio y las transacciones.  
- **Panel de Administración** - Panel para gestionar productos, usuarios y ventas.  

---

## 🚀 **Configuración del Sistema y Permisos**
Se configuraron permisos y grupos para mejorar la seguridad y la administración del proyecto:

### ✅ **Creación de grupos de usuarios**
Ejecuta los siguientes comandos para crear los grupos necesarios:
```bash
sudo groupadd desarrolladores
sudo groupadd admins
sudo groupadd soporte

✅ Agregar usuarios a los grupos
sudo usermod -aG desarrolladores nombre_usuario
sudo usermod -aG admins nombre_usuario
sudo usermod -aG soporte nombre_usuario

🔐 Permisos del Proyecto
Asignar permisos para que solo los desarrolladores puedan modificar el código y que los administradores tengan control completo:
sudo chown -R daniel:desarrolladores /home/daniel/proyectos/PrimeTel
sudo chmod -R 770 /home/daniel/proyectos/PrimeTel

💾 Script de Respaldo Automático
Se creó un script para realizar un respaldo automático de las configuraciones del sistema.

➡️ Crear el directorio para los respaldos
sudo mkdir -p /backup/etc_config
sudo chown :admins /backup/etc_config
sudo chmod 770 /backup/etc_config

➡️ Crear el script de respaldo
Crea el script en /usr/local/bin/respaldo_config.sh:
sudo nano /usr/local/bin/respaldo_config.sh

#!/bin/bash
# Script para hacer un respaldo de las configuraciones en /etc

# Directorio de destino del respaldo
BACKUP_DIR="/backup/etc_config"

# Crear el directorio si no existe
mkdir -p $BACKUP_DIR

# Usar rsync para copiar los archivos de configuración
rsync -av /etc/ $BACKUP_DIR

echo "Respaldo completado en $BACKUP_DIR"

Dale permisos de ejecución:
sudo chmod +x /usr/local/bin/respaldo_config.sh

🕒 Configurar Cron para respaldo automático
Para que el script se ejecute automáticamente todos los días a las 2:00 a.m.:

Abre el cron:
sudo crontab -e
Añade la siguiente línea al final del archivo:
0 2 * * * /usr/local/bin/respaldo_config.sh

🧪 Restauración desde el respaldo
Si necesitas restaurar una configuración desde el respaldo:
rsync -av /backup/etc_config/ /etc/

👥 Contribuciones
Desarrollador principal: Daniel y Carlos
Fecha de inicio: Marzo 2025
