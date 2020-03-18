---
title: Použití ukazatelů ke zkopírování pole bajtů – Programovací příručka jazyka C#
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 4929699c2d1e07b16d4694cff79f9b1394b1de38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75698453"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a><span data-ttu-id="53ffe-102">Použití ukazatelů ke zkopírování pole bajtů (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="53ffe-102">How to use pointers to copy an array of bytes (C# Programming Guide)</span></span>

<span data-ttu-id="53ffe-103">Následující příklad používá ukazatele ke kopírování bajtů z jednoho pole do druhého.</span><span class="sxs-lookup"><span data-stu-id="53ffe-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="53ffe-104">Tento příklad používá klíčové slovo [nebezpečné,](../../language-reference/keywords/unsafe.md) které umožňuje `Copy` použít ukazatele v metodě.</span><span class="sxs-lookup"><span data-stu-id="53ffe-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="53ffe-105">Příkaz [fixed](../../language-reference/keywords/fixed-statement.md) se používá k deklarování ukazatelů na zdrojová a cílová pole.</span><span class="sxs-lookup"><span data-stu-id="53ffe-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="53ffe-106">Příkaz `fixed` *připne* umístění zdrojového a cílového pole v paměti, aby nebyla přesunuta systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="53ffe-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="53ffe-107">Bloky paměti pro pole jsou po dokončení `fixed` bloku odepnuty.</span><span class="sxs-lookup"><span data-stu-id="53ffe-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="53ffe-108">Vzhledem `Copy` k tomu, `unsafe` že metoda v tomto příkladu používá klíčové slovo, musí být zkompilován s [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) kompilátoru možnost.</span><span class="sxs-lookup"><span data-stu-id="53ffe-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="53ffe-109">Tento příklad přistupuje k prvkům obou polí pomocí indexů, nikoli druhého nespravovaného ukazatele.</span><span class="sxs-lookup"><span data-stu-id="53ffe-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="53ffe-110">Deklarace `pSource` a `pTarget` ukazatele připne pole.</span><span class="sxs-lookup"><span data-stu-id="53ffe-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="53ffe-111">Tato funkce je k dispozici počínaje C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="53ffe-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="53ffe-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="53ffe-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="53ffe-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="53ffe-113">See also</span></span>

- [<span data-ttu-id="53ffe-114">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="53ffe-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="53ffe-115">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="53ffe-115">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="53ffe-116">-unsafe (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="53ffe-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [<span data-ttu-id="53ffe-117">Kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="53ffe-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
