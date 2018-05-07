---
title: '#Chyba (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 9ea4c24dcc3c0a4d39499bee5900cb9c6cc768c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="error-c-reference"></a>#error (referenční dokumentace jazyka C#)
`#error` Umožňuje generovat chybu z určitého umístění ve vašem kódu. Příklad:  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Poznámky  
 Běžně se používají `#error` v podmíněného direktivu.  
  
 Je také možné upozornění na uživatelem definované s [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).  
  
## <a name="example"></a>Příklad  
  
```csharp
// preprocessor_error.cs  
// CS1029 expected  
#define DEBUG  
class MainClass   
{  
    static void Main()   
    {  
#if DEBUG  
#error DEBUG is defined  
#endif  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [C# Direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)
