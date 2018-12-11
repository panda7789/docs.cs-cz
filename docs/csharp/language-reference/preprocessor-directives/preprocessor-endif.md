---
title: '#endif – C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 13b43919b666dcc8c5adfc3490eaad73960547ae
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243896"
---
# <a name="endif-c-reference"></a>#endif (referenční dokumentace jazyka C#)
`#endif` Určuje konec podmíněné direktivy, který začal [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) směrnice. Například  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a>Poznámky  
 Podmíněnou direktivu, počínaje `#if` směrnice, musí být explicitně ukončen direktivou `#endif` směrnice. Zobrazit [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) příklad, jak používat `#endif`.  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [C# Direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)
