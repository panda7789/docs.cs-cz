---
title: '#– Direktiva pragma upozornění - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 3b50585e0ae0964cf19379573bd85923daa552f4
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242716"
---
# <a name="pragma-warning-c-reference"></a>#pragma – upozornění (Referenční dokumentace jazyka C#)
`#pragma warning` můžete povolit nebo zakázat určité upozornění.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
#### <a name="parameters"></a>Parametry  
 `warning-list`  
 Čárkou oddělený seznam čísel upozornění. Předpona "CS" je volitelné.  
  
 Pokud nejsou zadány žádné čísla upozornění, `disable` zakazuje všechna upozornění a `restore` povoluje všechna upozornění.  
  
> [!NOTE]
>  V sadě Visual Studio najít čísla upozornění, sestavte projekt a potom vyhledejte čísla upozornění v **výstup** okna.  
  
## <a name="example"></a>Příklad  
  
```csharp
// pragma_warning.cs  
using System;  
  
#pragma warning disable 414, CS3021  
[CLSCompliant(false)]  
public class C  
{  
    int i = 1;  
    static void Main()  
    {  
    }  
}  
#pragma warning restore CS3021  
[CLSCompliant(false)]  // CS3021  
public class D  
{  
    int i = 1;  
    public static void F()  
    {  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [C# Direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)  
- [Chyby kompilátoru jazyka C#](../../../csharp/language-reference/compiler-messages/index.md)
