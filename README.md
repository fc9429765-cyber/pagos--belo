# 💳 Pasarela de Pagos Automática (Belo)

Este repositorio contiene la configuración automática para procesar cobros en criptomonedas utilizando la plataforma Belo.

## 📊 Configuración de la Base de Datos (SQL)
Si necesitas registrar las redes autorizadas en tu base de datos, ejecuta este comando:

```sql
CREATE TABLE crypto_gateways (
    id INT AUTO_INCREMENT PRIMARY KEY,
    ticker VARCHAR(10) NOT NULL,
    asset_name VARCHAR(50) NOT NULL,
    blockchain_network VARCHAR(50) NOT NULL,
    is_active BOOLEAN DEFAULT TRUE
);

INSERT INTO crypto_gateways (ticker, asset_name, blockchain_network) VALUES 
('BTC', 'Bitcoin', 'Bitcoin (Legacy)'),
('SOL', 'Solana', 'Solana');
```

## 🐍 Script de Lectura Automatizada (Python)
Para que el servidor procese el archivo de configuración de forma automática:

```python
import yaml

# Carga automática del archivo universal de redes
with open("belo_gateway.yaml", "r") as file:
    config = yaml.safe_load(file)

print(f"Estado de la pasarela: {config['gateway']['status']}")
```

> [!WARNING]
> **Nota de seguridad:** Asegúrate siempre de que el cliente envíe los fondos usando las redes especificadas arriba (Bitcoin Legacy o Solana). El uso de redes incorrectas causará la pérdida total de los activos.
