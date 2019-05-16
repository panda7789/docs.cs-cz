---
title: Pokyny v knihovně .NET Open source
description: Doporučení osvědčených postupů pro vývojáře k vytvoření vysoce kvalitní knihovny .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/17/2018
ms.openlocfilehash: 85d76c8b2bd0f030e3fbc1987e6ff51d6da44e76
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644389"
---
# <a name="open-source-library-guidance"></a>Pokyny pro open-source knihovnu

Tento návod obsahuje doporučení pro vývojáře umožňující vytváření vysoce kvalitních knihovny .NET. Tato dokumentace se zaměřuje na *co* a *proč* při sestavování knihovny .NET, ne *jak*.

Vysoce kvalitní knihoven .NET open-source aspekty:

> [!div class="checklist"]
> * **Inkluzivní** – knihovny .NET vhodné snažit se podporují mnoho platforem, programovacích jazyků a aplikací.
> * **Stabilní** – knihovny .NET dobré existovat vedle sebe v ekosystému .NET, používané aplikace sestavené s mnoha knihoven.
> * **Navržené tak, aby vyvíjí** – knihovny pro .NET by měl vylepšit a postupně při současné podpoře stávající uživatele.
> * **Laditelný** – knihovny pro .NET používali nejnovější nástroje potřebné k vytváření skvělé možnosti ladění pro uživatele.
> * **Důvěryhodné** – knihovny pro .NET mají vztah důvěryhodnosti vývojářů verzi publikováním NuGet pomocí osvědčené postupy zabezpečení.

> [!div class="nextstepaction"]
> [Začínáme](./get-started.md)

## <a name="types-of-recommendations"></a>Typů doporučení

Každý článek představuje čtyři typy doporučení: **Proveďte**, **vezměte v úvahu**, **vyhnout**, a **nepodporují**. Typ doporučení se jedná Určuje, jak důrazně má následovat.

Téměř vždy měli byste postupovat podle **proveďte** doporučení. Příklad:

**PROVEĎTE ✔️** distribuovat knihovny pomocí balíčku NuGet.

Na druhé straně **zvažte** byste obecně měli dodržet, doporučení, ale existují legitimní výjimky z pravidla a by neměl mít pocit chybný o není následující pokyny:

**✔️ ZVAŽTE** pomocí [SemVer 2.0.0](https://semver.org/) verzi balíčku NuGet.

**Vyhněte se** doporučení zmiňovat věcí, které nejsou obecně vhodné, ale někdy zásadní pravidlo smysl:

**❌ Nepoužívejte** odkazy na balíčky NuGet, které vyžadují přesnou verzi.

A nakonec **nejsou** doporučení znamenat něco téměř nikdy byste měli dělat:

**❌ NEPODPORUJÍ** publikování silným názvem a jiných silným názvem verzí knihovny. Například `Contoso.Api` a `Contoso.Api.StrongNamed`.

>[!div class="step-by-step"]
>[Next](get-started.md)
