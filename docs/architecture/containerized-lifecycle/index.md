---
title: Úvod ke kontejnerům a Dockeru
description: Získejte přehled o hlavních výhodách používání Dockeru na vysoké úrovni.
ms.date: 02/15/2019
ms.openlocfilehash: 9ac08a64cd2465b4b88a266c1ec0925f37680bf9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73738132"
---
# <a name="introduction-to-containers-and-docker"></a>Úvod do kontejnerů a Dockeru

*Kontejnerizace je přístup k vývoji softwaru, ve kterém aplikace nebo služby, její závislosti a jeho konfigurace (abstrahované jako soubory manifestu nasazení) jsou zabaleny společně jako image kontejneru. Potom můžete otestovat kontejnerizované aplikace jako celek a nasadit jako instance image kontejneru do hostitelského operačního systému (OS).*

Stejně jako přepravní kontejnery umožňují přepravu zboží lodí, vlakem nebo nákladním vozidlem bez ohledu na náklad uvnitř, softwarové kontejnery fungují jako standardní jednotka nasazení softwaru, která může obsahovat různé kódy a závislosti. Kontejnerizace softwaru tímto způsobem umožňuje vývojářům a odborníkům v oblasti IT nasadit je napříč prostředími s malou nebo žádnou úpravou.

Kontejnery také izolovat aplikace od sebe navzájem na sdíleném osu. Kontejnerizované aplikace běží na hostiteli kontejneru, který zase běží na operačním systému (Linux nebo Windows). Kontejnery mají proto mnohem menší nároky než image virtuálního počítače (VM).

Každý kontejner může spustit celou webovou aplikaci nebo službu, jak je znázorněno na obrázku 1-1. V tomto příkladu je hostitel Dockeru hostitel kontejneru a App1, App2, Svc1 a Svc2 jsou kontejnerizované aplikace nebo služby.

![Diagram znázorňující čtyři kontejnery spuštěné ve virtuálním provozu nebo na serveru.](./media/index/multiple-containers-single-host.png)

**Obrázek 1-1**. Více kontejnerů spuštěné na hostiteli kontejneru

Další výhodou, kterou můžete odvodit z kontejnerizace je škálovatelnost. Můžete rychle horizontální navýšení kapacity vytvořením nových kontejnerů pro krátkodobé úkoly. Z hlediska aplikace je vytváření instancí bitové kopie (vytvoření kontejneru) podobné vytvoření procesu, jako je služba nebo webová aplikace. Z důvodu spolehlivosti však při spuštění více instancí stejné bitové kopie na více hostitelských serverech obvykle chcete, aby každý kontejner (instance bitové kopie) běžel na jiném hostitelském serveru nebo virtuálním počítači v různých doménách selhání.

Stručně řečeno, kontejnery nabízejí výhody izolace, přenositelnost, flexibilitu, škálovatelnost a řízení v celém pracovním postupu životního cyklu aplikace. Nejdůležitější výhodou je izolace prostředí mezi Dev a Ops.

>[!div class="step-by-step"]
>[Další](what-is-docker.md)
