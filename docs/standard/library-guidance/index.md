---
title: Pokyny k open source knihovně .NET
description: Doporučení pro osvědčené postupy pro vývojáře k vytváření vysoce kvalitních knihoven .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/17/2018
ms.openlocfilehash: eff6c822757af6fb85622e88714accd40c32bcf5
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928962"
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

Každý článek nabízí čtyři typy doporučení: **Udělejte**, **zvažte**, **Vyhněte**sea nepoužívejte. Typ doporučení indikuje, jak by měl následovat.

Měli byste téměř **vždy postupovat podle doporučení do** . Příklad:

**✔️** k distribuci knihovny pomocí balíčku NuGet.

Na druhé **straně doporučujeme,** aby se obecně následovala doporučení, ale v tomto pravidle existují legitimní výjimky a neměli byste mít na starosti žádné informace o tom, co se s těmito pokyny nedaří:

**✔️ zvažte** použití [2.0.0 SemVer](https://semver.org/) k verzi balíčku NuGet.

**Vyhněte** se doporučením označení věcí, které obecně nejsou dobrý nápad, ale porušení pravidla je někdy vhodné:

**❌ Se vyhnout** Balíček NuGet odkazuje na přesnou verzi.

A nakonec nenaznačují doporučení, co byste měli skoro **nikdy dělat:**

**❌** Nepublikujte v knihovně silně pojmenované a nedostatečně pojmenované verze vaší knihovny. Například `Contoso.Api` a `Contoso.Api.StrongNamed`.

>[!div class="step-by-step"]
>[Next](get-started.md)
