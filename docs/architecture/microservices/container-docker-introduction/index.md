---
title: Úvod ke kontejnerům a Dockeru
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Úvod do kontejnerů a Dockeru
ms.date: 08/31/2018
ms.openlocfilehash: 364cbc0ba8149be1873df628a1ca243f420e7d0b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73740070"
---
# <a name="introduction-to-containers-and-docker"></a>Úvod ke kontejnerům a Dockeru

Kontejnerizace je přístup k vývoji softwaru, ve kterém aplikace nebo služby, její závislosti a jeho konfigurace (abstrahované jako soubory manifestu nasazení) jsou zabaleny společně jako image kontejneru. Kontejnerizovaná aplikace může být testována jako jednotka a nasazena jako instance image kontejneru do hostitelského operačního systému (OS).

Stejně jako přepravní kontejnery umožňují přepravu zboží lodí, vlakem nebo nákladním vozidlem bez ohledu na náklad uvnitř, softwarové kontejnery fungují jako standardní jednotka nasazení softwaru, která může obsahovat různé kódy a závislosti. Kontejnerizace softwaru tímto způsobem umožňuje vývojářům a odborníkům v oblasti IT nasadit je napříč prostředími s malou nebo žádnou úpravou.

Kontejnery také izolovat aplikace od sebe navzájem na sdíleném osu. Kontejnerizované aplikace běží na hostiteli kontejneru, který zase běží na operačním systému (Linux nebo Windows). Kontejnery mají proto výrazně menší nároky než image virtuálního počítače (VM).

Každý kontejner může spustit celou webovou aplikaci nebo službu, jak je znázorněno na obrázku 2-1. V tomto příkladu je hostitel Dockeru hostitel kontejneru a App1, App2, Svc 1 a Svc 2 jsou kontejnerizované aplikace nebo služby.

![Diagram znázorňující čtyři kontejnery spuštěné ve virtuálním provozu nebo na serveru.](./media/index/multiple-containers-single-host.png)

**Obrázek 2-1**. Více kontejnerů spuštěné na hostiteli kontejneru

Další výhodou kontejnerizace je škálovatelnost. Můžete rychle horizontální navýšení kapacity vytvořením nových kontejnerů pro krátkodobé úkoly. Z hlediska aplikace je vytváření instancí bitové kopie (vytvoření kontejneru) podobné vytvoření procesu, jako je služba nebo webová aplikace. Z důvodu spolehlivosti však při spuštění více instancí stejné bitové kopie na více hostitelských serverech obvykle chcete, aby každý kontejner (instance bitové kopie) běžel na jiném hostitelském serveru nebo virtuálním počítači v různých doménách selhání.

Stručně řečeno, kontejnery nabízejí výhody izolace, přenositelnost, flexibilitu, škálovatelnost a řízení v celém pracovním postupu životního cyklu aplikace. Nejdůležitější výhodou je izolace prostředí mezi Dev a Ops.

>[!div class="step-by-step"]
>[Předchozí](../index.md)
>[další](docker-defined.md)
