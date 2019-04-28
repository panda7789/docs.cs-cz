---
title: Pole jako objekty - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 8500cf508b77a0fa7e348ce0fe6b1f16fd2bab25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683974"
---
# <a name="arrays-as-objects-c-programming-guide"></a>Pole jako objekty (Průvodce programováním v C#)

V jazyce C# pole jsou ve skutečnosti objekty a právě adresovatelný oblastech souvislé paměti jako v jazyce C a C++. <xref:System.Array> je abstraktní základní typ pro všechny typy polí. Můžete použít vlastnosti a ostatních členů třídy, která <xref:System.Array> má. Příklad tohoto by pomocí <xref:System.Array.Length%2A> vlastnost získat délku pole. Následující kód přiřadí délka `numbers` pole, které je `5`, proměnné s názvem `lengthOfNumbers`:  
  
 [!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]  
  
 <xref:System.Array> Třída poskytuje mnoho dalších užitečných metod a vlastností pro řazení, hledání a kopírování polí.  
  
## <a name="example"></a>Příklad

 V tomto příkladu <xref:System.Array.Rank%2A> vlastnost zobrazíte počet rozměrů pole.  
  
 [!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Pole](../../../csharp/programming-guide/arrays/index.md)
- [Jednorozměrná pole](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)
- [Vícerozměrná pole](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
- [Vícenásobná pole](../../../csharp/programming-guide/arrays/jagged-arrays.md)
