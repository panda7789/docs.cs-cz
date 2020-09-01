---
description: '#pragma – upozornění – reference jazyka C#'
title: '#pragma – upozornění – reference jazyka C#'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 3085c21db386ca215d48bbe8ade83cd26732242c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137965"
---
# <a name="pragma-warning-c-reference"></a>#pragma – upozornění (Referenční dokumentace jazyka C#)
`#pragma warning` může povolit nebo zakázat určitá upozornění.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a>Parametry  
 `warning-list`  
 Seznam čísel upozornění oddělených čárkami. Předpona CS je volitelná.  
  
 Pokud nejsou zadaná žádná čísla upozornění, `disable` zakáže všechna upozornění a `restore` povolí všechna upozornění.  
  
> [!NOTE]
> Chcete-li najít čísla upozornění v aplikaci Visual Studio, sestavte projekt a vyhledejte čísla upozornění v okně **výstup** .  
  
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

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [C# – direktivy preprocesoru](./index.md)
- [Chyby kompilátoru C#](../compiler-messages/index.md)
