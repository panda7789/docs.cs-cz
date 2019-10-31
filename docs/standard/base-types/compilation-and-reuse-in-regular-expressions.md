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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091734"
---
# <a name="compilation-and-reuse-in-regular-expressions"></a>Kompilace a opětovné používání v regulárních výrazech
Můžete optimalizovat výkon aplikací, které využívají rozsáhlé používání regulárních výrazů, a porozumět, jak modul regulárních výrazů kompiluje výrazy a porozumění způsobu, jakým jsou regulární výrazy ukládány do mezipaměti. Toto téma popisuje kompilaci a ukládání do mezipaměti.  
  
## <a name="compiled-regular-expressions"></a>Kompilované regulární výrazy  
 Ve výchozím nastavení modul regulárních výrazů zkompiluje regulární výraz do sekvence vnitřních instrukcí (Jedná se o kódy vysoké úrovně, které se liší od jazyka MSIL nebo jazyka MSIL). Když modul spustí regulární výraz, interpretuje vnitřní kódy.  
  
 Pokud je objekt <xref:System.Text.RegularExpressions.Regex> vytvořen pomocí možnosti <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>, Kompiluje regulární výraz na explicitní kód jazyka MSIL namísto interních instrukcí regulárního výrazu vysoké úrovně. To umožňuje. Kompilátor JIT (just-in-time) pro převod výrazu na nativní strojový kód pro vyšší výkon.  
  
Generovaný jazyk MSIL však nelze uvolnit. Jediným způsobem, jak uvolnit kód, je uvolnit celou doménu aplikace (tj. pro uvolnění všech kódů vaší aplikace). Po kompilaci regulárního výrazu s možností <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> nikdy neuvolní prostředky používané kompilovaným výrazem, a to ani v případě, že regulární výraz byl vytvořen pomocí objektu <xref:System.Text.RegularExpressions.Regex>, který je samotný uvolněn do uvolňování paměti.  
  
 Musíte být opatrní, abyste omezili počet různých regulárních výrazů, které kompilujete s možností <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>, abyste se vyhnuli využívání příliš velkého počtu prostředků. Pokud aplikace musí používat velký nebo neohraničený počet regulárních výrazů, každý výraz by měl být interpretován, nikoli kompilován. Pokud se však používá malý počet regulárních výrazů opakovaně, měly by být kompilovány s <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> pro lepší výkon. Alternativou je použití předkompilovaných regulárních výrazů. Všechny vaše výrazy můžete zkompilovat do opakovaně použitelné knihovny DLL pomocí metody <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A>. Tím se vyhnete nutnosti kompilovat za běhu a přitom stále využívat rychlost kompilovaných regulárních výrazů.  
  
## <a name="the-regular-expressions-cache"></a>Mezipaměť regulárních výrazů  
 Pro zlepšení výkonu modul regulárních výrazů udržuje mezipaměť zkompilovaných regulárních výrazů v celé aplikaci. Mezipaměť ukládá vzory regulárních výrazů, které jsou používány pouze ve voláních statických metod. (Vzory regulárních výrazů dodávané do metod instancí nejsou ukládány do mezipaměti.) To brání nutnosti znovu analyzovat výraz do bajtového kódu vysoké úrovně pokaždé, když se použije.  
  
 Maximální počet regulárních výrazů uložených v mezipaměti je určen hodnotou `static` (`Shared` ve Visual Basic) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> Property. Ve výchozím nastavení modul regulárních výrazů ukládá do mezipaměti až 15 kompilovaných regulárních výrazů. Pokud počet zkompilovaných regulárních výrazů překročí velikost mezipaměti, je poslední nepoužitý regulární výraz zahozen a nový regulární výraz je uložen do mezipaměti.  
  
 Vaše aplikace může využít předkompilovaných regulárních výrazů jedním z následujících dvou způsobů:  
  
- Pomocí statické metody objektu <xref:System.Text.RegularExpressions.Regex> k definování regulárního výrazu. Pokud používáte vzor regulárního výrazu, který již byl definován v jiném volání statické metody, modul regulárních výrazů ho načte z mezipaměti. V takovém případě bude modul kompilovat regulární výraz a přidat jej do mezipaměti.  
  
- Tím, že znovu použijete existující <xref:System.Text.RegularExpressions.Regex> objekt, pokud je třeba jeho vzor regulárního výrazu.  
  
 Kvůli režii při vytváření instancí objektů a kompilaci regulárních výrazů vytváření a rychlé zničení řady <xref:System.Text.RegularExpressions.Regex> objektů je velmi nákladný proces. Pro aplikace, které používají velký počet různých regulárních výrazů, můžete optimalizovat výkon pomocí volání statických `Regex` metod a případně zvýšením velikosti mezipaměti regulárních výrazů.  
  
## <a name="see-also"></a>Viz také:

- [Regulární výrazy .NET](../../../docs/standard/base-types/regular-expressions.md)
