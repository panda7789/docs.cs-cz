---
title: '#chyba – odkaz jazyka C#'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 28e77304edee617adc1422e6a52d0a617cd9b3bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173403"
---
# <a name="error-c-reference"></a>#error (referenční dokumentace jazyka C#)
`#error`umožňuje generovat chybu definovanou uživatelem [CS1029](../compiler-messages/cs1029.md) z určitého umístění v kódu. Například:  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Poznámky  
 Běžné použití `#error` je v podmíněné směrnice.  
  
 Je také možné generovat uživatelem definované upozornění s [#warning](./preprocessor-warning.md).  
  
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

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [Direktivy preprocesoru jazyka C#](./index.md)
