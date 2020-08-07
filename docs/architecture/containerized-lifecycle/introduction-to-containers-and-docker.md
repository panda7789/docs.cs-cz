---
title: Úvod ke kontejnerům a Dockeru
description: Získejte přehled o hlavních výhodách používání Docker.
ms.date: 04/15/2020
ms.openlocfilehash: 79b4752ef4d2f0aa6199414aea5cf4ef357c86d3
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915949"
---
# <a name="introduction-to-containers-and-docker"></a>Úvod do kontejnerů a Docker

*Kontejnering je přístup k vývoji softwaru, ve kterém je aplikace nebo služba, její závislosti a její konfigurace (abstrakce jako soubory manifestu nasazení) zabaleny dohromady jako image kontejneru. Pak můžete aplikace s kontejnerem otestovat jako jednotku a nasadit ji jako instanci image kontejneru do hostitelského operačního systému (OS).*

Stejně jako přepravní kontejnery umožňují, aby se zboží předávalo dodávkou, vlakem nebo nákladním dopravcem bez ohledu na náklad uvnitř, kontejnery softwaru fungují jako standardní jednotka nasazení softwaru, která může obsahovat odlišný kód a závislosti. Uzavření software tímto způsobem umožňuje vývojářům a IT profesionálům jejich nasazení v různých prostředích bez jakýchkoli úprav.

Kontejnery také vzájemně izolují aplikace na sdíleném operačním systému. Kontejnerové aplikace běží nad hostitelem kontejneru, který zase běží v operačním systému (Linux nebo Windows). Kontejnery mají proto mnohem menší nároky než image virtuálních počítačů.

Každý kontejner může spustit celou webovou aplikaci nebo službu, jak je znázorněno na obrázku 1-1. V tomto příkladu je hostitelem Docker hostitel kontejneru a app1, app2, Svc1 a Svc2 jsou kontejnerové aplikace nebo služby.

![Diagram znázorňující čtyři kontejnery běžící na virtuálním počítači nebo na serveru.](./media/introduction-to-containers-and-docker/multiple-containers-single-host.png)

**Obrázek 1-1**. Více kontejnerů spuštěných v hostiteli kontejneru

Další výhodou, kterou můžete odvodit z kontejneru, je škálovatelnost. Horizontální navýšení kapacity můžete rychle škálovat tak, že vytvoříte nové kontejnery pro krátkodobé úlohy. Z pohledu aplikace je vytvoření instance obrázku (vytvoření kontejneru) podobné vytvoření instance procesu, jako je služba nebo webová aplikace. Pokud ale na více hostitelských serverech spustíte víc instancí stejné image, obvykle chcete, aby se každý kontejner (instance image) spouštěl na jiném hostitelském serveru nebo virtuálním počítači v různých doménách selhání.

V krátkém případě kontejnery nabízejí výhody izolace, přenositelnosti, flexibility, škálovatelnosti a řízení napříč celým pracovním postupem životního cyklu aplikace. Nejdůležitější výhodou je izolace prostředí, která je součástí vývoje a operace.

>[!div class="step-by-step"]
>[Předchozí](index.md) 
> [Další](what-is-docker.md)
