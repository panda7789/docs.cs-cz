---
title: 'Postupy: Deklarace struktury'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: a6b70d0973e92db90e35e61b7fed2279c5b0bac3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393971"
---
# <a name="how-to-declare-a-structure-visual-basic"></a><span data-ttu-id="7e3e5-102">Postupy: Definice struktury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e3e5-102">How to: Declare a Structure (Visual Basic)</span></span>
<span data-ttu-id="7e3e5-103">Zahájíte deklaraci struktury pomocí [příkazu struktury](../../../language-reference/statements/structure-statement.md)a ukončíte ji `End Structure` příkazem.</span><span class="sxs-lookup"><span data-stu-id="7e3e5-103">You begin a structure declaration with the [Structure Statement](../../../language-reference/statements/structure-statement.md), and you end it with the `End Structure` statement.</span></span> <span data-ttu-id="7e3e5-104">Mezi těmito dvěma příkazy musíte deklarovat alespoň jeden *prvek*.</span><span class="sxs-lookup"><span data-stu-id="7e3e5-104">Between these two statements you must declare at least one *element*.</span></span> <span data-ttu-id="7e3e5-105">Prvky mohou být libovolného datového typu, ale nejméně jedna musí být buď nesdílená proměnná, nebo nesdílená, nevlastní událost.</span><span class="sxs-lookup"><span data-stu-id="7e3e5-105">The elements can be of any data type, but at least one must be either a nonshared variable or a nonshared, noncustom event.</span></span>  
  
 <span data-ttu-id="7e3e5-106">V deklaraci struktury nelze inicializovat žádné prvky struktury.</span><span class="sxs-lookup"><span data-stu-id="7e3e5-106">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="7e3e5-107">Pokud deklarujete proměnnou, která má být typu struktury, přiřazujete hodnoty k prvkům jejich přístupem přes proměnnou.</span><span class="sxs-lookup"><span data-stu-id="7e3e5-107">When you declare a variable to be of a structure type, you assign values to the elements by accessing them through the variable.</span></span>  
  
 <span data-ttu-id="7e3e5-108">Diskuzi o rozdílech mezi strukturami a třídami naleznete v tématu [struktury a třídy](structures-and-classes.md).</span><span class="sxs-lookup"><span data-stu-id="7e3e5-108">For a discussion of the differences between structures and classes, see [Structures and Classes](structures-and-classes.md).</span></span>  
  
 <span data-ttu-id="7e3e5-109">Pro demonstrační účely Zvažte situaci, kdy si přejete sledovat jméno zaměstnance, telefonní linky a mzdu.</span><span class="sxs-lookup"><span data-stu-id="7e3e5-109">For demonstration purposes, consider a situation where you want to keep track of an employee's name, telephone extension, and salary.</span></span> <span data-ttu-id="7e3e5-110">Struktura vám to umožňuje v rámci jedné proměnné.</span><span class="sxs-lookup"><span data-stu-id="7e3e5-110">A structure allows you to do this in a single variable.</span></span>  
  
### <a name="to-declare-a-structure"></a><span data-ttu-id="7e3e5-111">Deklarace struktury</span><span class="sxs-lookup"><span data-stu-id="7e3e5-111">To declare a structure</span></span>  
  
1. <span data-ttu-id="7e3e5-112">Vytvořte na začátku a konci příkazy pro strukturu.</span><span class="sxs-lookup"><span data-stu-id="7e3e5-112">Create the beginning and ending statements for the structure.</span></span>  
  
     <span data-ttu-id="7e3e5-113">Úroveň přístupu ke struktuře můžete určit pomocí klíčového slova [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md)nebo [Private](../../../language-reference/modifiers/private.md) , nebo můžete nechat výchozí hodnotu `Public` .</span><span class="sxs-lookup"><span data-stu-id="7e3e5-113">You can specify the access level of a structure using the [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md), or [Private](../../../language-reference/modifiers/private.md) keyword, or you can let it default to `Public`.</span></span>  
  
    ```vb  
    Private Structure employee  
    End Structure  
    ```  
  
