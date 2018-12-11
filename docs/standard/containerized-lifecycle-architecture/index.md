---
title: Úvod ke kontejnerům a Dockeru
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: c2a6b9802bbb995939d33c5c40ef9c1afa1620e5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148818"
---
# <a name="introduction-to-containers-and-docker"></a>Úvod ke kontejnerům a Dockeru

Kontejnerizace je přístup k vývoji softwaru, ve kterém aplikace nebo služby, jeho závislosti a jeho konfigurace (abstrahovaná jako soubory manifestu nasazení) spojených oprav jako image kontejneru. Potom můžete otestovat kontejnerizovanou aplikaci jako celek a nasadit ho jako instance image kontejneru do hostitelského operačního systému.

Stejně jako v oboru přesouvání standardizované kontejnery používá k přesunutí zboží příjemce, trénování nebo nákladní vůz, bez ohledu na to nákladu v nich, plnit funkci softwarové kontejnery standardní jednotkou software, který může obsahovat odlišný kód a závislosti. Umístění softwaru do kontejnerů umožňuje vývojáři a odborníci na IT nasazování těchto kontejnerů napříč prostředími s téměř nebo vůbec žádné změny.

Kontejnery také izolace aplikací od sebe na sdílené operační systém (OS). Kontejnerizované aplikace běží na hostiteli, který zase běží na OS (Linux nebo Windows). Kontejnery tedy mít výrazně menší nároky na místo než imagí virtuálních počítačů (VM).

Každý kontejner můžete spustit celou webovou aplikaci nebo službu, jak ukazuje obrázek 1-1.

![](./media/image1.png)

Obrázek 1-1: Více kontejnerech je spuštěná na hostiteli

V tomto příkladu je hostitel kontejneru hostitele Docker a aplikace 1, 2 aplikace, Svc 1 a Svc 2 jsou kontejnerizovaných aplikací nebo služeb.

Další výhodou, které lze odvodit z kontejnerizace je škálovatelnost. Vám může horizontální navýšení kapacity rychle tak, že vytvoříte nové kontejnery pro krátkodobé úlohy. Z aplikace hlediska *vytvoření instance bitovou kopii* (vytváření kontejneru) se podobá vytvoření instance procesu, jako je service nebo do webové aplikace. Pro spolehlivost ale při spuštění více instancí stejné image napříč více hostitelských serverů, obvykle je vhodné každý kontejner (instance image) spustit ve jiný hostitelský server nebo virtuální počítač do různých domén selhání.

Stručně řečeno kontejnery nabízejí výhody izolace, přenositelnost, flexibilitu, škálovatelnost a ovládací prvek v pracovním postupu životní cyklus celé aplikace. Nejdůležitější výhoda spočívá v izolaci mezi Dev a Ops k dispozici.

>[!div class="step-by-step"]
>[Next](what-is-docker.md)