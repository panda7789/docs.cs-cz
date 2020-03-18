---
title: '#undef - C# Odkaz'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 21923412aa178c3b86e94a54bd911130e48e4deb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712439"
---
# <a name="undef-c-reference"></a><span data-ttu-id="3f7e7-102">#undef (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3f7e7-102">#undef (C# Reference)</span></span>
<span data-ttu-id="3f7e7-103">`#undef`umožňuje zrušit definici symbolu, takže pomocí symbolu jako výrazu v direktivě [#if](./preprocessor-if.md) bude výraz vyhodnocen na `false`.</span><span class="sxs-lookup"><span data-stu-id="3f7e7-103">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](./preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="3f7e7-104">Symbol lze definovat buď pomocí [#define](./preprocessor-define.md) direktivy nebo [-define](../compiler-options/define-compiler-option.md) kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="3f7e7-104">A symbol can be defined either with the [#define](./preprocessor-define.md) directive or the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="3f7e7-105">Směrnice `#undef` musí být uvedeny v souboru před použitím všechny příkazy, které nejsou také direktivy.</span><span class="sxs-lookup"><span data-stu-id="3f7e7-105">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f7e7-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="3f7e7-106">Example</span></span>  

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

<span data-ttu-id="3f7e7-107">**LADĚNÍ není definováno.**</span><span class="sxs-lookup"><span data-stu-id="3f7e7-107">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="3f7e7-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f7e7-108">See also</span></span>

- [<span data-ttu-id="3f7e7-109">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3f7e7-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3f7e7-110">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3f7e7-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3f7e7-111">Direktivy preprocesoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3f7e7-111">C# Preprocessor Directives</span></span>](./index.md)
