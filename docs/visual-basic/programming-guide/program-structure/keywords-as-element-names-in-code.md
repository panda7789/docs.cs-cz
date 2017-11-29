---
title: "Klíčová slova jako názvy elementu v kódu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f410a0eaac0dcc034d406a89ed1d01a8f228a583
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a><span data-ttu-id="428f5-102">Klíčová slova jako názvy elementu v kódu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="428f5-102">Keywords as Element Names in Code (Visual Basic)</span></span>
<span data-ttu-id="428f5-103">Žádné program element – například proměnné, třída nebo člen – může mít stejný název jako s omezeným přístupem – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="428f5-103">Any program element — such as a variable, class, or member — can have the same name as a restricted keyword.</span></span> <span data-ttu-id="428f5-104">Například můžete vytvořit proměnné s názvem `Loop`.</span><span class="sxs-lookup"><span data-stu-id="428f5-104">For example, you can create a variable named `Loop`.</span></span> <span data-ttu-id="428f5-105">Však k odkazování na vaší verzi, který má stejný název jako s omezeným přístupem `Loop` – klíčové slovo – musí předcházet řetězcem úplné kvalifikace nebo hranaté závorky (`[ ]`), jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="428f5-105">However, to refer to your version of it — which has the same name as the restricted `Loop` keyword — you must either precede it with a full qualification string or enclose it in square brackets (`[ ]`), as the following example shows.</span></span>  
  
 [!code-vb[VbVbcnConventions#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/keywords-as-element-names-in-code_1.vb)]  
  
 <span data-ttu-id="428f5-106">Pokud neprovedete tyto, pak jazyka Visual Basic předpokládá použití vnitřní `Loop` – klíčové slovo a vytvoří chybu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="428f5-106">If you do not do either of these, then Visual Basic assumes use of the intrinsic `Loop` keyword and produces an error, as in the following example:</span></span>  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 <span data-ttu-id="428f5-107">Hranaté závorky můžete použít k odkazování na formuláře a ovládací prvky a pokud deklarace proměnné nebo definování procedura se stejným názvem jako s omezeným přístupem – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="428f5-107">You can use square brackets when referring to forms and controls, and when declaring a variable or defining a procedure with the same name as a restricted keyword.</span></span> <span data-ttu-id="428f5-108">Může být snadno nezapomněli kvalifikovat názvy nebo zahrnují hranaté závorky a proto zavést kódu chyby a znesnadňuje ke čtení.</span><span class="sxs-lookup"><span data-stu-id="428f5-108">It can be easy to forget to qualify names or include square brackets, and thus introduce errors into your code and make it harder to read.</span></span> <span data-ttu-id="428f5-109">Z tohoto důvodu doporučujeme používat s omezeným přístupem klíčová slova jako názvy elementů programu.</span><span class="sxs-lookup"><span data-stu-id="428f5-109">For this reason, we recommend that you not use restricted keywords as the names of program elements.</span></span> <span data-ttu-id="428f5-110">Ale pokud budoucí verze aplikace Visual Basic definuje new – klíčové slovo, které jsou v konfliktu s existující formuláře nebo název ovládacího prvku, pak můžete tento postup při aktualizaci kódu pro práci s novou verzí.</span><span class="sxs-lookup"><span data-stu-id="428f5-110">However, if a future version of Visual Basic defines a new keyword that conflicts with an existing form or control name, then you can use this technique when updating your code to work with the new version.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="428f5-111">Váš program také mohou zahrnovat názvy elementů od ostatních odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="428f5-111">Your program also might include element names provided by other referenced assemblies.</span></span> <span data-ttu-id="428f5-112">Pokud tyto názvy v konfliktu s omezeným klíčová slova, pak umístění hranaté závorky je obcházet způsobí, že je interpretovat jako definované prvky jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="428f5-112">If these names conflict with restricted keywords, then placing square brackets around them causes Visual Basic to interpret them as your defined elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="428f5-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="428f5-113">See Also</span></span>  
 [<span data-ttu-id="428f5-114">Zásady vytváření názvů jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="428f5-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="428f5-115">Struktura programu a pravidla týkající se kódu</span><span class="sxs-lookup"><span data-stu-id="428f5-115">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="428f5-116">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="428f5-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
