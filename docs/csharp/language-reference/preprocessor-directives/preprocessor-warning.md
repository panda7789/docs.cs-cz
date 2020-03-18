---
title: '#upozornění - Odkaz jazyka C#'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 38c3807a696599390667060d3bf374c68845fed0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715074"
---
# <a name="warning-c-reference"></a>#warning (referenční dokumentace jazyka C#)
`#warning`umožňuje generovat upozornění kompilátoru úrovně [CS1030](../../misc/cs1030.md) z určitého umístění v kódu. Například:  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Poznámky
 Běžné použití `#warning` je v podmíněné směrnice. Je také možné generovat uživatelem definovanou chybu s [#error](./preprocessor-error.md).  
  
## <a name="example"></a>Příklad  

```csharp
// preprocessor_warning.cs  
// CS1030 expected  
#define DEBUG  
class MainClass
{  
    static void Main()
    {  
#if DEBUG  
#warning DEBUG is defined  
#endif  
    }  
}  
```  

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [Direktivy preprocesoru jazyka C#](./index.md)
