---
title: Obory názvů (Průvodce programováním v C#)
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: c4011092a6c605137053b544d4b9f14cce2fdb4c
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "44755707"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="64ec6-102">Obory názvů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="64ec6-102">Namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="64ec6-103">Obory názvů často slouží v jazyce C# programming dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="64ec6-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="64ec6-104">Nejprve rozhraní .NET Framework používá obory názvů pro uspořádání mnoho tříd, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="64ec6-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
[!code-csharp[csProgGuide#22](../inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
<span data-ttu-id="64ec6-105">`System` obor názvů a `Console` je třída v tomto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="64ec6-105">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="64ec6-106">`using` – Klíčové slovo je možné tak, že úplný název není povinné, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="64ec6-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
[!code-csharp[csProgGuide#1](../inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
[!code-csharp[csProgGuide#25](../inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
<span data-ttu-id="64ec6-107">Další informace najdete v tématu [direktiva using](../../language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="64ec6-107">For more information, see the [using Directive](../../language-reference/keywords/using-directive.md).</span></span>  
  
<span data-ttu-id="64ec6-108">Za druhé deklarující vlastní obory názvů vám může pomoct určit obor názvů třídy a metody do větších programovací projektů.</span><span class="sxs-lookup"><span data-stu-id="64ec6-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="64ec6-109">Použití [obor názvů](../../language-reference/keywords/namespace.md) – klíčové slovo k deklarování oboru názvů, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="64ec6-109">Use the [namespace](../../language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
[!code-csharp[csProgGuideNamespaces#6](codesnippet/CSharp/index_4.cs)]

<span data-ttu-id="64ec6-110">Název oboru názvů musí být platný C# [název identifikátoru](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="64ec6-110">The name of the namespace must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span>

## <a name="namespaces-overview"></a><span data-ttu-id="64ec6-111">Přehled názvových prostorů</span><span class="sxs-lookup"><span data-stu-id="64ec6-111">Namespaces Overview</span></span>  

<span data-ttu-id="64ec6-112">Obory názvů mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="64ec6-112">Namespaces have the following properties:</span></span>  
  
- <span data-ttu-id="64ec6-113">Organizují velkých kódových projektů.</span><span class="sxs-lookup"><span data-stu-id="64ec6-113">They organize large code projects.</span></span>  
- <span data-ttu-id="64ec6-114">Jsou oddělené pomocí `.` operátor.</span><span class="sxs-lookup"><span data-stu-id="64ec6-114">They are delimited by using the `.` operator.</span></span>  
- <span data-ttu-id="64ec6-115">`using directive` Požadavku k určení názvu oboru názvů pro každou třídu, vyloučí.</span><span class="sxs-lookup"><span data-stu-id="64ec6-115">The `using directive` obviates the requirement to specify the name of the namespace for every class.</span></span>  
- <span data-ttu-id="64ec6-116">`global` "Kořenový" obor názvů je obor názvů: `global::System` bude vždycky odkazovat na obor názvů rozhraní .NET Framework `System`.</span><span class="sxs-lookup"><span data-stu-id="64ec6-116">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET Framework namespace `System`.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="64ec6-117">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="64ec6-117">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="64ec6-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="64ec6-118">See Also</span></span>

- [<span data-ttu-id="64ec6-119">Použití oboru názvů</span><span class="sxs-lookup"><span data-stu-id="64ec6-119">Using Namespaces</span></span>](using-namespaces.md)
- [<span data-ttu-id="64ec6-120">Postupy: Použití aliasu globálního oboru názvů</span><span class="sxs-lookup"><span data-stu-id="64ec6-120">How to: Use the Global Namespace Alias</span></span>](how-to-use-the-global-namespace-alias.md)
- [<span data-ttu-id="64ec6-121">Postupy: Použití oboru názvů My</span><span class="sxs-lookup"><span data-stu-id="64ec6-121">How to: Use the My Namespace</span></span>](how-to-use-the-my-namespace.md)
- [<span data-ttu-id="64ec6-122">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="64ec6-122">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="64ec6-123">Názvy identifikátorů</span><span class="sxs-lookup"><span data-stu-id="64ec6-123">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="64ec6-124">Klíčová slova oboru názvů</span><span class="sxs-lookup"><span data-stu-id="64ec6-124">Namespace Keywords</span></span>](../../language-reference/keywords/namespace-keywords.md)  
- [<span data-ttu-id="64ec6-125">using – direktiva</span><span class="sxs-lookup"><span data-stu-id="64ec6-125">using Directive</span></span>](../../language-reference/keywords/using-directive.md)  
- [<span data-ttu-id="64ec6-126">:: – operátor</span><span class="sxs-lookup"><span data-stu-id="64ec6-126">:: Operator</span></span>](../../language-reference/operators/namespace-alias-qualifer.md)  
- [<span data-ttu-id="64ec6-127">. – operátor</span><span class="sxs-lookup"><span data-stu-id="64ec6-127">. Operator</span></span>](../../language-reference/operators/member-access-operator.md)
>>>>>>> <span data-ttu-id="64ec6-128">Přidejte identifikátor pravidla pojmenování</span><span class="sxs-lookup"><span data-stu-id="64ec6-128">add identifier naming rules</span></span>
