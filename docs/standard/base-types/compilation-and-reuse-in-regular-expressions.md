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
ms.openlocfilehash: b89f7f88233ecdab25ba2a74647aafeb4d8b74af
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344190"
---
# <a name="compilation-and-reuse-in-regular-expressions"></a>Kompilace a opětovné používání v regulárních výrazech
Můžete optimalizovat výkon aplikací, které poskytují rozsáhlé využití regulárních výrazů pochopením toho, jak modul regulárních výrazů kompiluje výrazy, a pochopením způsobu ukládání regulárních výrazů do mezipaměti. Toto téma popisuje kompilaci i ukládání do mezipaměti.  
  
## <a name="compiled-regular-expressions"></a>Zkompilované regulární výrazy  
 Ve výchozím nastavení modul regulárních výrazů zkompiluje regulární výraz do posloupnosti interních instrukcí (jedná se o kódy vysoké úrovně, které se liší od zprostředkujícího jazyka společnosti Microsoft nebo MSIL). Když modul spustí regulární výraz, interpretuje vnitřní kódy.  
  
 Pokud <xref:System.Text.RegularExpressions.Regex> je objekt vytvořen <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> s možností, zkompiluje regulární výraz do explicitního kódu MSIL namísto interních pokynů regulárního výrazu vysoké úrovně. To umožňuje . NET je just-in-time (JIT) kompilátor převést výraz na nativní strojový kód pro vyšší výkon.  Náklady na vytváření <xref:System.Text.RegularExpressions.Regex> objektu může být vyšší, ale náklady na provádění shody s ním je pravděpodobné, že bude mnohem menší.

 Alternativou je použití předkompilovaných regulárních výrazů. Pomocí metody můžete zkompilovat všechny výrazy do <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> opakovaně použitelné knihovny DLL. Tím se zabrání nutnosti kompilace za běhu a zároveň těžit z rychlosti kompilovaných regulárních výrazů.  
  
## <a name="the-regular-expressions-cache"></a>Mezipaměť regulárních výrazů  
 Pro zvýšení výkonu udržuje modul regulárních výrazů celou mezipaměť zkompilovaných regulárních výrazů. V mezipaměti jsou uloženy vzory regulárních výrazů, které se používají pouze při volání statické metody. (Vzory regulárních výrazů dodávané metodám instancí nejsou ukládány do mezipaměti.) Tím se zabrání nutnosti měnit analýzu výrazu do kódu bajtů vysoké úrovně při každém použití.  
  
 Maximální počet regulárních výrazů uložených v `static` `Shared` mezipaměti je <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> určen hodnotou vlastnosti ( in Visual Basic). Ve výchozím nastavení ukládá modul regulárních výrazů až 15 zkompilovaných regulárních výrazů. Pokud počet zkompilovaných regulárních výrazů překročí velikost mezipaměti, je zahozen nejméně naposledy použitý regulární výraz a nový regulární výraz je uložen do mezipaměti.  
  
 Aplikace může regulární výrazy znovu použít jedním z následujících dvou způsobů:  
  
- Pomocí statické metody objektu <xref:System.Text.RegularExpressions.Regex> k definování regulárního výrazu. Pokud používáte vzor regulárního výrazu, který již byl definován jiným voláním statické metody, modul regulárních výrazů se jej pokusí načíst z mezipaměti. Pokud není k dispozici v mezipaměti, modul zkompiluje regulární výraz a přidá jej do mezipaměti.
  
- Opětovným použitím <xref:System.Text.RegularExpressions.Regex> existujícího objektu tak dlouho, dokud je potřeba jeho vzor regulárního výrazu.  
  
 Z důvodu režie instanování objektů a kompilace regulárních výrazů je vytváření a rychlé ničení mnoha <xref:System.Text.RegularExpressions.Regex> objektů velmi nákladným procesem. Pro aplikace, které používají velký počet různých regulárních výrazů, můžete optimalizovat výkon pomocí volání statických `Regex` metod a případně zvětšením velikosti mezipaměti regulárních výrazů.  
  
## <a name="see-also"></a>Viz také

- [Regulární výrazy rozhraní .NET](../../../docs/standard/base-types/regular-expressions.md)
