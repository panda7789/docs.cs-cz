---
title: Použití ukazatelů ke kopírování pole průvodce C# programováním bajtů
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 4929699c2d1e07b16d4694cff79f9b1394b1de38
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75698453"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a><span data-ttu-id="77d02-102">Použití ukazatelů ke kopírování pole bajtů (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="77d02-102">How to use pointers to copy an array of bytes (C# Programming Guide)</span></span>

<span data-ttu-id="77d02-103">Následující příklad používá ukazatele ke kopírování bajtů z jednoho pole do jiného.</span><span class="sxs-lookup"><span data-stu-id="77d02-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="77d02-104">V tomto příkladu se používá klíčové slovo [unsafe](../../language-reference/keywords/unsafe.md) , které umožňuje použití ukazatelů v metodě `Copy`.</span><span class="sxs-lookup"><span data-stu-id="77d02-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="77d02-105">Příkaz [fixed](../../language-reference/keywords/fixed-statement.md) slouží k deklaraci ukazatelů na zdrojová a cílová pole.</span><span class="sxs-lookup"><span data-stu-id="77d02-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="77d02-106">*Příkaz `fixed`* přiřadí umístění zdrojových a cílových polí v paměti tak, aby se nepřesunuly pomocí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="77d02-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="77d02-107">Bloky paměti pro pole jsou po dokončení bloku `fixed` nepřipnutý.</span><span class="sxs-lookup"><span data-stu-id="77d02-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="77d02-108">Vzhledem k tomu, že metoda `Copy` v tomto příkladu používá klíčové slovo `unsafe`, musí být kompilována s možností kompilátoru [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="77d02-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="77d02-109">Tento příklad přistupuje k prvkům obou polí pomocí indexů místo druhého nespravovaného ukazatele.</span><span class="sxs-lookup"><span data-stu-id="77d02-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="77d02-110">Deklarace `pSource` a ukazatelů `pTarget` přiřadí pole.</span><span class="sxs-lookup"><span data-stu-id="77d02-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="77d02-111">Tato funkce je k dispozici C# od 7,3.</span><span class="sxs-lookup"><span data-stu-id="77d02-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="77d02-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="77d02-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="77d02-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77d02-113">See also</span></span>

- [<span data-ttu-id="77d02-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="77d02-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="77d02-115">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="77d02-115">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="77d02-116">-UNSAFEC# (možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="77d02-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [<span data-ttu-id="77d02-117">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="77d02-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
