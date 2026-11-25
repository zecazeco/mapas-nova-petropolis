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

## Novidade da versão 5 (nov/2026): o mapa Cicatrizes

O novo mapa **Cicatrizes** mostra onde a terra *já* deslizou de 2017 a 2026: cerca de
**1.000 deslizamentos** (230 ha) e **315 trechos de erosão na margem de rio** dentro do município,
encontrados pela própria série de imagens do satélite Sentinel-2 (uma imagem a cada 5 dias, pixel de 10 m).
Isso inclui anos em que não houve inventário oficial, como 2017, 2018, 2020, 2023 e 2025.

Atualização de nov/2026: entrou o ano de 2017 (com as chuvas fortes de abril e de junho–julho);
o mapa mostra também as manchas até 1 km além da divisa, para ver as duas margens do Rio Caí;
e as margens de rio foram limpas: saíram as que eram beira de açude ou estrada, cada trecho ficou
restrito a 30 m da água ou de um arroio, e trechos sobrepostos viraram um só (o cartão lista os
códigos e anos juntados).
Depois disso, **todas as manchas do mapa foram conferidas uma a uma** em imagem de alta resolução e
nas imagens do Sentinel-2 de antes e depois: saíram cerca de 270 que eram lavoura, corte de mata, obra,
estrada ou açude, e algumas trocaram de classe. O mapa ainda não mostra todas as cicatrizes que existem:
muitas não foram detectadas pelo modelo.

Como foi feito:

- Para cada pixel do município, o programa acompanha o verde da vegetação (NDVI) imagem por
  imagem e procura **quedas bruscas que não se recuperam logo**, comparando com o entorno.
- Um modelo de aprendizado de máquina separa o que parece deslizamento de outras mudanças
  (lavoura, corte de mata, obra, estrada, margem de rio), usando o formato da mancha, o relevo,
  a distância de estradas e rios, o comportamento da vegetação antes e depois e a chuva.
- O modelo foi ensinado e conferido com os inventários de 2024 (SGB e UFRGS) e com **sete
  rodadas de conferência às cegas**: 420 manchas sorteadas, olhadas uma a uma em imagens
  coloridas do Sentinel-2 e do satélite brasileiro CBERS-4A (2 m) antes e depois da queda.
- Para cada regra nova, o critério de aceite foi escrito **antes** de medir o resultado, e
  regras que não passaram ficaram de fora.
- Ficaram no mapa só as partes que passaram no teste:
  - os deslizamentos em área de mata ou com queda forte de vegetação;
  - os deslizamentos pequenos em área aberta, só quando houve chuva forte (≥ 77 mm em 24 h
    no pluviômetro de Nova Petrópolis ou, sem ele, na estimativa de satélite da NASA) até
    30 dias antes;
  - manchas com menos de ~600 m² só quando estão a até 50 m de construções ou estradas;
  - a erosão de margem só quando o modelo tem confiança alta.

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

### Cicatrizes: as manchas são mesmo deslizamentos?

| Teste | Resultado |
|---|---|
| Manchas sorteadas e conferidas nas imagens | **40% a 58%** confirmadas como deslizamento |
| Chuva de maio de 2024: manchas junto de um deslizamento do SGB ou da UFRGS | **84%** |
| Chuva de maio de 2024: deslizamentos do SGB e da UFRGS que o satélite viu | 308 de 816 (**38%**) |
| Erosão de margem conferida nas imagens | **44 de 45** confirmadas |

- Nas chuvas fortes o mapa é confiável: quase todas as manchas de maio de 2024 estão junto de
  deslizamentos confirmados no chão. Nos anos comuns, cerca de metade das manchas é outra
  coisa: corte de estrada ou obra, lavoura, ou mudança pequena demais para ter certeza.
- O satélite **não vê tudo**: deslizamentos pequenos, embaixo de árvores ou escondidos por
  nuvem escapam. Em 2024 ele viu cerca de 4 em cada 10 deslizamentos mapeados pelo SGB e pela UFRGS.
- A data mostrada é a da primeira imagem sem nuvem que mostra a mudança, e pode vir semanas
  depois do deslizamento.
- Os testes foram feitos com um modelo que não tinha visto a parte do município testada.

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
2. **Cicatrizes** (novo na versão 5): deslizamentos e erosão de margem de rio vistos pelo
   satélite de 2017 a 2026. Mostra o que já aconteceu; o mapa de Encostas mostra onde é mais
   provável acontecer. Cada mancha tem um código (toque nela): se alguma não confere com o
   terreno, informe o código para que seja corrigida.
3. **Rodovias**: trechos da BR-116 e da RS-235 mais sujeitos a queda de barreira, com a
   quilometragem das placas, pontes e bueiros que podem entupir e deslizamentos
   noticiados de 2016 a 2026. Cerca de 60% da BR-116 no município passa por encostas de
   atenção alta ou muito alta.
4. **Crescimento da cidade**: a área urbana ano a ano desde 1985 e as regiões com tendência
   de crescimento nos próximos 10 anos (cerca de 210 ha no ritmo atual). Mostra também
   quanto do crescimento recente avançou sobre encostas de atenção.
5. **Mata**: mata nativa e plantações ano a ano desde 2001, onde foram cortadas e onde a mata
   voltou, com destaque para cortes em encostas de atenção. De 2001 a 2025, cerca de
   1.850 ha de mata ou plantação foram cortados e não voltaram (240 ha em encostas de
   atenção), e cerca de 2.700 ha de mata surgiram ou voltaram.

Cada mapa pode ser visto sobre imagem de satélite ou mapa simples, em 2D ou 3D, e cada
painel traz os números de acerto ao lado da legenda.

## Fontes

- Imagens de satélite: Sentinel-2 (ESA/Copernicus), CBERS-4A (INPE) e Landsat (NASA/USGS)
- Resumo das imagens de satélite de 2023: Satellite Embeddings (Google DeepMind, via Google Earth Engine)
- Relevo: Copernicus DEM, FABDEM e Terrain Tiles (AWS)
- Inventários de deslizamentos de 2024: Serviço Geológico do Brasil (SGB), UFRGS e NASA
- Setores de risco: SGB, via Defesa Civil de Nova Petrópolis
- Construções: Google Open Buildings
- Mata e plantações: MapBiomas Brasil (Coleção 11)
- Cobertura e perda de floresta: ESA WorldCover e Global Forest Change (Hansen/UMD)
- Geologia e solos: IBGE
- Chuva: pluviômetro de Nova Petrópolis, UFRGS, NASA POWER e NASA IMERG
- Estradas e localidades: OpenStreetMap
- Notícias: Prefeitura de Nova Petrópolis, ABC+, Jornal do Comércio, GZH e Jornal A Ponte
- Fundo do mapa: Esri World Imagery e OpenFreeMap

## Limitações

- O relevo usado tem 30 m de resolução: encostas pequenas, cortes de estrada e aterros
  recentes podem não aparecer.
- O modelo aprendeu principalmente com as chuvas de 2024; outro tipo de chuva pode
  produzir outro padrão de deslizamentos.
- O mapa Cicatrizes depende de imagens sem nuvem: em meses muito nublados a data da queda
  fica imprecisa, e deslizamentos menores que cerca de 300 m² quase não aparecem.
- Profundidade do solo e drenagem de casas e estradas não são vistas por satélite e
  pesam muito no risco real.

## Aviso

Os mapas são estimativas feitas a partir de imagens de satélite e de um modelo estatístico.
Eles indicam onde olhar com mais atenção e não substituem a vistoria da Defesa Civil
(telefone 199) nem laudos técnicos. Áreas sem cor não são áreas sem risco.
