---
title: Doména usnadnění – odkaz jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 4a4319b03f3e0d7f9ec721e611b78c124a8a8ee5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713838"
---
# <a name="accessibility-domain-c-reference"></a><span data-ttu-id="2dd2f-102">Doména přístupnosti (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2dd2f-102">Accessibility Domain (C# Reference)</span></span>
<span data-ttu-id="2dd2f-103">Doména usnadnění člena určuje, ve kterých oddílech programu lze na člena odkazovat.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-103">The accessibility domain of a member specifies in which program sections a member can be referenced.</span></span> <span data-ttu-id="2dd2f-104">Pokud je člen vnořen do jiného typu, jeho doména usnadnění je určena [jak úrovní usnadnění](./accessibility-levels.md) člena, tak doménou usnadnění typu bezprostředně obsahujícího typ.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-104">If the member is nested within another type, its accessibility domain is determined by both the [accessibility level](./accessibility-levels.md) of the member and the accessibility domain of the immediately containing type.</span></span>  
  
 <span data-ttu-id="2dd2f-105">Doména usnadnění typu nejvyšší úrovně je alespoň text programu projektu, ve které je deklarován.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-105">The accessibility domain of a top-level type is at least the program text of the project that it is declared in.</span></span> <span data-ttu-id="2dd2f-106">To znamená, že doména obsahuje všechny zdrojové soubory tohoto projektu.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-106">That is, the domain includes all of the source files of this project.</span></span> <span data-ttu-id="2dd2f-107">Doména usnadnění vnořeného typu je alespoň text programu typu, ve kterém je deklarována.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-107">The accessibility domain of a nested type is at least the program text of the type in which it is declared.</span></span> <span data-ttu-id="2dd2f-108">To znamená, že doména je tělo typu, který zahrnuje všechny vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-108">That is, the domain is the type body, which includes all nested types.</span></span> <span data-ttu-id="2dd2f-109">Doména usnadnění vnořeného typu nikdy nepřekročí doménu obsahujícího typu.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-109">The accessibility domain of a nested type never exceeds that of the containing type.</span></span> <span data-ttu-id="2dd2f-110">Tyto koncepty jsou demonstrovány v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-110">These concepts are demonstrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2dd2f-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="2dd2f-111">Example</span></span>  
 <span data-ttu-id="2dd2f-112">Tento příklad obsahuje typ nejvyšší `T1`úrovně a dvě `M1` vnořené třídy a `M2`.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-112">This example contains a top-level type, `T1`, and two nested classes, `M1` and `M2`.</span></span> <span data-ttu-id="2dd2f-113">Třídy obsahují pole, která mají různé deklarované přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-113">The classes contain fields that have different declared accessibilities.</span></span> <span data-ttu-id="2dd2f-114">V `Main` metodě komentář následuje každý příkaz k označení domény usnadnění každého člena.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-114">In the `Main` method, a comment follows each statement to indicate the accessibility domain of each member.</span></span> <span data-ttu-id="2dd2f-115">Všimněte si, že příkazy, které se pokoušejí odkazovat na nepřístupné členy, jsou zakomentovány. Pokud chcete zobrazit chyby kompilátoru způsobené odkazováním na nepřístupný člen, odeberte komentáře po jednom.</span><span class="sxs-lookup"><span data-stu-id="2dd2f-115">Notice that the statements that try to reference the inaccessible members are commented out. If you want to see the compiler errors caused by referencing an inaccessible member, remove the comments one at a time.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a><span data-ttu-id="2dd2f-116">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2dd2f-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2dd2f-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="2dd2f-117">See also</span></span>

- [<span data-ttu-id="2dd2f-118">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2dd2f-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2dd2f-119">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2dd2f-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2dd2f-120">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="2dd2f-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="2dd2f-121">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="2dd2f-121">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="2dd2f-122">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="2dd2f-122">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="2dd2f-123">Omezení používání úrovní přístupu</span><span class="sxs-lookup"><span data-stu-id="2dd2f-123">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="2dd2f-124">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="2dd2f-124">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="2dd2f-125">Veřejné</span><span class="sxs-lookup"><span data-stu-id="2dd2f-125">public</span></span>](./public.md)
- [<span data-ttu-id="2dd2f-126">Soukromé</span><span class="sxs-lookup"><span data-stu-id="2dd2f-126">private</span></span>](./private.md)
- [<span data-ttu-id="2dd2f-127">protected</span><span class="sxs-lookup"><span data-stu-id="2dd2f-127">protected</span></span>](./protected.md)
- [<span data-ttu-id="2dd2f-128">Vnitřní</span><span class="sxs-lookup"><span data-stu-id="2dd2f-128">internal</span></span>](./internal.md)
