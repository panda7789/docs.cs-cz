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
ms.openlocfilehash: 2166412269a84329d42f58c7e3423229be4327b8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877741"
---
# <a name="compilation-and-reuse-in-regular-expressions"></a>Kompilace a opětovné používání v regulárních výrazech
Můžete optimalizovat výkon aplikací, které usnadňují rozsáhlé používání regulárních výrazů, pochopení, jak modul regulárních výrazů zkompiluje výrazy a principy regulárních výrazů v mezipaměti. Toto téma popisuje kompilace a ukládání do mezipaměti.  
  
## <a name="compiled-regular-expressions"></a>Kompilované regulární výrazy  
 Ve výchozím nastavení zkompiluje modul regulárních výrazů regulární výraz k sekvenci interních instrukcí (jedná se vysoké úrovně kódy, které se liší od jazyk Microsoft intermediate language, nebo jazyk MSIL). Když se modul spouští regulárního výrazu, interpretuje interní kódy.  
  
 Pokud <xref:System.Text.RegularExpressions.Regex> objekt je vytvořen s <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> možnost kompiluje regulární výraz k explicitní kód jazyka MSIL místo interní pokyny vysoké úrovně regulární výraz. To umožňuje. NET pro kompilátor just-in-time (JIT) převede výraz do nativního strojového kódu pro vyšší výkon.  
  
Generovaný jazyk MSIL však nelze uvolnit. Jediný způsob, jak uvolnit kód je k uvolnění domény celé aplikace (to znamená, uvolnit všechny aplikace v kódu.). Efektivně Jakmile regulární výraz je zkompilován s <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> možnost, nikdy uvolní prostředky využívané třídou kompilované výrazu i v případě, že byl vytvořen regulárního výrazu <xref:System.Text.RegularExpressions.Regex> objekt, který je sám uvolněn uvolňování paměti.  
  
 Musíte být opatrní a omezit počet různých regulárních výrazů při kompilaci s <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> možnost vyhnout se spotřebovávají příliš mnoho zdrojů. Pokud aplikace musí používat velká, nebo bez vazby počet regulárních výrazů, každý výraz by měl být interpretován, není zkompilován. Ale pokud malý počet regulárních výrazů jsou opakovaně používá, že by měl být zkompilován s <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> pro zajištění lepšího výkonu. Alternativou je použití předkompilované regulárních výrazů. Všechny vaše výrazy do opakovaně použitelné knihovny DLL můžete zkompilovat pomocí <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> metody. Tím se vyhnete nutnosti kompilace za běhu přitom výhod rychlost kompilované regulární výrazy.  
  
## <a name="the-regular-expressions-cache"></a>Mezipaměť regulárních výrazů  
 Kvůli zvýšení výkonu se modul regulárních výrazů udržuje mezipaměť celou aplikaci zkompilovaných regulárních výrazů. Mezipaměti ukládá vzory regulárních výrazů, které se používají pouze ve volání statické metody. (Vzory regulárních výrazů zadané metod, které nejsou uložené v mezipaměti.) Tím se vyhnete nutnosti rozboru výraz do vysoké úrovně bajtový kód pokaždé, když se používá.  
  
 Maximální počet v mezipaměti regulárních výrazů je určen hodnotou `static` (`Shared` v jazyce Visual Basic) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> vlastnost. Ve výchozím nastavení modul regulárních výrazů ukládá do mezipaměti až 15 kompilované regulární výrazy. Pokud počet zkompilovaných regulárních výrazů překračuje velikost mezipaměti, nejdéle regulárního výrazu zahozena a nové regulárního výrazu se uloží do mezipaměti.  
  
 Aplikace můžete využít předkompilované regulárních výrazů v jednom z následujících dvou způsobů:  
  
-   Pomocí statické metody <xref:System.Text.RegularExpressions.Regex> objektu k definování regulárního výrazu. Pokud používáte vzor regulárního výrazu, který již byl definován v jiné volání statické metody, modul regulárních výrazů budou načítat z mezipaměti. Pokud ne, modul se kompiluje regulární výraz a přidejte ji do mezipaměti.  
  
-   Opětovným použitím existující <xref:System.Text.RegularExpressions.Regex> objekt tak dlouho, dokud jeho vzor regulárního výrazu je potřeba.  
  
 Z důvodu režie vytváření instancí objektu a kompilace regulárních výrazů, vytváření a ničení rychle mnoho <xref:System.Text.RegularExpressions.Regex> objekty je velmi nákladný proces. Pro aplikace, které používají velký počet různých regulárních výrazů, můžete optimalizovat výkon pomocí volání statických `Regex` metody a případně zvětšením velikosti mezipaměti regulárních výrazů.  
  
## <a name="see-also"></a>Viz také:

- [Regulárních výrazů .NET](../../../docs/standard/base-types/regular-expressions.md)
