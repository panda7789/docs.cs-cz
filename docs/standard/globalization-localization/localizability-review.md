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
ms.openlocfilehash: b286bdd2c5d7b03a0a2b5f94478e252da6cd0ae2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120852"
---
# <a name="localizability-review"></a>Revize lokalizovatelnosti

Kontrola lokalizovatelnosti je mezikrokem ve vývoji aplikace připravené pro svět. Ověří, že globalizovaná aplikace je připravena k lokalizaci a identifikuje jakýkoli kód nebo jakékoli aspekty uživatelského rozhraní, které vyžadují zvláštní zpracování. Tento krok také pomáhá zajistit, že proces lokalizace nezavede do aplikace žádné funkční vady. Pokud byly vyřešeny všechny problémy vyvolané kontrolou lokalizovatelnosti, aplikace je připravena k lokalizaci. Pokud je kontrola lokalizovatelnosti důkladná, neměli byste během procesu lokalizace upravovat žádný zdrojový kód.

Přezkum lokalizovatelnosti se skládá z těchto tří kontrol:

- [Jsou doporučení globalizace implementována?](#global)

- [Jsou funkce citlivé na jazykovou verzi správně zpracovány?](#culture)

- [Testovali jste svou aplikaci s mezinárodními daty?](#test)

<a name="global"></a>
## <a name="implement-globalization-recommendations"></a>Implementace doporučení globalizace

Pokud jste navrhli a vyvinuli aplikaci s ohledem na lokalizaci a pokud jste postupovali podle doporučení popsaných v článku [globalizace,](../../../docs/standard/globalization-localization/globalization.md) bude kontrola lokalizovatelnosti do značné míry průchodem zajištění kvality. V opačném případě byste v této fázi měli zkontrolovat a implementovat doporučení pro [globalizaci](../../../docs/standard/globalization-localization/globalization.md) a opravit chyby ve zdrojovém kódu, které brání lokalizaci.

<a name="culture"></a>
## <a name="handle-culture-sensitive-features"></a>Zpracování funkcí citlivých na jazykovou verzi

Rozhraní .NET neposkytuje programovou podporu v řadě oblastí, které se značně liší podle jazykové verze. Ve většině případů je třeba napsat vlastní kód pro zpracování oblastí funkcí, jako je následující:

- Adresy

- Telefonní čísla

- Formáty papíru

- Měrné jednotky používané pro délky, závaží, plochu, objem a teploty

   Přestože rozhraní .NET nenabízí integrovanou podporu pro převod mezi <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> měrnými jednotkami, můžete pomocí této vlastnosti určit, zda určitá země nebo oblast používá systém metrik, jak ukazuje následující příklad.

   [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
   [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]

<a name="test"></a>
## <a name="test-your-application"></a>Testování aplikace

Před lokalizací aplikace byste ji měli otestovat pomocí mezinárodních dat v mezinárodních verzích operačního systému. Přestože většina uživatelského rozhraní nebude v tomto okamžiku lokalizována, budete moci zjistit problémy, jako jsou následující:

- Serializovaná data, která nejsou správně rekonstruována ve verzích operačního systému.

- Číselná data, která neodráží konvence aktuální jazykové verze. Čísla mohou být například zobrazena s nepřesnými oddělovači skupin, oddělovači desetinných míst nebo symboly měny.

- Data a čas dat, která neodráží konvence aktuální jazykové verze. Například čísla, která představují měsíc a den, se mohou zobrazit v nesprávném pořadí, oddělovače kalendářních dat mohou být nesprávné nebo informace o časovém pásmu mohou být nesprávné.

- Prostředky, které nelze najít, protože jste neidentifikovali výchozí jazykovou verzi aplikace.

- Řetězce, které jsou zobrazeny v neobvyklém pořadí pro konkrétní jazykovou verzi.

- Porovnání řetězců nebo porovnání rovnosti, které vracejí neočekávané výsledky.

Pokud jste postupovali podle doporučení globalizace při vývoji aplikace, správně zpracovány funkce citlivé na jazykovou verzi a identifikovat a řešit problémy lokalizace, které vznikly během testování, můžete přistoupit k dalšímu kroku, [Lokalizace](../../../docs/standard/globalization-localization/localization.md).

## <a name="see-also"></a>Viz také

- [Globalizace a lokalizace](../../../docs/standard/globalization-localization/index.md)
- [Lokalizace](../../../docs/standard/globalization-localization/localization.md)
- [Globalizace](../../../docs/standard/globalization-localization/globalization.md)
- [Prostředky v aplikacích klasické pracovní plochy](../../../docs/framework/resources/index.md)
