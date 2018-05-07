---
title: '#upozornění (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: c56458e0100c23450655e48b2abfb346e18e0bb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="warning-c-reference"></a>#warning (referenční dokumentace jazyka C#)
`#warning` Umožňuje generovat varováním na úrovni jednoho z určitého umístění ve vašem kódu. Příklad:  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Poznámky  
 Běžně se používají `#warning` v podmíněného direktivu. Je také možné generovat uživatelem definované chybové s [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).  
  
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
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [C# Direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)
