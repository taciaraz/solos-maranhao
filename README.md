# Mapeamento Digital de Solos do Maranhão – Scripts e Dados

Este repositório reúne os scripts e instruções utilizados no capítulo *"Mapeamento Digital de Solos do Maranhão: fundamentos, boas práticas e exemplos de mapeamento de classes e atributos"*.  
Ele está organizado para facilitar a reprodução dos resultados, com códigos separados para **granulometria** (execução no Google Earth Engine) e **classes de solo** (execução no R).

---

## 📂 Estrutura do repositório

- **`covariate-module`** – Módulos de covariáveis para o GEE.
- **`modeling`** – Scripts de modelagem preditiva.
- **`predicao-espacial`** – Scripts de predição espacial e exportação de mapas.
- **`classe-solo`** – Script em R para mapeamento de classes de solo.

---

## 🌱 Granulometria (GEE)

Os dados de treinamento para granulometria estão disponíveis no **SoilData**, no conjunto:

> *"Mapeamento Digital de Solos do Maranhão: fundamentos, boas práticas e exemplos de mapeamento de classes e atributos"*

Esse arquivo contém **489 amostras**, com teores de **areia**, **silte** e **argila**, além das variáveis transformadas por log-ratio:

- `log_clay_sand`: logaritmo da razão entre argila e areia  
- `log_silt_sand`: logaritmo da razão entre silte e areia  

### Execução
1. Acesse as pastas `covariate-module`, `modeling` e `predicao-espacial` neste repositório.
2. Copie os scripts para o editor do **[Google Earth Engine](https://code.earthengine.google.com/)**.
3. Siga a ordem indicada nos comentários dos scripts.
4. As covariáveis são carregadas diretamente do **MapBiomas Workspace**, não sendo necessário download prévio.

### Covariáveis utilizadas no GEE

| Nome da Covariável | Caminho do Asset |
|--------------------|------------------|
| Elevação (Elevation) | `MERIT/DEM/v1_0_3` |
| Declividade (Slope) | `projects/mapbiomas-workspace/SOLOS/COVARIAVEIS/OT_GEOMORPHOMETRY_90m` |
| Índice de Convergência (Convergence) | `projects/mapbiomas-workspace/SOLOS/COVARIAVEIS/OT_GEOMORPHOMETRY_90m` |
| Índice de Potência do Fluxo (SPI) | `projects/mapbiomas-workspace/SOLOS/COVARIAVEIS/OT_GEOMORPHOMETRY_90m` |
| Curvatura do relevo (Curvature) | `projects/mapbiomas-workspace/SOLOS/COVARIAVEIS/OT_GEOMORPHOMETRY_90m` |
| Rugosidade (Roughness) | `projects/mapbiomas-workspace/SOLOS/COVARIAVEIS/OT_GEOMORPHOMETRY_90m` |
| NDVI (Vegetação atual) | `projects/nexgenmap/MapBiomas2/LANDSAT/BRAZIL/mosaics-2` |
| Índice de minerais – Clay Minerals | `projects/mapbiomas-workspace/SOLOS/COVARIAVEIS/LANDSAT_CLAYMINERALS_BY_BYTE` |
| Índice de minerais – Oxides | `projects/mapbiomas-workspace/SOLOS/COVARIAVEIS/LANDSAT_OXIDES_BY_BYTE_v1` |
| Biomas brasileiros | `projects/mapbiomas-workspace/SOLOS/COVARIAVEIS/IBGE_BIOMAS_30M` |
| Fitofisionomias | `projects/mapbiomas-workspace/SOLOS/COVARIAVEIS/IBGE_2023_FITOFISIONOMIA_250MIL` |
| Köppen L1 | `projects/mapbiomas-workspace/SOLOS/COVARIAVEIS/IPEF_2013_KOPPEN_100M` |
| Köppen L2 | `projects/mapbiomas-workspace/SOLOS/COVARIAVEIS/IPEF_2013_KOPPEN_100M` |
| Köppen L3 | `projects/mapbiomas-workspace/SOLOS/COVARIAVEIS/IPEF_2013_KOPPEN_100M` |
| Classe litológica (Províncias geológicas) | `projects/mapbiomas-workspace/SOLOS/COVARIAVEIS/IBGE_PROVINCIAS_250MIL_DUMMY` |
| Mapa de solos (WRB – SoilGrids) | `projects/mapbiomas-workspace/SOLOS/COVARIAVEIS/WRB_ALL_SOILS_SOILGRIDS_30M_GAPFILL` |
| Black Soils – Probabilidade | `projects/mapbiomas-workspace/SOLOS/COVARIAVEIS/FAO_2022_BLACKSOIL_1KM` |
| Recorrência de água (1985–2023) | `projects/mapbiomas-workspace/SOLOS/COVARIAVEIS/MB_WATER_STATIC_WATER_RECURRENCE_1985_2023` |
| Latitude e Longitude | Calculadas via `ee.Image.pixelLonLat()` |

---

## 🌍 Classes de Solo (R)

Os dados de treinamento para classes de solo também estão no **SoilData**, no mesmo conjunto citado acima, mas em arquivo separado.  
Ele contém **364 observações** com as **classes taxonômicas de solos** no **2º nível categórico do SiBCS**.

### Execução
1. Acesse a pasta `classe-solo` neste repositório.
2. Abra o script em um ambiente **R** configurado com os pacotes necessários.
3. Baixe as covariáveis necessárias a partir do [Google Drive](https://drive.google.com/drive/folders/1sGOP6-b7p9ERx5tidED47mUN7Z_MD4DC).
4. Execute o script seguindo a ordem indicada nos comentários.

---

## 📌 Requisitos

### Para GEE:
- Conta no [Google Earth Engine](https://earthengine.google.com/)
- Permissão para acessar os assets do **MapBiomas Workspace**

### Para R:
- R >= 4.0
- Pacotes listados no script `classe-solo`
- Espaço para armazenar as covariáveis baixadas

---

## 🔗 Links úteis
- **Repositório GitHub:** [https://github.com/taciaraz/solos-maranhao](https://github.com/taciaraz/solos-maranhao)  
- **SoilData:** *(link direto para o conjunto quando disponível)*  
- **Google Drive com covariáveis para R:** [Acessar](https://drive.google.com/drive/folders/1sGOP6-b7p9ERx5tidED47mUN7Z_MD4DC)  

---
