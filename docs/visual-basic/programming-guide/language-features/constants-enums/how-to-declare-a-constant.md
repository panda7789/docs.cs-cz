---
title: 'Postupy: Deklarace konstanty (Visual Basic)'
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
ms.openlocfilehash: 8b84ab5e8edebba3048c5cddf723198cf3f28858
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579915"
---
# <a name="how-to-declare-a-constant-visual-basic"></a><span data-ttu-id="45a33-102">Postupy: Deklarace konstanty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45a33-102">How to: Declare A Constant (Visual Basic)</span></span>
<span data-ttu-id="45a33-103">Pomocí příkazu `Const` deklarujete konstantu a nastavíte její hodnotu.</span><span class="sxs-lookup"><span data-stu-id="45a33-103">You use the `Const` statement to declare a constant and set its value.</span></span> <span data-ttu-id="45a33-104">Deklarováním konstanty přiřadíte smysluplný název k hodnotě.</span><span class="sxs-lookup"><span data-stu-id="45a33-104">By declaring a constant, you assign a meaningful name to a value.</span></span> <span data-ttu-id="45a33-105">Jakmile je konstanta deklarována, nelze ji změnit ani jí přiřadit novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="45a33-105">Once a constant is declared, it cannot be modified or assigned a new value.</span></span>  
  
 <span data-ttu-id="45a33-106">Deklarujete konstantu v rámci procedury nebo v oddílu deklarace modulu, třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="45a33-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span></span> <span data-ttu-id="45a33-107">Konstanty na úrovni třídy nebo struktury jsou ve výchozím nastavení `Private`, ale mohou být také deklarovány jako `Public`, `Friend`, `Protected` nebo `Protected Friend` pro příslušnou úroveň přístupu kódu.</span><span class="sxs-lookup"><span data-stu-id="45a33-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span></span>  
  
 <span data-ttu-id="45a33-108">Konstanta musí mít platný symbolický název (pravidla jsou stejná jako pro vytváření názvů proměnných) a výraz tvořený číselnými nebo řetězcovými konstantami a operátory (ale žádné volání funkcí).</span><span class="sxs-lookup"><span data-stu-id="45a33-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a><span data-ttu-id="45a33-109">Deklarace konstanty</span><span class="sxs-lookup"><span data-stu-id="45a33-109">To declare a constant</span></span>  
  
- <span data-ttu-id="45a33-110">Napište deklaraci, která zahrnuje specifikátor přístupu, klíčové slovo `Const` a výraz, jako v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="45a33-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     <span data-ttu-id="45a33-111">Je-li [možnost navodit](../../../../visual-basic/language-reference/statements/option-infer-statement.md) `Off` a [možnost Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) je `On`, je nutné explicitně deklarovat konstantu zadáním datového typu (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, 0 , 1, 2, 3 nebo 4).</span><span class="sxs-lookup"><span data-stu-id="45a33-111">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span></span>  
  
     <span data-ttu-id="45a33-112">Pokud je `Option Infer` `On` nebo `Option Strict` `Off`, můžete deklarovat konstantu bez určení datového typu s klauzulí `As`.</span><span class="sxs-lookup"><span data-stu-id="45a33-112">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="45a33-113">Kompilátor určuje typ konstanty z typu výrazu.</span><span class="sxs-lookup"><span data-stu-id="45a33-113">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="45a33-114">Další informace naleznete v tématu [datové typy konstanty a literálu](constant-and-literal-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="45a33-114">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span></span>  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a><span data-ttu-id="45a33-115">Deklarace konstanty, která má explicitně uvedený datový typ</span><span class="sxs-lookup"><span data-stu-id="45a33-115">To declare a constant that has an explicitly stated data type</span></span>  
  
- <span data-ttu-id="45a33-116">Napište deklaraci, která zahrnuje klíčové slovo `As` a explicitní datový typ, jako v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="45a33-116">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     <span data-ttu-id="45a33-117">Můžete deklarovat více konstant na jednom řádku, i když je váš kód čitelnější, pokud deklarujete pouze jednu konstantu na řádek.</span><span class="sxs-lookup"><span data-stu-id="45a33-117">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span></span> <span data-ttu-id="45a33-118">Pokud deklarujete více konstant na jednom řádku, musí mít všechny stejnou úroveň přístupu (`Public`, `Private`, `Friend`, `Protected` nebo `Protected Friend`).</span><span class="sxs-lookup"><span data-stu-id="45a33-118">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span></span>  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a><span data-ttu-id="45a33-119">Deklarace více konstant na jednom řádku</span><span class="sxs-lookup"><span data-stu-id="45a33-119">To declare multiple constants on a single line</span></span>  
  
- <span data-ttu-id="45a33-120">Deklarace se oddělují čárkou a mezerou, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="45a33-120">Separate the declarations with a comma and a space, as in the following example:</span></span>  
  
    ```vb  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="45a33-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45a33-121">See also</span></span>

- [<span data-ttu-id="45a33-122">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="45a33-122">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="45a33-123">Datové typy konstanty a literálu</span><span class="sxs-lookup"><span data-stu-id="45a33-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="45a33-124">Přehled konstant</span><span class="sxs-lookup"><span data-stu-id="45a33-124">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="45a33-125">Postupy: Deklarace konstanty</span><span class="sxs-lookup"><span data-stu-id="45a33-125">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)
- [<span data-ttu-id="45a33-126">Uživatelem definované konstanty</span><span class="sxs-lookup"><span data-stu-id="45a33-126">User-Defined Constants</span></span>](user-defined-constants.md)
- [<span data-ttu-id="45a33-127">Datové typy konstanty a literálu</span><span class="sxs-lookup"><span data-stu-id="45a33-127">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="45a33-128">Postupy: Seskupení souvisejících hodnot konstant</span><span class="sxs-lookup"><span data-stu-id="45a33-128">How to: Group Related Constant Values Together</span></span>](how-to-group-related-constant-values-together.md)
- [<span data-ttu-id="45a33-129">Přehled výčtů</span><span class="sxs-lookup"><span data-stu-id="45a33-129">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="45a33-130">Postupy: Deklarace výčtů</span><span class="sxs-lookup"><span data-stu-id="45a33-130">How to: Declare Enumerations</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="45a33-131">Postupy: Odkazování na člena výčtu</span><span class="sxs-lookup"><span data-stu-id="45a33-131">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="45a33-132">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="45a33-132">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="45a33-133">Postupy: Iterace ve výčtu</span><span class="sxs-lookup"><span data-stu-id="45a33-133">How to: Iterate Through An Enumeration</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="45a33-134">Postupy: Určení řetězce spojeného s hodnotou výčtu</span><span class="sxs-lookup"><span data-stu-id="45a33-134">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="45a33-135">Kdy použít výčet</span><span class="sxs-lookup"><span data-stu-id="45a33-135">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)

- [<span data-ttu-id="45a33-136">Přehled výčtů</span><span class="sxs-lookup"><span data-stu-id="45a33-136">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="45a33-137">Přehled konstant</span><span class="sxs-lookup"><span data-stu-id="45a33-137">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="45a33-138">Postupy: deklarace výčtu</span><span class="sxs-lookup"><span data-stu-id="45a33-138">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="45a33-139">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="45a33-139">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="45a33-140">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="45a33-140">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="45a33-141">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="45a33-141">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
