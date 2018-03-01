---
title: 'Postupy: Deklarace konstanty (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 554f659e060087228fb43efd8b9d06103e21e980
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-a-constant-visual-basic"></a><span data-ttu-id="d0ad9-102">Postupy: Deklarace konstanty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0ad9-102">How to: Declare A Constant (Visual Basic)</span></span>
<span data-ttu-id="d0ad9-103">Můžete použít `Const` příkaz deklarace konstanty a nastavení jeho hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d0ad9-103">You use the `Const` statement to declare a constant and set its value.</span></span> <span data-ttu-id="d0ad9-104">Deklarováním konstanta, přiřaďte k hodnotě nějaký výstižný název.</span><span class="sxs-lookup"><span data-stu-id="d0ad9-104">By declaring a constant, you assign a meaningful name to a value.</span></span> <span data-ttu-id="d0ad9-105">Jakmile je deklarovaná konstanta, nelze změnit ani přiřazena nová hodnota.</span><span class="sxs-lookup"><span data-stu-id="d0ad9-105">Once a constant is declared, it cannot be modified or assigned a new value.</span></span>  
  
 <span data-ttu-id="d0ad9-106">Můžete deklarace konstanty v rámci procedury nebo v části deklarace modulu, třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="d0ad9-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span></span> <span data-ttu-id="d0ad9-107">Třída nebo konstanty na úrovni struktura `Private` ve výchozím nastavení, ale také může být deklarována jako `Public`, `Friend`, `Protected`, nebo `Protected Friend` pro příslušnou úroveň přístupu, kód.</span><span class="sxs-lookup"><span data-stu-id="d0ad9-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span></span>  
  
 <span data-ttu-id="d0ad9-108">Konstanty musí mít platný symbolický název (pravidla jsou stejné jako pro vytvoření názvy proměnných) a výrazu složený numeric nebo string konstanty a operátory (ale žádná volání funkce).</span><span class="sxs-lookup"><span data-stu-id="d0ad9-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a><span data-ttu-id="d0ad9-109">Chcete-li deklarace konstanty</span><span class="sxs-lookup"><span data-stu-id="d0ad9-109">To declare a constant</span></span>  
  
