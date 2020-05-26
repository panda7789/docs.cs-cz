---
title: '#region – Referenční dokumentace jazyka C#'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: 66583d6e067b006b03130d8ff842b56bf57bcebc
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802767"
---
# <a name="region-c-reference"></a>#region (referenční dokumentace jazyka C#)
`#region`umožňuje zadat blok kódu, který lze rozbalit nebo sbalit při použití funkce [sbalení](/visualstudio/ide/outlining) editoru kódu. V případě delších souborů kódu je možné sbalit nebo skrýt jednu nebo více oblastí, abyste se mohli soustředit na část souboru, na kterém právě pracujete. Následující příklad ukazuje, jak definovat oblast:  
  
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
 `#region`Blok musí být ukončen direktivou [#endregion](./preprocessor-endregion.md) .  
  
 `#region`Blok se nemůže překrývat s [#ifm](./preprocessor-if.md) blokem. `#region`Blok však může být vnořen v `#if` bloku a `#if` blok může být vnořen do `#region` bloku.  
  
## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [C# – direktivy preprocesoru](./index.md)
