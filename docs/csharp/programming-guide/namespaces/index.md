---
title: Obory názvů – programovací příručka jazyka C#
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 21452e259596c9ab10b3d653ec1d8fb90fad131d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75937617"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="9f8c5-102">Obory názvů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="9f8c5-102">Namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="9f8c5-103">Obory názvů jsou v programování jazyka C# silně používány dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="9f8c5-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="9f8c5-104">Nejprve rozhraní .NET používá obory názvů k uspořádání mnoha tříd takto:</span><span class="sxs-lookup"><span data-stu-id="9f8c5-104">First, .NET uses namespaces to organize its many classes, as follows:</span></span>  

[!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]

<span data-ttu-id="9f8c5-105"><xref:System>je obor názvů <xref:System.Console> a je třídou v tomto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9f8c5-105"><xref:System> is a namespace and <xref:System.Console> is a class in that namespace.</span></span> <span data-ttu-id="9f8c5-106">Klíčové `using` slovo lze použít tak, aby není vyžadován oúplný název, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9f8c5-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]

<span data-ttu-id="9f8c5-107">Další informace naleznete v [směrnici o používání .](../../language-reference/keywords/using-directive.md)</span><span class="sxs-lookup"><span data-stu-id="9f8c5-107">For more information, see the [using Directive](../../language-reference/keywords/using-directive.md).</span></span>

<span data-ttu-id="9f8c5-108">Za druhé deklarování vlastní chodů názvů vám může pomoci řídit rozsah názvů tříd a metod ve větších programovacích projektech.</span><span class="sxs-lookup"><span data-stu-id="9f8c5-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="9f8c5-109">Pomocí klíčového slova [oboru názvů](../../language-reference/keywords/namespace.md) deklarujte obor názvů, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9f8c5-109">Use the [namespace](../../language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>

[!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

<span data-ttu-id="9f8c5-110">Název oboru názvů musí být platný [název identifikátoru](../inside-a-program/identifier-names.md)jazyka C# .</span><span class="sxs-lookup"><span data-stu-id="9f8c5-110">The name of the namespace must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span>

## <a name="namespaces-overview"></a><span data-ttu-id="9f8c5-111">Obory názvů – přehled</span><span class="sxs-lookup"><span data-stu-id="9f8c5-111">Namespaces overview</span></span>

<span data-ttu-id="9f8c5-112">Obory názvů mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="9f8c5-112">Namespaces have the following properties:</span></span>

- <span data-ttu-id="9f8c5-113">Organizují velké projekty kódu.</span><span class="sxs-lookup"><span data-stu-id="9f8c5-113">They organize large code projects.</span></span>
- <span data-ttu-id="9f8c5-114">Jsou vymezeny pomocí `.` operátoru.</span><span class="sxs-lookup"><span data-stu-id="9f8c5-114">They are delimited by using the `.` operator.</span></span>
- <span data-ttu-id="9f8c5-115">Směrnice `using` odstraňuje požadavek zadat název oboru názvů pro každou třídu.</span><span class="sxs-lookup"><span data-stu-id="9f8c5-115">The `using` directive obviates the requirement to specify the name of the namespace for every class.</span></span>
- <span data-ttu-id="9f8c5-116">Obor `global` názvů je "kořenový" `global::System` obor názvů: bude <xref:System> vždy odkazovat na obor názvů .NET.</span><span class="sxs-lookup"><span data-stu-id="9f8c5-116">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET <xref:System> namespace.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9f8c5-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9f8c5-117">C# language specification</span></span>

<span data-ttu-id="9f8c5-118">Další informace naleznete v části [Namespaces](~/_csharplang/spec/namespaces.md) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="9f8c5-118">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9f8c5-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f8c5-119">See also</span></span>

- [<span data-ttu-id="9f8c5-120">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9f8c5-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9f8c5-121">Použití oborů názvů</span><span class="sxs-lookup"><span data-stu-id="9f8c5-121">Using Namespaces</span></span>](using-namespaces.md)
- [<span data-ttu-id="9f8c5-122">Jak používat obor názvů My</span><span class="sxs-lookup"><span data-stu-id="9f8c5-122">How to use the My namespace</span></span>](how-to-use-the-my-namespace.md)
- [<span data-ttu-id="9f8c5-123">Názvy identifikátorů</span><span class="sxs-lookup"><span data-stu-id="9f8c5-123">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="9f8c5-124">using – direktiva</span><span class="sxs-lookup"><span data-stu-id="9f8c5-124">using Directive</span></span>](../../language-reference/keywords/using-directive.md)
- [<span data-ttu-id="9f8c5-125">:: Operátor</span><span class="sxs-lookup"><span data-stu-id="9f8c5-125">:: Operator</span></span>](../../language-reference/operators/namespace-alias-qualifier.md)
