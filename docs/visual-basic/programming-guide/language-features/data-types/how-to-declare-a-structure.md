---
title: 'Postupy: Definice struktury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: c3090b5b8e53e5a5a990ae11c91464797bde9803
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582309"
---
# <a name="how-to-declare-a-structure-visual-basic"></a><span data-ttu-id="6f85a-102">Postupy: Definice struktury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f85a-102">How to: Declare a Structure (Visual Basic)</span></span>
<span data-ttu-id="6f85a-103">Zahájíte deklaraci struktury pomocí [příkazu struktury](../../../../visual-basic/language-reference/statements/structure-statement.md)a ukončíte ji pomocí příkazu `End Structure`.</span><span class="sxs-lookup"><span data-stu-id="6f85a-103">You begin a structure declaration with the [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md), and you end it with the `End Structure` statement.</span></span> <span data-ttu-id="6f85a-104">Mezi těmito dvěma příkazy musíte deklarovat alespoň jeden *prvek*.</span><span class="sxs-lookup"><span data-stu-id="6f85a-104">Between these two statements you must declare at least one *element*.</span></span> <span data-ttu-id="6f85a-105">Prvky mohou být libovolného datového typu, ale nejméně jedna musí být buď nesdílená proměnná, nebo nesdílená, nevlastní událost.</span><span class="sxs-lookup"><span data-stu-id="6f85a-105">The elements can be of any data type, but at least one must be either a nonshared variable or a nonshared, noncustom event.</span></span>  
  
 <span data-ttu-id="6f85a-106">V deklaraci struktury nelze inicializovat žádné prvky struktury.</span><span class="sxs-lookup"><span data-stu-id="6f85a-106">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="6f85a-107">Pokud deklarujete proměnnou, která má být typu struktury, přiřazujete hodnoty k prvkům jejich přístupem přes proměnnou.</span><span class="sxs-lookup"><span data-stu-id="6f85a-107">When you declare a variable to be of a structure type, you assign values to the elements by accessing them through the variable.</span></span>  
  
 <span data-ttu-id="6f85a-108">Diskuzi o rozdílech mezi strukturami a třídami naleznete v tématu [struktury a třídy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).</span><span class="sxs-lookup"><span data-stu-id="6f85a-108">For a discussion of the differences between structures and classes, see [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).</span></span>  
  
 <span data-ttu-id="6f85a-109">Pro demonstrační účely Zvažte situaci, kdy si přejete sledovat jméno zaměstnance, telefonní linky a mzdu.</span><span class="sxs-lookup"><span data-stu-id="6f85a-109">For demonstration purposes, consider a situation where you want to keep track of an employee's name, telephone extension, and salary.</span></span> <span data-ttu-id="6f85a-110">Struktura vám to umožňuje v rámci jedné proměnné.</span><span class="sxs-lookup"><span data-stu-id="6f85a-110">A structure allows you to do this in a single variable.</span></span>  
  
### <a name="to-declare-a-structure"></a><span data-ttu-id="6f85a-111">Deklarace struktury</span><span class="sxs-lookup"><span data-stu-id="6f85a-111">To declare a structure</span></span>  
  
1. <span data-ttu-id="6f85a-112">Vytvořte na začátku a konci příkazy pro strukturu.</span><span class="sxs-lookup"><span data-stu-id="6f85a-112">Create the beginning and ending statements for the structure.</span></span>  
  
     <span data-ttu-id="6f85a-113">Úroveň přístupu ke struktuře můžete určit pomocí klíčového slova [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)nebo [Private](../../../../visual-basic/language-reference/modifiers/private.md) , nebo můžete nechat výchozí `Public`.</span><span class="sxs-lookup"><span data-stu-id="6f85a-113">You can specify the access level of a structure using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, or you can let it default to `Public`.</span></span>  
  
    ```vb  
    Private Structure employee  
    End Structure  
    ```  
  
