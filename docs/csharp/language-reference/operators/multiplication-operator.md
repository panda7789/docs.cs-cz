---
title: '* Operator - C# odkaz'
ms.custom: seodec18
ms.date: 04/04/2018
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: f4490c4632d9344eb879ea55c20787b838781d91
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333730"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c9c39-102">\* – operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="c9c39-102">\* operator (C# Reference)</span></span>

<span data-ttu-id="c9c39-103">Operátor násobení (`*`) vypočítá součin z operandů.</span><span class="sxs-lookup"><span data-stu-id="c9c39-103">The multiplication operator (`*`) computes the product of its operands.</span></span> <span data-ttu-id="c9c39-104">Všechny číselné typy obsahuje předdefinované operátory násobení.</span><span class="sxs-lookup"><span data-stu-id="c9c39-104">All numeric types have predefined multiplication operators.</span></span>

<span data-ttu-id="c9c39-105">`*` slouží také jako operátor zrušení odkazu, který umožňuje čtení a zápis na ukazatel.</span><span class="sxs-lookup"><span data-stu-id="c9c39-105">`*` also serves as the dereference operator, which allows reading and writing to a pointer.</span></span>

## <a name="remarks"></a><span data-ttu-id="c9c39-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c9c39-106">Remarks</span></span>

<span data-ttu-id="c9c39-107">`*` Operátor se používá také, chcete-li deklarovat typy ukazatelů a ke zrušení ukazatele.</span><span class="sxs-lookup"><span data-stu-id="c9c39-107">The `*` operator is also used to declare pointer types and to dereference pointers.</span></span> <span data-ttu-id="c9c39-108">Tento operátor jde použít jenom v kontextu unsafe, udávají použití [nebezpečné](../keywords/unsafe.md) – klíčové slovo která vyžaduje [/ unsafe](../compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="c9c39-108">This operator can only be used in unsafe contexts, denoted by the use of the [unsafe](../keywords/unsafe.md) keyword, and requiring the [/unsafe](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span>  <span data-ttu-id="c9c39-109">Operátor zrušení odkazu se také označuje jako operátor dereference.</span><span class="sxs-lookup"><span data-stu-id="c9c39-109">The dereference operator is also known as the indirection operator.</span></span>

<span data-ttu-id="c9c39-110">Uživatelem definované typy mohou přetížit binárního souboru `*` – operátor (viz [operátor](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="c9c39-110">User-defined types can overload the binary `*` operator (see [operator](../keywords/operator.md)).</span></span> <span data-ttu-id="c9c39-111">Při je binární operátor přetížen, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="c9c39-111">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>

## <a name="example"></a><span data-ttu-id="c9c39-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="c9c39-112">Example</span></span>

[!code-csharp-interactive[csRefOperators#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#50)]

## <a name="example"></a><span data-ttu-id="c9c39-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="c9c39-113">Example</span></span>

[!code-csharp[csRefOperators#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#51)]

## <a name="see-also"></a><span data-ttu-id="c9c39-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9c39-114">See also</span></span>

- [<span data-ttu-id="c9c39-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c9c39-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c9c39-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c9c39-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c9c39-117">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="c9c39-117">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="c9c39-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c9c39-118">C# Operators</span></span>](index.md)