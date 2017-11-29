---
title: "Obory názvů (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3eb645f5beb61d3cec97a70a54e660c65be52091
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="00fbd-102">Obory názvů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="00fbd-102">Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="00fbd-103">Obory názvů výraznou slouží v jazyce C# programování dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="00fbd-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="00fbd-104">Rozhraní .NET Framework nejprve používá obory názvů pro uspořádání mnoho tříd, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="00fbd-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
 [!code-csharp[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
 <span data-ttu-id="00fbd-105">`System`je obor názvů a `Console` je třída v daném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="00fbd-105">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="00fbd-106">`using` – Klíčové slovo lze tak, aby úplný název není vyžadována, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="00fbd-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
 [!code-csharp[csProgGuide#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
 <span data-ttu-id="00fbd-107">Další informace najdete v tématu [using – direktiva](../../../csharp/language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="00fbd-107">For more information, see [using Directive](../../../csharp/language-reference/keywords/using-directive.md).</span></span>  
  
 <span data-ttu-id="00fbd-108">Druhý deklarace vlastní oborů názvů vám může pomoct řídit oboru názvů třídy a metody větší programovací projektů.</span><span class="sxs-lookup"><span data-stu-id="00fbd-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="00fbd-109">Použití [obor názvů](../../../csharp/language-reference/keywords/namespace.md) – klíčové slovo k deklaraci oboru názvů, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="00fbd-109">Use the [namespace](../../../csharp/language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#6](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/index_4.cs)]  
  
## <a name="namespaces-overview"></a><span data-ttu-id="00fbd-110">Přehled oborů názvů</span><span class="sxs-lookup"><span data-stu-id="00fbd-110">Namespaces Overview</span></span>  
 <span data-ttu-id="00fbd-111">Obory názvů mít následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="00fbd-111">Namespaces have the following properties:</span></span>  
  
-   <span data-ttu-id="00fbd-112">Jejich uspořádání projekty velké kódu.</span><span class="sxs-lookup"><span data-stu-id="00fbd-112">They organize large code projects.</span></span>  
  
-   <span data-ttu-id="00fbd-113">Jsou oddělené pomocí `.` operátor.</span><span class="sxs-lookup"><span data-stu-id="00fbd-113">They are delimited by using the `.` operator.</span></span>  
  
-   <span data-ttu-id="00fbd-114">`using directive` Požadavek na zadejte název oboru názvů pro každou třídu, vyloučí.</span><span class="sxs-lookup"><span data-stu-id="00fbd-114">The `using directive` obviates the requirement to specify the name of the namespace for every class.</span></span>  
  
-   <span data-ttu-id="00fbd-115">`global` Obor názvů je obor názvů "root": `global::System` bude vždy odkaz na obor názvů rozhraní .NET Framework `System`.</span><span class="sxs-lookup"><span data-stu-id="00fbd-115">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET Framework namespace `System`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="00fbd-116">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="00fbd-116">Related Sections</span></span>  
 <span data-ttu-id="00fbd-117">Najdete další informace o oborech názvů v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="00fbd-117">See the following topics for more information about namespaces:</span></span>  
  
-   [<span data-ttu-id="00fbd-118">Použití oboru názvů</span><span class="sxs-lookup"><span data-stu-id="00fbd-118">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="00fbd-119">Postupy: použití aliasu globálního Namespace</span><span class="sxs-lookup"><span data-stu-id="00fbd-119">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
-   [<span data-ttu-id="00fbd-120">Postupy: použití My Namespace</span><span class="sxs-lookup"><span data-stu-id="00fbd-120">How to: Use the My Namespace</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-my-namespace.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="00fbd-121">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="00fbd-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="00fbd-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="00fbd-122">See Also</span></span>  
 [<span data-ttu-id="00fbd-123">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="00fbd-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="00fbd-124">Namespace klíčová slova</span><span class="sxs-lookup"><span data-stu-id="00fbd-124">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="00fbd-125">Using – direktiva</span><span class="sxs-lookup"><span data-stu-id="00fbd-125">using Directive</span></span>](../../../csharp/language-reference/keywords/using-directive.md)  
 [<span data-ttu-id="00fbd-126">:: – Operátor</span><span class="sxs-lookup"><span data-stu-id="00fbd-126">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [<span data-ttu-id="00fbd-127">. Operátor</span><span class="sxs-lookup"><span data-stu-id="00fbd-127">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)
