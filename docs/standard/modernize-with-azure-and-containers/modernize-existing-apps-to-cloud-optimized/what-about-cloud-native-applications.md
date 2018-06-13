---
title: Co nativní cloudové aplikace?
description: Modernizovat existující aplikace .NET s kontejnery cloudu Azure a Windows | Co nativní cloudové aplikace?
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 0e880689001ece2b770811cfbe3fea43aa425b32
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958236"
---
# <a name="what-about-cloud-native-applications"></a>Co nativní cloudové aplikace?

I když [cloudu nativní](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) aplikace nejsou hlavní výběr tohoto průvodce, je vhodné získat představu o vyspělosti tento modernizace a ho odlišuje od optimalizovaný pro cloudové aplikace.

Obrázek 4-3 umisťuje cloudu nativní aplikace v úrovni vyspělosti modernizace aplikace:

![Umístění cloudu nativní aplikace](./media/image3.png)

> **Obrázek 4-3.** Umístění cloudu nativní aplikace

Vyspělosti cloudu nativní modernizace obvykle vyžaduje investice do nové vývoj. Přechodu na úroveň nativní cloudu je většinou vycházejí z obchodních potřeb modernizovat možné míře výrazně zlepšit měřítka ve velké aplikace tak, že vytvoříte autonomního subsystémy (mikroslužeb), které mohou být nasazeny a škálování aplikací nezávisle z jiných oblastí aplikace současně snižuje náklady v dlouhou dobu a zvýšení vývoj flexibility částí těchto autonomního aplikace, které poskytují pokouší významné výhody. 

Hlavní pilíře z [cloudu nativní](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) aplikací jsou založeny na mikroslužeb architektura přístupů, které můžete momentální s flexibility a škálovat limity, které může být obtížné zajistit v architektuře monolitický nasadit buď místní nebo cloudové prostředí.

Na obrázku 4-4 je hlavní vlastnosti cloudu nativní modelu.  

> ![Vlastnosti cloudu nativní jsou Mikroslužeb kontejnery, cloudu odolné, orchestrators a serverles](./media/image4.png)
>
> **Obrázek 4 – 4.** Vlastnosti nativní cloudu

Kromě toho můžete rozšířit základní moderní webové aplikace a nativní cloudové aplikace přidáním dalších služeb, jako jsou umělé intelligence (AI), machine learning (ML) a IoT. K rozšíření některé z možných přístupů optimalizovaných Cloudů může použít kterýkoli z těchto služeb.

V architektuře aplikace je zásadní rozdíl v aplikacích na úrovni cloudu nativní. [Nativní cloudu](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) aplikace jsou podle definice aplikace, které jsou založeny na mikroslužeb. Nativní cloudové aplikace vyžadují speciální architektury, technologie a platformy, ve srovnání s monolitický webové aplikace nebo tradiční N-vrstvá aplikace.

## <a name="cloud-native-applications-details"></a>Podrobnosti o cloudu nativní aplikace

[Nativní cloudu](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) více pokročilé nebo vyspělá stav pro velké a důležitých aplikací. Cloud nativní aplikace obvykle vyžadují architektury a návrhu, který vytvářejí od začátku místo modernizace stávající aplikace. Klíče rozdíl mezi nativní cloudové aplikace a jednodušší optimalizovaných Cloudů webové aplikace je doporučení k použití architektury mikroslužeb v cloudu nativní přístup. Optimalizovaný pro cloudové aplikace může být také monolitický webové aplikace nebo vícevrstvé aplikace.

