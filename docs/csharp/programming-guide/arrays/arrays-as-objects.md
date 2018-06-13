---
title: Pole jako objekty (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 07e824d21ffc02ba7a3c33507d22d1dc7a1ac638
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33312605"
---
# <a name="arrays-as-objects-c-programming-guide"></a>Pole jako objekty (Průvodce programováním v C#)
V jazyce C# pole jsou ve skutečnosti objekty a právě adresovatelné oblasti souvislé paměti jako C a C++. <xref:System.Array> je abstraktní základní typ všechny typy polí. Můžete použít vlastnosti a členy třídy, která <xref:System.Array> má. Příkladem by používat <xref:System.Array.Length%2A> vlastnost k získání délka pole. Následující kód přiřadí délka `numbers` pole, která je `5`, proměnné s názvem `lengthOfNumbers`:  
  
 [!code-csharp[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 <xref:System.Array> Třída poskytuje mnoho užitečných metod a vlastností pro řazení, vyhledávání a kopírování pole.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Array.Rank%2A> vlastnost zobrazíte počet rozměrů pole.  
  
 [!code-csharp[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Pole](../../../csharp/programming-guide/arrays/index.md)  
 [Jednorozměrná pole](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Vícerozměrná pole](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Vícenásobná pole](../../../csharp/programming-guide/arrays/jagged-arrays.md)
