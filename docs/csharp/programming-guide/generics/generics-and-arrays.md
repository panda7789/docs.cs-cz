---
title: Obecné typy a pole – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: f5b82d470f728129fc76851bc2708e20085d5326
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589673"
---
# <a name="generics-and-arrays-c-programming-guide"></a>Obecné typy a pole (Průvodce programováním v C#)
V C# 2,0 a novějších, jednorozměrná pole, která mají dolní mez s hodnotou nula automaticky implementována <xref:System.Collections.Generic.IList%601>. To umožňuje vytvořit obecné metody, které mohou použít stejný kód k iterování prostřednictvím polí a dalších typů kolekcí. Tato technika je primárně užitečná pro čtení dat v kolekcích. <xref:System.Collections.Generic.IList%601> Rozhraní nelze použít k přidání nebo odebrání prvků z pole. Pokud se pokusíte zavolat <xref:System.Collections.Generic.IList%601> metodu, jako <xref:System.Collections.Generic.IList%601.RemoveAt%2A> je například na pole v tomto kontextu, bude vyvolána výjimka.  
  
 Následující příklad kódu ukazuje, jak jedna obecná metoda, která přijímá <xref:System.Collections.Generic.IList%601> vstupní parametr, může iterovat v seznamu i v poli, v tomto případě pole celých čísel.  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- [Průvodce programováním v jazyce C#](../index.md)
- [Obecné typy](./index.md)
- [Pole](../arrays/index.md)
- [Obecné typy](~/docs/standard/generics/index.md)
