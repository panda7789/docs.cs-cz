---
title: Obecné typy a pole – Průvodce programováním v C#
description: Seznamte se s obecnými typy a poli v programování v jazyce C#. Podívejte se na příklady kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: f3d9e9e0c84d954278780e7598545f80aea0e58c
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299042"
---
# <a name="generics-and-arrays-c-programming-guide"></a>Obecné typy a pole (Průvodce programováním v C#)
V C# 2,0 a novějších, jednorozměrná pole, která mají dolní mez nulového automatického implementace <xref:System.Collections.Generic.IList%601> . To umožňuje vytvořit obecné metody, které mohou použít stejný kód k iterování prostřednictvím polí a dalších typů kolekcí. Tato technika je primárně užitečná pro čtení dat v kolekcích. <xref:System.Collections.Generic.IList%601>Rozhraní nelze použít k přidání nebo odebrání prvků z pole. Pokud se pokusíte zavolat <xref:System.Collections.Generic.IList%601> metodu, jako je například <xref:System.Collections.Generic.IList%601.RemoveAt%2A> na pole v tomto kontextu, bude vyvolána výjimka.  
  
 Následující příklad kódu ukazuje, jak jedna obecná metoda, která přijímá <xref:System.Collections.Generic.IList%601> vstupní parametr, může iterovat v seznamu i v poli, v tomto případě pole celých čísel.  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- [Průvodce programováním v C#](../index.md)
- [Obecné typy](./index.md)
- [Pole](../arrays/index.md)
- [Obecné typy](../../../standard/generics/index.md)
