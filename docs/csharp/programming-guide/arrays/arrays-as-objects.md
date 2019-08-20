---
title: Pole jako objekty – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: fd4496e0f84953204ad8c3f40db699e911c3f477
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597358"
---
# <a name="arrays-as-objects-c-programming-guide"></a>Pole jako objekty (Průvodce programováním v C#)

V C#jsou pole vlastně objekty a nikoli pouze adresovatelné oblasti souvislé paměti jako v jazyce C a C++. <xref:System.Array>je abstraktní základní typ pro všechny typy polí. Můžete použít vlastnosti a další členy třídy, které <xref:System.Array> mají. Příkladem je použití <xref:System.Array.Length%2A> vlastnosti k získání délky pole. Následující kód přiřadí délku `numbers` pole, `5`tj. proměnné s názvem `lengthOfNumbers`:  
  
 [!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]  
  
 <xref:System.Array> Třída poskytuje mnoho dalších užitečných metod a vlastností pro řazení, vyhledávání a kopírování polí.  
  
## <a name="example"></a>Příklad

 Tento příklad používá <xref:System.Array.Rank%2A> vlastnost k zobrazení počtu rozměrů pole.  
  
 [!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Pole](./index.md)
- [Jednorozměrná pole](./single-dimensional-arrays.md)
- [Vícerozměrná pole](./multidimensional-arrays.md)
- [Vícenásobná pole](./jagged-arrays.md)
