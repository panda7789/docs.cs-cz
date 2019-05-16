---
title: Co jsou nativní cloudové aplikace?
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a Windows kontejnery | A co aplikací nativních pro Cloud?
ms.date: 04/28/2018
ms.openlocfilehash: 2d459b4ab3e015bb328699aa1d53159593e06da0
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65643663"
---
# <a name="what-about-cloud-native-applications"></a>Co jsou nativní cloudové aplikace?

I když [nativní pro Cloud](https://azure.microsoft.com/overview/cloudnative/) aplikace nejsou hlavní výběr tohoto průvodce, je užitečné porozumět této úrovně vyspělosti modernizaci a aby se odlišil od aplikace optimalizované pro Cloud.

Obrázek 4-3 umístí nativních cloudových aplikací úrovně vyspělosti modernizaci aplikací:

![Umístění aplikací nativních pro Cloud](./media/image3.png)

> **Obrázek 4-3.** Umístění aplikací nativních pro Cloud

Nativní pro Cloud modernizaci vyspělosti obvykle vyžaduje nové investic do vývoje. Přechod na Cloud nativní úroveň obvykle doprovází obchodní potřebu modernizovat aplikace co nejvíc výrazně zlepšit horizontálně velké aplikace tak, že vytvoříte autonomní subsystémy (mikroslužeb), které je možné nasadit a škálování nezávisle na sobě z jiných oblastí aplikace při současném snižování nákladů v dlouhé flexibilitu vývoje období a zvýšení částí těchto autonomní aplikace, které poskytují soutěžit významné výhody.

Hlavní pilíře aplikací nativních pro Cloud, jsou založeny na přístupů architekturu mikroslužeb, které můžete vyvíjet s flexibilitou a škálujte na limity, které by bylo obtížné dosáhnout v monolitické architektury, místní nebo cloudové nasazení prostředí.

Vidět na obrázku 4-4 hlavní vlastnosti modelu nativní pro Cloud.

> ![Jsou to Mikroslužby, cloud odolné, orchestrátorů kontejnerů, charakteristiky nativní pro cloud a bez serveru](./media/image4.png)
>
> **Obrázek 4-4.** Vlastnosti nativní pro cloud

Kromě toho můžete rozšířit základní moderních webových aplikací a aplikací nativních pro cloud tak, že přidáte další služby, jako je umělá inteligence (AI), machine learning (ML) a IoT. Libovolné z těchto služeb můžete použít k rozšíření všech možných přístupů optimalizovaných pro Cloud.

V architektuře aplikace je zásadní rozdíl v aplikacích na úrovni nativní pro Cloud. Aplikací nativních pro cloud se podle definice aplikace, které jsou založené na mikroslužbách. Nativně cloudové aplikace vyžadují speciální architektury, technologie a platformy, ve srovnání s monolitické webovou aplikaci nebo tradiční N-vrstvou aplikaci.

## <a name="cloud-native-applications-details"></a>Podrobnosti o aplikací nativních pro cloud

Nativní pro cloud se o rozšířené nebo až po zralé stav pro velký i klíčové podnikové aplikace. Nativně cloudové aplikace obvykle vyžadují architektury a návrhu, které vytvářejí úplně od začátku místo modernizaci stávajících aplikací. Klíčovým rozdílem mezi aplikací nativních pro Cloud a jednodušší optimalizovaných Cloudů webové aplikace se doporučuje použít architekturu mikroslužeb v metodě nativní pro cloud. Optimalizovaných pro cloudové aplikace může být také monolitické web apps nebo N-vrstvé aplikace.

[12-Factor App](https://12factor.net/) (kolekce vzory, které jsou úzce související s přístupy k mikroslužeb) bude také považován za požadavek na architektury aplikací nativních pro cloud.

[Foundation nativní computingu na Cloud (CNCF)](https://www.cncf.io/) je primární promoter principů nativní pro cloud. Společnost Microsoft [člena CNCF](https://azure.microsoft.com/blog/announcing-cncf/).

Ukázková definice a další informace o vlastnostech aplikací nativních pro cloud, najdete v článku společnosti Gartner [architektury a návrhu aplikací nativních pro cloud](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications). Konkrétní pokyny od Microsoftu o tom, jak implementovat aplikace nativní pro cloud, najdete v části [mikroslužby .NET: Architektura pro kontejnerizované aplikace .NET](https://aka.ms/microservicesebook).

Nejdůležitějším faktorem vzít v úvahu, pokud migrujete celé aplikace nativní pro cloud modelu je, že musí úprava architektury na architekturu založených na mikroslužbách. Z důvodu velkého refaktoringu proces, který je zahrnutý to jasně vyžadovala významnou investici ve vývoji. Tato možnost je obvykle vybrána pro důležité podnikové aplikace, které vyžadují nové úrovni, škálovatelnost a pružnost dlouhodobé. Ale můžete začít s přesunem směrem k nativní pro cloud tak, že přidáte mikroslužeb pro několika nové scénáře a nakonec Refaktorovat aplikace plně jako mikroslužeb. Toto je přírůstkové přístup, který je nejlepší volbou pro několik scénářů.

## <a name="what-about-microservices"></a>Jak je to mikroslužby?

Principy mikroslužeb a jak fungují je důležité, pokud zvažujete aplikací nativních pro cloud pro vaši organizaci.

Architektura mikroslužeb představuje pokročilé přístup, který můžete použít pro aplikace, které se vytvoří úplně od začátku nebo vyvíjí stávající aplikace směrem k aplikací nativních pro cloud. Můžete začít tak, že přidáte několik mikroslužby do stávajících aplikací do další informace o nové modely mikroslužeb. Ale jasně, je potřeba architekt a kódem, zejména u tohoto typu architektonický přístup umožňuje vytvářet.

Mikroslužby ale nejsou povinné pro všechny nové nebo moderní aplikace. Mikroslužby nejsou "magic bullet" a jedné, nejlepší způsob, jak vytvořit každá aplikace, a proto nejsou. Jak a kdy použijete mikroslužeb závisí na typu aplikace, budete muset sestavit.

Architektura mikroslužeb se mění na upřednostňovaný způsob pro distribuované a rozsáhlých nebo složitých důležité podnikové aplikace, které jsou založeny na více nezávislých subsystémy ve formě autonomních služeb. V architektuře mikroslužeb na základě aplikace je vytvořený jako kolekce služeb, které se dají nezávisle vyvinuté, otestované, verze, nasadit a škálovat. To může zahrnovat všechny související, autonomních databáze na mikroslužbách.

Podrobný pohled na architekturu mikroslužeb, která můžete implementovat pomocí .NET Core, naleznete v tématu ke stažení PDF e kniha [mikroslužby .NET: Architektura pro kontejnerizované aplikace .NET](https://aka.ms/microservicesebook). V průvodci je dostupná také [online](../../microservices-architecture/index.md).

Ale i ve scénářích, ve kterých mikroslužeb nabízejí výkonné možnosti nezávislé na nasazení, silné subsystému hranice a technologie rozmanitosti-vyvolají také mnoho nové výzvy. Výzvy se vztahují k vývoji distribuované aplikace, jako je například fragmentace a nezávislé datové modely; zajištění odolného komunikace mezi mikroslužbami; potřebu konečné konzistence; a provozní složitost. Mikroslužby zavést vyšší úroveň složitosti ve srovnání s tradičním monolitické aplikace.

Z důvodu složitosti architekturu mikroslužeb jsou vhodné pro aplikace založené na mikroslužbách pouze konkrétních scénářů a určité typy aplikací. Patří mezi ně velkých a složitých aplikací, které obsahují více subsystémů se vyvíjejí. V těchto případech je vhodné prošetřují složitější architektury softwaru, pro dlouhodobou pohotovější a efektivnější údržbu aplikace. Ale pro scénáře, méně složitý, může být lepší pokračovat s přístupem monolitické aplikace nebo blíží jednodušší N-vrstvou.

Jako poslední poznámku, dokonce i jeho nebezpečí vrácení opakované o tento koncept by neměl podíváte na používání mikroslužeb ve vašich aplikacích jako "čistě nebo nic vůbec." Můžete rozšířit a rozvíjet existující monolitické aplikace tak, že přidáte nový, malé scénáře založené na mikroslužbách. Není nutné začít od nuly, pokud chcete začít pracovat s přístupem architekturu mikroslužeb. Doporučujeme ve skutečnosti můžete vyvíjet pomocí existující monolitické nebo N-vrstvou aplikaci tak, že přidáte nové scénáře. Nakonec můžete rozdělit aplikace do autonomní komponent a mikroslužeb. Chcete-li začít, vyvíjejí monolitických aplikací ve směru mikroslužeb, krok za krokem.

V každém případě zbývající část tohoto návod zaměřuje většinu všech na "žádný mikroslužbových aplikací" vzhledem k tomu, že tento návod je především cílení modernizaci stávajících aplikací, které mají obvykle monolitické nebo N-úrovňové architektury.

> [!div class="step-by-step"]
> [Předchozí](microsoft-technologies-in-cloud-optimized-applications.md)
> [další](deploy-existing-net-apps-as-windows-containers.md)
