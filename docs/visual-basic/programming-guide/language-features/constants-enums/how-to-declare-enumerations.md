---
title: 'Postupy: Deklarace výčtů'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: c8f228c205c93adf7f2f555dc840a7daac61950b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414450"
---
# <a name="how-to-declare-enumerations-visual-basic"></a><span data-ttu-id="27f6c-102">Postupy: Deklarace výčtů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27f6c-102">How to: Declare Enumerations (Visual Basic)</span></span>
<span data-ttu-id="27f6c-103">Vytvoříte výčet s `Enum` příkazem v oddílu deklarace třídy nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="27f6c-103">You create an enumeration with the `Enum` statement in the declarations section of a class or module.</span></span> <span data-ttu-id="27f6c-104">V rámci metody nelze deklarovat výčet.</span><span class="sxs-lookup"><span data-stu-id="27f6c-104">You cannot declare an enumeration within a method.</span></span> <span data-ttu-id="27f6c-105">Chcete-li určit příslušnou úroveň přístupu, použijte `Private` , `Protected` , `Friend` nebo `Public` .</span><span class="sxs-lookup"><span data-stu-id="27f6c-105">To specify the appropriate level of access, use `Private`, `Protected`, `Friend`, or `Public`.</span></span>  
  
 <span data-ttu-id="27f6c-106">`Enum`Typ má název, nadřízený typ a sadu polí, z nichž každý představuje konstantu.</span><span class="sxs-lookup"><span data-stu-id="27f6c-106">An `Enum` type has a name, an underlying type, and a set of fields, each representing a constant.</span></span> <span data-ttu-id="27f6c-107">Název musí být platným kvalifikátorem Visual Basic .NET.</span><span class="sxs-lookup"><span data-stu-id="27f6c-107">The name must be a valid Visual Basic .NET qualifier.</span></span> <span data-ttu-id="27f6c-108">Nadřízený typ musí být jeden z celočíselných typů – `Byte` , `Short` `Long` nebo `Integer` .</span><span class="sxs-lookup"><span data-stu-id="27f6c-108">The underlying type must be one of the integer types—`Byte`, `Short`, `Long` or `Integer`.</span></span> <span data-ttu-id="27f6c-109">`Integer` je výchozí možnost.</span><span class="sxs-lookup"><span data-stu-id="27f6c-109">`Integer` is the default.</span></span> <span data-ttu-id="27f6c-110">Výčty jsou vždy silného typu a nejsou zaměnitelné s celočíselnými typy čísel.</span><span class="sxs-lookup"><span data-stu-id="27f6c-110">Enumerations are always strongly typed and are not interchangeable with integer number types.</span></span>  
  
 <span data-ttu-id="27f6c-111">Výčty nemůžou mít hodnoty s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="27f6c-111">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="27f6c-112">Pokud je výčtu přiřazena hodnota s plovoucí desetinnou čárkou `Option Strict On` , výsledkem je chyba kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="27f6c-112">If an enumeration is assigned a floating-point value with `Option Strict On`, a compiler error results.</span></span> <span data-ttu-id="27f6c-113">Pokud `Option Strict` je `Off` , hodnota je automaticky převedena na `Enum` typ.</span><span class="sxs-lookup"><span data-stu-id="27f6c-113">If `Option Strict` is `Off`, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="27f6c-114">Informace o názvech a o tom, jak použít `Imports` příkaz k zajištění nepotřebné kvalifikace názvu, najdete v tématu [výčty a kvalifikace názvu](enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="27f6c-114">For information on names, and how to use the `Imports` statement to make name qualification unnecessary, see [Enumerations and Name Qualification](enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-declare-an-enumeration"></a><span data-ttu-id="27f6c-115">Deklarace výčtu</span><span class="sxs-lookup"><span data-stu-id="27f6c-115">To declare an enumeration</span></span>  
  
1. <span data-ttu-id="27f6c-116">Napište deklaraci, která obsahuje úroveň přístupu kódu, `Enum` klíčové slovo a platný název, jako v následujících příkladech, z nichž každý deklaruje jiný `Enum` .</span><span class="sxs-lookup"><span data-stu-id="27f6c-116">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name, as in the following examples, each of which declares a different `Enum`.</span></span>  
  
     [!code-vb[VbEnumsTask#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#3)]  
  
2. <span data-ttu-id="27f6c-117">Definujte konstanty ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="27f6c-117">Define the constants in the enumeration.</span></span> <span data-ttu-id="27f6c-118">Ve výchozím nastavení je první konstanta ve výčtu inicializována na `0` a další konstanty jsou inicializovány na hodnotu jednoho z více než předchozí konstanty.</span><span class="sxs-lookup"><span data-stu-id="27f6c-118">By default, the first constant in an enumeration is initialized to `0`, and subsequent constants are initialized to a value of one more than the previous constant.</span></span> <span data-ttu-id="27f6c-119">Například následující výčet `Days` obsahuje konstantu s názvem `Sunday` s hodnotou `0` , konstanta s názvem, `Monday` `1` konstanta s `Tuesday` hodnotou a `2` tak dále.</span><span class="sxs-lookup"><span data-stu-id="27f6c-119">For example, the following enumeration, `Days`, contains a constant named `Sunday` with the value `0`, a constant named `Monday` with the value `1`, a constant named `Tuesday` with the value of `2`, and so on.</span></span>  
  
     [!code-vb[VbEnumsTask#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#4)]  
  
3. <span data-ttu-id="27f6c-120">Můžete explicitně přiřadit hodnoty konstantám ve výčtu pomocí příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="27f6c-120">You can explicitly assign values to constants in an enumeration by using an assignment statement.</span></span> <span data-ttu-id="27f6c-121">Můžete přiřadit libovolné celočíselné hodnoty, včetně záporných čísel.</span><span class="sxs-lookup"><span data-stu-id="27f6c-121">You can assign any integer value, including negative numbers.</span></span> <span data-ttu-id="27f6c-122">Například může být vhodné, aby konstanty s hodnotami menšími než nula představovaly chybové stavy.</span><span class="sxs-lookup"><span data-stu-id="27f6c-122">For example, you may want constants with values less than zero to represent error conditions.</span></span> <span data-ttu-id="27f6c-123">V následujícím výčtu je konstantě `Invalid` explicitně přiřazena hodnota `–1` a konstanta `Sunday` je přiřazena hodnota `0` .</span><span class="sxs-lookup"><span data-stu-id="27f6c-123">In the following enumeration, the constant `Invalid` is explicitly assigned the value `–1`, and the constant `Sunday` is assigned the value `0`.</span></span> <span data-ttu-id="27f6c-124">Vzhledem k tomu, že se jedná o první konstantu ve výčtu, `Saturday` je také inicializována na hodnotu `0` .</span><span class="sxs-lookup"><span data-stu-id="27f6c-124">Because it is the first constant in the enumeration, `Saturday` is also initialized to the value `0`.</span></span> <span data-ttu-id="27f6c-125">Hodnota `Monday` je `1` (jedna hodnota `Sunday` ) `Tuesday` , hodnota je `2` , a tak dále.</span><span class="sxs-lookup"><span data-stu-id="27f6c-125">The value of `Monday` is `1` (one more than the value of `Sunday`); the value of `Tuesday` is `2`, and so on.</span></span>  
  
     [!code-vb[VbEnumsTask#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#5)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a><span data-ttu-id="27f6c-126">Deklarace výčtu jako explicitního typu</span><span class="sxs-lookup"><span data-stu-id="27f6c-126">To declare an enumeration as an explicit type</span></span>  
  
- <span data-ttu-id="27f6c-127">Zadejte typ výčtu pomocí `As` klauzule, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="27f6c-127">Specify the type of the enum by using the `As` clause, as shown in the following example.</span></span>  
  
     [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="27f6c-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="27f6c-128">See also</span></span>

- [<span data-ttu-id="27f6c-129">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="27f6c-129">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="27f6c-130">Postupy: Odkazování na člena výčtu</span><span class="sxs-lookup"><span data-stu-id="27f6c-130">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="27f6c-131">Postupy: Iterace ve výčtu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="27f6c-131">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="27f6c-132">Postupy: Určení řetězce spojeného s hodnotou výčtu</span><span class="sxs-lookup"><span data-stu-id="27f6c-132">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="27f6c-133">Kdy použít výčet</span><span class="sxs-lookup"><span data-stu-id="27f6c-133">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="27f6c-134">Přehled konstant</span><span class="sxs-lookup"><span data-stu-id="27f6c-134">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="27f6c-135">Datové typy konstanty a literálu</span><span class="sxs-lookup"><span data-stu-id="27f6c-135">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="27f6c-136">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="27f6c-136">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
