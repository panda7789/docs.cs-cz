---
title: '#odkaz na C# oblast'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: 723a904d18955caceea9e0d485ab51f84366c66e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715121"
---
# <a name="region-c-reference"></a>#region (referenční dokumentace jazyka C#)
`#region` umožňuje zadat blok kódu, který lze rozbalit nebo sbalit při použití funkce [sbalení](/visualstudio/ide/outlining) editoru Visual Studio Code. V případě delších souborů kódu je možné sbalit nebo skrýt jednu nebo více oblastí, abyste se mohli soustředit na část souboru, na kterém právě pracujete. Následující příklad ukazuje, jak definovat oblast:  
  
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
 Blok `#region` musí být ukončen direktivou [#endregion](./preprocessor-endregion.md) .  
  
 Blok `#region` se nemůže překrývat s blokem [#if](./preprocessor-if.md) . Blok `#region` ale může být vnořený do `#if` bloku a blok `#if` může být vnořený do `#region` bloku.  
  
## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [C# Direktivy preprocesoru](./index.md)
