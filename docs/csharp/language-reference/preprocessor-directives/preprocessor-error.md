---
title: '#Chyba (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: ed43c1f85142ec6c54e44db5e3b0b7de3ef36bb8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44067224"
---
# <a name="error-c-reference"></a>#error (referenční dokumentace jazyka C#)
`#error` Umožňuje generovat [CS1029](../compiler-messages/cs1029.md) uživatelem definované chybové z určitého umístění ve vašem kódu. Příklad:  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Poznámky  
 Běžně `#error` v podmíněnou direktivu.  
  
 Je také možné generovat upozornění definované uživatelem s [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).  
  
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

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [C# Direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)
