---
title: Pokyny k knihovně .NET s otevřeným zdrojovým kódem
description: Doporučení osvědčených postupů pro vývojáře k vytvoření vysoce kvalitních knihoven .NET.
ms.date: 10/17/2018
ms.openlocfilehash: 4c76dfae6ffc39df7f15381be64e33657067d79d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "76731434"
---
# <a name="open-source-library-guidance"></a>Pokyny pro open-source knihovnu

Tento návod obsahuje doporučení pro vývojáře k vytvoření vysoce kvalitních knihoven .NET. Tato dokumentace se zaměřuje na *co* a *proč* při vytváření *knihovny*.NET, nikoli jak .

Aspekty vysoce kvalitních open-source knihoven .NET:

> [!div class="checklist"]
>
> * **Včetně** - Dobré knihovny .NET se snaží podporovat mnoho platforem, programovacích jazyků a aplikací.
> * **Stable** - Good .NET knihovny koexistovat v ekosystému .NET, spuštěné v aplikacích vytvořených s mnoha knihovnami.
> * **Navrženo tak, aby se vyvíjelo** – knihovny .NET by se měly v průběhu času zlepšovat a vyvíjet a zároveň podporovat stávající uživatele.
> * **Laditelné** - knihovny .NET by měly používat nejnovější nástroje k vytvoření skvělého prostředí pro ladění pro uživatele.
> * **Důvěryhodné** - knihovny .NET mají důvěryhodnost vývojářů publikováním na NuGet pomocí osvědčených postupů zabezpečení.

> [!div class="nextstepaction"]
> [Začínáme](./get-started.md)

## <a name="types-of-recommendations"></a>Typy doporučení

Každý článek obsahuje čtyři typy doporučení: **Do**, **Zvažte**, **Vyhnout**, a **Ne**. Typ doporučení označuje, jak silně by měl být dodržován.

Měli byste téměř vždy dodržovat doporučení **Do.** Například:

✔️ do distribuovat knihovnu pomocí balíčku NuGet.

Na druhou stranu, **Zvažte** doporučení by měla být obecně dodržována, ale existují legitimní výjimky z pravidla a neměli byste se cítit špatně, že nedodržujete pokyny:

✔️ zvažte použití [SemVer 2.0.0](https://semver.org/) k verzi balíčku NuGet.

**Vyhněte se** doporučení zmínit věci, které jsou obecně není dobrý nápad, ale porušení pravidla někdy dává smysl:

❌VYHNĚTE se NuGet odkazy na balíček, které vyžadují přesnou verzi.

A konečně, **Nepoužívejte** doporučení naznačují něco, co byste měli téměř nikdy dělat:

❌NEPublikujte verze knihovny se silným názvem a bez silného název. Například `Contoso.Api` a `Contoso.Api.StrongNamed`.

>[!div class="step-by-step"]
>[Další](get-started.md)
