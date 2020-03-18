---
title: Co jsou nativní cloudové aplikace?
description: Modernizace stávajících aplikací .NET pomocí Azure Cloudu a kontejnerů Windows | A co aplikace nativní pro cloud?
ms.date: 04/28/2018
ms.openlocfilehash: d2a7f89e347d75ddbdae84c8eb57e32447b83297
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77543544"
---
# <a name="what-about-cloud-native-applications"></a>Co jsou nativní cloudové aplikace?

Přestože [cloudnativní](https://azure.microsoft.com/overview/cloudnative/) aplikace nejsou hlavním zaměřením této příručky, je užitečné mít pochopení této úrovně vyspělosti modernizace a odlišit ji od aplikací optimalizovaných pro cloud.

Obrázek 4-3 pozice Cloud-Nativní aplikace v úrovních splatnosti modernizace aplikace:

![Diagram znázorňující, jak umístit cloudnativní aplikace.](./media/what-about-cloud-native-applications/positioning-cloud-native-applications.png)

**Obrázek 4-3.** Umístění cloudových nativních aplikací

Úroveň vyspělosti modernizace cloud-native obvykle vyžaduje nové investice do rozvoje. Přechod na úroveň Cloud-Native je obvykle řízen obchodní potřebou co nejvíce modernizovat aplikace, aby se výrazně zlepšilo škálování ve velkých aplikacích vytvořením autonomních subsystémů (mikroslužeb), které lze nasadit a škálovat nezávisle z jiných oblastí aplikace při dlouhodobém snížení nákladů a zvýšení agility vývoje částí autonomní aplikace, které poskytují významné konkurenční výhody.

Hlavní pilíře cloudových nativních aplikací jsou založeny na přístupech architektury mikroslužeb, které se mohou vyvíjet s agilitou a škálovat na omezení, která by bylo obtížné dosáhnout v monolitické architektuře, nasazené v místním nebo cloudu Prostředí.

Obrázek 4-4 ukazuje hlavní charakteristiky modelu Cloud-Native.

![Diagram se seznamem hlavních charakteristik nativních v cloudu.](./media/what-about-cloud-native-applications/cloud-native-characteristics.png)

**Obrázek 4-4.** Charakteristiky nativní pro cloud

Kromě toho můžete rozšířit základní moderní webové aplikace a aplikace nativní pro cloud přidáním dalších služeb, jako je umělá inteligence (AI), strojové učení (ML) a IoT. Některou z těchto služeb můžete použít k rozšíření některého z možných přístupů optimalizovaných pro cloud.

Zásadní rozdíl v aplikacích na úrovni Cloud-Native je v architektuře aplikace. Cloudnativní aplikace jsou podle definice aplikace, které jsou založeny na mikroslužbách. Aplikace nativní pro cloud vyžadují speciální architektury, technologie a platformy ve srovnání s monolitickou webovou aplikací nebo tradiční nvrstvou aplikací.

## <a name="cloud-native-applications-details"></a>Podrobnosti o aplikacích nativních pro cloud

Cloud-Native je pokročilejší nebo vyspělejší stav pro velké a kritické aplikace. Cloudnativní aplikace obvykle vyžadují architekturu a návrh, které jsou vytvořeny od začátku namísto modernizací stávajících aplikací. Klíčovým rozdílem mezi aplikací cloud-native a jednodušší webovou aplikací optimalizovanou pro cloud je doporučení používat architektury mikroslužeb v přístupu nativním pro cloud. Aplikace optimalizované pro cloud mohou být také monolitické webové aplikace nebo nvrstvé aplikace.

[Aplikace twelve-factor](https://12factor.net/) (kolekce vzorů, které úzce souvisejí s přístupy mikroslužeb) je také považován za požadavek pro architektury aplikací nativní pro cloud.

[Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) je primárním propagátorem principů nativního pro cloud. Společnost Microsoft je [členem CNCF](https://azure.microsoft.com/blog/announcing-cncf/).

Podrobné pokyny k navrhování a vývoji aplikací nativních pro cloud například načtete následující bezplatné e-knihy:

* [Navrhování cloudových nativních aplikací .NET pro Azure](../../cloud-native/introduction.md)
* [.NET Microservices: Architektura pro kontejnerizované aplikace .NET](../../microservices/index.md).

Nejdůležitějším faktorem, který je třeba zvážit, pokud migrujete úplnou aplikaci do modelu nativního pro cloud, je, že je nutné předělat architekturu založenou na mikroslužbách. To jednoznačně vyžaduje značné investice do rozvoje vzhledem k rozsáhlému procesu refaktoringu. Tato možnost je obvykle vybrána pro klíčové aplikace, které vyžadují nové úrovně škálovatelnosti a dlouhodobé agility. Ale můžete začít přechod směrem ke cloudnativní přidáním mikroslužeb pro několik nových scénářů a nakonec refaktorovat aplikaci plně jako mikroslužeb. Toto je přírůstkový přístup, který je nejlepší volbou pro některé scénáře.

## <a name="what-about-microservices"></a>A co mikroslužby?

Pochopení mikroslužeb a jak fungují, je důležité, když uvažujete o cloudnativní aplikace pro vaši organizaci.

Architektura mikroslužeb je pokročilý přístup, který můžete použít pro aplikace, které jsou vytvořeny od začátku nebo při vývoji existujících aplikací směrem k aplikacím nativním pro cloud. Můžete začít přidáním několika mikroslužeb do existujících aplikací se dozvíte o nové paradigmata mikroslužeb. Ale je zřejmé, že je třeba architekt a kód, a to zejména pro tento typ architektonického přístupu.

Mikroslužby však nejsou povinné pro všechny nové nebo moderní aplikace. Mikroslužby nejsou "magické bullet" a nejsou jediný, nejlepší způsob, jak vytvořit každou aplikaci. Jak a kdy používáte mikroslužeb závisí na typu aplikace, které je třeba vytvořit.

Architektura mikroslužeb se stává upřednostňovaným přístupem pro distribuované a rozsáhlé nebo složité důležité aplikace, které jsou založeny na více nezávislých subsystémech ve formě autonomních služeb. V architektuře založené na mikroslužbách je aplikace vytvořena jako kolekce služeb, které lze nezávisle vyvíjet, testovat, nastavovat verzemi, nasazovat a škálovat. To může zahrnovat všechny související, autonomní databáze na mikroslužbu.

Podrobný pohled na architekturu mikroslužeb, kterou můžete implementovat pomocí .NET Core, naleznete v souboru PDF e-book [.NET microservices: Architecture for containerized .NET applications](https://aka.ms/microservicesebook). Průvodce je také k dispozici [on-line](../../microservices/index.md).

Ale i ve scénářích, ve kterých mikroslužby nabízejí výkonné nasazení nezávislé na možnostech, silné hranice subsystému a rozmanitost technologií- také vyvolávají mnoho nových výzev. Výzvy souvisejí s vývojem distribuovaných aplikací, jako jsou fragmentované a nezávislé datové modely; dosažení odolné komunikace mezi mikroslužbami; potřebu případné soudržnosti; a provozní složitosti. Mikroslužby zavést vyšší úroveň složitosti ve srovnání s tradiční monolitické aplikace.

Z důvodu složitosti architektury mikroslužeb jsou vhodné pouze konkrétní scénáře a určité typy aplikací pro aplikace založené na mikroslužbách. Patří mezi ně velké a složité aplikace, které mají více, vyvíjející se subsystémy. V těchto případech stojí za to investovat do složitější softwarové architektury pro zvýšení dlouhodobé flexibility a efektivnější údržby aplikací. Ale pro méně složité scénáře může být lepší pokračovat s monolitické aplikace přístup nebo jednodušší N-vrstvé přístupy.

Jako poslední poznámka, i na riziko, že se bude opakující o tomto konceptu, neměli byste se podívat na používání mikroslužeb ve vašich aplikacích jako "all-in nebo vůbec nic." Můžete rozšířit a vyvíjet stávající monolitické aplikace přidáním nových, malých scénářů založených na mikroslužbách. Nemusíte začínat od začátku začít pracovat s přístupem architektury mikroslužeb. Ve skutečnosti doporučujeme, abyste se vyvinuli z používání existující monolitické nebo N-vrstvé aplikace přidáním nových scénářů. Nakonec můžete rozdělit aplikace do autonomní ch odpočitadla nebo mikroslužeb. Můžete začít vyvíjet monolitické aplikace ve směru mikroslužeb krok za krokem.

V každém případě se zbytek tohoto současného návodu zaměřuje především na "žádné aplikace založené na mikroslužbách", protože tento návod se zaměřuje především na modernizaci stávajících aplikací, které obvykle mají monolitické nebo N-vrstvé architektury.

> [!div class="step-by-step"]
> [Předchozí](microsoft-technologies-in-cloud-optimized-applications.md)
> [další](deploy-existing-net-apps-as-windows-containers.md)
