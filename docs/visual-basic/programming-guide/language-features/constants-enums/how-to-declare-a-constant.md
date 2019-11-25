---
title: 'Postupy: Deklarace konstanty'
ms.date: 07/20/2015
f1_keywords:
- vb.constant
helpviewer_keywords:
- Integer data type [Visual Basic], declaring constants
- Single data type [Visual Basic], declaring constants
- Const statement [Visual Basic], declaring constants
- procedures [Visual Basic], declaration
- data types [Visual Basic], constants
- Long data type [Visual Basic], declaring constants
- Visual Basic code, declaring variables and constants
- Double data type [Visual Basic], declaring constants
- Boolean data type [Visual Basic], declaring constants
- modules, declaring constants
- Byte data type [Visual Basic], declaring constants
- constants [Visual Basic], declaring
- Date data type [Visual Basic], declaring constants
- String data type [Visual Basic], declaring constants
- declaring constants [Visual Basic], const keyword
- Currency data type [Visual Basic], declaring constants and variants
- module-level constants and variables
- Object data type [Visual Basic], declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
ms.openlocfilehash: 5054d4a4fc02d8bd22efceb01770fc54167d8cb3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347474"
---
# <a name="how-to-declare-a-constant-visual-basic"></a><span data-ttu-id="14fa1-102">Postupy: Deklarace konstanty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14fa1-102">How to: Declare A Constant (Visual Basic)</span></span>
<span data-ttu-id="14fa1-103">You use the `Const` statement to declare a constant and set its value.</span><span class="sxs-lookup"><span data-stu-id="14fa1-103">You use the `Const` statement to declare a constant and set its value.</span></span> <span data-ttu-id="14fa1-104">By declaring a constant, you assign a meaningful name to a value.</span><span class="sxs-lookup"><span data-stu-id="14fa1-104">By declaring a constant, you assign a meaningful name to a value.</span></span> <span data-ttu-id="14fa1-105">Once a constant is declared, it cannot be modified or assigned a new value.</span><span class="sxs-lookup"><span data-stu-id="14fa1-105">Once a constant is declared, it cannot be modified or assigned a new value.</span></span>  
  
 <span data-ttu-id="14fa1-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span><span class="sxs-lookup"><span data-stu-id="14fa1-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span></span> <span data-ttu-id="14fa1-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span><span class="sxs-lookup"><span data-stu-id="14fa1-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span></span>  
  
 <span data-ttu-id="14fa1-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span><span class="sxs-lookup"><span data-stu-id="14fa1-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a><span data-ttu-id="14fa1-109">To declare a constant</span><span class="sxs-lookup"><span data-stu-id="14fa1-109">To declare a constant</span></span>  
  
- <span data-ttu-id="14fa1-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span><span class="sxs-lookup"><span data-stu-id="14fa1-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     <span data-ttu-id="14fa1-111">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span><span class="sxs-lookup"><span data-stu-id="14fa1-111">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span></span>  
  
     <span data-ttu-id="14fa1-112">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span><span class="sxs-lookup"><span data-stu-id="14fa1-112">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="14fa1-113">The compiler determines the type of the constant from the type of the expression.</span><span class="sxs-lookup"><span data-stu-id="14fa1-113">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="14fa1-114">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="14fa1-114">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span></span>  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a><span data-ttu-id="14fa1-115">To declare a constant that has an explicitly stated data type</span><span class="sxs-lookup"><span data-stu-id="14fa1-115">To declare a constant that has an explicitly stated data type</span></span>  
  
- <span data-ttu-id="14fa1-116">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span><span class="sxs-lookup"><span data-stu-id="14fa1-116">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     <span data-ttu-id="14fa1-117">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span><span class="sxs-lookup"><span data-stu-id="14fa1-117">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span></span> <span data-ttu-id="14fa1-118">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span><span class="sxs-lookup"><span data-stu-id="14fa1-118">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span></span>  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a><span data-ttu-id="14fa1-119">To declare multiple constants on a single line</span><span class="sxs-lookup"><span data-stu-id="14fa1-119">To declare multiple constants on a single line</span></span>  
  
- <span data-ttu-id="14fa1-120">Separate the declarations with a comma and a space, as in the following example:</span><span class="sxs-lookup"><span data-stu-id="14fa1-120">Separate the declarations with a comma and a space, as in the following example:</span></span>  
  
    ```vb  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="14fa1-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14fa1-121">See also</span></span>

- [<span data-ttu-id="14fa1-122">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="14fa1-122">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="14fa1-123">Datové typy konstanty a literálu</span><span class="sxs-lookup"><span data-stu-id="14fa1-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="14fa1-124">Přehled konstant</span><span class="sxs-lookup"><span data-stu-id="14fa1-124">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="14fa1-125">Postupy: Deklarace konstanty</span><span class="sxs-lookup"><span data-stu-id="14fa1-125">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)
- [<span data-ttu-id="14fa1-126">Uživatelem definované konstanty</span><span class="sxs-lookup"><span data-stu-id="14fa1-126">User-Defined Constants</span></span>](user-defined-constants.md)
- [<span data-ttu-id="14fa1-127">Datové typy konstanty a literálu</span><span class="sxs-lookup"><span data-stu-id="14fa1-127">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="14fa1-128">Postupy: Seskupení souvisejících hodnot konstant</span><span class="sxs-lookup"><span data-stu-id="14fa1-128">How to: Group Related Constant Values Together</span></span>](how-to-group-related-constant-values-together.md)
- [<span data-ttu-id="14fa1-129">Přehled výčtů</span><span class="sxs-lookup"><span data-stu-id="14fa1-129">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="14fa1-130">Postupy: Deklarace výčtů</span><span class="sxs-lookup"><span data-stu-id="14fa1-130">How to: Declare Enumerations</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="14fa1-131">Postupy: Odkazování na člena výčtu</span><span class="sxs-lookup"><span data-stu-id="14fa1-131">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="14fa1-132">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="14fa1-132">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="14fa1-133">Postupy: Iterace ve výčtu</span><span class="sxs-lookup"><span data-stu-id="14fa1-133">How to: Iterate Through An Enumeration</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="14fa1-134">Postupy: Určení řetězce spojeného s hodnotou výčtu</span><span class="sxs-lookup"><span data-stu-id="14fa1-134">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="14fa1-135">Kdy použít výčet</span><span class="sxs-lookup"><span data-stu-id="14fa1-135">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)

- [<span data-ttu-id="14fa1-136">Přehled výčtů</span><span class="sxs-lookup"><span data-stu-id="14fa1-136">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="14fa1-137">Přehled konstant</span><span class="sxs-lookup"><span data-stu-id="14fa1-137">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="14fa1-138">How to: Declare an Enumeration</span><span class="sxs-lookup"><span data-stu-id="14fa1-138">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="14fa1-139">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="14fa1-139">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="14fa1-140">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="14fa1-140">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="14fa1-141">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="14fa1-141">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
