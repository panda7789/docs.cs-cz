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
ms.openlocfilehash: 54f14a4f31bef00dd222686cc523935b2d9dd5fa
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279035"
---
# <a name="compilation-and-reuse-in-regular-expressions"></a>Kompilace a opětovné používání v regulárních výrazech
Můžete optimalizovat výkon aplikací, které využívají rozsáhlé používání regulárních výrazů, a porozumět, jak modul regulárních výrazů kompiluje výrazy a porozumění způsobu, jakým jsou regulární výrazy ukládány do mezipaměti. Toto téma popisuje kompilaci a ukládání do mezipaměti.  
  
## <a name="compiled-regular-expressions"></a>Kompilované regulární výrazy  
 Ve výchozím nastavení modul regulárních výrazů zkompiluje regulární výraz do sekvence vnitřních instrukcí (Jedná se o kódy vysoké úrovně, které se liší od jazyka MSIL nebo jazyka MSIL). Když modul spustí regulární výraz, interpretuje vnitřní kódy.  
  
 Pokud <xref:System.Text.RegularExpressions.Regex> je objekt vytvořen s <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> možností, Kompiluje regulární výraz na explicitní kód jazyka MSIL namísto interních instrukcí regulárního výrazu vysoké úrovně. To umožňuje. Kompilátor JIT (just-in-time) pro převod výrazu na nativní strojový kód pro vyšší výkon.  Náklady na konstrukci <xref:System.Text.RegularExpressions.Regex> objektu mohou být vyšší, ale náklady na jejich Vyrovnávání je pravděpodobně mnohem menší.

 Alternativou je použití předkompilovaných regulárních výrazů. Všechny vaše výrazy můžete zkompilovat do opakovaně použitelné knihovny DLL pomocí <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> metody. Tím se vyhnete nutnosti kompilovat za běhu a přitom stále využívat rychlost kompilovaných regulárních výrazů.  
  
## <a name="the-regular-expressions-cache"></a>Mezipaměť regulárních výrazů  
 Pro zlepšení výkonu modul regulárních výrazů udržuje mezipaměť zkompilovaných regulárních výrazů v celé aplikaci. Mezipaměť ukládá vzory regulárních výrazů, které jsou používány pouze ve voláních statických metod. (Vzory regulárních výrazů dodávané do metod instancí nejsou ukládány do mezipaměti.) To brání nutnosti znovu analyzovat výraz do bajtového kódu vysoké úrovně pokaždé, když se použije.  
  
 Maximální počet regulárních výrazů uložených v mezipaměti je určen hodnotou `static` `Shared` vlastnosti (ve Visual Basic) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> . Ve výchozím nastavení modul regulárních výrazů ukládá do mezipaměti až 15 kompilovaných regulárních výrazů. Pokud počet zkompilovaných regulárních výrazů překročí velikost mezipaměti, je poslední nepoužitý regulární výraz zahozen a nový regulární výraz je uložen do mezipaměti.  
  
 Vaše aplikace může znovu použít regulární výrazy jedním z následujících dvou způsobů:  
  
- Pomocí statické metody <xref:System.Text.RegularExpressions.Regex> objektu pro definování regulárního výrazu. Pokud používáte vzor regulárního výrazu, který již byl definován jiným voláním statické metody, modul regulárních výrazů se pokusí načíst z mezipaměti. Pokud není v mezipaměti k dispozici, modul bude kompilovat regulární výraz a přidat jej do mezipaměti.
  
- Tím, že znovu použijete existující <xref:System.Text.RegularExpressions.Regex> objekt, pokud je třeba jeho vzor regulárního výrazu.  
  
 Kvůli režii při vytváření instancí objektů a kompilaci regulárních výrazů vytváření a rychlé zničení mnoha <xref:System.Text.RegularExpressions.Regex> objektů je velmi nákladný proces. Pro aplikace, které používají velký počet různých regulárních výrazů, můžete optimalizovat výkon pomocí volání statických `Regex` metod a případně zvýšením velikosti mezipaměti regulárních výrazů.  
  
## <a name="see-also"></a>Viz také

- [Regulární výrazy .NET](regular-expressions.md)
