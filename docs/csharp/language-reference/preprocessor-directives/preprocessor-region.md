---
title: "#<a name=\"region-c-reference\"></a>oblast (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#region'
helpviewer_keywords: '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cce4a8ac79c4687280e28618d8863d16cd193a3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="region-c-reference"></a>#region (referenční dokumentace jazyka C#)
`#region`Umožňuje zadat blok kódu, který můžete rozbalit nebo sbalit při použití [osnovy](/visualstudio/ide/outlining) funkce z editoru kódu sady Visual Studio. V souborech delší kódu je vhodnější moci sbalení a skrytí jeden nebo více oblastí tak, aby se mohli zaměřit části souboru, který aktuálně pracujete na. Následující příklad ukazuje, jak definovat oblasti:  
  
```csharp
#region MyClass definition  
public class MyClass   
{  
    static void Main()   
    {  
    }  
}  
#endregion  
```  
  
## <a name="remarks"></a>Poznámky  
 A `#region` bloku musí být ukončena s [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) – direktiva.  
  
 A `#region` bloku se nesmí překrývat s [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) bloku. Ale `#region` bloku mohou být použity v `#if` bloku a `#if` bloku mohou být použity v `#region` bloku.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [C# direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)
