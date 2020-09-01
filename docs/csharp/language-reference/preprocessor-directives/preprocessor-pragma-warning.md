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
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="ac40c-103">#pragma – upozornění (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ac40c-103">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="ac40c-104">`#pragma warning` může povolit nebo zakázat určitá upozornění.</span><span class="sxs-lookup"><span data-stu-id="ac40c-104">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac40c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac40c-105">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac40c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac40c-106">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="ac40c-107">Seznam čísel upozornění oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="ac40c-107">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="ac40c-108">Předpona CS je volitelná.</span><span class="sxs-lookup"><span data-stu-id="ac40c-108">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="ac40c-109">Pokud nejsou zadaná žádná čísla upozornění, `disable` zakáže všechna upozornění a `restore` povolí všechna upozornění.</span><span class="sxs-lookup"><span data-stu-id="ac40c-109">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ac40c-110">Chcete-li najít čísla upozornění v aplikaci Visual Studio, sestavte projekt a vyhledejte čísla upozornění v okně **výstup** .</span><span class="sxs-lookup"><span data-stu-id="ac40c-110">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac40c-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="ac40c-111">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ac40c-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac40c-112">See also</span></span>

- [<span data-ttu-id="ac40c-113">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ac40c-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ac40c-114">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="ac40c-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ac40c-115">C# – direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="ac40c-115">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="ac40c-116">Chyby kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="ac40c-116">C# Compiler Errors</span></span>](../compiler-messages/index.md)
