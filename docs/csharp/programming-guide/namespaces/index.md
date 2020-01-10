---
title: Obory C# názvů – Průvodce programováním
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: e3e9dc22186e5e319c63e34bd85e5e317effde88
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712010"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="df39b-102">Obory názvů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="df39b-102">Namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="df39b-103">Obory názvů jsou v C# programování silně používány dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="df39b-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="df39b-104">Nejprve .NET Framework používá obory názvů k uspořádání svých mnoha tříd následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="df39b-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
 [!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]  
  
<span data-ttu-id="df39b-105">`System` je obor názvů a `Console` je třída v tomto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="df39b-105">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="df39b-106">Klíčové slovo `using` lze použít, aby se nevyžadovalo úplné jméno, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="df39b-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]  
  
<span data-ttu-id="df39b-107">Další informace naleznete v [direktivě using](../../language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="df39b-107">For more information, see the [using Directive](../../language-reference/keywords/using-directive.md).</span></span>  
  
<span data-ttu-id="df39b-108">Za druhé deklarujete vlastní obory názvů, které vám pomohou řídit obor názvů tříd a metod ve větších programovacích projektech.</span><span class="sxs-lookup"><span data-stu-id="df39b-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="df39b-109">Použijte klíčové slovo [Namespace](../../language-reference/keywords/namespace.md) k deklarování oboru názvů, jak je uvedeno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="df39b-109">Use the [namespace](../../language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

<span data-ttu-id="df39b-110">Název oboru názvů musí být platný C# [název identifikátoru](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="df39b-110">The name of the namespace must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span>

## <a name="namespaces-overview"></a><span data-ttu-id="df39b-111">Přehled oborů názvů</span><span class="sxs-lookup"><span data-stu-id="df39b-111">Namespaces Overview</span></span>  

<span data-ttu-id="df39b-112">Obory názvů mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="df39b-112">Namespaces have the following properties:</span></span>  
  
- <span data-ttu-id="df39b-113">Organizují velké projekty kódu.</span><span class="sxs-lookup"><span data-stu-id="df39b-113">They organize large code projects.</span></span>  
- <span data-ttu-id="df39b-114">Jsou odděleny pomocí operátoru `.`.</span><span class="sxs-lookup"><span data-stu-id="df39b-114">They are delimited by using the `.` operator.</span></span>  
- <span data-ttu-id="df39b-115">Direktiva `using` obviates požadavek na zadání názvu oboru názvů pro každou třídu.</span><span class="sxs-lookup"><span data-stu-id="df39b-115">The `using` directive obviates the requirement to specify the name of the namespace for every class.</span></span>  
- <span data-ttu-id="df39b-116">Obor názvů `global` je kořenovým oborem názvů: `global::System` se vždycky odkazuje na obor názvů .NET <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="df39b-116">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET <xref:System> namespace.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="df39b-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="df39b-117">C# language specification</span></span>

<span data-ttu-id="df39b-118">Další informace najdete v části [obory názvů](~/_csharplang/spec/namespaces.md) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="df39b-118">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="df39b-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="df39b-119">See also</span></span>

- [<span data-ttu-id="df39b-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="df39b-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="df39b-121">Použití oboru názvů</span><span class="sxs-lookup"><span data-stu-id="df39b-121">Using Namespaces</span></span>](using-namespaces.md)
- [<span data-ttu-id="df39b-122">Jak používat můj obor názvů</span><span class="sxs-lookup"><span data-stu-id="df39b-122">How to use the My namespace</span></span>](how-to-use-the-my-namespace.md)
- [<span data-ttu-id="df39b-123">Názvy identifikátorů</span><span class="sxs-lookup"><span data-stu-id="df39b-123">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="df39b-124">using – direktiva</span><span class="sxs-lookup"><span data-stu-id="df39b-124">using Directive</span></span>](../../language-reference/keywords/using-directive.md)
- [<span data-ttu-id="df39b-125">:: – operátor</span><span class="sxs-lookup"><span data-stu-id="df39b-125">:: Operator</span></span>](../../language-reference/operators/namespace-alias-qualifier.md)
