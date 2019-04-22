---
title: Pole parametrů (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
ms.openlocfilehash: 8ea4c77056701b8f61c1ed5a53cf20d98ae913bc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834154"
---
# <a name="parameter-arrays-visual-basic"></a><span data-ttu-id="b9c64-102">Pole parametrů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9c64-102">Parameter Arrays (Visual Basic)</span></span>
<span data-ttu-id="b9c64-103">Obvykle nelze volat proceduru s více argumentů, než určuje deklaraci procedury.</span><span class="sxs-lookup"><span data-stu-id="b9c64-103">Usually, you cannot call a procedure with more arguments than the procedure declaration specifies.</span></span> <span data-ttu-id="b9c64-104">Když budete potřebovat nekonečný počet argumentů, je možné deklarovat *pole parametrů*, který umožňuje procedury tak, aby přijímal pole hodnot pro parametr.</span><span class="sxs-lookup"><span data-stu-id="b9c64-104">When you need an indefinite number of arguments, you can declare a *parameter array*, which allows a procedure to accept an array of values for a parameter.</span></span> <span data-ttu-id="b9c64-105">Není nutné znát počet prvků v poli parametrů při definování procesu.</span><span class="sxs-lookup"><span data-stu-id="b9c64-105">You do not have to know the number of elements in the parameter array when you define the procedure.</span></span> <span data-ttu-id="b9c64-106">Velikost pole je samostatně určeno každé volání do procedury.</span><span class="sxs-lookup"><span data-stu-id="b9c64-106">The array size is determined individually by each call to the procedure.</span></span>  
  
## <a name="declaring-a-paramarray"></a><span data-ttu-id="b9c64-107">Deklarace ParamArray</span><span class="sxs-lookup"><span data-stu-id="b9c64-107">Declaring a ParamArray</span></span>  
 <span data-ttu-id="b9c64-108">Můžete použít [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) – klíčové slovo k označení pole parametrů. v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="b9c64-108">You use the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) keyword to denote a parameter array in the parameter list.</span></span> <span data-ttu-id="b9c64-109">Platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="b9c64-109">The following rules apply:</span></span>  
  
-   <span data-ttu-id="b9c64-110">Postup lze definovat pouze jeden parametr pole a musí být poslední parametr v definici procedury.</span><span class="sxs-lookup"><span data-stu-id="b9c64-110">A procedure can define only one parameter array, and it must be the last parameter in the procedure definition.</span></span>  
  
-   <span data-ttu-id="b9c64-111">Pole parametrů musí být předán podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b9c64-111">The parameter array must be passed by value.</span></span> <span data-ttu-id="b9c64-112">To při programování je dobrým zvykem zahrnout explicitně [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) – klíčové slovo v definici procedury.</span><span class="sxs-lookup"><span data-stu-id="b9c64-112">It is good programming practice to explicitly include the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword in the procedure definition.</span></span>  
  
-   <span data-ttu-id="b9c64-113">Pole parametrů je automaticky volitelné.</span><span class="sxs-lookup"><span data-stu-id="b9c64-113">The parameter array is automatically optional.</span></span> <span data-ttu-id="b9c64-114">Výchozí hodnota je prázdné jednorozměrné pole typu prvku pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="b9c64-114">Its default value is an empty one-dimensional array of the parameter array's element type.</span></span>  
  
-   <span data-ttu-id="b9c64-115">Všechny parametry předchozí pole parametrů musí být povinné.</span><span class="sxs-lookup"><span data-stu-id="b9c64-115">All parameters preceding the parameter array must be required.</span></span> <span data-ttu-id="b9c64-116">Pole parametrů musí být pouze volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="b9c64-116">The parameter array must be the only optional parameter.</span></span>  
  
## <a name="calling-a-paramarray"></a><span data-ttu-id="b9c64-117">Volání ParamArray</span><span class="sxs-lookup"><span data-stu-id="b9c64-117">Calling a ParamArray</span></span>  
 <span data-ttu-id="b9c64-118">Při volání procedury, která definuje pole parametrů můžete zadat argument do některého z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="b9c64-118">When you call a procedure that defines a parameter array, you can supply the argument in any one of the following ways:</span></span>  
  
