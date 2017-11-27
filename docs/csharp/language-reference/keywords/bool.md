---
title: "bool (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords: bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1d52955d64a6c8063e4ea93ceb096459c1c5e984
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="bool-c-reference"></a>bool (Referenční dokumentace jazyka C#)
`bool` – Klíčové slovo je zástupce <xref:System.Boolean?displayProperty=nameWithType>. Se používá k deklaraci proměnné, které chcete uložit logické hodnoty [true](../../../csharp/language-reference/keywords/true.md) a [false](../../../csharp/language-reference/keywords/false.md).  
  
> [!NOTE]
>  Pokud požadujete logická hodnota proměnné, která může mít hodnotu `null`, použijte `bool?`. Další informace najdete v tématu [typy s možnou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md).  
  
## <a name="literals"></a>Literály  
 Můžete přiřadit logickou hodnotu k `bool` proměnné. Je také možné přiřadit výraz, který se vyhodnocuje `bool` k `bool` proměnné.  
  
 [!code-csharp[csrefKeywordsTypes#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_1.cs)]  
  
 Výchozí hodnota `bool` proměnná `false`. Výchozí hodnota `bool?` proměnná `null`.  
  
## <a name="conversions"></a>Převody  
 V jazyce C++ hodnotu typu `bool` lze převést na hodnotu typu `int`; jinými slovy, `false` se rovná nule a `true` je ekvivalentní nenulové hodnoty. V jazyce C#, neexistuje žádný převod mezi `bool` typu a dalších typů. Například následující `if` příkaz je neplatný v jazyce C#:  
  
 [!code-csharp[csrefKeywordsTypes#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_2.cs)]  
  
 K testování proměnné typu `int`, budete muset explicitně porovnávají ho na hodnotu, jako je například nula, následujícím způsobem:  
  
 [!code-csharp[csrefKeywordsTypes#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_3.cs)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu zadejte znak z klávesnice a program ověří, zda vstupní znak je písmeno. Pokud je písmeno, zkontroluje, pokud je malá nebo velká písmena. Tyto kontroly se provádějí pomocí <xref:System.Char.IsLetter%2A>, a <xref:System.Char.IsLower%2A>, obě které vrátit `bool` typ:  
  
 [!code-csharp[csrefKeywordsTypes#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_4.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabulka implicitních číselných převodů](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tabulka explicitních číselných převodů](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
