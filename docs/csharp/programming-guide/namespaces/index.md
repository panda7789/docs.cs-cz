---
title: Obory názvů (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 60e4c6e98ca9e71d1a095a0c7ee1df6be6d13f4b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334347"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="4fafd-102">Obory názvů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="4fafd-102">Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="4fafd-103">Obory názvů výraznou slouží v jazyce C# programování dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="4fafd-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="4fafd-104">Rozhraní .NET Framework nejprve používá obory názvů pro uspořádání mnoho tříd, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="4fafd-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
 [!code-csharp[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
 <span data-ttu-id="4fafd-105">`System` je obor názvů a `Console` je třída v daném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4fafd-105">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="4fafd-106">`using` – Klíčové slovo lze tak, aby úplný název není vyžadována, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="4fafd-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
 [!code-csharp[csProgGuide#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
 <span data-ttu-id="4fafd-107">Další informace najdete v tématu [using – direktiva](../../../csharp/language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="4fafd-107">For more information, see [using Directive](../../../csharp/language-reference/keywords/using-directive.md).</span></span>  
  
 <span data-ttu-id="4fafd-108">Druhý deklarace vlastní oborů názvů vám může pomoct řídit oboru názvů třídy a metody větší programovací projektů.</span><span class="sxs-lookup"><span data-stu-id="4fafd-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="4fafd-109">Použití [obor názvů](../../../csharp/language-reference/keywords/namespace.md) – klíčové slovo k deklaraci oboru názvů, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="4fafd-109">Use the [namespace](../../../csharp/language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#6](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/index_4.cs)]  
  
## <a name="namespaces-overview"></a><span data-ttu-id="4fafd-110">Přehled oborů názvů</span><span class="sxs-lookup"><span data-stu-id="4fafd-110">Namespaces Overview</span></span>  
 <span data-ttu-id="4fafd-111">Obory názvů mít následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="4fafd-111">Namespaces have the following properties:</span></span>  
  
-   <span data-ttu-id="4fafd-112">Jejich uspořádání projekty velké kódu.</span><span class="sxs-lookup"><span data-stu-id="4fafd-112">They organize large code projects.</span></span>  
  
-   <span data-ttu-id="4fafd-113">Jsou oddělené pomocí `.` operátor.</span><span class="sxs-lookup"><span data-stu-id="4fafd-113">They are delimited by using the `.` operator.</span></span>  
  
-   <span data-ttu-id="4fafd-114">`using directive` Požadavek na zadejte název oboru názvů pro každou třídu, vyloučí.</span><span class="sxs-lookup"><span data-stu-id="4fafd-114">The `using directive` obviates the requirement to specify the name of the namespace for every class.</span></span>  
  
-   <span data-ttu-id="4fafd-115">`global` Obor názvů je obor názvů "root": `global::System` bude vždy odkaz na obor názvů rozhraní .NET Framework `System`.</span><span class="sxs-lookup"><span data-stu-id="4fafd-115">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET Framework namespace `System`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4fafd-116">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="4fafd-116">Related Sections</span></span>  
 <span data-ttu-id="4fafd-117">Najdete další informace o oborech názvů v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="4fafd-117">See the following topics for more information about namespaces:</span></span>  
  
-   [<span data-ttu-id="4fafd-118">Použití oboru názvů</span><span class="sxs-lookup"><span data-stu-id="4fafd-118">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="4fafd-119">Postupy: Použití aliasu globálního oboru názvů</span><span class="sxs-lookup"><span data-stu-id="4fafd-119">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
-   [<span data-ttu-id="4fafd-120">Postupy: Použití oboru názvů My</span><span class="sxs-lookup"><span data-stu-id="4fafd-120">How to: Use the My Namespace</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-my-namespace.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="4fafd-121">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4fafd-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4fafd-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="4fafd-122">See Also</span></span>  
 [<span data-ttu-id="4fafd-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4fafd-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4fafd-124">Klíčová slova oboru názvů</span><span class="sxs-lookup"><span data-stu-id="4fafd-124">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="4fafd-125">using – direktiva</span><span class="sxs-lookup"><span data-stu-id="4fafd-125">using Directive</span></span>](../../../csharp/language-reference/keywords/using-directive.md)  
 [<span data-ttu-id="4fafd-126">:: – operátor</span><span class="sxs-lookup"><span data-stu-id="4fafd-126">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [<span data-ttu-id="4fafd-127">. – operátor</span><span class="sxs-lookup"><span data-stu-id="4fafd-127">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)