-   <span data-ttu-id="d0ad9-110">Zápis deklaraci, která zahrnuje specifikátor přístupu, `Const` – klíčové slovo a výraz, jako v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="d0ad9-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#8](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]  
  
     <span data-ttu-id="d0ad9-111">Když [Option Infer –](../../../../visual-basic/language-reference/statements/option-infer-statement.md) je `Off` a [možnost striktní](../../../../visual-basic/language-reference/statements/option-strict-statement.md) je `On`, musí deklarovat konstantu explicitně zadáním datový typ (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, nebo `String`).</span><span class="sxs-lookup"><span data-stu-id="d0ad9-111">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span></span>  
  
     <span data-ttu-id="d0ad9-112">Když `Option Infer` je `On` nebo `Option Strict` je `Off`, můžou deklarovat konstanta bez zadání datový typ s `As` klauzule.</span><span class="sxs-lookup"><span data-stu-id="d0ad9-112">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="d0ad9-113">Kompilátor Určuje typ konstanty z typu výraz.</span><span class="sxs-lookup"><span data-stu-id="d0ad9-113">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="d0ad9-114">Další informace najdete v tématu [literálové datové typy a konstanta](constant-and-literal-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="d0ad9-114">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span></span>  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a><span data-ttu-id="d0ad9-115">Chcete-li deklarovat konstanta, která má explicitně stanovené datový typ.</span><span class="sxs-lookup"><span data-stu-id="d0ad9-115">To declare a constant that has an explicitly stated data type</span></span>  
  
-   <span data-ttu-id="d0ad9-116">Zápis deklaraci, která zahrnuje `As` – klíčové slovo a explicitního datového typu, jako v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="d0ad9-116">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#9](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]  
  
     <span data-ttu-id="d0ad9-117">Na jeden řádek, můžou deklarovat více konstanty, i když váš kód je lépe čitelný, pokud je deklarovat pouze jeden konstanta na každý řádek.</span><span class="sxs-lookup"><span data-stu-id="d0ad9-117">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span></span> <span data-ttu-id="d0ad9-118">Pokud je na jednom řádku deklarovat několik konstanty, se musí mít stejnou úroveň přístupu (`Public`, `Private`, `Friend`, `Protected`, nebo `Protected Friend`).</span><span class="sxs-lookup"><span data-stu-id="d0ad9-118">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span></span>  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a><span data-ttu-id="d0ad9-119">Deklarovat na jednom řádku více konstant</span><span class="sxs-lookup"><span data-stu-id="d0ad9-119">To declare multiple constants on a single line</span></span>  
  
-   <span data-ttu-id="d0ad9-120">Deklarací oddělte čárkou a mezerou, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d0ad9-120">Separate the declarations with a comma and a space, as in the following example:</span></span>  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d0ad9-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0ad9-121">See Also</span></span>  
 [<span data-ttu-id="d0ad9-122">Const – příkaz</span><span class="sxs-lookup"><span data-stu-id="d0ad9-122">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="d0ad9-123">Datové typy konstanty a literálu</span><span class="sxs-lookup"><span data-stu-id="d0ad9-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)  
 <span data-ttu-id="d0ad9-124">[Přehled konstant](constants-overview.md) [postupy: deklarace konstanty](how-to-declare-a-constant.md) [uživatelem definované konstanty](user-defined-constants.md) [datové typy konstanty a literálu](constant-and-literal-data-types.md) [postup: skupiny Souvisejících hodnot konstant](how-to-group-related-constant-values-together.md) [přehled výčtů](enumerations-overview.md) [postupy: deklarace výčtů](how-to-declare-enumerations.md) [postupy: odkazování na člena výčtu](how-to-refer-to-an-enumeration-member.md) [Výčty a kvalifikace názvu](enumerations-and-name-qualification.md) [postupy: iterace výčet](how-to-iterate-through-an-enumeration.md) [postupy: určení řetězce spojeného s hodnotou výčtu](how-to-determine-the-string-associated-with-an-enumeration-value.md) [Kdy použít výčet](when-to-use-an-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="d0ad9-124">[Constants Overview](constants-overview.md) [How to: Declare A Constant](how-to-declare-a-constant.md) [User-Defined Constants](user-defined-constants.md) [Constant and Literal Data Types](constant-and-literal-data-types.md) [How to: Group Related Constant Values Together](how-to-group-related-constant-values-together.md) [Enumerations Overview](enumerations-overview.md) [How to: Declare Enumerations](how-to-declare-enumerations.md) [How to: Refer to an Enumeration Member](how-to-refer-to-an-enumeration-member.md) [Enumerations and Name Qualification](enumerations-and-name-qualification.md) [How to: Iterate Through An Enumeration](how-to-iterate-through-an-enumeration.md) [How to: Determine the String Associated with an Enumeration Value](how-to-determine-the-string-associated-with-an-enumeration-value.md) [When to Use an Enumeration](when-to-use-an-enumeration.md)</span></span>

 [<span data-ttu-id="d0ad9-125">Přehled výčtů</span><span class="sxs-lookup"><span data-stu-id="d0ad9-125">Enumerations Overview</span></span>](enumerations-overview.md)  
 [<span data-ttu-id="d0ad9-126">Přehled konstant</span><span class="sxs-lookup"><span data-stu-id="d0ad9-126">Constants Overview</span></span>](constants-overview.md)  
 [<span data-ttu-id="d0ad9-127">Postupy: deklarace výčtů</span><span class="sxs-lookup"><span data-stu-id="d0ad9-127">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)  
 [<span data-ttu-id="d0ad9-128">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="d0ad9-128">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)  
 [<span data-ttu-id="d0ad9-129">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="d0ad9-129">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="d0ad9-130">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="d0ad9-130">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
