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
# <a name="user-defined-constants-visual-basic"></a><span data-ttu-id="4877d-102">Uživatelem definované konstanty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4877d-102">User-Defined Constants (Visual Basic)</span></span>
<span data-ttu-id="4877d-103">Konstanta je smysluplný název, který přebírá místo čísla nebo řetězce, který se nemění.</span><span class="sxs-lookup"><span data-stu-id="4877d-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="4877d-104">Konstanty ukládají hodnoty, které jako název implikují, zůstávají během provádění aplikace konstantní.</span><span class="sxs-lookup"><span data-stu-id="4877d-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="4877d-105">Můžete použít konstanty, které jsou definovány ovládacími prvky nebo komponentami, se kterými pracujete, nebo můžete vytvořit vlastní.</span><span class="sxs-lookup"><span data-stu-id="4877d-105">You can use constants that are defined by the controls or components you work with, or you can create your own.</span></span> <span data-ttu-id="4877d-106">Konstanty, které vytvoříte sami, jsou popsány jako *uživatelsky definované*.</span><span class="sxs-lookup"><span data-stu-id="4877d-106">Constants you create yourself are described as *user-defined*.</span></span>  
  
 <span data-ttu-id="4877d-107">Deklarujete konstantu pomocí příkazu `Const` a použijete stejné pokyny jako pro vytvoření názvu proměnné.</span><span class="sxs-lookup"><span data-stu-id="4877d-107">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="4877d-108">Pokud je `Option Strict` `On`, musíte explicitně deklarovat typ konstanty.</span><span class="sxs-lookup"><span data-stu-id="4877d-108">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
## <a name="const-statement-usage"></a><span data-ttu-id="4877d-109">Použití příkazu const</span><span class="sxs-lookup"><span data-stu-id="4877d-109">Const Statement Usage</span></span>  
 <span data-ttu-id="4877d-110">Příkaz `Const` může představovat matematické nebo datum a čas:</span><span class="sxs-lookup"><span data-stu-id="4877d-110">A `Const` statement can represent a mathematical or date/time quantity:</span></span>  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 <span data-ttu-id="4877d-111">Může také definovat `String` konstanty:</span><span class="sxs-lookup"><span data-stu-id="4877d-111">It also can define `String` constants:</span></span>  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 <span data-ttu-id="4877d-112">Výraz na pravé straně znaménka rovná se (`=`) je často číslo nebo literální řetězec, ale může to být výraz, jehož výsledkem je číslo nebo řetězec (i když tento výraz nemůže obsahovat volání funkcí).</span><span class="sxs-lookup"><span data-stu-id="4877d-112">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span></span> <span data-ttu-id="4877d-113">Můžete dokonce definovat konstanty z podmínek dříve definovaných konstant:</span><span class="sxs-lookup"><span data-stu-id="4877d-113">You can even define constants in terms of previously defined constants:</span></span>  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a><span data-ttu-id="4877d-114">Rozsah uživatelsky definovaných konstant</span><span class="sxs-lookup"><span data-stu-id="4877d-114">Scope of User-Defined Constants</span></span>  
 <span data-ttu-id="4877d-115">Obor příkazu `Const` je stejný jako objekt proměnné deklarované ve stejném umístění.</span><span class="sxs-lookup"><span data-stu-id="4877d-115">A `Const` statement's scope is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="4877d-116">Rozsah můžete zadat některým z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="4877d-116">You can specify scope in any of the following ways:</span></span>  
  
- <span data-ttu-id="4877d-117">Chcete-li vytvořit konstantu, která existuje pouze v rámci procedury, deklarujte ji v rámci tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="4877d-117">To create a constant that exists only within a procedure, declare it within that procedure.</span></span>  
  
- <span data-ttu-id="4877d-118">Chcete-li vytvořit konstantu dostupnou pro všechny postupy v rámci třídy, ale ne pro žádný kód mimo tento modul, deklarujte ho v oddílu deklarace třídy.</span><span class="sxs-lookup"><span data-stu-id="4877d-118">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span></span>  
  
- <span data-ttu-id="4877d-119">Chcete-li vytvořit konstantu, která je k dispozici pro všechny členy sestavení, ale ne pro externí klienty sestavení, deklarujte ji pomocí klíčového slova `Friend` v oddílu deklarace třídy.</span><span class="sxs-lookup"><span data-stu-id="4877d-119">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span></span>  
  
- <span data-ttu-id="4877d-120">Chcete-li vytvořit konstantu dostupnou v celé aplikaci, deklarujte ji pomocí klíčového slova `Public` v oddílu deklarace třídy.</span><span class="sxs-lookup"><span data-stu-id="4877d-120">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span></span>  
  
 <span data-ttu-id="4877d-121">Další informace naleznete v tématu [How to: Declare a konstante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span><span class="sxs-lookup"><span data-stu-id="4877d-121">For more information, see [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span></span>  
  
### <a name="avoiding-circular-references"></a><span data-ttu-id="4877d-122">Zamezení cyklických odkazů</span><span class="sxs-lookup"><span data-stu-id="4877d-122">Avoiding Circular References</span></span>  
 <span data-ttu-id="4877d-123">Vzhledem k tomu, že konstanty lze definovat v souvislosti s jinými konstantami, je možné neúmyslně vytvořit *cyklus*nebo cyklický odkaz mezi dvěma nebo více konstantami.</span><span class="sxs-lookup"><span data-stu-id="4877d-123">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span></span> <span data-ttu-id="4877d-124">K cyklu dochází, když máte dvě nebo více veřejných konstant, z nichž každá je definována z hlediska druhé, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="4877d-124">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 <span data-ttu-id="4877d-125">Pokud dojde k cyklu, Visual Basic vygeneruje chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="4877d-125">If a cycle occurs, Visual Basic generates a compiler error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4877d-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4877d-126">See also</span></span>

- [<span data-ttu-id="4877d-127">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="4877d-127">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="4877d-128">Datové typy konstanty a literálu</span><span class="sxs-lookup"><span data-stu-id="4877d-128">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="4877d-129">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="4877d-129">Constants and Enumerations</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [<span data-ttu-id="4877d-130">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="4877d-130">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="4877d-131">Přehled výčtů</span><span class="sxs-lookup"><span data-stu-id="4877d-131">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [<span data-ttu-id="4877d-132">Přehled konstant</span><span class="sxs-lookup"><span data-stu-id="4877d-132">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="4877d-133">Postupy: deklarace výčtu</span><span class="sxs-lookup"><span data-stu-id="4877d-133">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="4877d-134">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="4877d-134">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="4877d-135">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="4877d-135">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
