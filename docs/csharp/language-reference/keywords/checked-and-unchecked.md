---
title: Zaškrtnuto a nezaškrtnuto (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: 26ea8a7864d93b8d64661db2b0dc1df6634f989a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="checked-and-unchecked-c-reference"></a>Zaškrtnuto a nezaškrtnuto (Referenční dokumentace jazyka C#)
Příkazy jazyka C# můžete spustit v kontextu zaškrtnuté nebo nezaškrtnuté. V kontextu zaškrtnuté Přetečení aritmetické funkce vyvolá výjimku. V kontextu nezaškrtnuté aritmetického přetečení je ignorován a výsledek je oříznuta.  
  
-   [zaškrtnutí](../../../csharp/language-reference/keywords/checked.md) zadejte zaškrtnutí kontextu.  
  
-   [nezaškrtnuté](../../../csharp/language-reference/keywords/unchecked.md) zadejte nezaškrtnuté kontextu.  
  
 Pokud ani `checked` ani `unchecked` je zadána výchozí kontext závisí na externí faktorech, například – možnosti kompilátoru.  
  
 Kontrola přetečení se týká následující operace:  
  
-   Pomocí následující předdefinované operátory na integrální typy výrazů:  
  
     `++` `--` -(unární)   `+` -   `*` `/`  
  
-   Explicitní číselné převody mezi integrální typy.  
  
 [/ Checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) – možnost kompilátoru umožňuje určit zaškrtnuté nebo nezaškrtnuté kontext pro všechny příkazy aritmetické celé číslo, které nejsou výslovně v oboru `checked` nebo `unchecked` – klíčové slovo.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Klíčová slova příkazů](../../../csharp/language-reference/keywords/statement-keywords.md)