2. <span data-ttu-id="7e3e5-114">Přidejte prvky do těla struktury.</span><span class="sxs-lookup"><span data-stu-id="7e3e5-114">Add elements to the body of the structure.</span></span>  
  
     <span data-ttu-id="7e3e5-115">Struktura musí mít alespoň jeden element.</span><span class="sxs-lookup"><span data-stu-id="7e3e5-115">A structure must have at least one element.</span></span> <span data-ttu-id="7e3e5-116">Musíte deklarovat každý prvek a zadat úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="7e3e5-116">You must declare every element and specify an access level for it.</span></span> <span data-ttu-id="7e3e5-117">Použijete-li [příkaz Dim](../../../language-reference/statements/dim-statement.md) bez klíčových slov, je výchozím nastavením přístupnosti `Public` .</span><span class="sxs-lookup"><span data-stu-id="7e3e5-117">If you use the [Dim Statement](../../../language-reference/statements/dim-statement.md) without any keywords, the accessibility defaults to `Public`.</span></span>  
  
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
  
     <span data-ttu-id="7e3e5-118">`salary`Pole v předchozím příkladu je `Private` , což znamená, že je nepřístupný mimo strukturu, dokonce i z nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="7e3e5-118">The `salary` field in the preceding example is `Private`, which means it is inaccessible outside the structure, even from the containing class.</span></span> <span data-ttu-id="7e3e5-119">`giveRaise`Postup je však `Public` , aby jej bylo možné volat mimo strukturu.</span><span class="sxs-lookup"><span data-stu-id="7e3e5-119">However, the `giveRaise` procedure is `Public`, so it can be called from outside the structure.</span></span> <span data-ttu-id="7e3e5-120">Podobně lze `salaryReviewTime` událost vyvolat mimo strukturu.</span><span class="sxs-lookup"><span data-stu-id="7e3e5-120">Similarly, you can raise the `salaryReviewTime` event from outside the structure.</span></span>  
  
     <span data-ttu-id="7e3e5-121">Kromě proměnných, `Sub` procedur a událostí můžete také definovat konstanty, `Function` procedury a vlastnosti ve struktuře.</span><span class="sxs-lookup"><span data-stu-id="7e3e5-121">In addition to variables, `Sub` procedures, and events, you can also define constants, `Function` procedures, and properties in a structure.</span></span> <span data-ttu-id="7e3e5-122">Můžete určit maximálně jednu vlastnost jako *výchozí vlastnost*za předpokladu, že převezme aspoň jeden argument.</span><span class="sxs-lookup"><span data-stu-id="7e3e5-122">You can designate at most one property as the *default property*, provided it takes at least one argument.</span></span> <span data-ttu-id="7e3e5-123">Událost můžete zpracovat pomocí [sdílené](../../../language-reference/modifiers/shared.md) `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="7e3e5-123">You can handle an event with a [Shared](../../../language-reference/modifiers/shared.md)`Sub` procedure.</span></span> <span data-ttu-id="7e3e5-124">Další informace naleznete v tématu [Postupy: deklarace a volání výchozí vlastnosti v Visual Basic](../procedures/how-to-declare-and-call-a-default-property.md).</span><span class="sxs-lookup"><span data-stu-id="7e3e5-124">For more information, see [How to: Declare and Call a Default Property in Visual Basic](../procedures/how-to-declare-and-call-a-default-property.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e3e5-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e3e5-125">See also</span></span>

- [<span data-ttu-id="7e3e5-126">Datové typy</span><span class="sxs-lookup"><span data-stu-id="7e3e5-126">Data Types</span></span>](index.md)
- [<span data-ttu-id="7e3e5-127">Základní datové typy</span><span class="sxs-lookup"><span data-stu-id="7e3e5-127">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="7e3e5-128">Složené datové typy</span><span class="sxs-lookup"><span data-stu-id="7e3e5-128">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="7e3e5-129">Typy hodnot a typy odkazu</span><span class="sxs-lookup"><span data-stu-id="7e3e5-129">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="7e3e5-130">Struktury</span><span class="sxs-lookup"><span data-stu-id="7e3e5-130">Structures</span></span>](structures.md)
- [<span data-ttu-id="7e3e5-131">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="7e3e5-131">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="7e3e5-132">Proměnné struktury</span><span class="sxs-lookup"><span data-stu-id="7e3e5-132">Structure Variables</span></span>](structure-variables.md)
- [<span data-ttu-id="7e3e5-133">Struktury a ostatní programovací elementy</span><span class="sxs-lookup"><span data-stu-id="7e3e5-133">Structures and Other Programming Elements</span></span>](structures-and-other-programming-elements.md)
- [<span data-ttu-id="7e3e5-134">Struktury a třídy</span><span class="sxs-lookup"><span data-stu-id="7e3e5-134">Structures and Classes</span></span>](structures-and-classes.md)
- [<span data-ttu-id="7e3e5-135">Uživatelský datový typ</span><span class="sxs-lookup"><span data-stu-id="7e3e5-135">User-Defined Data Type</span></span>](../../../language-reference/data-types/user-defined-data-type.md)
