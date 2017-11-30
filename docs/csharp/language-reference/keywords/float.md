---
title: "float (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- float
- float_CSharpKeyword
helpviewer_keywords:
- float keyword [C#]
- floating-point numbers [C#], float keyword
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 846f132812fe90a285c81a020d440fc846f88b5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="float-c-reference"></a>float (Referenční dokumentace jazyka C#)
`float` – Klíčové slovo označuje jednoduchý typ, který ukládá 32bitové hodnoty s plovoucí desetinnou čárkou. Následující tabulka uvádí přesnost a přibližnou rozsah `float` typu.  
  
|Typ|Přibližná rozsahu|Přesnost|Typ rozhraní .NET Framework|  
|----------|-----------------------|---------------|-------------------------|  
|`float`|-3.4 × 10<sup>38</sup>+ 3,4 × 10<sup>38</sup>|7 míst|<xref:System.Single?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Literály  
 Ve výchozím nastavení, je skutečně číselný literál na pravé straně operátoru přiřazení považován za [dvojité](double.md). Proto k chybě při inicializaci float proměnné, použijte příponu `f` nebo `F`, jako v následujícím příkladu:  
  
```csharp
float x = 3.5F;  
```
  
 Pokud nepoužijete příponou v předchozí deklaraci, zobrazí se chyba kompilace vzhledem k tomu, že se pokoušíte uložit [dvojité](double.md) hodnotu do `float` proměnné.  
  
## <a name="conversions"></a>Převody  
 Je možné kombinovat číselné integrální typy a typy s plovoucí desetinnou čárkou ve výrazu. Celočíselné typy v tomto případě se převedou na typy s plovoucí desetinnou čárkou. Vyhodnocení výrazu se provádí podle následujících pravidel:  
  
-   Pokud jeden z typů s plovoucí desetinnou čárkou je [dvojité](double.md), výsledkem výrazu [dvojité](double.md) nebo [bool](bool.md) ve výrazech relační nebo logická hodnota.  
  
-   Pokud neexistuje žádné [dvojité](double.md) zadejte výraz výraz vyhodnocen jako `float` nebo [bool](bool.md) ve výrazech relační nebo logická hodnota.  
  
 Výraz s plovoucí desetinnou čárkou mohou obsahovat následující sady hodnot:  
  
-   Kladné a záporné nuly  
  
-   Kladné a záporné infinity  
  
-   Hodnota not-a-Number (NaN)  
  
-   Konečné sadu nenulové hodnoty  
  
 Další informace o těchto hodnotách naleznete v tématu Standard IEEE pro binární aritmetiku, k dispozici na [IEEE](http://www.ieee.org) webu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se [int](int.md), [krátké](short.md)a `float` jsou zahrnuty v matematickém výrazu, která poskytuje `float` výsledek. (Nezapomeňte, že `float` je alias <xref:System.Single?displayProperty=nameWithType> typu.) Všimněte si, že neexistuje žádná [dvojité](double.md) ve výrazu.  
  
 [!code-csharp[csrefKeywordsTypes#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/float_1.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Single>  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Přetypování a převody typů](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [Klíčová slova jazyka C#](index.md)  
 [Tabulka celočíselných typů](integral-types-table.md)  
 [Tabulka předdefinovaných typů](built-in-types-table.md)  
 [Tabulka implicitních číselných převodů](implicit-numeric-conversions-table.md)  
 [Tabulka explicitních číselných převodů](explicit-numeric-conversions-table.md)
