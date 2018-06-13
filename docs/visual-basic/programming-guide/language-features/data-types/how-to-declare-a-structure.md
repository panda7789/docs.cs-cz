---
title: 'Postupy: Definice struktury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: 6128addd60609bfc88a1409648fb320bc7089974
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650024"
---
# <a name="how-to-declare-a-structure-visual-basic"></a><span data-ttu-id="cadf2-102">Postupy: Definice struktury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cadf2-102">How to: Declare a Structure (Visual Basic)</span></span>
<span data-ttu-id="cadf2-103">Zahájit deklarace struktury s [Structure – příkaz](../../../../visual-basic/language-reference/statements/structure-statement.md), a její `End` `Structure` příkaz.</span><span class="sxs-lookup"><span data-stu-id="cadf2-103">You begin a structure declaration with the [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md), and you end it with the `End` `Structure` statement.</span></span> <span data-ttu-id="cadf2-104">Mezi tyto dva příkazy, musí deklarovat alespoň jeden *element*.</span><span class="sxs-lookup"><span data-stu-id="cadf2-104">Between these two statements you must declare at least one *element*.</span></span> <span data-ttu-id="cadf2-105">Elementy mohou být jakéhokoli typu dat, ale alespoň jeden musí být na sdíleném proměnnou nebo sdíleném, nevlastní událostí.</span><span class="sxs-lookup"><span data-stu-id="cadf2-105">The elements can be of any data type, but at least one must be either a nonshared variable or a nonshared, noncustom event.</span></span>  
  
 <span data-ttu-id="cadf2-106">Nelze inicializovat všechny elementy struktury v deklarace struktury.</span><span class="sxs-lookup"><span data-stu-id="cadf2-106">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="cadf2-107">Když je deklarovat proměnnou být typu Struktura, přiřadit hodnoty k elementům podle k nim přistupovat pomocí proměnné.</span><span class="sxs-lookup"><span data-stu-id="cadf2-107">When you declare a variable to be of a structure type, you assign values to the elements by accessing them through the variable.</span></span>  
  
 <span data-ttu-id="cadf2-108">Informace o rozdílech mezi struktury a třídy, najdete v části [struktury a třídy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).</span><span class="sxs-lookup"><span data-stu-id="cadf2-108">For a discussion of the differences between structures and classes, see [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).</span></span>  
  
 <span data-ttu-id="cadf2-109">Pro demonstrační účely Představte si situaci, kde chcete uchovávání informací o název, telefonní číslo a mzda zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="cadf2-109">For demonstration purposes, consider a situation where you want to keep track of an employee's name, telephone extension, and salary.</span></span> <span data-ttu-id="cadf2-110">Struktury můžete k tomu do jedné proměnné.</span><span class="sxs-lookup"><span data-stu-id="cadf2-110">A structure allows you to do this in a single variable.</span></span>  
  
### <a name="to-declare-a-structure"></a><span data-ttu-id="cadf2-111">Chcete-li definice struktury</span><span class="sxs-lookup"><span data-stu-id="cadf2-111">To declare a structure</span></span>  
  
