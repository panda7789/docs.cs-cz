---
title: Obory názvů (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 60e4c6e98ca9e71d1a095a0c7ee1df6be6d13f4b
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934870"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="652a5-102">Obory názvů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="652a5-102">Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="652a5-103">Obory názvů často slouží v jazyce C# programming dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="652a5-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="652a5-104">Nejprve rozhraní .NET Framework používá obory názvů pro uspořádání mnoho tříd, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="652a5-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
 [!code-csharp[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
 <span data-ttu-id="652a5-105">`System` obor názvů a `Console` je třída v tomto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="652a5-105">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="652a5-106">`using` – Klíčové slovo je možné tak, že úplný název není povinné, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="652a5-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
 [!code-csharp[csProgGuide#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
 <span data-ttu-id="652a5-107">Další informace najdete v tématu [direktiva using](../../../csharp/language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="652a5-107">For more information, see [using Directive](../../../csharp/language-reference/keywords/using-directive.md).</span></span>  
  
 <span data-ttu-id="652a5-108">Za druhé deklarující vlastní obory názvů vám může pomoct určit obor názvů třídy a metody do větších programovací projektů.</span><span class="sxs-lookup"><span data-stu-id="652a5-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="652a5-109">Použití [obor názvů](../../../csharp/language-reference/keywords/namespace.md) – klíčové slovo k deklarování oboru názvů, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="652a5-109">Use the [namespace](../../../csharp/language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#6](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/index_4.cs)]  
  
## <a name="namespaces-overview"></a><span data-ttu-id="652a5-110">Přehled názvových prostorů</span><span class="sxs-lookup"><span data-stu-id="652a5-110">Namespaces Overview</span></span>  
 <span data-ttu-id="652a5-111">Obory názvů mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="652a5-111">Namespaces have the following properties:</span></span>  
  
-   <span data-ttu-id="652a5-112">Organizují velkých kódových projektů.</span><span class="sxs-lookup"><span data-stu-id="652a5-112">They organize large code projects.</span></span>  
  
-   <span data-ttu-id="652a5-113">Jsou oddělené pomocí `.` operátor.</span><span class="sxs-lookup"><span data-stu-id="652a5-113">They are delimited by using the `.` operator.</span></span>  
  
-   <span data-ttu-id="652a5-114">`using directive` Požadavku k určení názvu oboru názvů pro každou třídu, vyloučí.</span><span class="sxs-lookup"><span data-stu-id="652a5-114">The `using directive` obviates the requirement to specify the name of the namespace for every class.</span></span>  
  
-   <span data-ttu-id="652a5-115">`global` "Kořenový" obor názvů je obor názvů: `global::System` bude vždycky odkazovat na obor názvů rozhraní .NET Framework `System`.</span><span class="sxs-lookup"><span data-stu-id="652a5-115">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET Framework namespace `System`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="652a5-116">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="652a5-116">Related Sections</span></span>  
 <span data-ttu-id="652a5-117">Zobrazit další informace o oborech názvů v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="652a5-117">See the following topics for more information about namespaces:</span></span>  
  
-   [<span data-ttu-id="652a5-118">Použití oboru názvů</span><span class="sxs-lookup"><span data-stu-id="652a5-118">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="652a5-119">Postupy: Použití aliasu globálního oboru názvů</span><span class="sxs-lookup"><span data-stu-id="652a5-119">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
-   [<span data-ttu-id="652a5-120">Postupy: Použití oboru názvů My</span><span class="sxs-lookup"><span data-stu-id="652a5-120">How to: Use the My Namespace</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-my-namespace.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="652a5-121">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="652a5-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="652a5-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="652a5-122">See Also</span></span>  
 [<span data-ttu-id="652a5-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="652a5-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="652a5-124">Klíčová slova oboru názvů</span><span class="sxs-lookup"><span data-stu-id="652a5-124">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="652a5-125">using – direktiva</span><span class="sxs-lookup"><span data-stu-id="652a5-125">using Directive</span></span>](../../../csharp/language-reference/keywords/using-directive.md)  
 [<span data-ttu-id="652a5-126">:: – operátor</span><span class="sxs-lookup"><span data-stu-id="652a5-126">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [<span data-ttu-id="652a5-127">. – operátor</span><span class="sxs-lookup"><span data-stu-id="652a5-127">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)
