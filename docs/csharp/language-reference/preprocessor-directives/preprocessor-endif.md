---
title: '#endif - C# Reference'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: cc344a224e2308e843328b228dd5e2466d02069f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712543"
---
# <a name="endif-c-reference"></a>#endif (referenční dokumentace jazyka C#)
`#endif`určuje konec podmíněné směrnice, která začala [#if](./preprocessor-if.md) direktivou. Například:  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a>Poznámky  
 Podmíněná směrnice, počínaje `#if` směrnice, musí být explicitně ukončena direktivou. `#endif` Příklad použití [viz #if](./preprocessor-if.md) `#endif`.  
  
## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [Direktivy preprocesoru jazyka C#](./index.md)
