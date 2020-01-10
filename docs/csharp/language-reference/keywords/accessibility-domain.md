---
title: Přístup k doméně C# – referenční informace
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 4a4319b03f3e0d7f9ec721e611b78c124a8a8ee5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713838"
---
# <a name="accessibility-domain-c-reference"></a><span data-ttu-id="3fefc-102">Doména přístupnosti (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3fefc-102">Accessibility Domain (C# Reference)</span></span>
<span data-ttu-id="3fefc-103">Doména přístupnosti člena určuje, ve kterých oddílech programu může být členem odkazováno.</span><span class="sxs-lookup"><span data-stu-id="3fefc-103">The accessibility domain of a member specifies in which program sections a member can be referenced.</span></span> <span data-ttu-id="3fefc-104">Pokud je člen vnořen v jiném typu, jeho doména přístupnosti je určena [úrovní přístupnosti](./accessibility-levels.md) člena a doménou přístupnosti bezprostředně nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="3fefc-104">If the member is nested within another type, its accessibility domain is determined by both the [accessibility level](./accessibility-levels.md) of the member and the accessibility domain of the immediately containing type.</span></span>  
  
 <span data-ttu-id="3fefc-105">Doména přístupnosti typu nejvyšší úrovně je alespoň text programu projektu, v němž je deklarována.</span><span class="sxs-lookup"><span data-stu-id="3fefc-105">The accessibility domain of a top-level type is at least the program text of the project that it is declared in.</span></span> <span data-ttu-id="3fefc-106">To znamená, že doména zahrnuje všechny zdrojové soubory tohoto projektu.</span><span class="sxs-lookup"><span data-stu-id="3fefc-106">That is, the domain includes all of the source files of this project.</span></span> <span data-ttu-id="3fefc-107">Doména přístupnosti vnořeného typu je alespoň text programu typu, ve kterém je deklarována.</span><span class="sxs-lookup"><span data-stu-id="3fefc-107">The accessibility domain of a nested type is at least the program text of the type in which it is declared.</span></span> <span data-ttu-id="3fefc-108">To znamená, že doména je text typu, který zahrnuje všechny vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="3fefc-108">That is, the domain is the type body, which includes all nested types.</span></span> <span data-ttu-id="3fefc-109">Doména přístupnosti vnořeného typu nikdy nepřekračuje typ nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="3fefc-109">The accessibility domain of a nested type never exceeds that of the containing type.</span></span> <span data-ttu-id="3fefc-110">Tyto koncepty jsou znázorněné v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3fefc-110">These concepts are demonstrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fefc-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="3fefc-111">Example</span></span>  
 <span data-ttu-id="3fefc-112">Tento příklad obsahuje typ nejvyšší úrovně, `T1`a dvě vnořené třídy, `M1` a `M2`.</span><span class="sxs-lookup"><span data-stu-id="3fefc-112">This example contains a top-level type, `T1`, and two nested classes, `M1` and `M2`.</span></span> <span data-ttu-id="3fefc-113">Třídy obsahují pole, která mají různé deklarované přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="3fefc-113">The classes contain fields that have different declared accessibilities.</span></span> <span data-ttu-id="3fefc-114">V metodě `Main` komentář sleduje jednotlivé příkazy, aby označovaly doménu přístupnosti každého člena.</span><span class="sxs-lookup"><span data-stu-id="3fefc-114">In the `Main` method, a comment follows each statement to indicate the accessibility domain of each member.</span></span> <span data-ttu-id="3fefc-115">Všimněte si, že příkazy, které se pokoušejí odkázat na nepřístupné členy, jsou zakomentovány. Pokud chcete zobrazit chyby kompilátoru způsobené odkazem na nepřístupného člena, odstraňte komentáře po jednom.</span><span class="sxs-lookup"><span data-stu-id="3fefc-115">Notice that the statements that try to reference the inaccessible members are commented out. If you want to see the compiler errors caused by referencing an inaccessible member, remove the comments one at a time.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a><span data-ttu-id="3fefc-116">C# – jazyková specifikace</span><span class="sxs-lookup"><span data-stu-id="3fefc-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3fefc-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3fefc-117">See also</span></span>

- [<span data-ttu-id="3fefc-118">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="3fefc-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3fefc-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3fefc-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3fefc-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3fefc-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="3fefc-121">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="3fefc-121">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="3fefc-122">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="3fefc-122">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="3fefc-123">Omezení používání úrovní přístupu</span><span class="sxs-lookup"><span data-stu-id="3fefc-123">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="3fefc-124">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="3fefc-124">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="3fefc-125">public</span><span class="sxs-lookup"><span data-stu-id="3fefc-125">public</span></span>](./public.md)
- [<span data-ttu-id="3fefc-126">private</span><span class="sxs-lookup"><span data-stu-id="3fefc-126">private</span></span>](./private.md)
- [<span data-ttu-id="3fefc-127">protected</span><span class="sxs-lookup"><span data-stu-id="3fefc-127">protected</span></span>](./protected.md)
- [<span data-ttu-id="3fefc-128">internal</span><span class="sxs-lookup"><span data-stu-id="3fefc-128">internal</span></span>](./internal.md)