[Dvanácti-Factor aplikace](https://12factor.net/) (kolekce schémat, které úzce souvisejí s mikroslužeb přístupy) se také považuje za požadavek na [cloudu nativní](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) architektury aplikace.

[Foundation nativní Computing na cloudu (CNCF)](https://www.cncf.io/) je primární vykonavatel cloudu nativní norem. Společnost Microsoft [členem CNCF](https://azure.microsoft.com/blog/announcing-cncf/).

Ukázka definice a další informace o vlastnostech cloudu nativních aplikací, najdete v článku Gartner [pro navrhování a návrhu cloudu nativní aplikace](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications). Konkrétní pokyny od společnosti Microsoft o tom, jak implementovat nativní cloudové aplikace, najdete v části [mikroslužeb .NET: architektura pro kontejnerové aplikace .NET](https://aka.ms/microservicesebook).

Nejdůležitějším faktorem vzít v úvahu, pokud migrujete celou aplikaci do [cloudu nativní](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) modelu je, že musí rearchitect architektury se na základě mikroslužeb. To vyžaduje jasně významné investice do vývoj z důvodu velkého refaktoringu proces zahrnutý. Tato možnost je obvykle vybrána pro kritické aplikace, které potřebují nové úrovně, škálovatelnost a dlouhodobé flexibility. Ale můžete spustit přesun směrem k cloudu nativní přidáním mikroslužeb pro několika nové scénáře a nakonec Refaktorovat aplikace plně jako mikroslužeb. Toto je přírůstkové přístup, který je nejlepší možnost pro některé scénáře.

## <a name="what-about-microservices"></a>Co mikroslužeb? 

Principy mikroslužeb a jak pracují je důležité, pokud uvažujete o cloudu nativní aplikace pro vaši organizaci.

Architektura mikroslužeb je rozšířené, můžete použít pro aplikace, které jsou vytvořeny od nuly nebo momentální stávající aplikace směrem k cloudu nativní aplikace přístup. Můžete spustit přidáním několik mikroslužeb do stávajících aplikací Další informace o nových vzorů mikroslužeb. Ale je zřejmé, budete muset architekti a kód, zejména pro tento typ architektury přístup.

Mikroslužeb však nejsou povinné pro všechny nové nebo moderní aplikace. Mikroslužeb nejsou "magic bullet", a nejsou jeden, nejlepší způsob, jak vytvořit každou aplikaci. Jak a kdy použijete mikroslužeb závisí na typu aplikace, které potřebujete k vytvoření.

Architektura mikroslužeb se stává stále žádoucí pro distribuované a velké nebo složité kritické aplikace, které jsou založeny na více nezávislých subsystémy ve formě autonomního služby. V architektuře na základě mikroslužeb vychází aplikace jako kolekce služeb, které můžou být nezávisle vyvinuté, otestovaný, verzí, nasazení a škálovat. To může zahrnovat všechny související, autonomního databáze za mikroslužby.

Podrobný pohled na architekturu mikroslužeb, která můžete implementovat pomocí .NET Core, najdete v části Stažení PDF e kniha [mikroslužeb .NET: architektura pro kontejnerové aplikace .NET](https://aka.ms/microservicesebook). V průvodci je dostupná také [online](../../microservices-architecture/index.md).

Ale i ve scénářích, ve kterých mikroslužeb nabízí výkonné nasazení nezávislé na schopnosti, silné subsystému hranice a různorodost technologie-vyvolají mnoho nových problémů. Na výzvy se vztahují k vývoji distribuované aplikace, jako je například fragmentovaných a nezávislé datové modely; dosažení odolné komunikace mezi mikroslužeb; potřebu konzistence typu případné; a provozní složitost. Mikroslužeb zavést vyšší úroveň složitosti porovnání s tradiční monolitický aplikace.

Z důvodu složitosti mikroslužeb architektura jsou vhodné pro aplikace založené na mikroslužbu jenom konkrétních scénářů a některé typy aplikací. Patří mezi ně velké a komplexní aplikace, které mají více vyvíjející se subsystémy. V těchto případech je vhodné Investujete do složitější architektura softwaru, pro dlouhodobou vyšší flexibility a efektivnější Údržba aplikace. Ale pro méně složitých scénářů, může být lepší pokračujte s přístupem monolitický aplikace nebo blíží jednodušší N-vrstvá.

Jako poslední Poznámka, i jeho nebezpečí vrácení opakovaných o tento koncept nesmí si prohlédnete pomocí mikroslužeb ve svých aplikacích jako "celkovou nebo nic na všechny." Můžete rozšířit a momentální stávající monolitický aplikace tak, že přidáte nový, malé scénáře podle mikroslužeb. Nemusíte začít úplně od začátku, pokud chcete začít pracovat s přístupem architektura mikroslužeb. Ve skutečnosti doporučujeme vám momentální pomocí stávající monolitický nebo vícevrstvé aplikace přidáním nové scénáře. Nakonec se analyzují aplikaci do autonomního součásti nebo mikroslužeb. Můžete začít vyvíjející se aplikace monolitický mikroslužeb směrem, krok za krokem.

V každém případě zbytek přítomen návod zaměřuje většinu všech na "žádné aplikace, na základě mikroslužeb" vzhledem k tomu, že v tomto návodu je především cílení modernizace aplikace, které obvykle mají monolitický nebo vícevrstvé architektury.


>[!div class="step-by-step"]
[Předchozí](microsoft-technologies-in-cloud-optimized-applications.md)
[další](deploy-existing-net-apps-as-windows-containers.md)
