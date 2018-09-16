---
title: Doména přístupnosti (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 01854b60fb58d4dcd0a217552f19d6c0cd32ec78
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45664433"
---
# <a name="accessibility-domain-c-reference"></a><span data-ttu-id="a8387-102">Doména přístupnosti (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a8387-102">Accessibility Domain (C# Reference)</span></span>
<span data-ttu-id="a8387-103">Doména přístupnosti člena určuje, ve které části programu může být odkazováno člena.</span><span class="sxs-lookup"><span data-stu-id="a8387-103">The accessibility domain of a member specifies in which program sections a member can be referenced.</span></span> <span data-ttu-id="a8387-104">Pokud člen je vnořená v rámci jiného typu, jak je určen jeho doméně přístupnosti [úrovni přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md) z člena a doménou přístupnosti bezprostředně nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="a8387-104">If the member is nested within another type, its accessibility domain is determined by both the [accessibility level](../../../csharp/language-reference/keywords/accessibility-levels.md) of the member and the accessibility domain of the immediately containing type.</span></span>  
  
 <span data-ttu-id="a8387-105">Doména přístupnosti člena typu nejvyšší úrovně je alespoň textem programu, který je deklarován v projektu.</span><span class="sxs-lookup"><span data-stu-id="a8387-105">The accessibility domain of a top-level type is at least the program text of the project that it is declared in.</span></span> <span data-ttu-id="a8387-106">To znamená doména obsahuje všechny zdrojové soubory tohoto projektu.</span><span class="sxs-lookup"><span data-stu-id="a8387-106">That is, the domain includes all of the source files of this project.</span></span> <span data-ttu-id="a8387-107">Doména přístupnosti vnořeného typu je alespoň textem programu typu, ve kterém je deklarována.</span><span class="sxs-lookup"><span data-stu-id="a8387-107">The accessibility domain of a nested type is at least the program text of the type in which it is declared.</span></span> <span data-ttu-id="a8387-108">To znamená že doménu je typu text, který zahrnuje všechny vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="a8387-108">That is, the domain is the type body, which includes all nested types.</span></span> <span data-ttu-id="a8387-109">Doména přístupnosti vnořeného typu nikdy překročí nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="a8387-109">The accessibility domain of a nested type never exceeds that of the containing type.</span></span> <span data-ttu-id="a8387-110">Tyto koncepty je ukázán v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a8387-110">These concepts are demonstrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8387-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8387-111">Example</span></span>  
 <span data-ttu-id="a8387-112">V tomto příkladu obsahuje typu nejvyšší úrovně `T1`a dvě vnořené třídy, `M1` a `M2`.</span><span class="sxs-lookup"><span data-stu-id="a8387-112">This example contains a top-level type, `T1`, and two nested classes, `M1` and `M2`.</span></span> <span data-ttu-id="a8387-113">Třídy obsahovat pole, které mají různé deklarované přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="a8387-113">The classes contain fields that have different declared accessibilities.</span></span> <span data-ttu-id="a8387-114">V `Main` metody komentář následuje každý příkaz označíte, tak doména přístupnosti člena každý člen.</span><span class="sxs-lookup"><span data-stu-id="a8387-114">In the `Main` method, a comment follows each statement to indicate the accessibility domain of each member.</span></span> <span data-ttu-id="a8387-115">Všimněte si, že příkazy, které se pokouší odkazovat nepřístupní členové jsou označené jako komentář. Pokud chcete zobrazit chyby kompilátoru způsobené odkazuje na nepřístupný člena, odeberte komentáře jeden po druhém.</span><span class="sxs-lookup"><span data-stu-id="a8387-115">Notice that the statements that try to reference the inaccessible members are commented out. If you want to see the compiler errors caused by referencing an inaccessible member, remove the comments one at a time.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a><span data-ttu-id="a8387-116">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a8387-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a8387-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8387-117">See Also</span></span>  
- [<span data-ttu-id="a8387-118">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a8387-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="a8387-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a8387-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a8387-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a8387-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="a8387-121">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="a8387-121">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
- [<span data-ttu-id="a8387-122">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="a8387-122">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
- [<span data-ttu-id="a8387-123">Omezení používání úrovní přístupu</span><span class="sxs-lookup"><span data-stu-id="a8387-123">Restrictions on Using Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
- [<span data-ttu-id="a8387-124">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="a8387-124">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [<span data-ttu-id="a8387-125">public</span><span class="sxs-lookup"><span data-stu-id="a8387-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
- [<span data-ttu-id="a8387-126">private</span><span class="sxs-lookup"><span data-stu-id="a8387-126">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
- [<span data-ttu-id="a8387-127">protected</span><span class="sxs-lookup"><span data-stu-id="a8387-127">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
- [<span data-ttu-id="a8387-128">internal</span><span class="sxs-lookup"><span data-stu-id="a8387-128">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
