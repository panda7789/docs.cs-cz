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
ms.openlocfilehash: ffaa98f6af3d4b276f5c0b1153841acdea0809d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414476"
---
# <a name="how-to-declare-a-constant-visual-basic"></a><span data-ttu-id="add4f-102">Postupy: Deklarace konstanty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="add4f-102">How to: Declare A Constant (Visual Basic)</span></span>
<span data-ttu-id="add4f-103">Použijete `Const` příkaz k deklaraci konstanty a nastavení její hodnoty.</span><span class="sxs-lookup"><span data-stu-id="add4f-103">You use the `Const` statement to declare a constant and set its value.</span></span> <span data-ttu-id="add4f-104">Deklarováním konstanty přiřadíte smysluplný název k hodnotě.</span><span class="sxs-lookup"><span data-stu-id="add4f-104">By declaring a constant, you assign a meaningful name to a value.</span></span> <span data-ttu-id="add4f-105">Jakmile je konstanta deklarována, nelze ji změnit ani jí přiřadit novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="add4f-105">Once a constant is declared, it cannot be modified or assigned a new value.</span></span>  
  
 <span data-ttu-id="add4f-106">Deklarujete konstantu v rámci procedury nebo v oddílu deklarace modulu, třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="add4f-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span></span> <span data-ttu-id="add4f-107">Konstanty na úrovni třídy nebo struktury jsou `Private` ve výchozím nastavení, ale mohou být také deklarovány jako `Public` ,, `Friend` `Protected` nebo `Protected Friend` pro příslušnou úroveň přístupu kódu.</span><span class="sxs-lookup"><span data-stu-id="add4f-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span></span>  
  
 <span data-ttu-id="add4f-108">Konstanta musí mít platný symbolický název (pravidla jsou stejná jako pro vytváření názvů proměnných) a výraz tvořený číselnými nebo řetězcovými konstantami a operátory (ale žádné volání funkcí).</span><span class="sxs-lookup"><span data-stu-id="add4f-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a><span data-ttu-id="add4f-109">Deklarace konstanty</span><span class="sxs-lookup"><span data-stu-id="add4f-109">To declare a constant</span></span>  
  
- <span data-ttu-id="add4f-110">Napište deklaraci, která zahrnuje specifikátor přístupu, `Const` klíčové slovo a výraz, jako v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="add4f-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     <span data-ttu-id="add4f-111">Pokud je [možnost odvozená](../../../language-reference/statements/option-infer-statement.md) `Off` a [možnost Option Strict](../../../language-reference/statements/option-strict-statement.md) `On` , je nutné explicitně deklarovat konstantu zadáním datového typu ( `Boolean` , `Byte` , `Char` , `DateTime` , `Decimal` , `Double` , `Integer` , `Long` , `Short` , `Single` nebo `String` ).</span><span class="sxs-lookup"><span data-stu-id="add4f-111">When [Option Infer](../../../language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span></span>  
  
     <span data-ttu-id="add4f-112">Když `Option Infer` je `On` nebo `Option Strict` `Off` , můžete deklarovat konstantu bez zadání datového typu s `As` klauzulí.</span><span class="sxs-lookup"><span data-stu-id="add4f-112">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="add4f-113">Kompilátor určuje typ konstanty z typu výrazu.</span><span class="sxs-lookup"><span data-stu-id="add4f-113">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="add4f-114">Další informace naleznete v tématu [datové typy konstanty a literálu](constant-and-literal-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="add4f-114">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span></span>  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a><span data-ttu-id="add4f-115">Deklarace konstanty, která má explicitně uvedený datový typ</span><span class="sxs-lookup"><span data-stu-id="add4f-115">To declare a constant that has an explicitly stated data type</span></span>  
  
- <span data-ttu-id="add4f-116">Napište deklaraci, která zahrnuje `As` klíčové slovo a explicitní datový typ, jako v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="add4f-116">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     <span data-ttu-id="add4f-117">Můžete deklarovat více konstant na jednom řádku, i když je váš kód čitelnější, pokud deklarujete pouze jednu konstantu na řádek.</span><span class="sxs-lookup"><span data-stu-id="add4f-117">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span></span> <span data-ttu-id="add4f-118">Pokud deklarujete více konstant na jednom řádku, musí mít všechny stejnou úroveň přístupu ( `Public` , `Private` ,, `Friend` `Protected` nebo `Protected Friend` ).</span><span class="sxs-lookup"><span data-stu-id="add4f-118">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span></span>  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a><span data-ttu-id="add4f-119">Deklarace více konstant na jednom řádku</span><span class="sxs-lookup"><span data-stu-id="add4f-119">To declare multiple constants on a single line</span></span>  
  
- <span data-ttu-id="add4f-120">Deklarace se oddělují čárkou a mezerou, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="add4f-120">Separate the declarations with a comma and a space, as in the following example:</span></span>  
  
    ```vb  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="add4f-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="add4f-121">See also</span></span>

- [<span data-ttu-id="add4f-122">Const – příkaz</span><span class="sxs-lookup"><span data-stu-id="add4f-122">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)
- [<span data-ttu-id="add4f-123">Datové typy konstanty a literálu</span><span class="sxs-lookup"><span data-stu-id="add4f-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="add4f-124">Přehled konstant</span><span class="sxs-lookup"><span data-stu-id="add4f-124">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="add4f-125">Postupy: Deklarace konstanty</span><span class="sxs-lookup"><span data-stu-id="add4f-125">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)
- [<span data-ttu-id="add4f-126">Uživatelem definované konstanty</span><span class="sxs-lookup"><span data-stu-id="add4f-126">User-Defined Constants</span></span>](user-defined-constants.md)
- [<span data-ttu-id="add4f-127">Datové typy konstanty a literálu</span><span class="sxs-lookup"><span data-stu-id="add4f-127">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="add4f-128">Postupy: Seskupení souvisejících hodnot konstant</span><span class="sxs-lookup"><span data-stu-id="add4f-128">How to: Group Related Constant Values Together</span></span>](how-to-group-related-constant-values-together.md)
- [<span data-ttu-id="add4f-129">Přehled výčtů</span><span class="sxs-lookup"><span data-stu-id="add4f-129">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="add4f-130">Postupy: Deklarace výčtů</span><span class="sxs-lookup"><span data-stu-id="add4f-130">How to: Declare Enumerations</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="add4f-131">Postupy: Odkazování na člena výčtu</span><span class="sxs-lookup"><span data-stu-id="add4f-131">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="add4f-132">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="add4f-132">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="add4f-133">Postupy: Iterace ve výčtu</span><span class="sxs-lookup"><span data-stu-id="add4f-133">How to: Iterate Through An Enumeration</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="add4f-134">Postupy: Určení řetězce spojeného s hodnotou výčtu</span><span class="sxs-lookup"><span data-stu-id="add4f-134">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="add4f-135">Kdy použít výčet</span><span class="sxs-lookup"><span data-stu-id="add4f-135">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)

- [<span data-ttu-id="add4f-136">Přehled výčtů</span><span class="sxs-lookup"><span data-stu-id="add4f-136">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="add4f-137">Přehled konstant</span><span class="sxs-lookup"><span data-stu-id="add4f-137">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="add4f-138">Postupy: deklarace výčtu</span><span class="sxs-lookup"><span data-stu-id="add4f-138">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="add4f-139">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="add4f-139">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="add4f-140">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="add4f-140">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="add4f-141">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="add4f-141">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
