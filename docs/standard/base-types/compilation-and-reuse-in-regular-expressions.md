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
ms.openlocfilehash: 3e1dfe8373145286b03e503f038e267ff0d4c4f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091734"
---
# <a name="compilation-and-reuse-in-regular-expressions"></a>Kompilace a opětovné používání v regulárních výrazech
Můžete optimalizovat výkon aplikací, které poskytují rozsáhlé využití regulárních výrazů pochopením toho, jak modul regulárních výrazů kompiluje výrazy, a pochopením způsobu ukládání regulárních výrazů do mezipaměti. Toto téma popisuje kompilaci i ukládání do mezipaměti.  
  
## <a name="compiled-regular-expressions"></a>Zkompilované regulární výrazy  
 Ve výchozím nastavení modul regulárních výrazů zkompiluje regulární výraz do posloupnosti interních instrukcí (jedná se o kódy vysoké úrovně, které se liší od zprostředkujícího jazyka společnosti Microsoft nebo MSIL). Když modul spustí regulární výraz, interpretuje vnitřní kódy.  
  
 Pokud <xref:System.Text.RegularExpressions.Regex> je objekt vytvořen <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> s možností, zkompiluje regulární výraz do explicitního kódu MSIL namísto interních pokynů regulárního výrazu vysoké úrovně. To umožňuje . NET je just-in-time (JIT) kompilátor převést výraz na nativní strojový kód pro vyšší výkon.  
  
Vygenerovaný manit však nelze uvolnit. Jediným způsobem, jak uvolnit kód, je uvolnit celou doménu aplikace (to znamená uvolnit veškerý kód aplikace.). Efektivně, jakmile regulární výraz je <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> zkompilován s možností, nikdy uvolní prostředky používané zkompilovaný <xref:System.Text.RegularExpressions.Regex> výraz, i v případě, že regulární výraz byl vytvořen objektem, který je sám propuštěn do uvolňování paměti.  
  
 Musíte být opatrní omezit počet různých regulárních <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> výrazů, které kompilujete s možností, aby se zabránilo spotřebování příliš mnoho zdrojů. Pokud aplikace musí používat velký nebo neomezený počet regulárních výrazů, každý výraz by měl být interpretován, nikoli kompilován. Pokud se však opakovaně používá malý počet regulárních výrazů, měly by být kompilovány pro <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> lepší výkon. Alternativou je použití předkompilovaných regulárních výrazů. Pomocí metody můžete zkompilovat všechny výrazy do <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> opakovaně použitelné knihovny DLL. Tím se zabrání nutnosti kompilace za běhu a zároveň těžit z rychlosti kompilovaných regulárních výrazů.  
  
## <a name="the-regular-expressions-cache"></a>Mezipaměť regulárních výrazů  
 Pro zvýšení výkonu udržuje modul regulárních výrazů celou mezipaměť zkompilovaných regulárních výrazů. V mezipaměti jsou uloženy vzory regulárních výrazů, které se používají pouze při volání statické metody. (Vzory regulárních výrazů dodávané metodám instancí nejsou ukládány do mezipaměti.) Tím se zabrání nutnosti měnit analýzu výrazu do kódu bajtů vysoké úrovně při každém použití.  
  
 Maximální počet regulárních výrazů uložených v `static` `Shared` mezipaměti je <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> určen hodnotou vlastnosti ( in Visual Basic). Ve výchozím nastavení ukládá modul regulárních výrazů až 15 zkompilovaných regulárních výrazů. Pokud počet zkompilovaných regulárních výrazů překročí velikost mezipaměti, je zahozen nejméně naposledy použitý regulární výraz a nový regulární výraz je uložen do mezipaměti.  
  
 Aplikace může využít předkompilované regulární výrazy jedním z následujících dvou způsobů:  
  
- Pomocí statické metody objektu <xref:System.Text.RegularExpressions.Regex> k definování regulárního výrazu. Pokud používáte vzor regulárního výrazu, který již byl definován v jiném volání statické metody, modul regulárních výrazů jej načte z mezipaměti. Pokud ne, modul zkompiluje regulární výraz a přidá jej do mezipaměti.  
  
- Opětovným použitím <xref:System.Text.RegularExpressions.Regex> existujícího objektu tak dlouho, dokud je potřeba jeho vzor regulárního výrazu.  
  
 Z důvodu režie instanování objektů a kompilace regulárních výrazů je vytváření a rychlé ničení mnoha <xref:System.Text.RegularExpressions.Regex> objektů velmi nákladným procesem. Pro aplikace, které používají velký počet různých regulárních výrazů, můžete optimalizovat výkon pomocí volání statických `Regex` metod a případně zvětšením velikosti mezipaměti regulárních výrazů.  
  
## <a name="see-also"></a>Viz také

- [Regulární výrazy rozhraní .NET](../../../docs/standard/base-types/regular-expressions.md)