2. <span data-ttu-id="6f85a-114">Přidejte prvky do těla struktury.</span><span class="sxs-lookup"><span data-stu-id="6f85a-114">Add elements to the body of the structure.</span></span>  
  
     <span data-ttu-id="6f85a-115">Struktura musí mít alespoň jeden element.</span><span class="sxs-lookup"><span data-stu-id="6f85a-115">A structure must have at least one element.</span></span> <span data-ttu-id="6f85a-116">Musíte deklarovat každý prvek a zadat úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="6f85a-116">You must declare every element and specify an access level for it.</span></span> <span data-ttu-id="6f85a-117">Použijete-li [příkaz Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) bez klíčových slov, je výchozí nastavení přístupnosti `Public`.</span><span class="sxs-lookup"><span data-stu-id="6f85a-117">If you use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) without any keywords, the accessibility defaults to `Public`.</span></span>  
  
    ```vb  
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
  
     <span data-ttu-id="6f85a-118">Pole `salary` v předchozím příkladu je `Private`, což znamená, že je nepřístupný mimo strukturu, dokonce i z nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="6f85a-118">The `salary` field in the preceding example is `Private`, which means it is inaccessible outside the structure, even from the containing class.</span></span> <span data-ttu-id="6f85a-119">Nicméně procedura `giveRaise` je `Public`, takže může být volána mimo strukturu.</span><span class="sxs-lookup"><span data-stu-id="6f85a-119">However, the `giveRaise` procedure is `Public`, so it can be called from outside the structure.</span></span> <span data-ttu-id="6f85a-120">Podobně můžete vyvolat událost `salaryReviewTime` mimo strukturu.</span><span class="sxs-lookup"><span data-stu-id="6f85a-120">Similarly, you can raise the `salaryReviewTime` event from outside the structure.</span></span>  
  
     <span data-ttu-id="6f85a-121">Kromě proměnných, `Sub` procedur a událostí, můžete také definovat konstanty, `Function` procedury a vlastnosti ve struktuře.</span><span class="sxs-lookup"><span data-stu-id="6f85a-121">In addition to variables, `Sub` procedures, and events, you can also define constants, `Function` procedures, and properties in a structure.</span></span> <span data-ttu-id="6f85a-122">Můžete určit maximálně jednu vlastnost jako *výchozí vlastnost*za předpokladu, že převezme aspoň jeden argument.</span><span class="sxs-lookup"><span data-stu-id="6f85a-122">You can designate at most one property as the *default property*, provided it takes at least one argument.</span></span> <span data-ttu-id="6f85a-123">Událost můžete zpracovat pomocí [sdílené](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="6f85a-123">You can handle an event with a [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub` procedure.</span></span> <span data-ttu-id="6f85a-124">Další informace naleznete v tématu [Postupy: deklarace a volání výchozí vlastnosti v Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).</span><span class="sxs-lookup"><span data-stu-id="6f85a-124">For more information, see [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f85a-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6f85a-125">See also</span></span>

- [<span data-ttu-id="6f85a-126">Datové typy</span><span class="sxs-lookup"><span data-stu-id="6f85a-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="6f85a-127">Základní datové typy</span><span class="sxs-lookup"><span data-stu-id="6f85a-127">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="6f85a-128">Složené datové typy</span><span class="sxs-lookup"><span data-stu-id="6f85a-128">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="6f85a-129">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="6f85a-129">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="6f85a-130">Struktury</span><span class="sxs-lookup"><span data-stu-id="6f85a-130">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="6f85a-131">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="6f85a-131">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="6f85a-132">Proměnné struktury</span><span class="sxs-lookup"><span data-stu-id="6f85a-132">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [<span data-ttu-id="6f85a-133">Struktury a ostatní programovací elementy</span><span class="sxs-lookup"><span data-stu-id="6f85a-133">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [<span data-ttu-id="6f85a-134">Struktury a třídy</span><span class="sxs-lookup"><span data-stu-id="6f85a-134">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="6f85a-135">Uživatelský datový typ</span><span class="sxs-lookup"><span data-stu-id="6f85a-135">User-Defined Data Type</span></span>](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
