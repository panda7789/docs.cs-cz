---
title: Uživatelem definované konstanty (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9f4210193aeb386d3a4a76794cc9329cb24b2317
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="user-defined-constants-visual-basic"></a><span data-ttu-id="ace7b-102">Uživatelem definované konstanty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ace7b-102">User-Defined Constants (Visual Basic)</span></span>
<span data-ttu-id="ace7b-103">Konstanta je smysluplný název, který probíhá číslo nebo řetězec, který se nemění.</span><span class="sxs-lookup"><span data-stu-id="ace7b-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="ace7b-104">Konstanty ukládat hodnoty, které jak již název napovídá, zůstat konstantní po spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="ace7b-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="ace7b-105">Můžete použít konstanty, které jsou definovány pro ovládací prvky nebo součásti, se kterými můžete pracovat, nebo můžete vytvořit vlastní.</span><span class="sxs-lookup"><span data-stu-id="ace7b-105">You can use constants that are defined by the controls or components you work with, or you can create your own.</span></span> <span data-ttu-id="ace7b-106">Konstanty vytvořit sami jsou popsány jako *uživatelem definované*.</span><span class="sxs-lookup"><span data-stu-id="ace7b-106">Constants you create yourself are described as *user-defined*.</span></span>  
  
 <span data-ttu-id="ace7b-107">Deklarace konstanty s `Const` příkaz, pomocí stejné pokyny byste pro vytvoření název proměnné.</span><span class="sxs-lookup"><span data-stu-id="ace7b-107">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="ace7b-108">Pokud `Option Strict` je `On`, je potřeba explicitně deklarovat typu konstanty.</span><span class="sxs-lookup"><span data-stu-id="ace7b-108">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
## <a name="const-statement-usage"></a><span data-ttu-id="ace7b-109">Const – příkaz využití</span><span class="sxs-lookup"><span data-stu-id="ace7b-109">Const Statement Usage</span></span>  
 <span data-ttu-id="ace7b-110">A `Const` příkaz může představovat matematické nebo datum a čas množství:</span><span class="sxs-lookup"><span data-stu-id="ace7b-110">A `Const` statement can represent a mathematical or date/time quantity:</span></span>  
  
 [!code-vb[VbEnumsTask#10](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]  
  
 <span data-ttu-id="ace7b-111">Je také definovat `String` konstanty:</span><span class="sxs-lookup"><span data-stu-id="ace7b-111">It also can define `String` constants:</span></span>  
  
 [!code-vb[VbEnumsTask#13](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]  
  
 <span data-ttu-id="ace7b-112">Výraz na pravé straně znaménkem rovnosti ( `=` ) je často číslo nebo řetězcového literálu, ale také může být výraz, který je výsledkem číslo nebo řetězec (i když tento výraz nemůže obsahovat volání funkcí).</span><span class="sxs-lookup"><span data-stu-id="ace7b-112">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span></span> <span data-ttu-id="ace7b-113">Můžete definovat i konstanty z hlediska dříve definované konstanty:</span><span class="sxs-lookup"><span data-stu-id="ace7b-113">You can even define constants in terms of previously defined constants:</span></span>  
  
 [!code-vb[VbEnumsTask#15](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]  
  
## <a name="scope-of-user-defined-constants"></a><span data-ttu-id="ace7b-114">Rozsah uživatelem definované konstanty</span><span class="sxs-lookup"><span data-stu-id="ace7b-114">Scope of User-Defined Constants</span></span>  
 <span data-ttu-id="ace7b-115">A `Const` oboru na příkazu je stejný jako u proměnná definovaná ve stejném umístění.</span><span class="sxs-lookup"><span data-stu-id="ace7b-115">A `Const` statement's scope is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="ace7b-116">Můžete určit obor v některém z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="ace7b-116">You can specify scope in any of the following ways:</span></span>  
  
-   <span data-ttu-id="ace7b-117">Pokud chcete vytvořit konstanta, která existuje pouze v rámci procedury, deklarujte ji v rámci tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="ace7b-117">To create a constant that exists only within a procedure, declare it within that procedure.</span></span>  
  
-   <span data-ttu-id="ace7b-118">K vytvoření k dispozici všechny postupy v rámci třídy, ale není žádný kód mimo tento modul konstanta, deklarujte v sekci deklarace třídy.</span><span class="sxs-lookup"><span data-stu-id="ace7b-118">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="ace7b-119">Pokud chcete vytvořit konstanta, která je k dispozici pro všechny členy sestavení, ale ne mimo klientům sestavení, deklarujte ji pomocí `Friend` – klíčové slovo v sekci deklarace třídy.</span><span class="sxs-lookup"><span data-stu-id="ace7b-119">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="ace7b-120">K vytvoření k dispozici v celé aplikaci konstanta, deklarujte ji pomocí `Public` – klíčové slovo v prohlášeních části třídy.</span><span class="sxs-lookup"><span data-stu-id="ace7b-120">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span></span>  
  
 <span data-ttu-id="ace7b-121">Další informace najdete v tématu [postupy: deklarace konstanty A](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span><span class="sxs-lookup"><span data-stu-id="ace7b-121">For more information, see [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span></span>  
  
### <a name="avoiding-circular-references"></a><span data-ttu-id="ace7b-122">Zamezení cyklické odkazy</span><span class="sxs-lookup"><span data-stu-id="ace7b-122">Avoiding Circular References</span></span>  
 <span data-ttu-id="ace7b-123">Protože konstanty mohou být definovány jako ostatní konstanty, je možné nechtěně vytvořit *cyklus*, nebo cyklický odkaz mezi dva nebo více konstanty.</span><span class="sxs-lookup"><span data-stu-id="ace7b-123">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span></span> <span data-ttu-id="ace7b-124">Cyklus dojde, pokud máte dva nebo víc veřejných konstanty, z nichž každý je definována v jiné, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ace7b-124">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#16](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]  
[!code-vb[VbEnumsTask#17](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]  
  
 <span data-ttu-id="ace7b-125">Pokud dojde k cyklus, Visual Basic generuje chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="ace7b-125">If a cycle occurs, Visual Basic generates a compiler error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ace7b-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="ace7b-126">See Also</span></span>  
 [<span data-ttu-id="ace7b-127">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="ace7b-127">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="ace7b-128">Datové typy konstanty a literálu</span><span class="sxs-lookup"><span data-stu-id="ace7b-128">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="ace7b-129">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="ace7b-129">Constants and Enumerations</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)  
 [<span data-ttu-id="ace7b-130">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="ace7b-130">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [<span data-ttu-id="ace7b-131">Přehled výčtů</span><span class="sxs-lookup"><span data-stu-id="ace7b-131">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [<span data-ttu-id="ace7b-132">Přehled konstant</span><span class="sxs-lookup"><span data-stu-id="ace7b-132">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="ace7b-133">Postupy: deklarace výčtů</span><span class="sxs-lookup"><span data-stu-id="ace7b-133">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="ace7b-134">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="ace7b-134">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="ace7b-135">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="ace7b-135">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
