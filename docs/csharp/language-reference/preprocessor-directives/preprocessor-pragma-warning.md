---
title: '#– Direktiva pragma upozornění (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 89ff8151d55ac58a1b114f7727297704ce26b9a7
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43873689"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="b9ce2-102">#pragma – upozornění (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b9ce2-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="b9ce2-103">`#pragma warning` můžete povolit nebo zakázat určité upozornění.</span><span class="sxs-lookup"><span data-stu-id="b9ce2-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9ce2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9ce2-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9ce2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b9ce2-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="b9ce2-106">Čárkou oddělený seznam čísel upozornění.</span><span class="sxs-lookup"><span data-stu-id="b9ce2-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="b9ce2-107">Předpona "CS" je volitelné.</span><span class="sxs-lookup"><span data-stu-id="b9ce2-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="b9ce2-108">Pokud nejsou zadány žádné čísla upozornění, `disable` zakazuje všechna upozornění a `restore` povoluje všechna upozornění.</span><span class="sxs-lookup"><span data-stu-id="b9ce2-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9ce2-109">V sadě Visual Studio najít čísla upozornění, sestavte projekt a potom vyhledejte čísla upozornění v **výstup** okna.</span><span class="sxs-lookup"><span data-stu-id="b9ce2-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9ce2-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="b9ce2-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b9ce2-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9ce2-111">See Also</span></span>

- [<span data-ttu-id="b9ce2-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b9ce2-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="b9ce2-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b9ce2-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b9ce2-114">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="b9ce2-114">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
- [<span data-ttu-id="b9ce2-115">Chyby kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b9ce2-115">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)
