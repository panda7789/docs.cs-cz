---
title: Revize lokalizovatelnosti
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- world-ready applications, localizability
- application development [.NET Framework], localization
- localizability [.NET Framework]
- international applications [.NET Framework], localizability
- globalization [.NET Framework], localizability
- culture, localizability
- localization [.NET Framework], localizability
- global applications, localizability
- localizing resources
ms.assetid: 3aee2fbb-de47-4e37-8fe4-ddebb9719247
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8645f77c8d03a475fe0fcc49f3e6d5e28829f9e9
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442955"
---
# <a name="localizability-review"></a>Přezkoumání lokalizovatelnosti

Přezkoumání lokalizovatelnosti je mezikroku vývoj světově připravených aplikací. Ověřuje, že globalizovaná aplikace je připravena k lokalizaci a identifikuje jakýkoli kód, nebo všechny aspekty uživatelského rozhraní, které vyžadují speciální zacházení. Tento krok také pomáhá zajistit, že proces lokalizace nezpůsobí žádné funkčních chyb do vaší aplikace. Při všech problémech, přezkoumání lokalizovatelnosti vyvolané vyřeší, vaše aplikace je připravena k lokalizaci. Pokud je důkladné přezkoumání lokalizovatelnosti, by nemělo být upravit veškerý kód zdroje během proces lokalizace.

Přezkoumání lokalizovatelnosti se skládá z následujících tří kontroly:

- [Implementace doporučení pro globalizaci?](#global)

- [Jazykové funkce správného zpracování?](#culture)

- [Otestovali jste aplikaci s mezinárodními daty?](#test)

<a name="global"></a>
## <a name="implement-globalization-recommendations"></a>Implementace doporučení pro globalizaci

Pokud máte navržená a vyvinutá vaší aplikace pomocí na lokalizaci a pokud jste postupovali podle doporučení popsaných v [globalizace](../../../docs/standard/globalization-localization/globalization.md) článku, přezkoumání lokalizovatelnosti do značné míry budou pouze kontrolou kvality . V opačném případě během této fáze je vhodné zkontrolovat a implementaci doporučení pro [globalizace](../../../docs/standard/globalization-localization/globalization.md) a opravte chyby ve zdrojovém kódu, které brání lokalizaci.

<a name="culture"></a>
## <a name="handle-culture-sensitive-features"></a>Jazykové funkce

.NET neposkytuje programové podpory v různých oblastech, které výrazně lišit podle jazykové verze. Ve většině případů musíte napsat vlastní kód pro zpracování oblasti funkcí, jako je následující:

- Adresy

- Telefonní čísla

- Formáty papíru

- Jednotky délky, váhy, oblasti, svazek a teploty

   Přestože .NET nenabízí integrovanou podporu pro převod mezi měrné jednotky, můžete použít <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> a určí, zda konkrétní zemi nebo oblast používá metrika systému, jak ukazuje následující příklad.

   [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
   [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]

<a name="test"></a>
## <a name="test-your-application"></a>Testování aplikace

Předtím, než je lokalizovat aplikaci, měli byste otestovat pomocí mezinárodní data na mezinárodních verzích operačního systému. I když většina uživatelského rozhraní nebude v tomto okamžiku lokalizována, bude možné zjišťovat problémy, jako je následující:

- Serializovaná data, která není správně deserializovat mezi verzemi operačního systému.

- Číselná data, která nebere v úvahu konvence aktuální jazykové verze. Například může být zobrazena čísla s nepřesné skupiny oddělovače, oddělovače desetinných míst nebo symboly měny.

- Datum a čas dat, který nepředstavuje konvence aktuální jazykové verze. Například číslo představující měsíc a den mohou objevit v nesprávném pořadí, oddělovače data může být nesprávný nebo může být nesprávné informace o časovém pásmu.

- Prostředky, které nelze nalézt, protože nebylo nalezeno výchozí jazykovou verzi pro vaši aplikaci.

- Řetězce, které jsou zobrazeny v neobvyklé objednávky pro konkrétní jazykovou verzi.

- Řetězec porovnání nebo porovnání rovnosti, které vrací neočekávané výsledky.

Pokud jste postupovali podle doporučení pro globalizaci při vývoji vaší aplikace, zpracovává zohledňující jazykovou verzi funkce správně a identifikovat a řešit problémy lokalizace, které vznikly během testování, můžete přejít k dalšímu kroku, [Lokalizace](../../../docs/standard/globalization-localization/localization.md).

## <a name="see-also"></a>Viz také:

- [Globalizace a lokalizace](../../../docs/standard/globalization-localization/index.md)
- [Lokalizace](../../../docs/standard/globalization-localization/localization.md)
- [Globalizace](../../../docs/standard/globalization-localization/globalization.md)
- [Prostředky v desktopových aplikacích](../../../docs/framework/resources/index.md)
