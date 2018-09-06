---
title: 'Postupy: Použití ukazatelů ke kopírování pole bajtů (Průvodce programováním v C#)'
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 061bbbc4557cb25d39edfb1f6235bb065a5de7bd
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881392"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a><span data-ttu-id="54d02-102">Postupy: Použití ukazatelů ke kopírování pole bajtů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="54d02-102">How to: Use Pointers to Copy an Array of Bytes  (C# Programming Guide)</span></span>

<span data-ttu-id="54d02-103">Následující příklad používá ukazatelů ke kopírování bajtů z jednoho pole do jiného.</span><span class="sxs-lookup"><span data-stu-id="54d02-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="54d02-104">Tento příklad používá [unsafe](../../language-reference/keywords/unsafe.md) – klíčové slovo, které vám umožní použít ukazatele ve `Copy` metody.</span><span class="sxs-lookup"><span data-stu-id="54d02-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="54d02-105">[Oprava](../../language-reference/keywords/fixed-statement.md) prohlášení se používá k deklaraci ukazatele na zdrojové a cílové pole.</span><span class="sxs-lookup"><span data-stu-id="54d02-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="54d02-106">`fixed` Příkaz *PIN kódy* indexy pole zdrojové a cílové umístění v paměti, aby nebude možné přesunout uvolňováním paměti.</span><span class="sxs-lookup"><span data-stu-id="54d02-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="54d02-107">Bloky paměti pro pole nepřipnuté, pokud `fixed` bloku je dokončena.</span><span class="sxs-lookup"><span data-stu-id="54d02-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="54d02-108">Protože `Copy` metoda v tomto příkladu používá `unsafe` – klíčové slovo, se musí být kompilována s [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="54d02-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="54d02-109">V tomto příkladu přistupuje k prvky obou polí pomocí indexů spíše než druhý nespravovaného ukazatele.</span><span class="sxs-lookup"><span data-stu-id="54d02-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="54d02-110">Deklarace `pSource` a `pTarget` připíná ukazatele pole.</span><span class="sxs-lookup"><span data-stu-id="54d02-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="54d02-111">Tato funkce je dostupná, od C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="54d02-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="54d02-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="54d02-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="54d02-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="54d02-113">See Also</span></span>

- [<span data-ttu-id="54d02-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="54d02-114">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="54d02-115">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="54d02-115">Unsafe Code and Pointers</span></span>](index.md)  
- [<span data-ttu-id="54d02-116">-unsafe (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="54d02-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)  
- [<span data-ttu-id="54d02-117">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="54d02-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)  
