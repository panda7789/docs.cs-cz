---
title: '#pragma varování - C# Reference'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 5620ea9e5f31c22e26bee95a450335bb179ced25
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712465"
---
# <a name="pragma-warning-c-reference"></a>#pragma – upozornění (Referenční dokumentace jazyka C#)
`#pragma warning`povolit nebo zakázat určitá varování.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a>Parametry  
 `warning-list`  
 Seznam výstražných čísel oddělených čárkami. Předpona "CS" je volitelná.  
  
 Pokud nejsou zadána `disable` žádná čísla upozornění, zakáže všechna upozornění a `restore` povolí všechna upozornění.  
  
> [!NOTE]
> Chcete-li najít čísla upozornění v sadě Visual Studio, vytvořte projekt a vyhledejte čísla upozornění v okně **Výstup.**  
  
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

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [Direktivy preprocesoru jazyka C#](./index.md)
- [Chyby kompilátoru jazyka C#](../compiler-messages/index.md)
