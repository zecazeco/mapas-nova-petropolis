# Mapas de Risco de Nova Petrópolis

Mapas interativos de Nova Petrópolis (RS) feitos a partir de imagens de satélite, para
ajudar moradores, Defesa Civil e quem usa as rodovias a enxergar onde o terreno é mais
frágil, como a cidade cresce e o que acontece com a mata.

**Acesse:** https://zecazeco.github.io/mapas-nova-petropolis/

## Por que estes mapas

Em maio de 2024, as chuvas extremas no Rio Grande do Sul provocaram centenas de
deslizamentos em Nova Petrópolis. Muitos deles aconteceram em encostas que já davam
sinais de fragilidade quando vistas de cima: declive forte, terreno côncavo que junta
água, beira de estrada e mata cortada. Estes mapas reúnem essas pistas num lugar só,
numa linguagem simples, para que mais gente saiba onde olhar com atenção antes da próxima
chuva forte.

## Quanto os mapas acertam

> **Resumo:** as encostas pintadas no mapa ocupam **16% do município** e reuniram
> **73% dos deslizamentos de 2024**. Nas áreas de atenção **muito alta**, houve **7 vezes
> mais deslizamentos** que na média do município.

### Encostas: deslizamentos de 2024 em cada cor

| Cor no mapa | Área do município | Deslizamentos de 2024 | Comparado à média |
|---|---:|---:|---:|
| 🟥 Atenção muito alta | 5% | **48%** | **7,0×** |
| 🟧 Atenção alta | 10% | **25%** | **2,4×** |
| Sem cor (média e baixa) | 84% | 27% | 0,4× |

- O teste usou os 335 deslizamentos de 2024 mapeados pelo Serviço Geológico do Brasil.
  Cada parte do município foi avaliada por um modelo que **não tinha visto** os
  deslizamentos daquela parte, para medir o acerto em lugares "novos" e não só repetir o
  que o modelo decorou.
- Em outro inventário independente (pontos da NASA), 79% dos deslizamentos caíram nas
  áreas coloridas.
- Dos 15 pontos de deslizamento conhecidos de moradores, 14 ficaram em áreas de atenção
  alta ou muito alta (13 em muito alta), e 9 de 13 quedas de barreira noticiadas nas
  rodovias também.
- **Como ler:** a cor diz onde é *mais provável*, não que vai deslizar. Mesmo em atenção
  muito alta, só cerca de 3,4% do terreno deslizou em 2024, uma das chuvas mais fortes já
  registradas. E cerca de um quarto dos deslizamentos aconteceu em áreas sem cor: **área sem cor
  não é área sem risco**.

### Crescimento da cidade: a tendência acerta?

A tendência foi testada no passado: um modelo treinado só com o crescimento de 2006 a 2015
apontou onde a cidade cresceria de 2016 a 2021, e o resultado foi comparado com o que de
fato aconteceu.

| Azul no mapa | Virou cidade ali ou a até 100 m | O próprio terreno virou cidade | Comparado ao acaso |
|---|---:|---:|---:|
| Forte | **69%** | 9,2% | **18×** |
| Média | 57% | 5,7% | 11× |
| Fraca | 53% | 4,2% | 8× |

- **60%** de tudo o que virou cidade de 2016 a 2021 ficou dentro do azul ou a até 100 m dele.
- **Como ler:** o mapa acerta bem a *região* para onde a cidade vai, não o *lote*. O teste
  cobriu 6 anos; em 10 anos, como no mapa, as taxas tendem a ser maiores.

## Os mapas

1. **Encostas**: áreas de atenção alta ou muito alta para deslizamento, setores de
   risco oficiais do Serviço Geológico do Brasil e sinais de alerta no terreno. O modelo
   olha o relevo (declive, forma da encosta, caminho da água), a cobertura do solo e o
   histórico de corte da mata, e aprendeu com os deslizamentos de 2024 de toda a região da Serra,
   não só do município. Desde a versão 4 (nov/2026), usa também um resumo do que os
   satélites viam de cada lugar em 2023, antes do desastre.
2. **Rodovias**: trechos da BR-116 e da RS-235 mais sujeitos a queda de barreira, com a
   quilometragem das placas, pontes e bueiros que podem entupir e deslizamentos
   noticiados de 2016 a 2026. Cerca de 60% da BR-116 no município passa por encostas de
   atenção alta ou muito alta.
3. **Crescimento da cidade**: a área urbana ano a ano desde 1985 e as regiões com tendência
   de crescimento nos próximos 10 anos (cerca de 210 ha no ritmo atual). Mostra também
   quanto do crescimento recente avançou sobre encostas de atenção.
4. **Mata**: mata nativa e plantações ano a ano desde 2001, onde foram cortadas e onde a mata
   voltou, com destaque para cortes em encostas de atenção. De 2001 a 2025, cerca de
   1.850 ha de mata ou plantação foram cortados e não voltaram (240 ha em encostas de
   atenção), e cerca de 2.700 ha de mata surgiram ou voltaram.

Cada mapa pode ser visto sobre imagem de satélite ou mapa simples, em 2D ou 3D, e cada
painel traz os números de acerto ao lado da legenda.

## Fontes

- Imagens de satélite: Sentinel-2 (ESA/Copernicus) e Landsat (NASA/USGS)
- Resumo das imagens de satélite de 2023: Satellite Embeddings (Google DeepMind, via Google Earth Engine)
- Relevo: Copernicus DEM, FABDEM e Terrain Tiles (AWS)
- Inventários de deslizamentos de 2024: Serviço Geológico do Brasil (SGB), UFRGS e NASA
- Setores de risco: SGB, via Defesa Civil de Nova Petrópolis
- Construções: Google Open Buildings
- Mata e plantações: MapBiomas Brasil (Coleção 11)
- Cobertura e perda de floresta: ESA WorldCover e Global Forest Change (Hansen/UMD)
- Geologia e solos: IBGE
- Chuva: UFRGS e NASA POWER
- Estradas e localidades: OpenStreetMap
- Notícias: Prefeitura de Nova Petrópolis, ABC+, Jornal do Comércio, GZH e Jornal A Ponte
- Fundo do mapa: Esri World Imagery e OpenFreeMap

## Limitações

- O relevo usado tem 30 m de resolução: encostas pequenas, cortes de estrada e aterros
  recentes podem não aparecer.
- O modelo aprendeu principalmente com as chuvas de 2024; outro tipo de chuva pode
  produzir outro padrão de deslizamentos.
- Profundidade do solo e drenagem de casas e estradas não são vistas por satélite e
  pesam muito no risco real.

## Aviso

Os mapas são estimativas feitas a partir de imagens de satélite e de um modelo estatístico.
Eles indicam onde olhar com mais atenção e não substituem a vistoria da Defesa Civil
(telefone 199) nem laudos técnicos. Áreas sem cor não são áreas sem risco.
