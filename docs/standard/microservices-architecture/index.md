---
title: Mikroslužby .NET. Architektura pro kontejnerizované aplikace .NET
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Mikroslužby jsou modulární a umožňují nezávislé nasazení služby. Kontejnery dockeru (pro systémy Linux a Windows) zjednodušit nasazování a testování seskupí služby a jeho závislosti do jedné jednotky, které je potom spouštět v izolovaném prostředí.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: e1b36f5a6ddc2176e344dfe2a216429190dcc1dc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615143"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a>Mikroslužby .NET: Architektura pro kontejnerizované aplikace .NET

![Titulní knihy](./media/cover-small.png)

**EDICE v2.2.00** – aktualizováno, aby ASP.NET Core 2.2

Tato příručka slouží jako úvod k vývoji aplikací založených na mikroslužbách a správu kontejnerů. Tento článek popisuje kontrol architektonického návrhu a implementace přístupy pomocí .NET Core a kontejnery Dockeru. 

Aby bylo snazší, abyste mohli začít, průvodce se zaměřuje na odkaz kontejnerizovaných a aplikací založených na mikroslužbách, kterou můžete prozkoumat. Referenční aplikace je k dispozici na [aplikaci eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) úložiště GitHub.

## <a name="action-links"></a>Odkazy na akce

