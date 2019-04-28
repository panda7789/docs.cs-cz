---
title: '#– Direktiva pragma upozornění - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 0145df533572ff9d5004a653bb232a7ff60af5f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61659992"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="d5e29-102">#pragma – upozornění (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d5e29-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="d5e29-103">`#pragma warning` můžete povolit nebo zakázat určité upozornění.</span><span class="sxs-lookup"><span data-stu-id="d5e29-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5e29-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5e29-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5e29-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5e29-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="d5e29-106">Čárkou oddělený seznam čísel upozornění.</span><span class="sxs-lookup"><span data-stu-id="d5e29-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="d5e29-107">Předpona "CS" je volitelné.</span><span class="sxs-lookup"><span data-stu-id="d5e29-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="d5e29-108">Pokud nejsou zadány žádné čísla upozornění, `disable` zakazuje všechna upozornění a `restore` povoluje všechna upozornění.</span><span class="sxs-lookup"><span data-stu-id="d5e29-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5e29-109">V sadě Visual Studio najít čísla upozornění, sestavte projekt a potom vyhledejte čísla upozornění v **výstup** okna.</span><span class="sxs-lookup"><span data-stu-id="d5e29-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5e29-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="d5e29-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d5e29-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5e29-111">See also</span></span>

- [<span data-ttu-id="d5e29-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d5e29-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="d5e29-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d5e29-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d5e29-114">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="d5e29-114">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
- [<span data-ttu-id="d5e29-115">Chyby kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d5e29-115">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)
