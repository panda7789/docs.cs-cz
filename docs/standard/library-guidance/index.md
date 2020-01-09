---
title: Pokyny k open source knihovně .NET
description: Doporučení pro osvědčené postupy pro vývojáře k vytváření vysoce kvalitních knihoven .NET.
ms.date: 10/17/2018
ms.openlocfilehash: c1e1c302eede86fd5555a8e84630e216e96f1ce7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706449"
---
# <a name="open-source-library-guidance"></a>Pokyny pro open-source knihovnu

Tento průvodce poskytuje doporučení pro vývojáře k vytváření vysoce kvalitních knihoven .NET. Tato dokumentace se zaměřuje na to, *co* a *Proč* při sestavování knihovny .NET, nikoli na *jak*.

Aspekty vysoce kvalitních Open Source knihoven .NET:

> [!div class="checklist"]
>
> * **Včetně** kvalitních knihoven .NET usiluje o podporu řady platforem, programovacích jazyků a aplikací.
> * **Stabilní** knihovny .NET v ekosystému .NET společně fungují v aplikacích, které jsou sestavené s mnoha knihovnami.
> * **Navrženo pro vývoj** – knihovny .NET by se měly zlepšovat a vyvíjet v průběhu času a podporovat stávající uživatele.
> * **Laditelné** – knihovny .NET by měly používat nejnovější nástroje k vytvoření skvělého prostředí ladění pro uživatele.
> * **Důvěryhodné** knihovny .NET mají důvěru vývojářů publikováním do NuGet pomocí osvědčených postupů zabezpečení.

> [!div class="nextstepaction"]
> [Začínáme](./get-started.md)

## <a name="types-of-recommendations"></a>Typy doporučení

Každý článek nabízí čtyři typy doporučení: **udělejte**, **zvažte**, **Vyhněte**se a **nepoužívejte.** Typ doporučení indikuje, jak by měl následovat.

Měli byste téměř **vždy postupovat podle doporučení do** . Příklad:

**✔️** k distribuci knihovny pomocí balíčku NuGet.

Na druhé **straně doporučujeme,** aby se obecně následovala doporučení, ale v tomto pravidle existují legitimní výjimky a neměli byste mít na starosti žádné informace o tom, co se s těmito pokyny nedaří:

**✔️ zvažte** použití [2.0.0 SemVer](https://semver.org/) k verzi balíčku NuGet.

**Vyhněte** se doporučením označení věcí, které obecně nejsou dobrý nápad, ale porušení pravidla je někdy vhodné:

**❌ se vyhnout** Balíček NuGet odkazuje na přesnou verzi.

A nakonec nenaznačují doporučení, co byste měli skoro **nikdy dělat:**

**❌** nepublikujte v knihovně silně pojmenované a nedostatečně pojmenované verze vaší knihovny. Například `Contoso.Api` a `Contoso.Api.StrongNamed`.

>[!div class="step-by-step"]
>[Next](get-started.md)
