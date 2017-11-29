---
title: "Zaškrtnuto a nezaškrtnuto (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4b7b18b39dbfa7ed0818d9ea6e9e62ef79a9f5b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="checked-and-unchecked-c-reference"></a>Zaškrtnuto a nezaškrtnuto (Referenční dokumentace jazyka C#)
Příkazy jazyka C# můžete spustit v kontextu zaškrtnuté nebo nezaškrtnuté. V kontextu zaškrtnuté Přetečení aritmetické funkce vyvolá výjimku. V kontextu nezaškrtnuté aritmetického přetečení je ignorován a výsledek je oříznuta.  
  
-   [zaškrtnutí](../../../csharp/language-reference/keywords/checked.md) zadejte zaškrtnutí kontextu.  
  
-   [nezaškrtnuté](../../../csharp/language-reference/keywords/unchecked.md) zadejte nezaškrtnuté kontextu.  
  
 Pokud ani `checked` ani `unchecked` je zadána výchozí kontext závisí na externí faktorech, například – možnosti kompilátoru.  
  
 Kontrola přetečení se týká následující operace:  
  
-   Pomocí následující předdefinované operátory na integrální typy výrazů:  
  
     `++``--` -(unární) `+`  -    `*``/`  
  
-   Explicitní číselné převody mezi integrální typy.  
  
 [/ Checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) – možnost kompilátoru umožňuje určit zaškrtnuté nebo nezaškrtnuté kontext pro všechny příkazy aritmetické celé číslo, které nejsou výslovně v oboru `checked` nebo `unchecked` – klíčové slovo.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Klíčová slova příkazů](../../../csharp/language-reference/keywords/statement-keywords.md)
