---
title: Úvod ke kontejnerům a Dockeru
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Úvod ke kontejnerům a Dockeru
ms.date: 08/31/2018
ms.openlocfilehash: cb6244939f6ae89ba1dc824b55a21d1e010cef5e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644519"
---
# <a name="introduction-to-containers-and-docker"></a>Úvod ke kontejnerům a Dockeru

Kontejnerizace je přístup k vývoji softwaru, ve kterém aplikace nebo služby, jeho závislosti a jeho konfigurace (abstrahovaná jako soubory manifestu nasazení) spojených oprav jako image kontejneru. Kontejnerizovanou aplikaci jako celek otestovat a nasadit jako instance image kontejneru do hostitelského operačního systému (OS).

Stejně jako kontejnery umožňují přepravy příjemce, trénování nebo truck bez ohledu na to nákladu uvnitř zboží, plnit funkci softwarové kontejnery standardní jednotka nasazení softwaru, který může obsahovat odlišný kód a závislosti. Uzavření do kontejneru software tímto způsobem umožňuje vývojářům a IT profesionály nasazení napříč prostředími s téměř nebo vůbec žádné změny.

Kontejnery také izolace aplikací od sebe navzájem na sdílené operačního systému. Kontejnerizované aplikace běží na hostiteli, který zase běží na OS (Linux nebo Windows). Kontejnery tedy mít výrazně menší nároky na místo než imagí virtuálních počítačů (VM).

Každý kontejner můžete spustit celou webovou aplikaci nebo službu, jak je znázorněno v obrázek 2-1. V tomto příkladu hostitele Docker je hostiteli a jsou App1, počítači App2, Svc 1 a Svc 2 kontejnerizovaných aplikací nebo služeb.

![Dvě aplikace a dvě služby, které běží na operačním systému virtuálního počítače nebo fyzického serveru](./media/image1.png)

**Obrázek 2 – 1**. Více kontejnerech je spuštěná na hostiteli

Další výhodou kontejnerizace je škálovatelnost. Vytvořením nové kontejnery pro krátkodobé úlohy, můžete se rychle škálovat. Z aplikace hlediska vytváření instancí bitovou kopii (vytváření kontejneru) je podobné jako vytvoření instance procesu, jako je service nebo do webové aplikace. Pro spolehlivost ale při spuštění více instancí stejné image napříč více hostitelských serverů, obvykle je vhodné každý kontejner (instance image) spustit ve jiný hostitelský server nebo virtuální počítač do různých domén selhání.

Stručně řečeno kontejnery nabízejí výhody izolace, přenositelnost, flexibilitu, škálovatelnost a ovládací prvek v pracovním postupu životního cyklu celou aplikaci. Nejdůležitější výhoda spočívá v prostředí izolace, kterou poskytuje mezi Dev a Ops.

>[!div class="step-by-step"]
>[Předchozí](../index.md)
>[další](docker-defined.md)
