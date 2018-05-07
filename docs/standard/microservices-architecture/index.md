---
title: Rozhraní .NET Mikroslužeb. Architektura pro aplikace .NET Kontejnerizované
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Úvodní část
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: d4499384d63f11a1d78d0aa84749aed8ea554794
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
![](./media/cover.png)

# <a name="net-microservices-architecture-for-containerized-net-applications"></a>Rozhraní .NET Mikroslužeb. Architektura pro aplikace .NET Kontejnerizované

Stáhněte si k dispozici na: <https://aka.ms/microservicesebook>

PUBLIKOVÁNO

Týmy pro produkt Microsoft Developer dělení, rozhraní .NET a Visual Studio

Dělení společnosti Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © Microsoft Corporation 2017

Všechna práva vyhrazena. Žádná z částí obsah této příručky je možné reprodukovat nebo přenést v žádný formulář nebo žádnými prostředky bez předchozího písemného souhlasu vydavatele.

Tato kniha je k dispozici "jako-je" a vyjadřoval zobrazení a názory vytvářením obsahu. Zobrazení, názory a informace v této příručce, včetně adres URL a dalších odkazů na internetové weby, mohou změnit bez předchozího upozornění.

Některé příklady použité v ukázkách jsou jenom ilustrativní a smyšlené. Žádný skutečný vztah nebo připojení je určený nebo událostmi.

Společnost Microsoft a ochranné známky uvedený na http://www.microsoft.com na webové stránce "Ochranné známky" jsou obchodní známky společností skupiny Microsoft.

Mac a systému macOS jsou ochranné známky společnosti Apple, Inc.

Logo velryba Docker je registrovaná ochranná známka společnosti Docker, Inc. Pomocí oprávnění.

Všechny ostatní značky a loga jsou vlastnictvím příslušných vlastníků.

Spoluautoři:

> **Cesaru členka Torre**, Sr. PM, .NET produktový tým Microsoft Corp.
>
> **Faktury Wagnera**, Sr. Obsahu Developer, C + E, Microsoft Corp.
>
> **Jan Rousos**, hlavní softwaru pracovníka, týmu DevDiv CAT, Microsoft

Editory:

> **Jan Pope**
>
> **Steve Hoag**

Účastníci a recenzenti:

> **Jana Richter**, Eng softwaru partnera, tým Azure, Microsoft
>
> **Jimmy Bogard**, hlavní architekt v Headspring
>
> **UDI Dahan**, zakladatele & CEO, určitého softwaru
>
> **Jimmy Nilsson**, společné zakladatele a CEO Factor10
>
> **Glenn Condron**, Sr. Manažer programu ASP.NET team
>
> **Označit Fussell**, hlavní PM realizace, tým Azure Service Fabric, Microsoft
>
> **Diego Vega**, PM realizace, rozhraní Entity Framework tým Microsoft
>
> **Jiří Dorrans**, Sr. Program Správce zabezpečení
>
> **Rowan Lukeš**, Sr. Manažer programu Microsoft
>
> **Ankit Asthana**, hlavní manažer PM, .NET tým Microsoft
>
> **Scott Hunter**, ředitel partnera PM, .NET tým Microsoft
>
> **Dylan Reisenberger**, architekty a vývojáře realizace v Polly
>
> **Steve Smith**, Craftsman softwaru & Trainer ve ASPSmith Ltd.
>
> **Ian Cooper**, kódování architektury v jasnější
>
> **Unai Zorrilla**, architekty a vývojáře realizace na prostý koncepty
>
> **Eduard Tomáši**, Dev realizace na prostý koncepty
>
> **Tomáši Ramon**, Developer na prostý koncepty
>
> **David Sanz**, Developer na prostý koncepty
>
> **Javier Valero**, ředitel operační vedoucím v Grupo řešení
>
> **Proso Pierre**, Sr. Poradce, Microsoft
>
> **Michael Friis**, správce produktu, Inc Docker
>
> **Charlese Lowell**, softwaru pracovníka, týmu VS CAT, Microsoft

## <a name="introduction"></a>Úvod

Podniky jsou stále porozumění úsporu nákladů, řešení problémů s nasazením a zvýšení operace DevOps a produkční pomocí kontejnerů. Microsoft má byla vydává inovace kontejner pro systém Windows a Linux tak, že vytvoříte produkty, jako je Azure Container Service a Azure Service Fabric a prostřednictvím partnerských vedoucími jako Docker, Mesosphere a Kubernetes. Tyto produkty dodat kontejneru řešení, které pomáhají společnosti sestavení a nasazení aplikací v cloudu rychlost a škálování, ať si sami vyberou platformy nebo nástrojů.

Docker se stává stále de facto standardem v kontejneru odvětví, jsou nejdůležitější dodavatelé v systému Windows a Linux ekosystémů nepodporuje. (Microsoft je jeden z dodavatelů hlavní cloudu podpora Docker.) V budoucnu Docker bude pravděpodobně všudypřítomný do všech datových center v cloudu nebo místně.

