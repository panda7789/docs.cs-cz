---
title: "Pole jako objekty (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e29685af509009f42f38ba2dbf8524075e880ff9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="arrays-as-objects-c-programming-guide"></a>Pole jako objekty (Průvodce programováním v C#)
V jazyce C# pole jsou ve skutečnosti objekty a právě adresovatelné oblasti souvislé paměti jako C a C++. <xref:System.Array>je abstraktní základní typ všechny typy polí. Můžete použít vlastnosti a členy třídy, která <xref:System.Array> má. Příkladem by používat <xref:System.Array.Length%2A> vlastnost k získání délka pole. Následující kód přiřadí délka `numbers` pole, která je `5`, proměnné s názvem `lengthOfNumbers`:  
  
 [!code-csharp[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 <xref:System.Array> Třída poskytuje mnoho užitečných metod a vlastností pro řazení, vyhledávání a kopírování pole.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Array.Rank%2A> vlastnost zobrazíte počet rozměrů pole.  
  
 [!code-csharp[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Pole](../../../csharp/programming-guide/arrays/index.md)  
 [Jednorozměrná pole](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Vícerozměrná pole](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Vícenásobná pole](../../../csharp/programming-guide/arrays/jagged-arrays.md)
