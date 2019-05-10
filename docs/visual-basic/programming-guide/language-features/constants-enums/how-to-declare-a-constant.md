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
ms.openlocfilehash: b84afe4e354d4029bc61ba67bc93bd36a3430de4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64610603"
---
# <a name="how-to-declare-a-constant-visual-basic"></a><span data-ttu-id="29f32-102">Postupy: Deklarace konstanty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29f32-102">How to: Declare A Constant (Visual Basic)</span></span>
<span data-ttu-id="29f32-103">Můžete použít `Const` příkazu deklarace konstanty a nastavení jeho hodnoty.</span><span class="sxs-lookup"><span data-stu-id="29f32-103">You use the `Const` statement to declare a constant and set its value.</span></span> <span data-ttu-id="29f32-104">Deklarací konstantu, přiřaďte k hodnotě smysluplný název.</span><span class="sxs-lookup"><span data-stu-id="29f32-104">By declaring a constant, you assign a meaningful name to a value.</span></span> <span data-ttu-id="29f32-105">Jakmile je deklarována konstanta, nelze změnit ani přiřazena nová hodnota.</span><span class="sxs-lookup"><span data-stu-id="29f32-105">Once a constant is declared, it cannot be modified or assigned a new value.</span></span>  
  
 <span data-ttu-id="29f32-106">Můžete deklarovat konstanty v rámci procedury nebo v části deklarace modulu, třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="29f32-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span></span> <span data-ttu-id="29f32-107">Třída nebo struktura úroveň konstanty jsou `Private` ve výchozím nastavení, ale může také deklarovány jako `Public`, `Friend`, `Protected`, nebo `Protected Friend` pro odpovídající úroveň přístup ke kódu.</span><span class="sxs-lookup"><span data-stu-id="29f32-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span></span>  
  
 <span data-ttu-id="29f32-108">Konstanty musí mít platný symbolický název (pravidla jsou stejné jako u vytváření názvy proměnných) a výraz složené číselné nebo řetězcové konstanty a operátory (ale bez volání funkce).</span><span class="sxs-lookup"><span data-stu-id="29f32-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a><span data-ttu-id="29f32-109">Chcete-li deklarovat konstanty</span><span class="sxs-lookup"><span data-stu-id="29f32-109">To declare a constant</span></span>  
  
- <span data-ttu-id="29f32-110">Zápis deklarace, která zahrnuje specifikátor přístupu, `Const` – klíčové slovo a výraz, stejně jako v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="29f32-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     <span data-ttu-id="29f32-111">Když [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) je `Off` a [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) je `On`, musí deklarace konstanty explicitně tak, že zadáte datový typ (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, nebo `String`).</span><span class="sxs-lookup"><span data-stu-id="29f32-111">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span></span>  
  
     <span data-ttu-id="29f32-112">Když `Option Infer` je `On` nebo `Option Strict` je `Off`, je možné deklarovat konstanty bez zadání datový typ s `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="29f32-112">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="29f32-113">Kompilátor Určuje typ konstanty z typu výrazu.</span><span class="sxs-lookup"><span data-stu-id="29f32-113">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="29f32-114">Další informace najdete v tématu [konstanty a literálu datové typy](constant-and-literal-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="29f32-114">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span></span>  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a><span data-ttu-id="29f32-115">Chcete-li deklarovat konstantu, která je explicitně uvedená datový typ</span><span class="sxs-lookup"><span data-stu-id="29f32-115">To declare a constant that has an explicitly stated data type</span></span>  
  
- <span data-ttu-id="29f32-116">Zápis deklarace, která zahrnuje `As` – klíčové slovo a explicitního datového typu, stejně jako v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="29f32-116">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     <span data-ttu-id="29f32-117">Na jednom řádku, může deklarovat více konstant, i když je váš kód lépe čitelný, je-li deklarovat jenom jednu konstantu na řádek.</span><span class="sxs-lookup"><span data-stu-id="29f32-117">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span></span> <span data-ttu-id="29f32-118">Je-li deklarovat více konstant na jednom řádku, musí všechny mají stejnou úroveň přístupu (`Public`, `Private`, `Friend`, `Protected`, nebo `Protected Friend`).</span><span class="sxs-lookup"><span data-stu-id="29f32-118">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span></span>  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a><span data-ttu-id="29f32-119">Chcete-li deklarovat více konstant na jednom řádku</span><span class="sxs-lookup"><span data-stu-id="29f32-119">To declare multiple constants on a single line</span></span>  
  
- <span data-ttu-id="29f32-120">Deklarace oddělujte čárkou a mezerou, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="29f32-120">Separate the declarations with a comma and a space, as in the following example:</span></span>  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="29f32-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29f32-121">See also</span></span>

- [<span data-ttu-id="29f32-122">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="29f32-122">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="29f32-123">Datové typy konstanty a literálu</span><span class="sxs-lookup"><span data-stu-id="29f32-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="29f32-124">Přehled konstant</span><span class="sxs-lookup"><span data-stu-id="29f32-124">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="29f32-125">Postupy: Deklarace konstanty</span><span class="sxs-lookup"><span data-stu-id="29f32-125">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)
- [<span data-ttu-id="29f32-126">Uživatelem definované konstanty</span><span class="sxs-lookup"><span data-stu-id="29f32-126">User-Defined Constants</span></span>](user-defined-constants.md)
- [<span data-ttu-id="29f32-127">Datové typy konstanty a literálu</span><span class="sxs-lookup"><span data-stu-id="29f32-127">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="29f32-128">Postupy: Seskupení souvisejících hodnot konstant</span><span class="sxs-lookup"><span data-stu-id="29f32-128">How to: Group Related Constant Values Together</span></span>](how-to-group-related-constant-values-together.md)
- [<span data-ttu-id="29f32-129">Přehled výčtů</span><span class="sxs-lookup"><span data-stu-id="29f32-129">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="29f32-130">Postupy: Deklarace výčtů</span><span class="sxs-lookup"><span data-stu-id="29f32-130">How to: Declare Enumerations</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="29f32-131">Postupy: Odkazování na člena výčtu</span><span class="sxs-lookup"><span data-stu-id="29f32-131">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="29f32-132">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="29f32-132">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="29f32-133">Postupy: Iterace ve výčtu</span><span class="sxs-lookup"><span data-stu-id="29f32-133">How to: Iterate Through An Enumeration</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="29f32-134">Postupy: Určení řetězce spojeného s hodnotou výčtu</span><span class="sxs-lookup"><span data-stu-id="29f32-134">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="29f32-135">Kdy použít výčet</span><span class="sxs-lookup"><span data-stu-id="29f32-135">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)

- [<span data-ttu-id="29f32-136">Přehled výčtů</span><span class="sxs-lookup"><span data-stu-id="29f32-136">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="29f32-137">Přehled konstant</span><span class="sxs-lookup"><span data-stu-id="29f32-137">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="29f32-138">Postupy: Deklarace výčtů</span><span class="sxs-lookup"><span data-stu-id="29f32-138">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="29f32-139">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="29f32-139">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="29f32-140">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="29f32-140">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="29f32-141">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="29f32-141">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
