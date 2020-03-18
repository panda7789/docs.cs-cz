---
title: '#region – odkaz jazyka C#'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: 48e8a6796c3b07b348fd988a9b8501ee496b8ad5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173390"
---
# <a name="region-c-reference"></a>#region (referenční dokumentace jazyka C#)
`#region`umožňuje určit blok kódu, který můžete rozbalit nebo sbalit při použití funkce [osnovy](/visualstudio/ide/outlining) Editoru kódu sady Visual Studio. V delších souborech kódu je vhodné sbalit nebo skrýt jednu nebo více oblastí, abyste se mohli zaměřit na část souboru, na které právě pracujete. Následující příklad ukazuje, jak definovat oblast:  
  
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
 Blok `#region` musí být ukončen direktivou [#endregion.](./preprocessor-endregion.md)  
  
 Blok `#region` se nemůže překrývat s [#if](./preprocessor-if.md) blokem. Blok však může být vnořen `#if` do `#if` bloku a blok `#region` může být vnořen do bloku. `#region`  
  
## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [Direktivy preprocesoru jazyka C#](./index.md)
