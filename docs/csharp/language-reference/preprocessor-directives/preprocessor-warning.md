---
title: '#upozornění – C# referenční informace'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 3d09cd95ef4d53e3f11d9feb9675ebba22d6f857
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608521"
---
# <a name="warning-c-reference"></a>#warning (referenční dokumentace jazyka C#)
`#warning`umožňuje generovat upozornění na [CS1030](../../misc/cs1030.md) úrovně jednoho kompilátoru z konkrétního umístění v kódu. Příklad:  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Poznámky
 Běžné použití `#warning` je v podmíněných direktivách. K dispozici je také možnost generovat uživatelem definovanou chybu pomocí [#error](./preprocessor-error.md).  
  
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

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [C# Direktivy preprocesoru](./index.md)
