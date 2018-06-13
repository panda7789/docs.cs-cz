---
title: Provádění poddotazů na skupinách
description: Postup provádění poddotazů na skupinách.
ms.date: 12/1/2016
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: 209d05c2fe8719fa9116061d199272366146f465
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277326"
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a>Provádění poddotazů na skupinách

Toto téma ukazuje dva různé způsoby vytvoření dotaz, který řadí zdrojová data do skupin a potom provede poddotazu přes každou skupinu jednotlivě. Základní technika v obou příkladech je seskupit pomocí zdrojové elementy *pokračování* s názvem `newGroup`a pak generovat nové poddotazu proti `newGroup`. Tato poddotazu je spustit pro každou novou skupinu, který byl vytvořený vnější dotazu. Všimněte si, že v tomto konkrétním příkladu finální výstup není skupinu, ale ploché posloupnost anonymní typy.  
  
 Další informace o tom, jak skupiny najdete v tématu [group – klauzule](../language-reference/keywords/group-clause.md).  
  
 Další informace o pokračování najdete v tématu [do](../language-reference/keywords/into.md). Následující příklad používá jako zdroj dat pro strukturu dat v paměti, ale stejné zásady platí pro libovolný zdroj dat LINQ.  
  
## <a name="example"></a>Příklad 

 > [!NOTE]
 > Tento příklad obsahuje odkazy na objekty, které jsou definovány v ukázkovém kódu v [dotazování na kolekci objektů](query-a-collection-of-objects.md).

 [!code-csharp[csProgGuideLINQ#23](../../../samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]  
   
## <a name="see-also"></a>Viz také  
 [LINQ – výrazy dotazů](index.md)
