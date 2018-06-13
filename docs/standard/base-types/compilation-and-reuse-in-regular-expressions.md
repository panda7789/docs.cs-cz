---
title: Kompilace a opětovné používání v regulárních výrazech
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing text with regular expressions, compilation
- searching with regular expressions, compilation
- .NET Framework regular expressions, engines
- .NET Framework regular expressions, compilation
- regular expressions, compilation
- compilation, regular expressions
- pattern-matching with regular expressions, compilation
- regular expressions, engines
ms.assetid: 182ec76d-5a01-4d73-996c-0b0d14fcea18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a9adb5d39eb420496030d85dacd95a1cccd6fd2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568755"
---
# <a name="compilation-and-reuse-in-regular-expressions"></a>Kompilace a opětovné používání v regulárních výrazech
Můžete optimalizovat výkon aplikací, které rozsáhlé používání regulárních výrazů pochopení, jak modul regulárních výrazů zkompiluje výrazy a vysvětlení, jak běžných výrazů v mezipaměti. Toto téma popisuje kompilace a ukládání do mezipaměti.  
  
## <a name="compiled-regular-expressions"></a>Kompilované regulární výrazy  
 Ve výchozím nastavení modul regulárních výrazů zkompiluje regulární výraz k posloupnost vnitřních pokynů (jsou tyto kódy vysoké úrovně, které se liší od společnosti Microsoft převodní jazyk nebo MSIL). Když modul provede regulární výraz, interpretuje interní kódy.  
  
 Pokud <xref:System.Text.RegularExpressions.Regex> objektu je vytvořený pomocí <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> možnost, se zkompiluje regulární výraz explicitní MSIL kód místo interní pokynů vysoké úrovně regulárního výrazu. To umožňuje. Kompilátor v běhu (JIT) pro NET převést výraz do nativního kódu počítače pro vyšší výkon.  
  
Vygenerovaný MSIL však nemůže být odpojen. Jediným způsobem, jak uvolnit kód je k uvolnění domény aplikace celý (to znamená, uvolnit všechny vaše aplikace je kód.). Efektivní Jakmile regulární výraz zkompilován s <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> možnost, nikdy uvolní prostředky využívané kompilované výrazem i v případě, že byl vytvořen s regulárním výrazem <xref:System.Text.RegularExpressions.Regex> objekt, který je sám uvolněn uvolňování paměti.  
  
 Je třeba dbát omezit počet různých regulárních výrazů, které zkompilujete pomocí <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> možnost, aby se zabránilo spotřebovávají příliš mnoho zdrojů. Pokud aplikace musí používat velká nebo neomezený počet regulární výrazy, každý výraz by měl interpretovány, není zkompilovat. Ale pokud malý počet regulární výrazy se používají opakovaně, že má kompilovat s <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> pro dosažení vyššího výkonu. Další možností je použití předkompilovaných regulárních výrazů. Všechny vaše výrazy do opakovaně použitelné knihovny DLL můžete zkompilovat pomocí <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> metoda. Tím je zabráněno potřeba kompilace za běhu při stále využívání rychlosti zkompilovaných regulárních výrazů.  
  
## <a name="the-regular-expressions-cache"></a>Mezipaměť regulárních výrazů  
 Chcete-li zvýšit výkon, modul regulárních výrazů udržuje mezipaměť celou aplikaci kompilované regulární výrazy. Mezipaměti ukládá vzory regulárních výrazů, které se používají pouze ve voláních statickou metodu. (Regulární výraz vzory zadaný metod, které nejsou v mezipaměti.) Tím je zabráněno potřeba převedení výrazu do byte kódu vysoké úrovně pokaždé, když se používá.  
  
 Maximální počet regulárních výrazů v mezipaměti je dáno hodnotu `static` (`Shared` v jazyce Visual Basic) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> vlastnost. Ve výchozím nastavení modul regulárních výrazů ukládá do mezipaměti až 15 kompilované regulární výrazy. Pokud počet zkompilovaných regulárních výrazů překračuje velikost mezipaměti, budou zahozeny nejdéle nepoužitých regulárnímu výrazu a nové regulární výraz je uložený v mezipaměti.  
  
 Aplikace mohou využít výhod předkompilovaných regulárních výrazů v jednom z následujících dvou způsobů:  
  
-   Pomocí statické metody <xref:System.Text.RegularExpressions.Regex> objekt, který chcete definovat regulární výraz. Pokud používáte vzor regulárního výrazu, který již byl definován v jiném volání statickou metodu, modul regulárních výrazů budou načítat z mezipaměti. Pokud ne, modul bude zkompilovat regulárnímu výrazu a přidejte ji do mezipaměti.  
  
-   Opětovným použitím stávající <xref:System.Text.RegularExpressions.Regex> objektu, dokud je zapotřebí jeho vzor regulárního výrazu.  
  
 Z důvodu režijní náklady na vytvoření instance objektu a kompilace regulárních výrazů, vytváření a rychle rušení velkého množství <xref:System.Text.RegularExpressions.Regex> objektů je velmi nákladný proces. Pro aplikace, které používají velké množství různých regulárních výrazů, můžete optimalizovat výkon pomocí volání statických `Regex` metody a případně zvětšením velikosti mezipaměti regulárních výrazů.  
  
## <a name="see-also"></a>Viz také  
 [Regulární výrazy rozhraní .NET](../../../docs/standard/base-types/regular-expressions.md)
