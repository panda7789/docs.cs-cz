---
title: Úvod ke kontejnerům a Docker
description: Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje
keywords: Docker, Mikroslužeb, ASP.NET, kontejneru
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 31260dc372f87305ad9d4556673a1cc94e24bfcc
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="introduction-to-containers-and-docker"></a>Úvod ke kontejnerům a Docker

Rozdělení do kontejnerů je přístup k vývoji softwaru, ve kterém aplikace nebo služby, jeho závislosti a jeho konfigurace (abstrahované jako soubory manifestu nasazení) a instalace balíčku jako obrázek na kontejneru. Potom můžete otestovat kontejnerizované aplikaci jako celek a nasaďte ho jako instanci kontejneru bitové kopie pro hostitelský operační systém.

Stejně jako v odvětví přesouvání používá standardizované kontejnery přesunout zboží lodě, train nebo vůz, bez ohledu na to nákladní v nich, kontejnery softwaru fungují jako jednotka se software, který může obsahovat různé kódu a závislosti. Umístění softwaru do kontejnerů umožňuje pro vývojáře a IT odborníky nasazení těchto kontejnerů v rámci prostředí s žádné nebo téměř žádné změny.

Kontejnery také izolace aplikace od sebe navzájem na sdílené operační systém (OS). Kontejnerizované aplikace spustit na vrcholku kontejneru hostitele, který naopak běží na operačním systémem (Linux nebo Windows). Kontejnery tedy mít výrazně menší nároky než bitové kopie virtuálních počítačů (VM).

Každý kontejner můžete spustit celou webovou aplikaci nebo službu, jak ukazuje obrázek 1-1.

![](./media/image1.png)

Obrázek 1-1: několika kontejnerů spuštěny v hostiteli kontejneru

V tomto příkladu je Docker hostitel hostitelem kontejneru a aplikace 1, 2 aplikace, Svc 1 a Svc 2 jsou kontejnerizované aplikace nebo služby.

Mezi další výhody, které může být odvozen z rozdělení do kontejnerů je škálovatelnost. Vám může Škálováním na více systémů rychle vytvořit nové kontejnery pro krátkodobé úlohy. Z aplikace hlediska *vytváření instancí bitovou kopii* (vytvoření kontejneru) je podobná vytváření instancí procesu, jako jsou služby nebo webovou aplikaci. Pro spolehlivost ale při spuštění více instancí stejnou bitovou kopii na více serverů hostitele, obvykle je vhodné každé kontejneru (image instance) ke spuštění na serveru jiného hostitele nebo virtuálních počítačů v doménách jiné chyby.

Stručně řečeno kontejnery nabízejí výhody izolace, přenositelnost, flexibility, škálovatelnost a řízení napříč pracovního postupu životní cyklus celou aplikaci. Nejdůležitější výhodou je, izolaci mezi vývojářů a Ops k dispozici.


>[!div class="step-by-step"]
[Další] (what-is-docker.md)
