---
title: Doména přístupnosti (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 8e6af35ea41f6d062bc2b8ee771a1fac21667462
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208351"
---
# <a name="accessibility-domain-c-reference"></a><span data-ttu-id="9523b-102">Doména přístupnosti (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9523b-102">Accessibility Domain (C# Reference)</span></span>
<span data-ttu-id="9523b-103">Doména přístupnosti člena určuje, ve které části program může být odkazováno členem.</span><span class="sxs-lookup"><span data-stu-id="9523b-103">The accessibility domain of a member specifies in which program sections a member can be referenced.</span></span> <span data-ttu-id="9523b-104">Pokud člen vnořen v rámci jiného typu, jak je určen jeho doména přístupnosti [úrovni přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md) člena a doména přístupnosti okamžitě nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="9523b-104">If the member is nested within another type, its accessibility domain is determined by both the [accessibility level](../../../csharp/language-reference/keywords/accessibility-levels.md) of the member and the accessibility domain of the immediately containing type.</span></span>  
  
 <span data-ttu-id="9523b-105">Doména přístupnosti typu nejvyšší úrovně je alespoň text projekt, který je deklarován v programu.</span><span class="sxs-lookup"><span data-stu-id="9523b-105">The accessibility domain of a top-level type is at least the program text of the project that it is declared in.</span></span> <span data-ttu-id="9523b-106">To znamená doména obsahuje všechny zdrojových souborů tohoto projektu.</span><span class="sxs-lookup"><span data-stu-id="9523b-106">That is, the domain includes all of the source files of this project.</span></span> <span data-ttu-id="9523b-107">Doména přístupnosti vnořeného typu je alespoň text program typu, ve kterém je deklarovaná.</span><span class="sxs-lookup"><span data-stu-id="9523b-107">The accessibility domain of a nested type is at least the program text of the type in which it is declared.</span></span> <span data-ttu-id="9523b-108">To znamená že doménu je typu text, který obsahuje všechny vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="9523b-108">That is, the domain is the type body, which includes all nested types.</span></span> <span data-ttu-id="9523b-109">Doména přístupnosti vnořeného typu nikdy přesahuje nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="9523b-109">The accessibility domain of a nested type never exceeds that of the containing type.</span></span> <span data-ttu-id="9523b-110">Tyto koncepty jsou ukázáno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9523b-110">These concepts are demonstrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9523b-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="9523b-111">Example</span></span>  
 <span data-ttu-id="9523b-112">Tento příklad obsahuje typu nejvyšší úrovně `T1`a dva vnořené třídy `M1` a `M2`.</span><span class="sxs-lookup"><span data-stu-id="9523b-112">This example contains a top-level type, `T1`, and two nested classes, `M1` and `M2`.</span></span> <span data-ttu-id="9523b-113">Třídy obsahovat pole, které mají různé deklarované přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="9523b-113">The classes contain fields that have different declared accessibilities.</span></span> <span data-ttu-id="9523b-114">V `Main` metody komentář následuje každý příkaz k označení doména přístupnosti u každého člena.</span><span class="sxs-lookup"><span data-stu-id="9523b-114">In the `Main` method, a comment follows each statement to indicate the accessibility domain of each member.</span></span> <span data-ttu-id="9523b-115">Všimněte si, že jsou komentované příkazy, které se pokusí o odkazovat nepřístupný členy. Pokud chcete zobrazit chyby kompilátoru způsobené odkazování na člena nedostupné, odeberte komentáře jeden najednou.</span><span class="sxs-lookup"><span data-stu-id="9523b-115">Notice that the statements that try to reference the inaccessible members are commented out. If you want to see the compiler errors caused by referencing an inaccessible member, remove the comments one at a time.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a><span data-ttu-id="9523b-116">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9523b-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9523b-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="9523b-117">See Also</span></span>  
 [<span data-ttu-id="9523b-118">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9523b-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9523b-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9523b-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9523b-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9523b-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="9523b-121">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="9523b-121">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="9523b-122">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="9523b-122">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="9523b-123">Omezení používání úrovní přístupu</span><span class="sxs-lookup"><span data-stu-id="9523b-123">Restrictions on Using Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [<span data-ttu-id="9523b-124">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="9523b-124">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="9523b-125">public</span><span class="sxs-lookup"><span data-stu-id="9523b-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="9523b-126">private</span><span class="sxs-lookup"><span data-stu-id="9523b-126">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="9523b-127">protected</span><span class="sxs-lookup"><span data-stu-id="9523b-127">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="9523b-128">internal</span><span class="sxs-lookup"><span data-stu-id="9523b-128">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
