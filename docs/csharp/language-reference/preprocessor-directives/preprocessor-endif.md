---
title: '#endif- C# reference'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 74205c836b4eeb2d8b17b907bb13708f3225df08
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608577"
---
# <a name="endif-c-reference"></a>#endif (referenční dokumentace jazyka C#)
`#endif`určuje konec podmíněné direktivy, která začala s direktivou [#if](./preprocessor-if.md) . Například  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a>Poznámky  
 Podmíněná direktiva, která `#if` začíná direktivou, musí být explicitně ukončena `#endif` direktivou. Příklad [](./preprocessor-if.md) použití `#endif`naleznete v tématu #if.  
  
## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [C# Direktivy preprocesoru](./index.md)
