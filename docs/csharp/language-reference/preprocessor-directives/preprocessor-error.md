---
title: '#Chyba – C# referenční informace'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: f18dbd007e80397b815256231a1d56e5ca50010e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608555"
---
# <a name="error-c-reference"></a>#error (referenční dokumentace jazyka C#)
`#error`umožňuje generovat [CS1029](../compiler-messages/cs1029.md) uživatelem definované chyby z konkrétního umístění v kódu. Příklad:  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Poznámky  
 Běžné použití `#error` je v podmíněných direktivách.  
  
 Je také možné vygenerovat upozornění definované uživatelem pomocí [#warning](./preprocessor-warning.md).  
  
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
  
## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [C# Direktivy preprocesoru](./index.md)
