---
title: Mikroslužby .NET. Architektura pro kontejnerizované aplikace .NET
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Mikroslužeb jsou modulární a nezávisle nasaditelné služby. Kontejnery Dockeru (pro Linux a Windows) zjednodušují nasazení a testování sdružováním služby a jejích závislostí do jedné jednotky, která se pak spouštějí v izolovaném prostředí.
ms.date: 01/30/2020
ms.openlocfilehash: 1337fe56e78e03a85627737bd52a089fd946b842
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77543531"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a>.NET Microservices: Architektura pro kontejnerizované aplikace .NET

![Obálka knihy](./media/cover-small.png)

**EDITION v3.1** - Aktualizováno na ASP.NET Jádro 3.1

Tato příručka je úvodem do vývoje aplikací založených na mikroslužbách a jejich správě pomocí kontejnerů. Popisuje architektury návrhu a implementace přístupy pomocí .NET Core a Docker kontejnery.

Chcete-li usnadnit začít, průvodce se zaměřuje na odkaz kontejnerizované a mikroslužeb založené aplikace, které můžete prozkoumat. Referenční aplikace je k dispozici na [repo eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub.

## <a name="action-links"></a>Akční odkazy

- Tato e-kniha je také k dispozici ve formátu PDF (pouze anglická verze) [Ke stažení](https://aka.ms/microservicesebook)

- Klonovat/rozvintí referenční aplikace [eShopOnContainers na GitHubu](https://github.com/dotnet-architecture/eShopOnContainers)

- Podívejte se na [úvodní video na kanálu 9](https://aka.ms/microservices-video)

- Seznamte se s [architekturou mikroslužeb](https://aka.ms/MicroservicesArchitecture) ihned

## <a name="introduction"></a>Úvod

Podniky stále více realizuje úspory nákladů, řeší problémy s nasazením a vylepšují devops a výrobní operace pomocí kontejnerů. Microsoft vydává inovace kontejnerů pro Windows a Linux tím, že vytváří produkty, jako je Azure Kubernetes Service a Azure Service Fabric, a spolupracuje s vedoucími pracovníky v oboru, jako jsou Docker, Mesosphere a Kubernetes. Tyto produkty poskytují kontejnerová řešení, která pomáhají společnostem vytvářet a nasazovat aplikace rychlostí a škálovatrychlostí cloudu, bez ohledu na jejich výběr platformy nebo nástrojů.

Docker se stává de facto standardem v kontejnerovém průmyslu, podporovaný nejvýznamnějšími dodavateli v ekosystémech Windows a Linux. (Microsoft je jedním z hlavních dodavatelů cloudu podporující docker.) V budoucnu bude Docker pravděpodobně všudypřítomný v libovolném datovém centru v cloudu nebo v místním prostředí.

Kromě toho architektura [mikroslužeb](https://martinfowler.com/articles/microservices.html) se objevuje jako důležitý přístup pro distribuované důležité aplikace. V architektuře založené na mikroslužbách je aplikace postavena na kolekci služeb, které lze vyvíjet, testovat, nasazovat a vyvíjet nezávisle.

## <a name="about-this-guide"></a>O této příručce

Tato příručka je úvodem do vývoje aplikací založených na mikroslužbách a jejich správě pomocí kontejnerů. Popisuje architektury návrhu a implementace přístupy pomocí .NET Core a Docker kontejnery. Chcete-li usnadnit začít s kontejnery a mikroslužeb, průvodce se zaměřuje na odkaz kontejnerizované a mikroslužeb založené aplikace, které můžete prozkoumat. Ukázková aplikace je k dispozici v úložišti [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub.

Tato příručka poskytuje základní vývoj a architektonické pokyny především na úrovni vývojového prostředí se zaměřením na dvě technologie: Docker a .NET Core. Naším záměrem je, abyste si přečetli tuto příručku při přemýšlení o návrhu aplikace, aniž byste se zaměřili na infrastrukturu (cloud nebo místní) vašeho produkčního prostředí. O vaší infrastruktuře se budete rozhodovat později, až vytvoříte aplikace připravené pro produkční prostředí. Proto tato příručka je určena k infrastruktury agnostik a více na vývoj prostředí.

Po prostudování této příručky by dalším krokem bylo získat informace o mikroslužbách připravených pro produkční prostředí v Microsoft Azure.

## <a name="version"></a>Version

Tato příručka byla revidována tak, aby pokrývala verzi **.NET Core 3.1** spolu s mnoha dalšími aktualizacemi souvisejícími se stejnou "vlnou" technologií (tj. Azure a dalšími technologiemi třetích stran), které se časově mění s verzí .NET Core 3.1. To je důvod, proč kniha verze byla také aktualizována na verzi **3.1**.

## <a name="what-this-guide-does-not-cover"></a>Co tato příručka nezahrnuje

Tato příručka se nezaměřuje na životní cyklus aplikace, devops, ci/cd kanály nebo týmovou práci. Na toto téma se zaměřuje doplňková příručka [Containerized Docker Application Lifecycle s platformou Microsoft Platform and Tools.](https://aka.ms/dockerlifecycleebook) Aktuální průvodce také neposkytuje podrobnosti implementace infrastruktury Azure, jako jsou informace o konkrétních orchestrátorech.

### <a name="additional-resources"></a>Další zdroje

- **Kontejnerizovaný životní cyklus aplikací Dockeru s platformou Microsoft Platform and Tools** (e-kniha ke stažení)  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a>Kdo by měl používat tuto příručku

Napsali jsme tuto příručku pro vývojáře a architekty řešení, kteří jsou noví ve vývoji aplikací založených na Dockeru a na architektuře založené na mikroslužbách. Tato příručka je pro vás, pokud se chcete dozvědět, jak architekt, návrh a implementaci proof-of-concept aplikací s vývojovými technologiemi Microsoftu (se zvláštním zaměřením na .NET Core) a s kontejnery Dockeru.

Tuto příručku také považujete za užitečnou, pokud jste technický rozhodovací orgán, například podnikový architekt, který chce přehled architektury a technologie, než se rozhodnete, jaký přístup vybrat pro nové a moderní distribuované aplikace.

### <a name="how-to-use-this-guide"></a>Jak používat tohoto průvodce

První část této příručky zavádí kontejnery Dockeru, popisuje, jak si vybrat mezi .NET Core a rozhraní .NET Framework jako vývojové rozhraní a poskytuje přehled mikroslužeb. Tento obsah je určen architektům a technickým rozhodovacím orgánům, kteří chtějí přehled, ale nemusí se zaměřovat na podrobnosti implementace kódu.

Druhá část průvodce začíná [procesem vývoje pro aplikace založené na Dockeru.](./docker-application-development-process/index.md) Zaměřuje se na vývoj a mikroslužby vzory pro implementaci aplikací pomocí .NET Core a Docker. Tato část bude nejvíce zajímat vývojáře a architekty, kteří se chtějí zaměřit na kód a na vzory a podrobnosti implementace.

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a>Související referenční aplikace mikroslužeb a kontejnerů: eShopOnContainers

Aplikace eShopOnContainers je referenční aplikace s otevřeným zdrojovým kódem pro .NET Core a mikroslužby, která je určena k nasazení pomocí kontejnerů Dockeru. Aplikace se skládá z více subsystémů, včetně několika front-endů uživatelského nastavení e-store (webová aplikace MVC, Web SPA a nativní mobilní aplikace). Obsahuje také back-endové mikroslužby a kontejnery pro všechny požadované operace na straně serveru.

Účelem aplikace je předvést architektonické vzory. **Není to šablona připravená na výrobu** pro spuštění reálných aplikací. Ve skutečnosti je aplikace v trvalém stavu beta, protože se také používá k testování nových potenciálně zajímavých technologií, jak se objevují.

## <a name="send-us-your-feedback"></a>Pošlete nám svůj názor!

Napsali jsme tuto příručku, která vám pomůže pochopit architekturu kontejnerizovaných aplikací a mikroslužeb v rozhraní .NET. Průvodce a související referenční aplikace se bude vyvíjet, takže uvítáme vaši zpětnou vazbu! Pokud máte připomínky k tomu, jak lze <https://aka.ms/ebookfeedback>tuto příručku zlepšit, odešlete zpětnou vazbu na adrese .

## <a name="credits"></a>Kredity

Spoluautoři:

> **Cesar de la Torre**, Sr. PM, produktový tým .NET, Microsoft Corp.
>
> **Bill Wagner**, sr. Content Developer, C + E, Microsoft Corp.
>
> **Mike Rousos**, hlavní softwarový inženýr, DevDiv CAT tým, Microsoft

Editory:

> **Mike Papež**
>
> **Steva Hoaga**

Účastníci a recenzenti:

> **Jeffrey Richter**, Partner Software Eng, Tým Azure, Microsoft
>
> **Jimmy Bogard**, hlavní architekt ve společnosti Headspring
>
> **Udi Dahan**, zakladatel & generální ředitel, Konkrétní software
>
> **Jimmy Nilsson**, spoluzakladatel a generální ředitel společnosti Factor10
>
> **Glenn Condron**, sr. programový manažer, ASP.NET tým
>
> **Mark Fussell**, hlavní vedoucí pm, tým Azure Service Fabric, Microsoft
>
> **Diego Vega**, PM Lead, Entity Framework tým, Microsoft
>
> **Barry Dorrans**, vedoucí bezpečnostního programu
>
> **Rowan Miller**, Sr. Program Manager, Microsoft
>
> **Ankit Asthana**, hlavní pm manažer, .NET tým, Microsoft
>
> **Scott Hunter**, partnerský ředitel PM, .NET tým, Microsoft
>
> **Nish Anil**, Sr. Program Manager, .NET tým, Microsoft
>
> **Dylan Reisenberger**, architekt a dev olovo v Polly
>
> **Steve "ardalis" Smith** - softwarový architekt a trenér - [Ardalis.com](https://ardalis.com)
>
> **Ian Cooper**, Coding Architect ve společnosti Brighter
>
> **Unai Zorrilla**, architekt a dev olovo ve společnosti Plain Concepts
>
> **Eduard Tomas**, Dev Lead ve společnosti Plain Concepts
>
> **Ramon Tomas**, Developer ve společnosti Plain Concepts
>
> **David Sanz**, Developer ve společnosti Plain Concepts
>
> **Javier Valero**, provozní ředitel společnosti Grupo Solutio
>
> **Pierre Millet**, senior konzultant, Microsoft
>
> **Michael Friis**, produktový manažer, Docker Inc
>
> **Charles Lowell**, softwarový inženýr, Tým VS CAT, Microsoft
>
> **Miguel Veloso**, software development engineer ve společnosti Plain Concepts

## <a name="copyright"></a>Copyright

PUBLIKOVAL(A)

Produktové týmy Microsoft Developer Division, .NET a Visual Studio

Divize společnosti Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Autorská práva © 2020 společností Microsoft Corporation

Všechna práva vyhrazena. Žádná část obsahu této knihy nesmí být reprodukována nebo přenášena v jakékoli formě nebo jakýmkoli způsobem bez písemného souhlasu vydavatele.

Tato kniha je poskytována "tak, jak je" a vyjadřuje názory a názory autora. Názory, názory a informace vyjádřené v této knize, včetně URL a dalších odkazů na internetové stránky, se mohou změnit bez předchozího upozornění.

Některé zde uvedené příklady slouží pouze k znázornění a jsou smyšlené. Neměli byste z nich vyvozovat žádné skutečné vztahy či spojení.

Společnost Microsoft a ochranné <https://www.microsoft.com> známky uvedené na webové stránce "Ochranné známky" jsou ochrannými známkami skupiny společností Microsoft.

Mac a macOS jsou ochranné známky společnosti Apple Inc.

Logo velryby Docker je registrovaná ochranná známka společnosti Docker, Inc. Používá se svolením.

Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.

>[!div class="step-by-step"]
>[Další](container-docker-introduction/index.md)
