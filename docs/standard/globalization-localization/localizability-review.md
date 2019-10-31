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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120852"
---
# <a name="localizability-review"></a>Revize lokalizovatelnosti

Kontrola lokalizovatelnosti je přechodný krok vývoje aplikace připravené pro použití ve světě. Ověřuje, zda je globální aplikace připravena k lokalizaci a identifikuje jakýkoli kód nebo jakékoli aspekty uživatelského rozhraní, které vyžadují zvláštní zpracování. Tento krok také pomáhá zajistit, že proces lokalizace nezavede do vaší aplikace žádné funkční nedostatky. Když byly vyřešeny všechny problémy vyvolané přezkoumáním lokalizovatelnosti, je vaše aplikace připravená na lokalizaci. Pokud je kontrola lokalizovatelnosti důkladná, neměli byste během procesu lokalizace upravovat žádný zdrojový kód.

Kontrola lokalizovatelnosti se skládá z následujících tří kontrol:

- [Jsou implementovaná doporučení globalizace?](#global)

- [Jsou funkce závislé na jazykové verzi zpracovávány správně?](#culture)

- [Otestovali jste aplikaci s mezinárodními daty?](#test)

<a name="global"></a>
## <a name="implement-globalization-recommendations"></a>Implementace doporučení globalizace

Pokud jste aplikaci navrhli a vyvinuli s lokalizací a pokud jste postupovali s doporučeními popsanými v článku [globalizace](../../../docs/standard/globalization-localization/globalization.md) , přezkoumání lokalizovatelnosti bude převážně složitosti. V opačném případě byste měli v průběhu této fáze zkontrolovat a implementovat doporučení pro [globalizaci](../../../docs/standard/globalization-localization/globalization.md) a opravit chyby ve zdrojovém kódu, které brání lokalizaci.

<a name="culture"></a>
## <a name="handle-culture-sensitive-features"></a>Zpracování funkcí závislých na jazykové verzi

Rozhraní .NET neposkytuje programovou podporu v řadě oblastí, které jsou široce závislé na jazykové verzi. Ve většině případů je třeba napsat vlastní kód, který bude zpracovávat oblasti funkcí jako následující:

- Adresy

- Telefonní čísla

- Velikosti papíru

- Měrné jednotky používané pro délky, váhy, oblast, hlasitost a teploty

   I když rozhraní .NET nenabízí integrovanou podporu pro převod mezi jednotkami měření, můžete použít vlastnost <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> k určení, zda konkrétní země nebo oblast používá systém metriky, jak ukazuje následující příklad.

   [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
   [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]

<a name="test"></a>
## <a name="test-your-application"></a>Testování aplikace

Před lokalizací aplikace byste ji měli otestovat pomocí mezinárodních dat v mezinárodní verzi operačního systému. I když většina uživatelského rozhraní nebude v tomto okamžiku lokalizována, budete moci detekovat následující problémy:

- Serializovaná data, která nejsou v rámci verzí operačního systému správně reserializována.

- Číselná data, která nereflektují konvence aktuální jazykové verze. Čísla lze například zobrazit s nepřesnými oddělovači skupin, oddělovači desetinných míst nebo symboly měny.

- Data a času, která nereflektují konvence aktuální jazykové verze. Například čísla představující měsíc a den se mohou zobrazit v nesprávném pořadí, oddělovače dat mohou být nesprávné nebo informace o časovém pásmu mohou být nesprávné.

- Prostředky, které se nenašly, protože jste pro svou aplikaci neoznačili výchozí jazykovou verzi.

- Řetězce, které jsou zobrazeny v neobvyklém pořadí pro konkrétní jazykovou verzi.

- Porovnávání řetězců nebo porovnání pro rovnost, které vracejí neočekávané výsledky.

Pokud jste postupovali s doporučeními globalizace při vývoji aplikace, zpracování funkcí závislých na jazykové verzi a identifikaci a řešení problémů lokalizace, které vznikly během testování, můžete přejít k dalšímu kroku [. Lokalizace](../../../docs/standard/globalization-localization/localization.md).

## <a name="see-also"></a>Viz také:

- [Globalizace a lokalizace](../../../docs/standard/globalization-localization/index.md)
- [Lokalizace](../../../docs/standard/globalization-localization/localization.md)
- [Globalizace](../../../docs/standard/globalization-localization/globalization.md)
- [Prostředky v desktopových aplikacích](../../../docs/framework/resources/index.md)
