---
title: Provádění poddotazů na operace seskupení (LINQ v JAZYKU C#)
description: Jak k provádění poddotazů na operace seskupení pomocí jazyka LINQ v jazyce C#.
ms.date: 12/1/2016
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: 514db81b80557a3026589f00177910cc9446c0f4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43475995"
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a>Provádění poddotazů na operace seskupení

Tento článek popisuje dva různé způsoby vytvoření dotazu, který seřadí zdroj dat do skupin a potom provede poddotaz v každé skupině jednotlivě. Základní postup v obou příkladech je seskupení zdrojové prvky pomocí *pokračování* s názvem `newGroup`a potom generovat nové poddotaz proti `newGroup`. Tato poddotaz spustí pro každou novou skupinu, která se vytvořila vnější dotaz. Všimněte si, že v tomto konkrétním příkladu závěrečný výstup skupinu, ale plochý sekvence anonymních typů.  
  
Další informace o tom, jak skupiny, najdete v části [group – klauzule](../language-reference/keywords/group-clause.md).  
  
Další informace o pokračování naleznete v tématu [do](../language-reference/keywords/into.md). Následující příklad používá jako zdroj dat pro strukturu dat v paměti, ale stejné zásady platí i pro jakýkoli druh zdroje dat LINQ.  
  
## <a name="example"></a>Příklad

> [!NOTE]
> Obsahuje odkazy na objekty, které jsou definovány ve vzorovém kódu v tomto příkladu [dotazování na kolekci objektů](query-a-collection-of-objects.md).

[!code-csharp[csProgGuideLINQ#23](~/samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]  

## <a name="see-also"></a>Viz také:

- [LINQ (Language Integrated Query)](index.md)
