---
title: Představení referenční aplikace eShopOnContainers
description: Představujeme referenční aplikaci eShopOnContainers Cloud Native mikroslužeb pro ASP.NET Core a Azure.
ms.date: 06/30/2019
ms.openlocfilehash: 20f9175ada2e5439be363781a2b187c10ba86d37
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182858"
---
# <a name="introducing-eshoponcontainers-reference-app"></a>Představení referenční aplikace eShopOnContainers

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Společnost Microsoft ve spolupráci s předními odborníky ze komunity vytvořila plnohodnotnou referenční aplikaci mikroslužeb pro cloudové služby, která je eShopOnContainers. Tato aplikace se sestavuje pomocí .NET Core a Docker a volitelně z Azure, Kubernetes a sady Visual Studio k vytvoření online prezentace.

![Snímek obrazovky ukázkové aplikace eShopOnContainers](./media/eshoponcontainers-sample-app-screenshot.png)

**Obrázek 2-1**. Snímek obrazovky ukázkové aplikace eShopOnContainers

Před zahájením této kapitoly doporučujeme stáhnout si [referenční aplikaci eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers). V takovém případě byste měli být jednodušší sledovat spolu se zobrazenými informacemi.

## <a name="features-and-requirements"></a>Funkce a požadavky

Pojďme začít s přezkoumáním funkcí a požadavků aplikace. Aplikace eShopOnContainers představuje online obchod, který prodává různé fyzické produkty, jako jsou trička a káva mugs. Pokud jste si koupili cokoli online, měli byste se seznámit s tím, jak by se úložiště mělo používat poměrně. Tady jsou některé základní funkce, které úložiště implementuje:

- Výpis položek katalogu
- Filtrovat položky podle typu
- Filtrovat položky podle značky
- Přidání položek do nákupního košíku
- Upravit nebo odebrat položky z koše
- Registr
- Registrace účtu
- Přihlášení
- Odhlásit se
- Revidovat objednávky

Aplikace má také tyto nefunkční požadavky:

- Je potřeba, aby byla vysoce dostupná a musí se automaticky škálovat, aby se dosáhlo zvýšeného objemu provozu (a mohlo by se škálovat zpátky po přenosu dat). 
- Měla by poskytovat snadno použitelné monitorování svých stavových protokolů a diagnostické protokoly, které vám pomůžou vyřešit případné problémy, se kterými se setká. 
- Měl by podporovat proces agilního vývoje, včetně podpory pro průběžnou integraci a nasazování (CI/CD). 
- Kromě dvou webových front-endy (tradiční a jednostránkové aplikace) musí aplikace podporovat také mobilní klientské aplikace s různými druhy operačních systémů. 
- Měla by podporovat hostování mezi platformami a vývoj pro různé platformy.

![Architektura vývoje referenčních aplikací eShopOnContainers.](./media/eshoponcontainers-development-architecture.png)

**Obrázek 2-2**. Architektura vývoje referenčních aplikací eShopOnContainers.

Aplikace eShopOnContainers je přístupná z webových nebo mobilních klientů, kteří přistupují k aplikaci přes HTTPS cílící na serverovou aplikaci ASP.NET Core MVC nebo příslušnou bránu API. Brány rozhraní API nabízejí několik výhod, jako je například oddálení back-endové služby od jednotlivých front-end klientů a zajištění vyššího zabezpečení. Aplikace také využívá související vzor známý jako back-endy (BFF), což doporučuje vytvořit samostatné brány rozhraní API pro každého front-end klienta. Referenční architektura ukazuje rozdělení bran rozhraní API na základě toho, zda požadavek pochází z webového nebo mobilního klienta.

Funkce aplikace je rozdělená na řadu různých mikroslužeb. Existují služby zodpovědné za ověřování a identitu, výpis položek z katalogu produktů, správu nákupních košíků uživatelů a zadávání objednávek. Každá z těchto samostatných služeb má své vlastní trvalé úložiště. Všimněte si, že neexistuje žádné jediné hlavní úložiště dat, se kterým pracují všechny služby. Místo toho je koordinace a komunikace mezi službami prováděna podle potřeby a pomocí sběrnice zpráv.

Každá z různých mikroslužeb je navržena odlišně na základě jejich individuálních požadavků. To znamená, že jejich technologický zásobník se může lišit, i když jsou všechny sestavené pomocí .NET Core a jsou navržené pro Cloud. Jednodušší služby poskytují základní přístup k vytvoření a čtení-aktualizaci-odstranění (CRUD) pro základní úložiště dat, zatímco pokročilejší služby využívají přístupy k návrhu založené na doméně a vzory pro správu složitosti firmy.

![Různé druhy mikroslužeb](./media/different-kinds-of-microservices.png)

**Obrázek 2-3**. Různé druhy mikroslužeb.

## <a name="overview-of-the-code"></a>Přehled kódu

Vzhledem k tomu, že využívá mikroslužby, zahrnuje aplikace eShopOnContainers ve svém úložišti GitHub poměrně několik samostatných projektů a řešení. Kromě samostatných řešení a spustitelných souborů jsou různé služby navržené tak, aby běžely v jejich vlastních kontejnerech, a to jak během místního vývoje, tak za běhu v produkčním prostředí. Obrázek 2-4 ukazuje úplné řešení sady Visual Studio, ve kterém jsou uspořádány různé různé projekty.

![Projekty v řešení Visual Studio.](./media/projects-in-visual-studio-solution.png)

**Obrázek 2-4**. Projekty v řešení Visual Studio.

Kód je uspořádán tak, aby podporoval různé mikroslužby, a v rámci každé mikroslužby je kód rozdělen do logiky domény, aspekty infrastruktury a uživatelského rozhraní nebo koncového bodu služby. V mnoha případech můžou být závislosti každé služby splněné v produkčním prostředí, stejně jako alternativní možnosti pro místní vývoj. Pojďme se podívat, jak jsou požadavky aplikace mapovány na služby Azure.

## <a name="understanding-microservices"></a>Porozumění mikroslužbám

Tato kniha se zaměřuje na nativní cloudové aplikace sestavené pomocí technologie Azure. Další informace o osvědčených postupech mikroslužeb a o tom, jak navrhovat aplikace založené na mikroslužbách, najdete v doprovodné příručce [pro .NET mikroslužby: Architektura pro kontejnerové aplikace](https://dotnet.microsoft.com/learn/aspnet/microservices-architecture).NET. Kniha je dostupná online, ve formátu PDF nebo ve formátech eReader.

>[!div class="step-by-step"]
>[Předchozí](candidate-apps.md)
>[Další](map-eshoponcontainers-azure-services.md)
