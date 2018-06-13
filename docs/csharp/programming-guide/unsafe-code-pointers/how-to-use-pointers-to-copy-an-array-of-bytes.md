---
title: 'Postupy: Použití ukazatelů ke kopírování pole bajtů (Průvodce programováním v C#)'
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 800a600f0fa7ca52d0433c8d90039434bf6b7f19
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331198"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a><span data-ttu-id="0d3b2-102">Postupy: Použití ukazatelů ke kopírování pole bajtů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="0d3b2-102">How to: Use Pointers to Copy an Array of Bytes  (C# Programming Guide)</span></span>

<span data-ttu-id="0d3b2-103">Následující příklad používá ukazatele kopírování bajtů z jednoho pole do jiné.</span><span class="sxs-lookup"><span data-stu-id="0d3b2-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="0d3b2-104">Tento příklad používá [unsafe](../../language-reference/keywords/unsafe.md) – klíčové slovo, které vám umožní použít ukazatele v `Copy` metoda.</span><span class="sxs-lookup"><span data-stu-id="0d3b2-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="0d3b2-105">[Pevné](../../language-reference/keywords/fixed-statement.md) příkaz se používá k deklaraci ukazatele na zdrojové a cílové pole.</span><span class="sxs-lookup"><span data-stu-id="0d3b2-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="0d3b2-106">`fixed` Příkaz *PIN* umístění zdrojové a cílové maticových v paměti, aby nebude možné přesunout podle uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0d3b2-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="0d3b2-107">Bloky paměti pro pole jsou Odepnout, kdy `fixed` blok dokončení.</span><span class="sxs-lookup"><span data-stu-id="0d3b2-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="0d3b2-108">Protože `Copy` metoda v tomto příkladu používá `unsafe` – klíčové slovo, se musí být zkompilovány s [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="0d3b2-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="0d3b2-109">Tento příklad používá elementy obou polí pomocí indexů spíše než druhý nespravovaný ukazatel.</span><span class="sxs-lookup"><span data-stu-id="0d3b2-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="0d3b2-110">Prohlášení o `pSource` a `pTarget` ukazatele PIN kódy pole.</span><span class="sxs-lookup"><span data-stu-id="0d3b2-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="0d3b2-111">Tato funkce je k dispozici počínaje 7.3 C#.</span><span class="sxs-lookup"><span data-stu-id="0d3b2-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="0d3b2-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="0d3b2-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="0d3b2-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d3b2-113">See Also</span></span>
 [<span data-ttu-id="0d3b2-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0d3b2-114">C# Programming Guide</span></span>](../index.md)  
 [<span data-ttu-id="0d3b2-115">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="0d3b2-115">Unsafe Code and Pointers</span></span>](index.md)  
 [<span data-ttu-id="0d3b2-116">-unsafe (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="0d3b2-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)  
 [<span data-ttu-id="0d3b2-117">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="0d3b2-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)  
