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
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="facbb-102">#pragma – upozornění (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="facbb-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="facbb-103">`#pragma warning`povolit nebo zakázat určitá varování.</span><span class="sxs-lookup"><span data-stu-id="facbb-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="facbb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="facbb-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a><span data-ttu-id="facbb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="facbb-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="facbb-106">Seznam výstražných čísel oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="facbb-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="facbb-107">Předpona "CS" je volitelná.</span><span class="sxs-lookup"><span data-stu-id="facbb-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="facbb-108">Pokud nejsou zadána `disable` žádná čísla upozornění, zakáže všechna upozornění a `restore` povolí všechna upozornění.</span><span class="sxs-lookup"><span data-stu-id="facbb-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="facbb-109">Chcete-li najít čísla upozornění v sadě Visual Studio, vytvořte projekt a vyhledejte čísla upozornění v okně **Výstup.**</span><span class="sxs-lookup"><span data-stu-id="facbb-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="facbb-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="facbb-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="facbb-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="facbb-111">See also</span></span>

- [<span data-ttu-id="facbb-112">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="facbb-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="facbb-113">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="facbb-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="facbb-114">Direktivy preprocesoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="facbb-114">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="facbb-115">Chyby kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="facbb-115">C# Compiler Errors</span></span>](../compiler-messages/index.md)
