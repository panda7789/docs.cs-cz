---
title: '#pragma – upozornění C# – reference'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 5620ea9e5f31c22e26bee95a450335bb179ced25
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712465"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="26670-102">#pragma – upozornění (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="26670-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="26670-103">`#pragma warning` může povolit nebo zakázat určitá upozornění.</span><span class="sxs-lookup"><span data-stu-id="26670-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26670-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26670-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a><span data-ttu-id="26670-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="26670-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="26670-106">Seznam čísel upozornění oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="26670-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="26670-107">Předpona CS je volitelná.</span><span class="sxs-lookup"><span data-stu-id="26670-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="26670-108">Pokud nejsou zadána žádná čísla upozornění, `disable` zakáže všechna upozornění a `restore` povolí všechna upozornění.</span><span class="sxs-lookup"><span data-stu-id="26670-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="26670-109">Chcete-li najít čísla upozornění v aplikaci Visual Studio, sestavte projekt a vyhledejte čísla upozornění v okně **výstup** .</span><span class="sxs-lookup"><span data-stu-id="26670-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26670-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="26670-110">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="26670-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="26670-111">See also</span></span>

- [<span data-ttu-id="26670-112">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="26670-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="26670-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="26670-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="26670-114">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="26670-114">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="26670-115">Chyby kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="26670-115">C# Compiler Errors</span></span>](../compiler-messages/index.md)
