---
title: "Vytvoření vnořené skupiny"
description: "Postup vytvoření vnořené skupiny."
keywords: "Rozhraní .NET, rozhraní .NET core, C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 232aa46d975d7c338bbc776e3867f2e566601fde
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
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
