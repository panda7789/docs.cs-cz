---
title: "#– Direktiva pragma upozornění (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5330b448dc2b328992b2d29699557d20df56dee4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="b6a28-102">#pragma – upozornění (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b6a28-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="b6a28-103">`#pragma warning`můžete povolit nebo zakázat určité upozornění.</span><span class="sxs-lookup"><span data-stu-id="b6a28-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6a28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6a28-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6a28-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6a28-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="b6a28-106">Seznam upozornění čísel oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="b6a28-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="b6a28-107">Předpona "CS" je volitelné.</span><span class="sxs-lookup"><span data-stu-id="b6a28-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="b6a28-108">Pokud nejsou zadány žádné upozornění čísla, `disable` zakáže všechna upozornění a `restore` umožňuje všech upozornění.</span><span class="sxs-lookup"><span data-stu-id="b6a28-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6a28-109">Zjištění čísel upozornění v sadě Visual Studio, sestavení projektu a potom vyhledejte čísla upozornění v **výstup** okno.</span><span class="sxs-lookup"><span data-stu-id="b6a28-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6a28-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="b6a28-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b6a28-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6a28-111">See Also</span></span>  
 [<span data-ttu-id="b6a28-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b6a28-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b6a28-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="b6a28-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b6a28-114">C# direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="b6a28-114">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [<span data-ttu-id="b6a28-115">Chyby kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b6a28-115">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)
