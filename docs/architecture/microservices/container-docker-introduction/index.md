---
title: Úvod ke kontejnerům a Dockeru
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Úvod do kontejnerů a Docker
ms.date: 08/31/2018
ms.openlocfilehash: cb6244939f6ae89ba1dc824b55a21d1e010cef5e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296157"
---
# <a name="introduction-to-containers-and-docker"></a>Úvod ke kontejnerům a Dockeru

Kontejnering je přístup k vývoji softwaru, ve kterém je aplikace nebo služba, její závislosti a její konfigurace (abstrakce jako soubory manifestu nasazení) zabaleny dohromady jako image kontejneru. Kontejnerová aplikace může být testována jako jednotka a nasazena jako instance image kontejneru do hostitelského operačního systému (OS).

Stejně jako přepravní kontejnery umožňují, aby se zboží předávalo dodávkou, vlakem nebo nákladním dopravcem bez ohledu na náklad uvnitř, kontejnery softwaru fungují jako standardní jednotka nasazení softwaru, která může obsahovat odlišný kód a závislosti. Uzavření software tímto způsobem umožňuje vývojářům a IT profesionálům jejich nasazení v různých prostředích bez jakýchkoli úprav.

Kontejnery také vzájemně izolují aplikace na sdíleném operačním systému. Kontejnerové aplikace běží nad hostitelem kontejneru, který zase běží v operačním systému (Linux nebo Windows). Kontejnery proto mají výrazně menší nároky než image virtuálních počítačů.

Každý kontejner může spustit celou webovou aplikaci nebo službu, jak je znázorněno na obrázku 2-1. V tomto příkladu je hostitelem Docker hostitel kontejneru a app1, app2, svc 1 a svc 2 jsou kontejnery aplikace nebo služby.

![Dvě aplikace a dvě služby běžící v operačním systému ve virtuálním počítači nebo fyzickém serveru](./media/image1.png)

**Obrázek 2-1**. Více kontejnerů spuštěných v hostiteli kontejneru

Další výhodou kontejneru je škálovatelnost. Horizontální navýšení kapacity můžete rychle škálovat tak, že vytvoříte nové kontejnery pro krátkodobé úlohy. Z pohledu aplikace je vytvoření instance obrázku (vytvoření kontejneru) podobné vytvoření instance procesu, jako je služba nebo webová aplikace. Pokud ale na více hostitelských serverech spustíte víc instancí stejné image, obvykle chcete, aby se každý kontejner (instance image) spouštěl na jiném hostitelském serveru nebo virtuálním počítači v různých doménách selhání.

V krátkém případě kontejnery nabízejí výhody izolace, přenositelnosti, flexibility, škálovatelnosti a řízení napříč celým pracovním postupem životního cyklu aplikace. Nejdůležitější výhodou je izolace prostředí, která je součástí vývoje a operace.

>[!div class="step-by-step"]
>[Předchozí](../index.md)Další
>[](docker-defined.md)
