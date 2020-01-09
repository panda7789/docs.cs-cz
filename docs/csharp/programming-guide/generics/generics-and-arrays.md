---
title: Obecné typy a pole – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: a8fad38fac07b9e8d51529d3ab7070328a333dbb
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75703010"
---
# <a name="generics-and-arrays-c-programming-guide"></a>Obecné typy a pole (Průvodce programováním v C#)
V C# 2,0 a novějších, jednorozměrná pole, která mají dolní mez nula, automaticky implementuje <xref:System.Collections.Generic.IList%601>. To umožňuje vytvořit obecné metody, které mohou použít stejný kód k iterování prostřednictvím polí a dalších typů kolekcí. Tato technika je primárně užitečná pro čtení dat v kolekcích. Rozhraní <xref:System.Collections.Generic.IList%601> nelze použít k přidání nebo odebrání prvků v poli. Pokud se pokusíte zavolat metodu <xref:System.Collections.Generic.IList%601>, například <xref:System.Collections.Generic.IList%601.RemoveAt%2A> v poli tohoto kontextu, bude vyvolána výjimka.  
  
 Následující příklad kódu ukazuje, jak jedna obecná metoda, která přebírá vstupní parametr <xref:System.Collections.Generic.IList%601>, může iterovat v seznamu i v poli, v tomto případě pole celých čísel.  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- [Průvodce programováním v jazyce C#](../index.md)
- [Obecné typy](./index.md)
- [Pole](../arrays/index.md)
- [Obecné typy](../../../standard/generics/index.md)
