---
title: Pole jako objekty – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: d8b929eccf9be259874d03dd93f49a49798bb349
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715095"
---
# <a name="arrays-as-objects-c-programming-guide"></a>Pole jako objekty (Průvodce programováním v C#)

V jazyce C# pole jsou ve skutečnosti objekty a není pouze adresovatelné oblasti souvislé paměti jako v jazyce C a C++. <xref:System.Array>je abstraktní základní typ všech typů polí. Můžete použít vlastnosti a další <xref:System.Array> členy třídy, které má. Příkladem je použití vlastnosti <xref:System.Array.Length%2A> získat délku pole. Následující kód přiřadí délku `numbers` pole, `5`což je , `lengthOfNumbers`proměnné s názvem :

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

Třída <xref:System.Array> poskytuje mnoho dalších užitečných metod a vlastností pro řazení, vyhledávání a kopírování polí.

## <a name="example"></a>Příklad

Tento příklad <xref:System.Array.Rank%2A> používá vlastnost k zobrazení počtu dimenzí pole.

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Pole](./index.md)
- [Jednorozměrná pole](./single-dimensional-arrays.md)
- [Vícerozměrná pole](./multidimensional-arrays.md)
- [Vícenásobná pole](./jagged-arrays.md)
