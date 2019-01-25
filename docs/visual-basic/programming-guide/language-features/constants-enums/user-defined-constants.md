---
title: Uživatelem definované konstanty (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: dc940105bbeb5e54819b8df5d5b3c831c7a6e145
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527312"
---
# <a name="user-defined-constants-visual-basic"></a><span data-ttu-id="92234-102">Uživatelem definované konstanty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92234-102">User-Defined Constants (Visual Basic)</span></span>
<span data-ttu-id="92234-103">Konstanta je smysluplný název, který probíhá číslo nebo řetězec, který se nemění.</span><span class="sxs-lookup"><span data-stu-id="92234-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="92234-104">Konstanty ukládání hodnot, které, jak již název napovídá, zůstanou neměnný po celou dobu spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="92234-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="92234-105">Můžete použít konstanty, které jsou definovány ovládací prvky nebo komponenty, které můžete pracovat, nebo můžete vytvořit svoje vlastní.</span><span class="sxs-lookup"><span data-stu-id="92234-105">You can use constants that are defined by the controls or components you work with, or you can create your own.</span></span> <span data-ttu-id="92234-106">Konstanty, které si sami vytvoříte, jsou popsány jako *uživatelem definované*.</span><span class="sxs-lookup"><span data-stu-id="92234-106">Constants you create yourself are described as *user-defined*.</span></span>  
  
 <span data-ttu-id="92234-107">Deklarace konstanty s `Const` příkaz pomocí stejné pokyny jako byste to udělali pro vytvoření názvu proměnné.</span><span class="sxs-lookup"><span data-stu-id="92234-107">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="92234-108">Pokud `Option Strict` je `On`, musíte explicitně deklarovat typ konstanty.</span><span class="sxs-lookup"><span data-stu-id="92234-108">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
## <a name="const-statement-usage"></a><span data-ttu-id="92234-109">Const – příkaz využití</span><span class="sxs-lookup"><span data-stu-id="92234-109">Const Statement Usage</span></span>  
 <span data-ttu-id="92234-110">A `Const` příkaz může představovat matematické nebo datum a čas, množství:</span><span class="sxs-lookup"><span data-stu-id="92234-110">A `Const` statement can represent a mathematical or date/time quantity:</span></span>  
  
 [!code-vb[VbEnumsTask#10](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]  
  
 <span data-ttu-id="92234-111">Je také definovat `String` konstanty:</span><span class="sxs-lookup"><span data-stu-id="92234-111">It also can define `String` constants:</span></span>  
  
 [!code-vb[VbEnumsTask#13](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]  
  
 <span data-ttu-id="92234-112">Výraz na pravé straně znaménka rovnosti ( `=` ) je často číslo nebo řetězcový literál, ale také může být výraz, jehož výsledkem číslo nebo řetězec (i když tento výraz nemůže obsahovat volání funkcí).</span><span class="sxs-lookup"><span data-stu-id="92234-112">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span></span> <span data-ttu-id="92234-113">Můžete dokonce definovat konstanty z hlediska dříve definované konstanty:</span><span class="sxs-lookup"><span data-stu-id="92234-113">You can even define constants in terms of previously defined constants:</span></span>  
  
 [!code-vb[VbEnumsTask#15](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]  
  
## <a name="scope-of-user-defined-constants"></a><span data-ttu-id="92234-114">Rozsah uživatelem definované konstanty</span><span class="sxs-lookup"><span data-stu-id="92234-114">Scope of User-Defined Constants</span></span>  
 <span data-ttu-id="92234-115">A `Const` obor příkazu je stejné jako u proměnné deklarované ve stejném umístění.</span><span class="sxs-lookup"><span data-stu-id="92234-115">A `Const` statement's scope is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="92234-116">Zadejte rozsah v některém z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="92234-116">You can specify scope in any of the following ways:</span></span>  
  
-   <span data-ttu-id="92234-117">Chcete-li vytvořit konstantu, která existuje pouze v rámci procedury, deklarujte ho v rámci tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="92234-117">To create a constant that exists only within a procedure, declare it within that procedure.</span></span>  
  
-   <span data-ttu-id="92234-118">K vytvoření konstantu k dispozici pro všechny postupy v rámci třídy, ale ne k žádným kódem mimo modul, ji deklarujte v sekci prohlášení třídy.</span><span class="sxs-lookup"><span data-stu-id="92234-118">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="92234-119">Pokud chcete vytvořit konstantu, která je k dispozici všem členům sestavení, ale ne ke klientům mimo sestavení, deklarujete jej s použitím `Friend` – klíčové slovo v sekci prohlášení třídy.</span><span class="sxs-lookup"><span data-stu-id="92234-119">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="92234-120">Pokud chcete vytvořit konstantní k dispozici v celé aplikaci, deklarujete jej s použitím `Public` části – klíčové slovo v deklaracích třídy.</span><span class="sxs-lookup"><span data-stu-id="92234-120">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span></span>  
  
 <span data-ttu-id="92234-121">Další informace najdete v tématu [jak: Deklarace konstanty](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span><span class="sxs-lookup"><span data-stu-id="92234-121">For more information, see [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span></span>  
  
### <a name="avoiding-circular-references"></a><span data-ttu-id="92234-122">Jak se vyhnout cyklické odkazy</span><span class="sxs-lookup"><span data-stu-id="92234-122">Avoiding Circular References</span></span>  
 <span data-ttu-id="92234-123">Protože jde o dalších konstant lze definovat konstanty, je možné neúmyslně vytvořit *cyklu*, nebo cyklický odkaz mezi dva nebo více konstant.</span><span class="sxs-lookup"><span data-stu-id="92234-123">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span></span> <span data-ttu-id="92234-124">Cyklus dojde, pokud mají dvě nebo více veřejné konstanty, z nichž každý je definována v jiné, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="92234-124">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#16](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]  
[!code-vb[VbEnumsTask#17](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]  
  
 <span data-ttu-id="92234-125">Pokud dochází k zacyklení, Visual Basic vygeneruje chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="92234-125">If a cycle occurs, Visual Basic generates a compiler error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92234-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92234-126">See also</span></span>
- [<span data-ttu-id="92234-127">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="92234-127">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="92234-128">Datové typy konstanty a literálu</span><span class="sxs-lookup"><span data-stu-id="92234-128">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="92234-129">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="92234-129">Constants and Enumerations</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [<span data-ttu-id="92234-130">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="92234-130">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="92234-131">Přehled výčtů</span><span class="sxs-lookup"><span data-stu-id="92234-131">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [<span data-ttu-id="92234-132">Přehled konstant</span><span class="sxs-lookup"><span data-stu-id="92234-132">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="92234-133">Postupy: Deklarace výčtů</span><span class="sxs-lookup"><span data-stu-id="92234-133">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="92234-134">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="92234-134">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="92234-135">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="92234-135">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
