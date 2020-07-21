---
title: Pole jako objekty – Průvodce programováním v C#
description: Pole v jazyce C# jsou objekty abstraktního základního typu pole. Můžete použít vlastnosti a další členy třídy Array, jako je například vlastnost length.
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 984def3ef74b07d7099fae6cae6d6f8ce7e03e12
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474719"
---
# <a name="arrays-as-objects-c-programming-guide"></a>Pole jako objekty (Průvodce programováním v C#)

V jazyce C# jsou pole vlastně objekty a nikoli pouze adresovatelné oblasti souvislé paměti jako v jazyce C a C++. <xref:System.Array>je abstraktní základní typ pro všechny typy polí. Můžete použít vlastnosti a další členy třídy, které <xref:System.Array> mají. Příkladem je použití <xref:System.Array.Length%2A> Vlastnosti k získání délky pole. Následující kód přiřadí délku `numbers` pole, tj `5` . proměnné s názvem `lengthOfNumbers` :

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<xref:System.Array>Třída poskytuje mnoho dalších užitečných metod a vlastností pro řazení, vyhledávání a kopírování polí.

## <a name="example"></a>Příklad

Tento příklad používá <xref:System.Array.Rank%2A> vlastnost k zobrazení počtu rozměrů pole.

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Pole](./index.md)
- [Jednorozměrná pole](./single-dimensional-arrays.md)
- [Vícerozměrná pole](./multidimensional-arrays.md)
- [Vícenásobná pole](./jagged-arrays.md)
