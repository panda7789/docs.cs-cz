---
title: Obecné typy a pole - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: 50d649c4662114e76fdc0a6161ab0cbbeb04756d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237451"
---
# <a name="generics-and-arrays-c-programming-guide"></a>Obecné typy a pole (Průvodce programováním v C#)
V jazyce C# 2.0 nebo novější, jednorozměrné pole, které mají nižší mez nula automaticky implementovat <xref:System.Collections.Generic.IList%601>. To umožňuje vytvořit obecné metody, které můžete použít stejný kód k iteraci v rámci pole a typy kolekcí. Tato technika je užitečné hlavně pro čtení dat v kolekcích. <xref:System.Collections.Generic.IList%601> Rozhraní nelze použít k přidání nebo odebrání prvků pole. Bude vyvolána výjimka, pokud se pokusíte volat <xref:System.Collections.Generic.IList%601> metody, jako <xref:System.Collections.Generic.IList%601.RemoveAt%2A> na pole v tomto kontextu.  
  
 Následující příklad kódu ukazuje, jak jedné obecné metody, která přebírá <xref:System.Collections.Generic.IList%601> vstupní parametr iterovat přes seznam a pole, v tomto případě pole celých čísel.  
  
 [!code-csharp[csProgGuideGenerics#35](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-arrays_1.cs)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic>  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Obecné typy](../../../csharp/programming-guide/generics/index.md)  
- [Pole](../../../csharp/programming-guide/arrays/index.md)  
- [Obecné typy](~/docs/standard/generics/index.md)
