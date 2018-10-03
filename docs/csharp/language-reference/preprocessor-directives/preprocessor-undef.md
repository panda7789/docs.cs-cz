---
title: '#undef (referenční dokumentace jazyka C#)'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 3957d58f61e51fab01618f5e1146be9cd0da58fd
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48034581"
---
# <a name="undef-c-reference"></a><span data-ttu-id="51246-102">#undef (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="51246-102">#undef (C# Reference)</span></span>
<span data-ttu-id="51246-103">`#undef` můžete nedefinovat symbol, tak, že při použití symbolu jako výraz v [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) direktiv, bude výraz vyhodnocen na `false`.</span><span class="sxs-lookup"><span data-stu-id="51246-103">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="51246-104">Symbol může být definována buď [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) – direktiva nebo [-definovat](../../../csharp/language-reference/compiler-options/define-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="51246-104">A symbol can be defined either with the [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) directive or the [-define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="51246-105">`#undef` Direktiva musí být uvedená v souboru, než použijete všechny příkazy, které nejsou také direktivy.</span><span class="sxs-lookup"><span data-stu-id="51246-105">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51246-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="51246-106">Example</span></span>  

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

<span data-ttu-id="51246-107">**LADĚNÍ není definován.**</span><span class="sxs-lookup"><span data-stu-id="51246-107">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="51246-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="51246-108">See Also</span></span>

- [<span data-ttu-id="51246-109">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="51246-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="51246-110">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="51246-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="51246-111">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="51246-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
