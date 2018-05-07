---
title: '#oblast (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: 88632b04ec8932e22f5bf7a23b8f0edf14d89f27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="region-c-reference"></a>#region (referenční dokumentace jazyka C#)
`#region` Umožňuje zadat blok kódu, který můžete rozbalit nebo sbalit při použití [osnovy](/visualstudio/ide/outlining) funkce z editoru kódu sady Visual Studio. V souborech delší kódu je vhodnější moci sbalení a skrytí jeden nebo více oblastí tak, aby se mohli zaměřit části souboru, který aktuálně pracujete na. Následující příklad ukazuje, jak definovat oblasti:  
  
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
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [C# Direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)
