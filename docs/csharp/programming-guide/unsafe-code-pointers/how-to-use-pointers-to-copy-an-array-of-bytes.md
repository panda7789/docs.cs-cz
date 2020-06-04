---
title: Použití ukazatelů ke kopírování pole bajtů – Průvodce programováním v C#
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 8c1afc06fb567a923d604ad53dc26f94178a8d60
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397412"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a><span data-ttu-id="f4b05-102">Použití ukazatelů ke kopírování pole bajtů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="f4b05-102">How to use pointers to copy an array of bytes (C# Programming Guide)</span></span>

<span data-ttu-id="f4b05-103">Následující příklad používá ukazatele ke kopírování bajtů z jednoho pole do jiného.</span><span class="sxs-lookup"><span data-stu-id="f4b05-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="f4b05-104">V tomto příkladu se používá klíčové slovo [unsafe](../../language-reference/keywords/unsafe.md) , které umožňuje použití ukazatelů v `Copy` metodě.</span><span class="sxs-lookup"><span data-stu-id="f4b05-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="f4b05-105">Příkaz [fixed](../../language-reference/keywords/fixed-statement.md) slouží k deklaraci ukazatelů na zdrojová a cílová pole.</span><span class="sxs-lookup"><span data-stu-id="f4b05-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="f4b05-106">Příkaz přiřadí `fixed` umístění zdrojových a cílových polí v paměti tak, aby se nepřesunuly pomocí uvolňování paměti. *pins*</span><span class="sxs-lookup"><span data-stu-id="f4b05-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="f4b05-107">Bloky paměti pro pole jsou po `fixed` dokončení bloku odpojeny.</span><span class="sxs-lookup"><span data-stu-id="f4b05-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="f4b05-108">Vzhledem k tomu `Copy` , že metoda v tomto příkladu používá `unsafe` klíčové slovo, musí být zkompilována s možností [– nezabezpečený](../../language-reference/compiler-options/unsafe-compiler-option.md) kompilátor.</span><span class="sxs-lookup"><span data-stu-id="f4b05-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="f4b05-109">Tento příklad přistupuje k prvkům obou polí pomocí indexů místo druhého nespravovaného ukazatele.</span><span class="sxs-lookup"><span data-stu-id="f4b05-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="f4b05-110">Deklarace `pSource` a `pTarget` odkazuje na pole.</span><span class="sxs-lookup"><span data-stu-id="f4b05-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="f4b05-111">Tato funkce je k dispozici od jazyka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="f4b05-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="f4b05-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="f4b05-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="f4b05-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4b05-113">See also</span></span>

- [<span data-ttu-id="f4b05-114">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="f4b05-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f4b05-115">Nezabezpečený kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="f4b05-115">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="f4b05-116">-unsafe (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="f4b05-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [<span data-ttu-id="f4b05-117">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="f4b05-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