1.  <span data-ttu-id="cadf2-112">Vytvořte počáteční a koncové příkazy pro strukturu.</span><span class="sxs-lookup"><span data-stu-id="cadf2-112">Create the beginning and ending statements for the structure.</span></span>  
  
     <span data-ttu-id="cadf2-113">Můžete zadat úroveň přístupu tohoto struktura pomocí [veřejné](../../../../visual-basic/language-reference/modifiers/public.md), [chráněné](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), nebo [privátní](../../../../visual-basic/language-reference/modifiers/private.md) – klíčové slovo, nebo můžete nechat ji ve výchozím nastavení týkají `Public`.</span><span class="sxs-lookup"><span data-stu-id="cadf2-113">You can specify the access level of a structure using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, or you can let it default to `Public`.</span></span>  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2.  <span data-ttu-id="cadf2-114">Přidáte k tělu struktury elementů.</span><span class="sxs-lookup"><span data-stu-id="cadf2-114">Add elements to the body of the structure.</span></span>  
  
     <span data-ttu-id="cadf2-115">Struktury musí mít alespoň jeden element.</span><span class="sxs-lookup"><span data-stu-id="cadf2-115">A structure must have at least one element.</span></span> <span data-ttu-id="cadf2-116">Musíte deklarovat každý element a zadejte úroveň přístupu pro ni.</span><span class="sxs-lookup"><span data-stu-id="cadf2-116">You must declare every element and specify an access level for it.</span></span> <span data-ttu-id="cadf2-117">Pokud použijete [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md) bez jakékoli klíčová slova, usnadnění výchozí `Public`.</span><span class="sxs-lookup"><span data-stu-id="cadf2-117">If you use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) without any keywords, the accessibility defaults to `Public`.</span></span>  
  
    ```  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     <span data-ttu-id="cadf2-118">`salary` Pole v předchozím příkladu je `Private`, což znamená, že je pravděpodobně nepřístupný mimo strukturu, i z obsahující třídy.</span><span class="sxs-lookup"><span data-stu-id="cadf2-118">The `salary` field in the preceding example is `Private`, which means it is inaccessible outside the structure, even from the containing class.</span></span> <span data-ttu-id="cadf2-119">Ale `giveRaise` postup je `Public`, takže může být volána z mimo strukturu.</span><span class="sxs-lookup"><span data-stu-id="cadf2-119">However, the `giveRaise` procedure is `Public`, so it can be called from outside the structure.</span></span> <span data-ttu-id="cadf2-120">Podobně můžete zvýšit `salaryReviewTime` událost z mimo strukturu.</span><span class="sxs-lookup"><span data-stu-id="cadf2-120">Similarly, you can raise the `salaryReviewTime` event from outside the structure.</span></span>  
  
     <span data-ttu-id="cadf2-121">Kromě proměnné `Sub` procedury a události, můžete také definovat konstanty, `Function` procedury a vlastnosti ve struktuře.</span><span class="sxs-lookup"><span data-stu-id="cadf2-121">In addition to variables, `Sub` procedures, and events, you can also define constants, `Function` procedures, and properties in a structure.</span></span> <span data-ttu-id="cadf2-122">Můžete určit maximálně jednu vlastnost jako *výchozí vlastnost*za předpokladu, že trvá nejméně jeden argument.</span><span class="sxs-lookup"><span data-stu-id="cadf2-122">You can designate at most one property as the *default property*, provided it takes at least one argument.</span></span> <span data-ttu-id="cadf2-123">Dokáže zpracovat událost se [sdílené](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="cadf2-123">You can handle an event with a [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub` procedure.</span></span> <span data-ttu-id="cadf2-124">Další informace najdete v tématu [postupy: deklarace a volání výchozí vlastnosti v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).</span><span class="sxs-lookup"><span data-stu-id="cadf2-124">For more information, see [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cadf2-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="cadf2-125">See Also</span></span>  
 [<span data-ttu-id="cadf2-126">Datové typy</span><span class="sxs-lookup"><span data-stu-id="cadf2-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="cadf2-127">Základní datové typy</span><span class="sxs-lookup"><span data-stu-id="cadf2-127">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="cadf2-128">Složené datové typy</span><span class="sxs-lookup"><span data-stu-id="cadf2-128">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="cadf2-129">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="cadf2-129">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="cadf2-130">Struktury</span><span class="sxs-lookup"><span data-stu-id="cadf2-130">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="cadf2-131">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="cadf2-131">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="cadf2-132">Proměnné struktury</span><span class="sxs-lookup"><span data-stu-id="cadf2-132">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 [<span data-ttu-id="cadf2-133">Struktury a ostatní programovací elementy</span><span class="sxs-lookup"><span data-stu-id="cadf2-133">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [<span data-ttu-id="cadf2-134">Struktury a třídy</span><span class="sxs-lookup"><span data-stu-id="cadf2-134">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [<span data-ttu-id="cadf2-135">Uživatelský datový typ</span><span class="sxs-lookup"><span data-stu-id="cadf2-135">User-Defined Data Type</span></span>](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
