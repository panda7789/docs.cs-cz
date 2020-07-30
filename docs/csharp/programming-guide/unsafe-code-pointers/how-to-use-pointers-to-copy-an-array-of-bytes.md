---
title: Použití ukazatelů ke kopírování pole bajtů – Průvodce programováním v C#
description: Naučte se používat ukazatele na kopírování pole bajtů. Podívejte se na příklad kódu a další dostupné prostředky.
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 70ab1441d25ea69afb2244bd94bd404a3e32838d
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381785"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a><span data-ttu-id="9a96b-104">Použití ukazatelů ke kopírování pole bajtů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="9a96b-104">How to use pointers to copy an array of bytes (C# Programming Guide)</span></span>

<span data-ttu-id="9a96b-105">Následující příklad používá ukazatele ke kopírování bajtů z jednoho pole do jiného.</span><span class="sxs-lookup"><span data-stu-id="9a96b-105">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="9a96b-106">V tomto příkladu se používá klíčové slovo [unsafe](../../language-reference/keywords/unsafe.md) , které umožňuje použití ukazatelů v `Copy` metodě.</span><span class="sxs-lookup"><span data-stu-id="9a96b-106">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="9a96b-107">Příkaz [fixed](../../language-reference/keywords/fixed-statement.md) slouží k deklaraci ukazatelů na zdrojová a cílová pole.</span><span class="sxs-lookup"><span data-stu-id="9a96b-107">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="9a96b-108">Příkaz přiřadí `fixed` umístění zdrojových a cílových polí v paměti tak, aby se nepřesunuly pomocí uvolňování paměti. *pins*</span><span class="sxs-lookup"><span data-stu-id="9a96b-108">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="9a96b-109">Bloky paměti pro pole jsou po `fixed` dokončení bloku odpojeny.</span><span class="sxs-lookup"><span data-stu-id="9a96b-109">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="9a96b-110">Vzhledem k tomu `Copy` , že metoda v tomto příkladu používá `unsafe` klíčové slovo, musí být zkompilována s možností [– nezabezpečený](../../language-reference/compiler-options/unsafe-compiler-option.md) kompilátor.</span><span class="sxs-lookup"><span data-stu-id="9a96b-110">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="9a96b-111">Tento příklad přistupuje k prvkům obou polí pomocí indexů místo druhého nespravovaného ukazatele.</span><span class="sxs-lookup"><span data-stu-id="9a96b-111">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="9a96b-112">Deklarace `pSource` a `pTarget` odkazuje na pole.</span><span class="sxs-lookup"><span data-stu-id="9a96b-112">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="9a96b-113">Tato funkce je k dispozici od jazyka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="9a96b-113">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="9a96b-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="9a96b-114">Example</span></span>

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="9a96b-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a96b-115">See also</span></span>

- [<span data-ttu-id="9a96b-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="9a96b-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9a96b-117">Nezabezpečený kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="9a96b-117">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="9a96b-118">-unsafe (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="9a96b-118">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [<span data-ttu-id="9a96b-119">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="9a96b-119">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