-   <span data-ttu-id="b9c64-119">Nothing – to znamená, můžete vynechat [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argument.</span><span class="sxs-lookup"><span data-stu-id="b9c64-119">Nothing — that is, you can omit the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argument.</span></span> <span data-ttu-id="b9c64-120">V takovém případě prázdné pole je předán do procedury.</span><span class="sxs-lookup"><span data-stu-id="b9c64-120">In this case, an empty array is passed to the procedure.</span></span> <span data-ttu-id="b9c64-121">Můžete také předat [nic](../../../../visual-basic/language-reference/nothing.md) – klíčové slovo se stejný účinek.</span><span class="sxs-lookup"><span data-stu-id="b9c64-121">You can also pass the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, with the same effect.</span></span>  
  
-   <span data-ttu-id="b9c64-122">Seznam libovolný počet argumentů, oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="b9c64-122">A list of an arbitrary number of arguments, separated by commas.</span></span> <span data-ttu-id="b9c64-123">Datový typ každého argumentu musí být implicitně převeditelný na `ParamArray` typ elementu.</span><span class="sxs-lookup"><span data-stu-id="b9c64-123">The data type of each argument must be implicitly convertible to the `ParamArray` element type.</span></span>  
  
-   <span data-ttu-id="b9c64-124">Pole se stejným typem elementu jako typ elementu pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="b9c64-124">An array with the same element type as the parameter array's element type.</span></span>  
  
 <span data-ttu-id="b9c64-125">Ve všech případech se kód v rámci postupu považuje za jednorozměrné pole s prvky stejného datového typu jako pole parametrů `ParamArray` datového typu.</span><span class="sxs-lookup"><span data-stu-id="b9c64-125">In all cases, the code within the procedure treats the parameter array as a one-dimensional array with elements of the same data type as the `ParamArray` data type.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b9c64-126">Pokaždé, když budete pracovat s polem, které mohou být po neomezenou dobu velké, existuje riziko přetečení vnitřní nějakým vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="b9c64-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="b9c64-127">Pokud souhlasíte s polem parametrů, měli byste otestovat pro velikost pole, které do něho předaný volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="b9c64-127">If you accept a parameter array, you should test for the size of the array that the calling code passed to it.</span></span> <span data-ttu-id="b9c64-128">Přijmout vhodná opatření, pokud je příliš velký pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b9c64-128">Take appropriate steps if it is too large for your application.</span></span> <span data-ttu-id="b9c64-129">Další informace najdete v tématu [pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="b9c64-129">For more information, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9c64-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="b9c64-130">Example</span></span>  
 <span data-ttu-id="b9c64-131">Následující příklad definuje a volá funkci `calcSum`.</span><span class="sxs-lookup"><span data-stu-id="b9c64-131">The following example defines and calls the function `calcSum`.</span></span> <span data-ttu-id="b9c64-132">`ParamArray` Modifikátor parametru `args` umožňuje funkci tak, aby přijímal proměnný počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="b9c64-132">The `ParamArray` modifier for the parameter `args` enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 <span data-ttu-id="b9c64-133">Následující příklad definuje proceduru s polem parametrů a vypíše hodnoty ze všech prvků pole předat pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="b9c64-133">The following example defines a procedure with a parameter array, and outputs the values of all the array elements passed to the parameter array.</span></span>  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a><span data-ttu-id="b9c64-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9c64-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="b9c64-135">Procedury</span><span class="sxs-lookup"><span data-stu-id="b9c64-135">Procedures</span></span>](./index.md)
- [<span data-ttu-id="b9c64-136">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="b9c64-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="b9c64-137">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="b9c64-137">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="b9c64-138">Předávání argumentů podle pozice a názvu</span><span class="sxs-lookup"><span data-stu-id="b9c64-138">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="b9c64-139">Nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="b9c64-139">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="b9c64-140">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="b9c64-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="b9c64-141">Pole</span><span class="sxs-lookup"><span data-stu-id="b9c64-141">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="b9c64-142">Optional</span><span class="sxs-lookup"><span data-stu-id="b9c64-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
