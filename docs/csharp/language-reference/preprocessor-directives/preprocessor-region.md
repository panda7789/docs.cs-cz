---
description: '#region – Referenční dokumentace jazyka C#'
title: '#region – Referenční dokumentace jazyka C#'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: ed40d895fedb9be271bb389a4f8de69d7ae3f266
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137939"
---
# <a name="region-c-reference"></a>#region (referenční dokumentace jazyka C#)
`#region` umožňuje zadat blok kódu, který lze rozbalit nebo sbalit při použití funkce [sbalení](/visualstudio/ide/outlining) editoru kódu. V případě delších souborů kódu je možné sbalit nebo skrýt jednu nebo více oblastí, abyste se mohli soustředit na část souboru, na kterém právě pracujete. Následující příklad ukazuje, jak definovat oblast:  
  
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
