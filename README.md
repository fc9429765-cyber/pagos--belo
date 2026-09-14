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

import yaml

# Carga automática del archivo universal
with open("belo_gateway.yaml", "r") as file:
    config = yaml.safe_load(file)

print(f"Estado de la pasarela: {config['gateway']['status']}")


