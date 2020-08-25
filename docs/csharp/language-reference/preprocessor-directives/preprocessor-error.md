---
title: '#chyba – Referenční dokumentace jazyka C#'
ms.date: 08/24/2020
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: cc1e0640886e3f3c1c74a54f64961a56c8b030e4
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812364"
---
# <a name="error-c-reference"></a><span data-ttu-id="81279-102">#error (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="81279-102">#error (C# Reference)</span></span>

<span data-ttu-id="81279-103">`#error` umožňuje generovat [CS1029](../compiler-messages/cs1029.md) uživatelem definované chyby z konkrétního umístění v kódu.</span><span class="sxs-lookup"><span data-stu-id="81279-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="81279-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="81279-104">For example:</span></span>

```csharp
#error Deprecated code in this method.
```

> [!NOTE]
> <span data-ttu-id="81279-105">Kompilátor zpracovává `#error version` speciální způsob a hlásí chybu kompilátoru CS8304 se zprávou obsahující použitou kompilátor a jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="81279-105">The compiler treats `#error version` in a special way and reports a compiler error, CS8304, with a message containing the used compiler and language versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="81279-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81279-106">Remarks</span></span>

<span data-ttu-id="81279-107">Běžné použití `#error` je v podmíněných direktivách.</span><span class="sxs-lookup"><span data-stu-id="81279-107">A common use of `#error` is in a conditional directive.</span></span>

<span data-ttu-id="81279-108">Je také možné vygenerovat upozornění definované uživatelem pomocí [#warning](./preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="81279-108">It is also possible to generate a user-defined warning with [#warning](./preprocessor-warning.md).</span></span>

## <a name="example"></a><span data-ttu-id="81279-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="81279-109">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="81279-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="81279-110">See also</span></span>

- [<span data-ttu-id="81279-111">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="81279-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="81279-112">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="81279-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="81279-113">C# – direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="81279-113">C# Preprocessor Directives</span></span>](./index.md)
