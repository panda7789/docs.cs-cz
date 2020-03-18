---
title: Obecné typy a pole – programovací příručka jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: a8fad38fac07b9e8d51529d3ab7070328a333dbb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75703010"
---
# <a name="generics-and-arrays-c-programming-guide"></a>Obecné typy a pole (Průvodce programováním v C#)
V C# 2.0 a novější jednorozměrné pole, které mají <xref:System.Collections.Generic.IList%601>dolní mez nula automaticky implementovat . To umožňuje vytvořit obecné metody, které můžete použít stejný kód k iterování prostřednictvím polí a jiných typů kolekcí. Tato technika je užitečná především pro čtení dat v kolekcích. Rozhraní <xref:System.Collections.Generic.IList%601> nelze použít k přidání nebo odebrání prvků z pole. Výjimka bude vyvolána, pokud se <xref:System.Collections.Generic.IList%601> pokusíte <xref:System.Collections.Generic.IList%601.RemoveAt%2A> volat metodu, například na pole v tomto kontextu.  
  
 Následující příklad kódu ukazuje, jak může jedna <xref:System.Collections.Generic.IList%601> obecná metoda, která přebírá vstupní parametr, iterovat seznamem i polem, v tomto případě polem celých čísel.  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic>
- [Programovací příručka jazyka C#](../index.md)
- [Obecné typy](./index.md)
- [Pole](../arrays/index.md)
- [Obecné typy](../../../standard/generics/index.md)
