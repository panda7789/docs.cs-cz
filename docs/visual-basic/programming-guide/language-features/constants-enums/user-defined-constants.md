---
title: Uživatelem definované konstanty
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: 194a420b3749ca5c858a65c07b8c164287c1582a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354010"
---
# <a name="user-defined-constants-visual-basic"></a><span data-ttu-id="4359c-102">Uživatelem definované konstanty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4359c-102">User-Defined Constants (Visual Basic)</span></span>
<span data-ttu-id="4359c-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span><span class="sxs-lookup"><span data-stu-id="4359c-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="4359c-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span><span class="sxs-lookup"><span data-stu-id="4359c-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="4359c-105">You can use constants that are defined by the controls or components you work with, or you can create your own.</span><span class="sxs-lookup"><span data-stu-id="4359c-105">You can use constants that are defined by the controls or components you work with, or you can create your own.</span></span> <span data-ttu-id="4359c-106">Constants you create yourself are described as *user-defined*.</span><span class="sxs-lookup"><span data-stu-id="4359c-106">Constants you create yourself are described as *user-defined*.</span></span>  
  
 <span data-ttu-id="4359c-107">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span><span class="sxs-lookup"><span data-stu-id="4359c-107">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="4359c-108">If `Option Strict` is `On`, you must explicitly declare the constant type.</span><span class="sxs-lookup"><span data-stu-id="4359c-108">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
## <a name="const-statement-usage"></a><span data-ttu-id="4359c-109">Const Statement Usage</span><span class="sxs-lookup"><span data-stu-id="4359c-109">Const Statement Usage</span></span>  
 <span data-ttu-id="4359c-110">A `Const` statement can represent a mathematical or date/time quantity:</span><span class="sxs-lookup"><span data-stu-id="4359c-110">A `Const` statement can represent a mathematical or date/time quantity:</span></span>  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 <span data-ttu-id="4359c-111">It also can define `String` constants:</span><span class="sxs-lookup"><span data-stu-id="4359c-111">It also can define `String` constants:</span></span>  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 <span data-ttu-id="4359c-112">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span><span class="sxs-lookup"><span data-stu-id="4359c-112">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span></span> <span data-ttu-id="4359c-113">You can even define constants in terms of previously defined constants:</span><span class="sxs-lookup"><span data-stu-id="4359c-113">You can even define constants in terms of previously defined constants:</span></span>  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a><span data-ttu-id="4359c-114">Scope of User-Defined Constants</span><span class="sxs-lookup"><span data-stu-id="4359c-114">Scope of User-Defined Constants</span></span>  
 <span data-ttu-id="4359c-115">A `Const` statement's scope is the same as that of a variable declared in the same location.</span><span class="sxs-lookup"><span data-stu-id="4359c-115">A `Const` statement's scope is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="4359c-116">You can specify scope in any of the following ways:</span><span class="sxs-lookup"><span data-stu-id="4359c-116">You can specify scope in any of the following ways:</span></span>  
  
- <span data-ttu-id="4359c-117">To create a constant that exists only within a procedure, declare it within that procedure.</span><span class="sxs-lookup"><span data-stu-id="4359c-117">To create a constant that exists only within a procedure, declare it within that procedure.</span></span>  
  
- <span data-ttu-id="4359c-118">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span><span class="sxs-lookup"><span data-stu-id="4359c-118">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span></span>  
  
- <span data-ttu-id="4359c-119">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span><span class="sxs-lookup"><span data-stu-id="4359c-119">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span></span>  
  
- <span data-ttu-id="4359c-120">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span><span class="sxs-lookup"><span data-stu-id="4359c-120">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span></span>  
  
 <span data-ttu-id="4359c-121">For more information, see [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span><span class="sxs-lookup"><span data-stu-id="4359c-121">For more information, see [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span></span>  
  
### <a name="avoiding-circular-references"></a><span data-ttu-id="4359c-122">Avoiding Circular References</span><span class="sxs-lookup"><span data-stu-id="4359c-122">Avoiding Circular References</span></span>  
 <span data-ttu-id="4359c-123">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span><span class="sxs-lookup"><span data-stu-id="4359c-123">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span></span> <span data-ttu-id="4359c-124">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span><span class="sxs-lookup"><span data-stu-id="4359c-124">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 <span data-ttu-id="4359c-125">If a cycle occurs, Visual Basic generates a compiler error.</span><span class="sxs-lookup"><span data-stu-id="4359c-125">If a cycle occurs, Visual Basic generates a compiler error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4359c-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4359c-126">See also</span></span>

- [<span data-ttu-id="4359c-127">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="4359c-127">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="4359c-128">Datové typy konstanty a literálu</span><span class="sxs-lookup"><span data-stu-id="4359c-128">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="4359c-129">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="4359c-129">Constants and Enumerations</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [<span data-ttu-id="4359c-130">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="4359c-130">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="4359c-131">Přehled výčtů</span><span class="sxs-lookup"><span data-stu-id="4359c-131">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [<span data-ttu-id="4359c-132">Přehled konstant</span><span class="sxs-lookup"><span data-stu-id="4359c-132">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="4359c-133">How to: Declare an Enumeration</span><span class="sxs-lookup"><span data-stu-id="4359c-133">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="4359c-134">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="4359c-134">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="4359c-135">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="4359c-135">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
