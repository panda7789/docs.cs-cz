---
title: Pole jako objekty – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: d8b929eccf9be259874d03dd93f49a49798bb349
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715095"
---
# <a name="arrays-as-objects-c-programming-guide"></a>Pole jako objekty (Průvodce programováním v C#)

V C#jsou pole vlastně objekty a nikoli pouze adresovatelné oblasti souvislé paměti jako v jazyce C a C++. <xref:System.Array> je abstraktní základní typ pro všechny typy polí. Můžete použít vlastnosti a jiné členy třídy, které <xref:System.Array> má. Příkladem je použití vlastnosti <xref:System.Array.Length%2A> k získání délky pole. Následující kód přiřadí délku `numbers` pole, které je `5`, do proměnné s názvem `lengthOfNumbers`:

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

Třída <xref:System.Array> poskytuje mnoho dalších užitečných metod a vlastností pro řazení, vyhledávání a kopírování polí.

## <a name="example"></a>Příklad

V tomto příkladu se používá vlastnost <xref:System.Array.Rank%2A> k zobrazení počtu rozměrů pole.

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Pole](./index.md)
- [Jednorozměrná pole](./single-dimensional-arrays.md)
- [Vícerozměrná pole](./multidimensional-arrays.md)
- [Vícenásobná pole](./jagged-arrays.md)
