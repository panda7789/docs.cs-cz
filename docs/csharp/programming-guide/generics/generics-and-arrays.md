---
title: Obecné typy a pole - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: 145203d259b943bea1f43a9e49db2c7889bf914a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680139"
---
# <a name="generics-and-arrays-c-programming-guide"></a>Obecné typy a pole (Průvodce programováním v C#)
V jazyce C# 2.0 nebo novější, jednorozměrné pole, které mají nižší mez nula automaticky implementovat <xref:System.Collections.Generic.IList%601>. To umožňuje vytvořit obecné metody, které můžete použít stejný kód k iteraci v rámci pole a typy kolekcí. Tato technika je užitečné hlavně pro čtení dat v kolekcích. <xref:System.Collections.Generic.IList%601> Rozhraní nelze použít k přidání nebo odebrání prvků pole. Bude vyvolána výjimka, pokud se pokusíte volat <xref:System.Collections.Generic.IList%601> metody, jako <xref:System.Collections.Generic.IList%601.RemoveAt%2A> na pole v tomto kontextu.  
  
 Následující příklad kódu ukazuje, jak jedné obecné metody, která přebírá <xref:System.Collections.Generic.IList%601> vstupní parametr iterovat přes seznam a pole, v tomto případě pole celých čísel.  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Obecné typy](../../../csharp/programming-guide/generics/index.md)
- [Pole](../../../csharp/programming-guide/arrays/index.md)
- [Obecné typy](~/docs/standard/generics/index.md)