* Stáhněte si tuto e-kniha ve formát vašeho výběru: | [PDF](https://aka.ms/microservicesebook) | [MOBI](https://www.microsoft.com/net/download/thank-you/microservices-architecture-ebook-mobi) | [EPUB](https://www.microsoft.com/net/download/thank-you/microservices-architecture-ebook-epub) |

* Klon/Forku referenční aplikace [aplikaci eShopOnContainers na Githubu](https://github.com/dotnet-architecture/eShopOnContainers)
 
* Podívejte [úvodní video na Channel 9](https://aka.ms/microservices-video)

* Seznamte se [architektury Mikroslužeb](https://aka.ms/MicroservicesArchitecture) hned

## <a name="introduction"></a>Úvod

Podniky jsou stále porozumění úspory nákladů, řešení problémů s nasazením a zlepšení operace DevOps a produkčním prostředí pomocí kontejnerů. Microsoft má byla uvolnění inovace kontejner pro Windows a Linux tak, že vytvoříte produkty, jako je Azure Container Service a Azure Service Fabric a díky partnerství s vedoucím postavením, jako je Docker, Mesosphere a Kubernetes. Tyto produkty poskytovat kontejneru řešení, která pomáhají společnostem sestavovat a nasazovat aplikace v cloudu rychlost a škálování, kterou si sami vyberou platformy nebo nástroje.

Docker je stále de facto standardem v odvětví kontejneru, podporovány jsou nejdůležitější dodavatelé v ekosystémů Windows a Linux. (Microsoft je hlavní cloudových vendorů, podporu Dockeru.) V budoucích verzích Dockeru bude pravděpodobně všudypřítomná v libovolné datacentrum do cloudu nebo lokálně.

Kromě toho [mikroslužeb](https://martinfowler.com/articles/microservices.html) architektura je nově vznikající jako důležité přístup pro distribuované klíčové aplikace. V architektuře s využitím mikroslužeb je aplikace sestavená u kolekce služeb, které mohou být vytvořeny, otestovat, nasazené a systémovou správou verzí nezávisle na sobě.

## <a name="about-this-guide"></a>Informace o této příručce

Tato příručka slouží jako úvod k vývoji aplikací založených na mikroslužbách a správu kontejnerů. Tento článek popisuje kontrol architektonického návrhu a implementace přístupy pomocí .NET Core a kontejnery Dockeru. Aby bylo snazší začít pracovat s kontejnery a mikroslužby, průvodce se zaměřuje na odkaz kontejnerizovaných a aplikací založených na mikroslužbách, kterou můžete prozkoumat. Ukázková aplikace je k dispozici na [aplikaci eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) úložiště GitHub.

Tato příručka obsahuje základní vývoj a doprovodné materiály k architektuře primárně na úrovni prostředí vývoj se zaměřením na technologie: .NET Core a docker. Naším úmyslem je, že si přečtete tuto příručku při posuzování návrhu aplikace, nemusíte se soustředit na infrastrukturu (v cloudu nebo místních) vašeho produkčního prostředí. Bude rozhodnutí o infrastruktuře později, při vytváření aplikace připravené pro produkční prostředí. Proto tato příručka je určena být nezávislá a více vývojové prostředí – zaměřené na infrastrukturu.

Po zkoumali této příručce, bude dalším krokem je další informace o mikroslužbách připravené pro produkční prostředí v Microsoft Azure.

## <a name="version"></a>Version

Tento průvodce byl změněn na pokrytí **.NET Core 2.2** verze a mnoho dalších aktualizace související s stejné "wave" technologií (tj. Azure a další 3. stran technologie) okamžiku v čase s nástroji .NET Core 2.2. To je důvod, proč verze knihy se také aktualizovala na verzi **2.2**. 

## <a name="what-this-guide-does-not-cover"></a>Co tato příručka nepopisuje

Tato příručka se nezaměřuje na životního cyklu aplikací, vývoj a provoz kanálů CI/CD nebo tým pracovat. Doplňkové průvodce [Kontejnerizovaných životní cyklus aplikace Dockeru s platformou a nástroji Microsoft](https://aka.ms/dockerlifecycleebook) se zaměřuje na tohoto subjektu. Aktuální Průvodce také neposkytuje podrobné informace o implementaci na infrastrukturu Azure, jako je například informace o konkrétní orchestrátorů.

### <a name="additional-resources"></a>Další zdroje

- **Životní cyklus aplikace Dockeru s platformou a nástroji Microsoft kontejnerizovaných** (ke stažení e kniha)  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a>Kdo by měl používat tohoto průvodce

Jsme napsali Tato příručka pro vývojáře a architekty řešení, kteří jsou nové pro vývoj aplikací založených na Dockeru a architektura založená na mikroslužbách. Tento průvodce je pro, pokud chcete získat informace tom, jak navrhovat, navrhování a implementace aplikací testování konceptu s vývojovým technologiím Microsoftu (se zvláštním zaměřením na .NET Core) a s kontejnery Dockeru.

Také zjistíte Tato příručka užitečné, pokud jste technický pracovník s rozhodovací pravomocí, jako je například podnikový architekt, kdo chce, aby se architektura a přehledu technologie před rozhodnout, na jaké přístup k výběru pro nové a moderní distribuované aplikace.

### <a name="how-to-use-this-guide"></a>Jak používat tohoto průvodce

První části této příručky zavádí kontejnery Dockeru, popisuje, jak si vybrat mezi .NET Core a .NET Framework jako rozhraní pro vývoj a najdete zde přehled mikroslužeb. Tento obsah je pro architekty a technické pracovníky s rozhodovací pravomocí, kteří mají přehled, ale není potřeba zaměřit se na podrobnosti implementace kódu.

Začíná druhé části v průvodci [aplikací založených na proces vývoje pro Docker](./docker-application-development-process/index.md) oddílu. Zaměřuje se na vývoj a mikroslužeb vzory pro provádění aplikací pomocí .NET Core a Docker. Tato část bude mít největší zájem vývojářům a architektům, kteří chtějí soustředit se na kód a vzorců a podrobnosti implementace.

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a>Související mikroslužby a aplikace založené na kontejnerech odkaz: aplikaci eShopOnContainers

Aplikaci eShopOnContainers aplikace je odkaz na open source aplikace pro .NET Core a mikroslužeb, která slouží k nasazení kontejnerů Dockeru. Aplikace se skládá z více subsystémů, včetně několik e-store uživatelského rozhraní front-endů (aplikace Web MVC, SPA webové a nativní mobilní aplikace). Zahrnuje také back-end mikroslužeb a kontejnerů pro všechny požadované operace na straně serveru. 

Účelem aplikace je k prezentaci vzorech architektury. **IT není připravené pro produkční prostředí ŠABLONU** ke spouštění skutečných aplikací. Aplikace ve skutečnosti je ve stavu trvalé beta, jak se také používá k testování nových potenciálně zajímavý technologií, jako zobrazí.

## <a name="send-us-your-feedback"></a>Pošlete nám svůj názor!

Jsme napsali této příručce, které vám pomůžou porozumět architektuře mikroslužeb v rozhraní .NET a kontejnerizovaných aplikací. Průvodce a související referenční aplikace bude se vyvíjí, takže vaše připomínky budou vítány! Pokud máte připomínky jak se tento průvodce může zlepšit, odešlete jim:

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

## <a name="credits"></a>Závěrečné titulky

Spoluautoři:

> **De la Torre Cesarovi**, Senior PM, .NET produktový tým Microsoft Corp.
>
> **Bill Wagnera**, Senior obsahu pro vývojáře, C + E, Microsoft Corp.
>
> **Mike Rousos**, hlavní softwarový inženýr, týmu DevDiv CAT, Microsoft

Editory:

> **Mike Pope**
>
> **Steve Hoag**

Účastníci a recenzenti:

> **Jeffrey Richter**, Partner softwaru Eng týmu Azure, Microsoft
>
> **Jimmy Bogard**, hlavní architekt na Headspring
>
> **UDI Dahan**, Zakladatel a generální ředitel, určitého softwaru
>
> **Jimmy Nilsson**, Spoluzakladatel a generální Factor10
>
> **Glenn Condron**, Senior Program Manager tým ASP.NET
>
> **Označit Fussell**, hlavní Projektový manažer zájemce, tým Azure Service Fabric, Microsoft
>
> **Diego Vega**, PM zájemce, Entity Framework týmu, Microsoft
>
> **Jiří Dorrans**, hlavní manažer programu zabezpečení
>
> **Rowan Miller**, Senior Program Manager, Microsoft
>
> **Ankit Asthana**, hlavní manažer PM, týmu .NET, Microsoft
>
> **Scott Hunter**, Partner Director oddělení PM, týmu .NET, Microsoft
>
> **Dokončení Anil**, hlavní programový manažer týmu .NET, Microsoft
>
> **Dylan Reisenberger**, architekt a vedoucí vývoje v Polly
>
> **Steve Smith**, Tvůrce softwaru & Trainer na ASPSmith Ltd.
>
> **Ian Cooper**, kódování navrhovat jasnější na
>
> **Unai Zorrilla**, architekt a vedoucí vývoje v Plain Concepts
>
> **Eduard Tomáši**, vedoucí vývoje v Plain Concepts
>
> **Ramon Tomáši**, vývojář v Plain Concepts
>
> **David Sanz**, vývojář v Plain Concepts
>
> **Javier Valero**, hlavní, provozní ředitel ve Grupo řešení
>
> **Pierre Millet**, Sr. Consultant, Microsoft
>
> **Michael Friis**, správce produktu, Inc Dockeru
>
> **Charles Lowell**, softwarový inženýr, týmu VS CAT, Microsoft
>
> **Miguel Veloso**, Senior konzultant na Turing výzvy

## <a name="copyright"></a>Copyright

Ke stažení je k dispozici na: <https://aka.ms/microservicesebook>

PUBLIKOVAL(A)

Microsoft Developer Division, .NET a Visual Studio produktových týmů

A division of Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2018 by Microsoft Corporation

Všechna práva vyhrazena. Žádná část obsahu této knihy může reprodukovat nebo v libovolné formě nebo jakýmikoli prostředky bez písemného souhlasu vydavatele.

Tato kniha je k dispozici "jako-je" a vyjadřuje zobrazení autora a názory. Zobrazení, názory a informace v této knize, včetně adres URL a jiných odkazů na internetové weby, mohou změnit bez předchozího upozornění.

Některé zde uvedené příklady jsou k dispozici pouze pro ilustraci a jsou smyšlené. Žádný skutečný vztah nebo spojení ani je určena ji vyvozovat.

Microsoft a ochranné známky uvedený na <https://www.microsoft.com> na webové stránce "Ochranné známky" jsou obchodní známky společností skupiny Microsoft.

Mac a macOS jsou ochranné známky společnosti Apple Inc.

Velryba logo Dockeru je registrovaná ochranná známka společnosti Docker, Inc. Použít oprávnění.

Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.

>[!div class="step-by-step"]
>[Next](container-docker-introduction/index.md)
