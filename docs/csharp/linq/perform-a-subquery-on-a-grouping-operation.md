---
title: "Provádění poddotazů na skupinách"
description: "Postup provádění poddotazů na skupinách."
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: f638b8a679a15891d04e02f1597d6bf7934a9e74
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
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
