---
title: '#undef – C# odkaz'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: fdf22e90be766e87e823a7f8cc27ea00c17d2bb5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605586"
---
# <a name="undef-c-reference"></a><span data-ttu-id="f0998-102">#undef (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f0998-102">#undef (C# Reference)</span></span>
<span data-ttu-id="f0998-103">`#undef`umožňuje zrušit definici symbolu, například pomocí symbolu jako výrazu v direktivě [#if](./preprocessor-if.md) `false`. výraz se vyhodnotí jako.</span><span class="sxs-lookup"><span data-stu-id="f0998-103">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](./preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="f0998-104">Symbol lze definovat buď pomocí direktivy [#define](./preprocessor-define.md) , nebo pomocí možnosti kompilátoru [-define](../compiler-options/define-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="f0998-104">A symbol can be defined either with the [#define](./preprocessor-define.md) directive or the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="f0998-105">`#undef` Direktiva musí být uvedena v souboru předtím, než použijete příkazy, které nejsou zároveň direktivami.</span><span class="sxs-lookup"><span data-stu-id="f0998-105">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0998-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="f0998-106">Example</span></span>  

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

<span data-ttu-id="f0998-107">**LADĚNÍ není definováno.**</span><span class="sxs-lookup"><span data-stu-id="f0998-107">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="f0998-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f0998-108">See also</span></span>

- [<span data-ttu-id="f0998-109">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="f0998-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f0998-110">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f0998-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f0998-111">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="f0998-111">C# Preprocessor Directives</span></span>](./index.md)
