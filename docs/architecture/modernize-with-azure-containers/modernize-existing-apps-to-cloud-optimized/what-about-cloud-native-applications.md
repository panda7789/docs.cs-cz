---
title: Co jsou nativní cloudové aplikace?
description: Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows | Co jsou aplikace Cloud Native?
ms.date: 04/28/2018
ms.openlocfilehash: cf4c3b24a4eeb62ed84a5fccb294b675d38fcc36
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/08/2019
ms.locfileid: "72318443"
---
# <a name="what-about-cloud-native-applications"></a>Co jsou nativní cloudové aplikace?

I když nativní aplikace v [cloudu](https://azure.microsoft.com/overview/cloudnative/) nejsou hlavním soustředěním tohoto průvodce, je užitečné pochopit tuto úroveň zralosti a odlišit ji od cloudově optimalizovaných aplikací.

Obrázek 4-3 pozice cloudových nativních aplikací v úrovni vyspělosti aplikací:

![Diagram znázorňující, jak umístit aplikace nativní pro Cloud](./media/what-about-cloud-native-applications/positioning-cloud-native-applications.png)

**Obrázek 4-3.** Umísťování cloudových nativních aplikací

Úroveň zralosti nativní v cloudu obvykle vyžaduje nové investice do vývoje. Přechod na nativní úroveň cloudu je typicky založený na potřebě modernizovat aplikací tak, aby bylo možné výrazně zlepšit škálování ve velkých aplikacích, a to vytvořením autonomních subsystémů (mikroslužby), které se dají nasadit a škálovat nezávisle. z jiných oblastí aplikace při současném snížení nákladů a zvýšení flexibility vývoje částí autonomní aplikace, které poskytují významné konkurenční výhody.

Hlavní pilíře nativních aplikací pro Cloud jsou založené na přístupech k architektuře mikroslužeb, které se můžou vyvíjet s flexibilitou a škálováním na omezení, která by byla obtížné dosáhnout v monolitické architektuře nasazené do místního prostředí nebo cloudu. hlediska.

Obrázek 4-4 ukazuje hlavní charakteristiky modelu nativního cloudu.

![Diagram se seznamem základních vlastností nativního cloudu.](./media/what-about-cloud-native-applications/cloud-native-characteristics.png)

**Obrázek 4-4.** Nativní charakteristiky cloudu

Kromě toho můžete rozšířit základní moderní webové aplikace a cloudové nativní aplikace tím, že přidáte další služby, jako je například aplikace umělal Intelligence (AI), Machine Learning (ML) a IoT. Některé z těchto služeb můžete použít k rozšiřování libovolných možných cloudově optimalizovaných přístupů.

Základní rozdíl v aplikacích na úrovni nativní pro Cloud je součástí architektury aplikace. Nativní aplikace v cloudu jsou podle definice aplikace založené na mikroslužbách. Nativní aplikace pro Cloud vyžadují speciální architektury, technologie a platformy, které se rovnají monolitické webové aplikaci nebo tradiční N-vrstvé aplikaci.

## <a name="cloud-native-applications-details"></a>Podrobnosti o nativních aplikacích cloudu

Cloud – nativní je pokročilejší nebo vyspělý stav pro rozsáhlé a klíčové aplikace. Nativní aplikace pro Cloud jsou obvykle vyžadovány architekturou a návrhem, které jsou vytvářeny od začátku a nikoli pomocí stávajících aplikací modernizaci. Klíčový rozdíl mezi cloudovou nativní aplikací a jednodušší cloudovou webovou aplikací je doporučení k používání architektury mikroslužeb v nativním přístupu v cloudu. Cloudově optimalizované aplikace můžou být taky monolitické webové aplikace nebo N-vrstvé aplikace.

[32bitová aplikace](https://12factor.net/) (kolekce vzorů, které úzce souvisejí s přístupy k mikroslužbám), je rovněž považována za požadavek pro architektury cloudových nativních aplikací.

[Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) je primárním zvýšením principů nativních pro Cloud. Microsoft je [členem služby CNCF](https://azure.microsoft.com/blog/announcing-cncf/).

Ukázku definice a další informace o vlastnostech cloudových nativních aplikací najdete v článku Gartner, [jak architektovat a navrhovat aplikace Cloud Native](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications). Konkrétní pokyny od Microsoftu o implementaci nativní cloudové aplikace najdete v tématu [mikroslužby .NET: architektura pro kontejnerové aplikace .NET](https://aka.ms/microservicesebook).

Nejdůležitější faktor, který je třeba vzít v úvahu při migraci úplné aplikace do nativního modelu cloudu, je, že je nutné přearchitektit architekturu založenou na mikroslužbách. To jasně vyžaduje významné investice do vývoje, protože se jedná o velký proces refaktoringu. Tato možnost se obvykle volí pro klíčové aplikace, které vyžadují nové úrovně škálovatelnosti a dlouhodobé flexibility. Můžete ale začít přecházet ke cloudovým nativním přidáním mikroslužeb pro pár nových scénářů a nakonec Refaktorovat aplikaci úplně jako mikroslužby. Toto je postupný přístup, který je nejlepší volbou pro některé scénáře.

## <a name="what-about-microservices"></a>Co jsou mikroslužby?

Porozumění mikroslužbám a způsobu jejich fungování je důležité v případě, že zvažujete nativní aplikace cloudu pro vaši organizaci.

Architektura mikroslužeb je pokročilý přístup, který můžete použít pro aplikace, které jsou vytvořené úplně od začátku, nebo když vyvíjíte stávající aplikace pro cloudové nativní aplikace. Můžete začít přidáním několika mikroslužeb do stávajících aplikací, abyste se dozvěděli o nových paradigmatech mikroslužeb. Jasně ale budete potřebovat architekt a kód, zejména pro tento typ přístupu k architektuře.

Nicméně mikroslužby nejsou povinné pro žádnou novou nebo moderní aplikaci. Mikroslužby nejsou "Magic Bullet" a nejedná se o jednotný, nejlepší způsob, jak vytvořit každou aplikaci. Jak a když používáte mikroslužby, závisí na typu aplikace, kterou potřebujete sestavit.

Architektura mikroslužeb se stává upřednostňovaným přístupem k distribuovaným a rozsáhlým nebo složitým podnikovým aplikacím, které jsou založeny na několika nezávislých subsystémech ve formě autonomních služeb. V architektuře založené na mikroslužbách je aplikace sestavená jako kolekce služeb, které se dají nezávisle vyvíjet, testovat, nasazovat a škálovat. To může zahrnovat všechny související, autonomní databáze na mikroslužby.

Podrobný pohled na architekturu mikroslužeb, kterou můžete implementovat pomocí .NET Core, najdete v tématu věnovaném použití mikroslužeb rozhraní .NET, ke stažení ve formátu PDF v elektronické knize [: architektura pro kontejnerové aplikace .NET](https://aka.ms/microservicesebook). Tato příručka je také k dispozici [online](../../microservices/index.md).

Ale dokonce i ve scénářích, kdy mikroslužby nabízejí výkonné možnosti nezávislé na možnostech nasazení, silné hranice subsystému a technologické rozmanitosti – také vyvolává mnoho nových výzev. Tyto výzvy souvisejí s vývojem distribuovaných aplikací, jako jsou fragmentované a nezávislé datové modely; dosažení odolné komunikace mezi mikroslužbami; nutnost případné konzistence; a provozní složitost. Mikroslužby představují vyšší úroveň složitosti v porovnání s tradičními monolitické aplikacemi.

Z důvodu složitosti architektury mikroslužeb jsou pro aplikace založené na mikroslužbách vhodné jenom určité scénáře a určité typy aplikací. Mezi ně patří velké a komplexní aplikace, které mají několik vyvíjejících se subsystémů. V těchto případech se jedná o investici do složitější softwarové architektury pro zvýšení dlouhodobé flexibility a efektivnější údržby aplikací. Ale u méně složitých scénářů může být lepší pokračovat s přístupem k aplikacím v monolitické nebo jednodušším stupněm přístupů.

Jako poslední Poznámka, a to i v případě, že se o tomto konceptu chystáte, byste neměli v aplikacích používat mikroslužby jako "vše" nebo "nic vůbec". Stávající aplikace monolitické můžete rozvinout a vyvíjet přidáním nových malých scénářů založených na mikroslužbách. Abyste mohli začít pracovat s přístupem k architektuře mikroslužeb, nemusíte začít od začátku. V podstatě doporučujeme, abyste se rozhodli, že budete vyvíjet z používání stávající monolitické nebo N-vrstvé aplikace přidáním nových scénářů. Nakonec můžete aplikaci rozdělit na autonomní součásti nebo mikroslužby. Můžete začít s vývojem aplikací monolitické ve směru mikroslužeb, krok za krokem.

V každém případě se zbytek těchto současných pokynů zaměřuje na většinu všech aplikací založených na mikroslužbách, protože tyto doprovodné materiály jsou primárně zaměřené na modernizaci stávajících aplikací, které obvykle mají monolitické nebo N-vrstvé architektury.

> [!div class="step-by-step"]
> [Předchozí](microsoft-technologies-in-cloud-optimized-applications.md)
> [Další](deploy-existing-net-apps-as-windows-containers.md)