Kromě toho [mikroslužeb](https://martinfowler.com/articles/microservices.html) architektura je rozvíjející jako důležité přístup pro distribuované kritických aplikací. V architektuře na základě mikroslužbu aplikace je založený na kolekce služeb, které mohou být vytvořeny, otestovat, nasazené a verzí nezávisle.

## <a name="about-this-guide"></a>Informace o této příručce

Tato příručka je Úvod k vývoji aplikace založené na mikroslužeb a jejich správě použití kontejnerů. Popisuje architektury návrhu a implementace blíží použití .NET Core a Docker kontejnerů. Aby bylo snazší začít pracovat s kontejnery a mikroslužeb, se v Průvodci zaměřuje na odkaz kontejnerizované a na základě mikroslužbu aplikace, kterou můžete prozkoumat. Ukázkové aplikace je k dispozici na [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) úložiště GitHub.

Tato příručka poskytuje základní vývoj a architektury pokyny především na úrovni vývoj prostředí se zaměřením na dvě technologie: Docker a .NET Core. Naším úmyslem je čtení této příručky, pokud přemýšlíte o návrhu aplikace bez zaměřené na infrastrukturu (cloudové nebo místní) vašeho produkčního prostředí. Bude rozhodnutí o infrastruktuře později, při vytváření aplikace produkční prostředí. Proto tato příručka je určená jako infrastruktury lhostejné a více vývoj prostředí-na střed.

Po zkoumali této příručce, dalším krokem bude další informace o mikroslužeb produkční prostředí v Microsoft Azure.

## <a name="what-this-guide-does-not-cover"></a>Co tato příručka nepopisuje

Tato příručka není soustředit na životním cyklu aplikací DevOps, CI/CD kanály, nebo tým spolupracovat. Průvodci doplňkové [Kontejnerizované Docker cyklu aplikací s Microsoft platforma a nástroje](https://aka.ms/dockerlifecycleebook) se zaměřuje na tomto subjektu. Aktuální Průvodce také neposkytuje informace o implementaci na infrastrukturu Azure, jako je například informace o konkrétní orchestrators.

### <a name="additional-resources"></a>Další zdroje

-   **Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje** (ke stažení elektronická kniha) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)

## <a name="who-should-use-this-guide"></a>Tato příručka, kdo by měl používat

Napsali jsme Tato příručka pro vývojáře a řešení architektům, kteří jsou nové pro vývoj aplikací na základě Docker a architektura založená na mikroslužeb. Tato příručka je pro další informace o architektury, chcete-li navrhování a implementaci testování konceptu aplikací pomocí technologie Microsoft vývoje (s speciální aktivní .NET Core) a s Docker kontejnery.

Je také k dispozici tato příručka užitečné, pokud jsou technické rozhodovací pravomocí, jako je například architekti enterprise, kdo chce architekturu a Přehled technologie předtím, než se rozhodnete, na jaký způsob vyberte pro nový a moderní distribuované aplikace.

### <a name="how-to-use-this-guide"></a>Jak používat tato příručka

První část tohoto průvodce uvádí Docker kontejnery, popisuje, jak si vybrat mezi .NET Core a rozhraní .NET Framework jako rozhraní pro vývoj a poskytuje přehled mikroslužeb. Tento obsah je pro architekty a technické vedoucím pracovníkům, kteří chtějí přehled ale nemusíte zaměřit se na podrobnosti implementace kódu.

Druhá část průvodce začíná [procesu vývoje pro Docker aplikace založené na](#ch_dev_process_for_docker_based_apps) oddílu. Zaměřuje se na vývoj a mikroslužbu vzory pro implementaci aplikace s použitím .NET Core a Docker. Tato část bude většina zajímavé pro vývojáře a architektům, kteří chtějí zaměřit se na kód a na vzory a podrobnosti implementace.

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a>Související s mikroslužbu a aplikace na základě kontejneru odkaz: eShopOnContainers

Aplikace eShopOnContainers je odkaz na aplikaci pro .NET Core a mikroslužeb, který slouží k nasazení pomocí Docker kontejnery. Aplikace se skládá z několika subsystémy, včetně několik e úložiště uživatelského rozhraní front-end (webové aplikace a nativní mobilní aplikace). Zahrnuje taky mikroslužeb back-end a kontejnery pro všechny požadované operace na straně serveru.

Tento mikroslužbu a aplikace založené na kontejneru zdrojový kód je open source a je k dispozici [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) úložiště GitHub.

## <a name="send-us-your-feedback"></a>Pošlete nám svůj názor!

Napsali jsme tento průvodce vám pomůže pochopit architektura kontejnerizované aplikací a mikroslužeb v rozhraní .NET. Průvodce a související referenční aplikace bude mít vyvíjejí, tak Uvítáme vaše názory! Pokud máte komentáře o tom, jak je možné zlepšit této příručce, pošlete prosím, aby:

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

>[!div class="step-by-step"]
[Další] (container-docker-introduction/index.md)
