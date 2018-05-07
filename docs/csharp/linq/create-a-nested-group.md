---
title: Vytvoření vnořené skupiny
description: Postup vytvoření vnořené skupiny.
ms.date: 12/1/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: dd1158bfa1456342fe8967aed5e02ecebae591c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="create-a-nested-group"></a>Vytvoření vnořené skupiny

Následující příklad ukazuje postup vytvoření vnořené skupiny ve výrazu dotazu LINQ. Každou skupinu, která je vytvořena podle úrovně rok nebo úrovni student je pak dále rozdělit na skupiny založené na názvy pro osob.  
  
## <a name="example"></a>Příklad

 > [!NOTE]
 > Tento příklad obsahuje odkazy na objekty, které jsou definovány v ukázkovém kódu v [dotazování na kolekci objektů](query-a-collection-of-objects.md). 

 [!code-csharp[csProgGuideLINQ#24](../../../samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]  
  
 Všimněte si, že tři vnořené `foreach` smyčky jsou nutné k iteraci nad vnitřní prvky vnořené skupiny.  
  
## <a name="see-also"></a>Viz také  
 [LINQ – výrazy dotazů](index.md)
