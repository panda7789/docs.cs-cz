---
title: Úvod ke kontejnerům a Docker
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Úvod ke kontejnerům a Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 8d9334785b2f3ee770c5f0e6bd2e13faa995b6f2
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106824"
---
# <a name="introduction-to-containers-and-docker"></a>Úvod ke kontejnerům a Docker

Rozdělení do kontejnerů je přístup k vývoji softwaru, ve kterém aplikace nebo služby, jeho závislosti a jeho konfigurace (abstrahované jako soubory manifestu nasazení) a instalace balíčku jako obrázek na kontejneru. Kontejnerizované aplikace jako jednotku otestovat a nasadit jako instance image kontejner pro hostitelský operační systém (OS).

Stejně jako kontejnery přesouvání povolit přepravy lodě, train nebo vůz bez ohledu na to nákladní uvnitř zboží, kontejnery softwaru fungují jako jednotka se software, který může obsahovat různé kódu a závislosti. Containerizing softwaru tímto způsobem umožňuje vývojářům a odborníkům nasadit v prostředí s žádné nebo téměř žádné změny.

Kontejnery také izolace aplikace od sebe navzájem na sdílené operačního systému. Kontejnerizované aplikace spustit na vrcholku kontejneru hostitele, který naopak běží na operačním systémem (Linux nebo Windows). Kontejnery tudíž výrazně menší nároky než bitové kopie virtuálních počítačů (VM).

Každý kontejner můžete spustit celou webové aplikace nebo služby, jak je znázorněno v obrázku 2-1. V tomto příkladu je Docker hostitel hostitelem kontejneru a App1, počítači App2, Svc 1 a Svc 2 jsou kontejnerizované aplikace nebo služby.

![](./media/image1.png)

**Obrázek 2-1**. Více kontejnerů, které jsou spuštěny v hostiteli kontejneru

Další výhodou rozdělení do kontejnerů je škálovatelnost. Vytvořením nové kontejnery pro krátkodobé úlohy, můžete se rychle škálovat. Z aplikace hlediska vytváření instancí bitovou kopii (vytvoření kontejneru) je podobná vytváření instancí procesu, jako jsou služby nebo webovou aplikaci. Pro spolehlivost ale při spuštění více instancí stejnou bitovou kopii na více serverů hostitele, obvykle je vhodné každé kontejneru (image instance) ke spuštění na serveru jiného hostitele nebo virtuálních počítačů v doménách jiné chyby.

Stručně řečeno kontejnery nabízejí výhody izolace, přenositelnost, flexibility, škálovatelnost a řízení napříč celou aplikaci pracovního postupu životního cyklu. Nejdůležitější výhodou je, izolaci mezi vývojářů a Ops k dispozici.


>[!div class="step-by-step"]
[Předchozí](../index.md)
[další](docker-defined.md)
