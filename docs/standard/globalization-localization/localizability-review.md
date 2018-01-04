---
title: Revize lokalizovatelnosti
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2aaf7c466c6662611e2b37d5c967a99d050158df
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="localizability-review"></a>Revize lokalizovatelnosti
Revize lokalizovatelnosti je přechodný krok pro vývoj aplikací připravených. Ověří, že globalizovaná aplikace je připravena k lokalizaci a identifikuje kód, nebo všechny aspekty uživatelského rozhraní, které vyžadují zvláštní zpracování. Tento krok také pomáhá zajistit, že proces lokalizace nezavedou žádné funkční vady do vaší aplikace. Pokud byla vyřešili všechny problémy, které jsou vydané revize lokalizovatelnosti, je aplikace připravená pro lokalizaci. Pokud revize lokalizovatelnosti důkladné, by neměl mít k úpravě jakékoli zdrojového kódu během procesu lokalizace.  
  
 Revize lokalizovatelnosti se skládá z následujících tří kontroly:  
  
-   [Jsou implementované doporučení globalizace?](#global)  
  
-   [Jazykové funkce zpracovává správně?](#culture)  
  
-   [Jste otestovali vaší aplikace pomocí mezinárodní dat?](#test)  
  
<a name="global"></a>   
## <a name="implementing-globalization-recommendations"></a>Implementace doporučení pro globalizaci  
 Pokud jste vytvořili a vyvinutá vaší aplikace pomocí na lokalizaci, a pokud jste postupovali podle doporučení popsaných v [globalizace](../../../docs/standard/globalization-localization/globalization.md) článku revize lokalizovatelnosti do značné míry budou kontrolou kvality . V opačném během této fáze je vhodné zkontrolovat a doporučení pro implementaci [globalizace](../../../docs/standard/globalization-localization/globalization.md)a opravte chyby ve zdrojovém kódu, které zabraňují lokalizace.  
  
<a name="culture"></a>   
## <a name="handling-culture-sensitive-features"></a>Zpracování funkcí závislých na jazykové verzi  
 Rozhraní .NET Framework neposkytuje programové podpory v různých oblastech, které jsou závislé na jazykové verzi. Ve většině případů budete muset psát vlastní kód pro zpracování oblastech funkce takto:  
  
-   Adresy.  
  
-   Telefonních čísel.  
  
-   Formáty papíru.  
  
-   Jednotky měření, délky, váhu, oblasti, svazku a teploty. Přestože rozhraní .NET Framework nenabízí integrovanou podporu pro převod mezi měrné jednotky, můžete použít <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> vlastnosti k určení, jestli konkrétní zemi či oblasti, používá metrika systému, jak ukazuje následující příklad.  
  
     [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
     [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]  
  
<a name="test"></a>   
## <a name="testing-your-application"></a>Testování aplikace  
 Předtím, než je lokalizovat aplikaci, byste měli otestovat pomocí mezinárodní data na mezinárodní verze operačního systému. I když většina uživatelského rozhraní pro nebude v tomto okamžiku lokalizované, bude možné ke zjišťování problémů například následující:  
  
-   Serializovaná data, která není správně deserializovat mezi verzemi operačního systému.  
  
-   Číselná data, která nemusí odpovídat konvence aktuální jazykové verze. Například může zobrazit čísla s oddělovače nesprávné skupin, oddělovače desetinných míst nebo symboly měny.  
  
-   Datum a čas data, která nemusí odpovídat konvence aktuální jazykové verze. Například čísla, která představují měsíce a dne se mohou objevit v nesprávném pořadí, oddělovače dat může být nesprávný nebo může být nesprávné informace o časovém pásmu.  
  
-   Prostředky, které nelze nalézt, protože nebyly identifikovány výchozí jazykovou verzi pro vaši aplikaci.  
  
-   Řetězce, které se zobrazují v neobvyklou pořadí pro konkrétní jazykové verze.  
  
-   Řetězec porovnání nebo porovnání rovnosti, které vracejí neočekávané výsledky.  
  
 Pokud jste postupovali podle doporučení globalizace při vývoji aplikace, zpracovává jazykové funkce správně a identifikovat a řešit problémy lokalizace, které vznikly během testování, můžete přejít k dalšímu kroku, [Lokalizace](../../../docs/standard/globalization-localization/localization.md).  
  
## <a name="see-also"></a>Viz také  
 [Globalizace a lokalizace](../../../docs/standard/globalization-localization/index.md)  
 [Lokalizace](../../../docs/standard/globalization-localization/localization.md)  
 [Globalizace](../../../docs/standard/globalization-localization/globalization.md)  
 [Prostředky v desktopových aplikacích](../../../docs/framework/resources/index.md)
