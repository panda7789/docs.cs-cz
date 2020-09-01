---
description: '#chyba – Referenční dokumentace jazyka C#'
title: '#chyba – Referenční dokumentace jazyka C#'
ms.date: 08/24/2020
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 76325901c5e39f340545b186a0aa9546cd853ff8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138095"
---
# <a name="error-c-reference"></a><span data-ttu-id="e9bd3-103">#error (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e9bd3-103">#error (C# Reference)</span></span>

<span data-ttu-id="e9bd3-104">`#error` umožňuje generovat [CS1029](../compiler-messages/cs1029.md) uživatelem definované chyby z konkrétního umístění v kódu.</span><span class="sxs-lookup"><span data-stu-id="e9bd3-104">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="e9bd3-105">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e9bd3-105">For example:</span></span>

```csharp
#error Deprecated code in this method.
```

> [!NOTE]
> <span data-ttu-id="e9bd3-106">Kompilátor zpracovává `#error version` speciální způsob a hlásí chybu kompilátoru CS8304 se zprávou obsahující použitou kompilátor a jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="e9bd3-106">The compiler treats `#error version` in a special way and reports a compiler error, CS8304, with a message containing the used compiler and language versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="e9bd3-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e9bd3-107">Remarks</span></span>

<span data-ttu-id="e9bd3-108">Běžné použití `#error` je v podmíněných direktivách.</span><span class="sxs-lookup"><span data-stu-id="e9bd3-108">A common use of `#error` is in a conditional directive.</span></span>

<span data-ttu-id="e9bd3-109">Je také možné vygenerovat upozornění definované uživatelem pomocí [#warning](./preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="e9bd3-109">It is also possible to generate a user-defined warning with [#warning](./preprocessor-warning.md).</span></span>

## <a name="example"></a><span data-ttu-id="e9bd3-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="e9bd3-110">Example</span></span>

```csharp
// preprocessor_error.cs
// CS1029 expected
#define DEBUG
class MainClass
{
    static void Main()
    {
#if DEBUG
#error DEBUG is defined
#endif
    }
}
```

## <a name="see-also"></a><span data-ttu-id="e9bd3-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9bd3-111">See also</span></span>

- [<span data-ttu-id="e9bd3-112">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e9bd3-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e9bd3-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="e9bd3-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e9bd3-114">C# – direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="e9bd3-114">C# Preprocessor Directives</span></span>](./index.md)
