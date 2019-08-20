---
title: '#odkaz na C# oblast'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: ba5b47d77c69761a77b05ac6079e1b003af336b3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608753"
---
# <a name="region-c-reference"></a>#region (referenční dokumentace jazyka C#)
`#region`umožňuje zadat blok kódu, který lze rozbalit nebo sbalit při použití funkce [sbalení](/visualstudio/ide/outlining) editoru Visual Studio Code. V případě delších souborů kódu je možné sbalit nebo skrýt jednu nebo více oblastí, abyste se mohli soustředit na část souboru, na kterém právě pracujete. Následující příklad ukazuje, jak definovat oblast:  
  
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
 Blok musí být ukončen direktivou [#endregion.](./preprocessor-endregion.md) `#region`  
  
 Blok se nemůže překrývat s #ifm blokem. [](./preprocessor-if.md) `#region` Blok však může být vnořen `#if` v bloku a `#if` blok může být vnořen do `#region` bloku. `#region`  
  
## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [C# Direktivy preprocesoru](./index.md)
