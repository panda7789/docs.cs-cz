---
description: Doména usnadnění – Referenční dokumentace jazyka C#
title: Doména usnadnění – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 2cfc4cc72a79b33276b7d822a2b31eb518dcf784
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89127058"
---
# <a name="accessibility-domain-c-reference"></a><span data-ttu-id="ad171-103">Doména přístupnosti (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ad171-103">Accessibility Domain (C# Reference)</span></span>
<span data-ttu-id="ad171-104">Doména přístupnosti člena určuje, ve kterých oddílech programu může být členem odkazováno.</span><span class="sxs-lookup"><span data-stu-id="ad171-104">The accessibility domain of a member specifies in which program sections a member can be referenced.</span></span> <span data-ttu-id="ad171-105">Pokud je člen vnořen v jiném typu, jeho doména přístupnosti je určena [úrovní přístupnosti](./accessibility-levels.md) člena a doménou přístupnosti bezprostředně nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="ad171-105">If the member is nested within another type, its accessibility domain is determined by both the [accessibility level](./accessibility-levels.md) of the member and the accessibility domain of the immediately containing type.</span></span>  
  
 <span data-ttu-id="ad171-106">Doména přístupnosti typu nejvyšší úrovně je alespoň text programu projektu, v němž je deklarována.</span><span class="sxs-lookup"><span data-stu-id="ad171-106">The accessibility domain of a top-level type is at least the program text of the project that it is declared in.</span></span> <span data-ttu-id="ad171-107">To znamená, že doména zahrnuje všechny zdrojové soubory tohoto projektu.</span><span class="sxs-lookup"><span data-stu-id="ad171-107">That is, the domain includes all of the source files of this project.</span></span> <span data-ttu-id="ad171-108">Doména přístupnosti vnořeného typu je alespoň text programu typu, ve kterém je deklarována.</span><span class="sxs-lookup"><span data-stu-id="ad171-108">The accessibility domain of a nested type is at least the program text of the type in which it is declared.</span></span> <span data-ttu-id="ad171-109">To znamená, že doména je text typu, který zahrnuje všechny vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="ad171-109">That is, the domain is the type body, which includes all nested types.</span></span> <span data-ttu-id="ad171-110">Doména přístupnosti vnořeného typu nikdy nepřekračuje typ nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="ad171-110">The accessibility domain of a nested type never exceeds that of the containing type.</span></span> <span data-ttu-id="ad171-111">Tyto koncepty jsou znázorněné v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ad171-111">These concepts are demonstrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad171-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad171-112">Example</span></span>  
 <span data-ttu-id="ad171-113">Tento příklad obsahuje typ nejvyšší úrovně, `T1` , a dvě vnořené třídy `M1` a `M2` .</span><span class="sxs-lookup"><span data-stu-id="ad171-113">This example contains a top-level type, `T1`, and two nested classes, `M1` and `M2`.</span></span> <span data-ttu-id="ad171-114">Třídy obsahují pole, která mají různé deklarované přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="ad171-114">The classes contain fields that have different declared accessibilities.</span></span> <span data-ttu-id="ad171-115">V `Main` metodě se komentář řídí jednotlivými příkazy k označení domény přístupnosti každého člena.</span><span class="sxs-lookup"><span data-stu-id="ad171-115">In the `Main` method, a comment follows each statement to indicate the accessibility domain of each member.</span></span> <span data-ttu-id="ad171-116">Všimněte si, že příkazy, které se pokoušejí odkázat na nepřístupné členy, jsou zakomentovány. Pokud chcete zobrazit chyby kompilátoru způsobené odkazem na nepřístupného člena, odstraňte komentáře po jednom.</span><span class="sxs-lookup"><span data-stu-id="ad171-116">Notice that the statements that try to reference the inaccessible members are commented out. If you want to see the compiler errors caused by referencing an inaccessible member, remove the comments one at a time.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a><span data-ttu-id="ad171-117">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ad171-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ad171-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad171-118">See also</span></span>

- [<span data-ttu-id="ad171-119">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ad171-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ad171-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="ad171-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ad171-121">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ad171-121">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="ad171-122">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="ad171-122">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="ad171-123">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="ad171-123">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="ad171-124">Omezení používání úrovní přístupu</span><span class="sxs-lookup"><span data-stu-id="ad171-124">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="ad171-125">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="ad171-125">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="ad171-126">public</span><span class="sxs-lookup"><span data-stu-id="ad171-126">public</span></span>](./public.md)
- [<span data-ttu-id="ad171-127">private</span><span class="sxs-lookup"><span data-stu-id="ad171-127">private</span></span>](./private.md)
- [<span data-ttu-id="ad171-128">protected</span><span class="sxs-lookup"><span data-stu-id="ad171-128">protected</span></span>](./protected.md)
- [<span data-ttu-id="ad171-129">internal</span><span class="sxs-lookup"><span data-stu-id="ad171-129">internal</span></span>](./internal.md)
