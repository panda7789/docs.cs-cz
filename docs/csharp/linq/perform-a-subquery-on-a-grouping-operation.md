---
title: Provedení poddotazu na operaci seskupení (LINQ v c#)
description: Jak provést poddotaz na operaci seskupení pomocí LINQ v C#.
ms.date: 12/01/2016
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: fd26f87ad7d5b4892f086bf8c7a34cf19a7f9e02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173364"
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a>Provádění poddotazů na skupinách

Tento článek ukazuje dva různé způsoby, jak vytvořit dotaz, který seřazuje zdrojová data do skupin a potom provádí poddotaz na každou skupinu jednotlivě. Základní technikou v každém příkladu je seskupit zdrojové prvky pomocí `newGroup` *pokračování* s názvem `newGroup`a potom generování nového poddotazu proti . Tento poddotaz je spuštěn proti každé nové skupině, která je vytvořena vnějším dotazem. Všimněte si, že v tomto konkrétním příkladu konečný výstup není skupina, ale ploché posloupnosti anonymních typů.  
  
Další informace o způsobu seskupení naleznete v [tématu group clause](../language-reference/keywords/group-clause.md).  
  
Další informace o pokračování naleznete [v tématu](../language-reference/keywords/into.md). Následující příklad používá jako zdroj dat strukturu dat v paměti, ale stejné zásady platí pro jakýkoli druh zdroje dat LINQ.  
  
## <a name="example"></a>Příklad

> [!NOTE]
> Tento příklad obsahuje odkazy na objekty, které jsou definovány v ukázkovém kódu v [aplikaci Query a collection of objects](query-a-collection-of-objects.md).

[!code-csharp[csProgGuideLINQ#23](~/samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]

Dotaz ve výše uvedeném fragmentu výstřižek lze také zapsat pomocí syntaxe metody. Následující fragment kódu má sémanticky ekvivalentní dotaz napsaný pomocí syntaxe metody.

[!code-csharp[csProgGuideLINQ#86](~/samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_2.cs)]

## <a name="see-also"></a>Viz také

- [LINQ (Language Integrated Query)](index.md)
