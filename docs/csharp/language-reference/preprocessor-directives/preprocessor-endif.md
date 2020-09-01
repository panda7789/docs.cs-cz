---
description: '#endif – Referenční dokumentace jazyka C#'
title: '#endif – Referenční dokumentace jazyka C#'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 8068a6e437145178fd5c88763c86692a8700c349
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138160"
---
# <a name="endif-c-reference"></a>#endif (referenční dokumentace jazyka C#)
`#endif` určuje konec podmíněné direktivy, která začala s direktivou [#if](./preprocessor-if.md) . Příklad:  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a>Poznámky  
 Podmíněná direktiva, která začíná `#if` direktivou, musí být explicitně ukončena `#endif` direktivou. Příklad použití naleznete v tématu [#if](./preprocessor-if.md) `#endif` .  
  
## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [C# – direktivy preprocesoru](./index.md)
