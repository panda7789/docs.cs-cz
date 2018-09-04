---
title: '#upozornění (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 59ca63d5089e377627a9116f24f9a0a1681bb4b2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506344"
---
# <a name="warning-c-reference"></a>#warning (referenční dokumentace jazyka C#)
`#warning` Umožňuje generovat [CS1030](../../misc/cs1030.md) úroveň jedno upozornění kompilátoru z určitého umístění ve vašem kódu. Příklad:  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Poznámky
 Běžně `#warning` v podmíněnou direktivu. Je také možné vytvořit uživatelem definované chybové s [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).  
  
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

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [C# Direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)
