---
title: '#– Direktiva pragma upozornění (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 079045f4eb52f03afa8733620029396d80cb75fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273654"
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
 Seznam upozornění čísel oddělených čárkami. Předpona "CS" je volitelné.  
  
 Pokud nejsou zadány žádné upozornění čísla, `disable` zakáže všechna upozornění a `restore` umožňuje všech upozornění.  
  
> [!NOTE]
>  Zjištění čísel upozornění v sadě Visual Studio, sestavení projektu a potom vyhledejte čísla upozornění v **výstup** okno.  
  
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
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [C# Direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [Chyby kompilátoru jazyka C#](../../../csharp/language-reference/compiler-messages/index.md)
