---
title: "char (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords: char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 41f672e9b12481fa5cce78015e95d2c5245a26db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="char-c-reference"></a>char (Referenční dokumentace jazyka C#)
`char` – Klíčové slovo se používá k deklaraci instance <xref:System.Char?displayProperty=nameWithType> struktura, která rozhraní .NET Framework se používá k reprezentaci znak Unicode. Hodnota `Char` objekt je hodnotu numerické 16bitové (pořadí).  
  
 Znaky kódování Unicode se používají k vyjádření většinu psané jazyky po celém světě.  
  
|Typ|Rozsah|Velikost|Typ rozhraní .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`char`|U + 0000 U + FFFF|16bitové znak Unicode|<xref:System.Char?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Literály  
 Konstanty z `char` typu lze zapsat jako znakové literály, šestnáctková řídicí sekvence nebo reprezentace kódování Unicode. Můžete také přetypování kódy integrální znaků. V následujícím příkladu čtyři `char` proměnné se inicializují ve stejném `X`:  
  
 [!code-csharp[csrefKeywordsTypes#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/char_1.cs)]  
  
## <a name="conversions"></a>Převody  
 A `char` může být implicitně převedena na [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [Celé_číslo](../../../csharp/language-reference/keywords/uint.md), [dlouho](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md) , [float](../../../csharp/language-reference/keywords/float.md), [dvojité](../../../csharp/language-reference/keywords/double.md), nebo [decimal](../../../csharp/language-reference/keywords/decimal.md). Existují však žádná implicitní převody z ostatních typů k `char` typu.  
  
 <xref:System.Char?displayProperty=nameWithType> Typu poskytuje několik statické metody pro práci s `char` hodnoty.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Char>  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabulka implicitních číselných převodů](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tabulka explicitních číselných převodů](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [Typy s možnou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md)  
 [Řetězce](../../../csharp/programming-guide/strings/index.md)
