---
title: '#endif (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 1686e706ce5cae3b2eaa28a7e1c89b5694b2be88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269974"
---
# <a name="endif-c-reference"></a>#endif (referenční dokumentace jazyka C#)
`#endif` Určuje konec podmíněného – direktiva, což začal s [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) – direktiva. Například  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a>Poznámky  
 Podmíněné – direktiva, počínaje `#if` – direktiva, musí být explicitně ukončena s `#endif` – direktiva. V tématu [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) příklad použití `#endif`.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [C# Direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)
