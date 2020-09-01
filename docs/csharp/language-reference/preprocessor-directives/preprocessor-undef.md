---
description: '#undef – Referenční dokumentace jazyka C#'
title: '#undef – Referenční dokumentace jazyka C#'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 97f99ab4230585e61fed0e057552b78c7a4c2bb5
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137861"
---
# <a name="undef-c-reference"></a><span data-ttu-id="e9c0a-103">#undef (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e9c0a-103">#undef (C# Reference)</span></span>
<span data-ttu-id="e9c0a-104">`#undef` umožňuje zrušit definici symbolu, například pomocí symbolu jako výrazu v direktivě [#if](./preprocessor-if.md) . výraz se vyhodnotí jako `false` .</span><span class="sxs-lookup"><span data-stu-id="e9c0a-104">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](./preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="e9c0a-105">Symbol lze definovat buď pomocí direktivy [#define](./preprocessor-define.md) , nebo pomocí možnosti kompilátoru [-define](../compiler-options/define-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="e9c0a-105">A symbol can be defined either with the [#define](./preprocessor-define.md) directive or the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="e9c0a-106">`#undef`Direktiva musí být uvedena v souboru předtím, než použijete příkazy, které nejsou zároveň direktivami.</span><span class="sxs-lookup"><span data-stu-id="e9c0a-106">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9c0a-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="e9c0a-107">Example</span></span>  

```csharp
// preprocessor_undef.cs  
// compile with: /d:DEBUG  
#undef DEBUG  
using System;  
class MyClass
{  
    static void Main()
    {  
#if DEBUG  
        Console.WriteLine("DEBUG is defined");  
#else  
        Console.WriteLine("DEBUG is not defined");  
#endif  
    }  
}  
```

<span data-ttu-id="e9c0a-108">**LADĚNÍ není definováno.**</span><span class="sxs-lookup"><span data-stu-id="e9c0a-108">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="e9c0a-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9c0a-109">See also</span></span>

- [<span data-ttu-id="e9c0a-110">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e9c0a-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e9c0a-111">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="e9c0a-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e9c0a-112">C# – direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="e9c0a-112">C# Preprocessor Directives</span></span>](./index.md)
