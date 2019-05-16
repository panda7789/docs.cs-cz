---
title: Úvod ke kontejnerům a Dockeru
description: Získejte základní přehled o hlavní výhody použití Dockeru.
ms.date: 02/15/2019
ms.openlocfilehash: a03c67ed4fbc55c84e69fba5b7978863c8305e00
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644958"
---
# <a name="introduction-to-containers-and-docker"></a>Úvod ke kontejnerům a Dockeru

*Kontejnerizace je přístup k vývoji softwaru, ve kterém aplikace nebo služby, jeho závislosti a jeho konfigurace (abstrahovaná jako soubory manifestu nasazení) spojených oprav jako image kontejneru. Potom můžete otestovat kontejnerizovanou aplikaci jako celek a nasadit ho jako instance image kontejneru do hostitelského operačního systému (OS).*

Stejně jako kontejnery umožňují přepravy příjemce, trénování nebo truck bez ohledu na to nákladu uvnitř zboží, plnit funkci softwarové kontejnery standardní jednotka nasazení softwaru, který může obsahovat odlišný kód a závislosti. Uzavření do kontejneru software tímto způsobem umožňuje vývojářům a IT profesionály nasazení napříč prostředími s téměř nebo vůbec žádné změny.

Kontejnery také izolace aplikací od sebe navzájem na sdílené operačního systému. Kontejnerizované aplikace běží na hostiteli, který zase běží na OS (Linux nebo Windows). Kontejnery tedy mít mnohem menší nároky na místo než imagí virtuálních počítačů (VM).

Každý kontejner můžete spustit celou webovou aplikaci nebo službu, jak ukazuje obrázek 1-1. V tomto příkladu hostitele Docker je hostiteli a jsou App1, počítači App2, Svc1 a Svc2 kontejnerizovaných aplikací nebo služeb.

![Dvě aplikace a dvě služby, které běží na operačním systému virtuálního počítače nebo fyzického serveru](./media/image1.png)

**Obrázek 1-1**. Více kontejnerech je spuštěná na hostiteli

Další výhodou, které lze odvodit z kontejnerizace je škálovatelnost. Vytvořením nové kontejnery pro krátkodobé úlohy, můžete se rychle škálovat. Z aplikace hlediska vytváření instancí bitovou kopii (vytváření kontejneru) je podobné jako vytvoření instance procesu, jako je service nebo do webové aplikace. Pro spolehlivost ale při spuštění více instancí stejné image napříč více hostitelských serverů, obvykle je vhodné každý kontejner (instance image) spustit ve jiný hostitelský server nebo virtuální počítač do různých domén selhání.

Stručně řečeno kontejnery nabízejí výhody izolace, přenositelnost, flexibilitu, škálovatelnost a ovládací prvek v pracovním postupu životního cyklu celé aplikace. Nejdůležitější výhoda spočívá v prostředí izolace mezi Dev a Ops k dispozici.

>[!div class="step-by-step"]
>[Next](what-is-docker.md)
