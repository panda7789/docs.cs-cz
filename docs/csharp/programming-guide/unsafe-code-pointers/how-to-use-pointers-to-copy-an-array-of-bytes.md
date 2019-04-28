---
title: 'Postupy: Použití ukazatelů ke kopírování pole bajtů - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: d174f51fa1709a70b98473a4dbbad89b9c62c22a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61708909"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a><span data-ttu-id="0fb99-102">Postupy: Použití ukazatelů ke kopírování pole bajtů (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="0fb99-102">How to: Use Pointers to Copy an Array of Bytes  (C# Programming Guide)</span></span>

<span data-ttu-id="0fb99-103">Následující příklad používá ukazatelů ke kopírování bajtů z jednoho pole do jiného.</span><span class="sxs-lookup"><span data-stu-id="0fb99-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="0fb99-104">Tento příklad používá [unsafe](../../language-reference/keywords/unsafe.md) – klíčové slovo, které vám umožní použít ukazatele ve `Copy` metody.</span><span class="sxs-lookup"><span data-stu-id="0fb99-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="0fb99-105">[Oprava](../../language-reference/keywords/fixed-statement.md) prohlášení se používá k deklaraci ukazatele na zdrojové a cílové pole.</span><span class="sxs-lookup"><span data-stu-id="0fb99-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="0fb99-106">`fixed` Příkaz *PIN kódy* indexy pole zdrojové a cílové umístění v paměti, aby nebude možné přesunout uvolňováním paměti.</span><span class="sxs-lookup"><span data-stu-id="0fb99-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="0fb99-107">Bloky paměti pro pole nepřipnuté, pokud `fixed` bloku je dokončena.</span><span class="sxs-lookup"><span data-stu-id="0fb99-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="0fb99-108">Protože `Copy` metoda v tomto příkladu používá `unsafe` – klíčové slovo, se musí být kompilována s [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="0fb99-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="0fb99-109">V tomto příkladu přistupuje k prvky obou polí pomocí indexů spíše než druhý nespravovaného ukazatele.</span><span class="sxs-lookup"><span data-stu-id="0fb99-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="0fb99-110">Deklarace `pSource` a `pTarget` připíná ukazatele pole.</span><span class="sxs-lookup"><span data-stu-id="0fb99-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="0fb99-111">Tato funkce je dostupná, od C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="0fb99-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="0fb99-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="0fb99-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="0fb99-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0fb99-113">See also</span></span>

- [<span data-ttu-id="0fb99-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0fb99-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0fb99-115">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="0fb99-115">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="0fb99-116">-unsafe (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="0fb99-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [<span data-ttu-id="0fb99-117">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="0fb99-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
