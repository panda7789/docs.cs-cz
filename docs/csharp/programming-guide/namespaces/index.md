---
title: Obory názvů – Průvodce programováním v C#
description: Přečtěte si o oborech názvů v programování v jazyce C#. Podívejte se na Přehled vlastností oboru názvů a Prohlédněte si další zdroje informací.
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: fca2c641520bd9cd19a48bff2119a6f09c3713ea
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382097"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="e3b92-104">Obory názvů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="e3b92-104">Namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="e3b92-105">Obory názvů se silně využívají v programování v jazyce C# dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="e3b92-105">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="e3b92-106">Rozhraní .NET nejprve používá obory názvů k uspořádání svých mnoha tříd, a to takto:</span><span class="sxs-lookup"><span data-stu-id="e3b92-106">First, .NET uses namespaces to organize its many classes, as follows:</span></span>  

[!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]

<span data-ttu-id="e3b92-107"><xref:System>je obor názvů a <xref:System.Console> je třída v tomto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e3b92-107"><xref:System> is a namespace and <xref:System.Console> is a class in that namespace.</span></span> <span data-ttu-id="e3b92-108">`using`Klíčové slovo lze použít, aby nebylo vyžadováno celé jméno, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e3b92-108">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]

<span data-ttu-id="e3b92-109">Další informace naleznete v [direktivě using](../../language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="e3b92-109">For more information, see the [using Directive](../../language-reference/keywords/using-directive.md).</span></span>

<span data-ttu-id="e3b92-110">Za druhé deklarujete vlastní obory názvů, které vám pomohou řídit obor názvů tříd a metod ve větších programovacích projektech.</span><span class="sxs-lookup"><span data-stu-id="e3b92-110">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="e3b92-111">Použijte klíčové slovo [Namespace](../../language-reference/keywords/namespace.md) k deklarování oboru názvů, jak je uvedeno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e3b92-111">Use the [namespace](../../language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>

[!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

<span data-ttu-id="e3b92-112">Název oboru názvů musí být platný [název identifikátoru](../inside-a-program/identifier-names.md)C#.</span><span class="sxs-lookup"><span data-stu-id="e3b92-112">The name of the namespace must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span>

## <a name="namespaces-overview"></a><span data-ttu-id="e3b92-113">Přehled oborů názvů</span><span class="sxs-lookup"><span data-stu-id="e3b92-113">Namespaces overview</span></span>

<span data-ttu-id="e3b92-114">Obory názvů mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="e3b92-114">Namespaces have the following properties:</span></span>

- <span data-ttu-id="e3b92-115">Organizují velké projekty kódu.</span><span class="sxs-lookup"><span data-stu-id="e3b92-115">They organize large code projects.</span></span>
- <span data-ttu-id="e3b92-116">Jsou odděleny pomocí `.` operátoru.</span><span class="sxs-lookup"><span data-stu-id="e3b92-116">They are delimited by using the `.` operator.</span></span>
- <span data-ttu-id="e3b92-117">`using`Direktiva obviates požadavek na zadání názvu oboru názvů pro každou třídu.</span><span class="sxs-lookup"><span data-stu-id="e3b92-117">The `using` directive obviates the requirement to specify the name of the namespace for every class.</span></span>
- <span data-ttu-id="e3b92-118">`global`Obor názvů je "kořenový" obor názvů: `global::System` bude vždycky odkazovat na <xref:System> obor názvů .NET.</span><span class="sxs-lookup"><span data-stu-id="e3b92-118">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET <xref:System> namespace.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e3b92-119">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e3b92-119">C# language specification</span></span>

<span data-ttu-id="e3b92-120">Další informace najdete v části [obory názvů](~/_csharplang/spec/namespaces.md) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="e3b92-120">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e3b92-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3b92-121">See also</span></span>

- [<span data-ttu-id="e3b92-122">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="e3b92-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e3b92-123">Používání oborů názvů</span><span class="sxs-lookup"><span data-stu-id="e3b92-123">Using Namespaces</span></span>](using-namespaces.md)
- [<span data-ttu-id="e3b92-124">Jak používat obor názvů My</span><span class="sxs-lookup"><span data-stu-id="e3b92-124">How to use the My namespace</span></span>](how-to-use-the-my-namespace.md)
- [<span data-ttu-id="e3b92-125">Názvy identifikátorů</span><span class="sxs-lookup"><span data-stu-id="e3b92-125">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="e3b92-126">using – direktiva</span><span class="sxs-lookup"><span data-stu-id="e3b92-126">using Directive</span></span>](../../language-reference/keywords/using-directive.md)
- [<span data-ttu-id="e3b92-127">:: – Operátor</span><span class="sxs-lookup"><span data-stu-id="e3b92-127">:: Operator</span></span>](../../language-reference/operators/namespace-alias-qualifier.md)
