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
ms.openlocfilehash: a91da0d9e16ff11fdd4980588fee64b3e4a603c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652374"
---
# <a name="parameter-arrays-visual-basic"></a><span data-ttu-id="0e3af-102">Pole parametrů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e3af-102">Parameter Arrays (Visual Basic)</span></span>
<span data-ttu-id="0e3af-103">Obvykle nelze volání procedury s další argumenty, než určuje postup deklarace.</span><span class="sxs-lookup"><span data-stu-id="0e3af-103">Usually, you cannot call a procedure with more arguments than the procedure declaration specifies.</span></span> <span data-ttu-id="0e3af-104">Pokud budete potřebovat nekonečný počet argumentů, můžou deklarovat *parametr pole*, což umožňuje postupu tak, aby přijímal pole hodnot parametru.</span><span class="sxs-lookup"><span data-stu-id="0e3af-104">When you need an indefinite number of arguments, you can declare a *parameter array*, which allows a procedure to accept an array of values for a parameter.</span></span> <span data-ttu-id="0e3af-105">Nemusíte vědět počet prvků v poli parametrů, když definujete postup.</span><span class="sxs-lookup"><span data-stu-id="0e3af-105">You do not have to know the number of elements in the parameter array when you define the procedure.</span></span> <span data-ttu-id="0e3af-106">Velikost pole je určena jednotlivě každý volání k postupu.</span><span class="sxs-lookup"><span data-stu-id="0e3af-106">The array size is determined individually by each call to the procedure.</span></span>  
  
## <a name="declaring-a-paramarray"></a><span data-ttu-id="0e3af-107">Deklarace ParamArray</span><span class="sxs-lookup"><span data-stu-id="0e3af-107">Declaring a ParamArray</span></span>  
 <span data-ttu-id="0e3af-108">Můžete použít [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) – klíčové slovo k označení parametr pole v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="0e3af-108">You use the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) keyword to denote a parameter array in the parameter list.</span></span> <span data-ttu-id="0e3af-109">Platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="0e3af-109">The following rules apply:</span></span>  
  
-   <span data-ttu-id="0e3af-110">Procedury můžete definovat jenom jeden parametr pole a musí být poslední parametr v definici postupu.</span><span class="sxs-lookup"><span data-stu-id="0e3af-110">A procedure can define only one parameter array, and it must be the last parameter in the procedure definition.</span></span>  
  
-   <span data-ttu-id="0e3af-111">Hodnotou musí být předán pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="0e3af-111">The parameter array must be passed by value.</span></span> <span data-ttu-id="0e3af-112">Je dobrým zvykem explicitně zahrnovat programování [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) – klíčové slovo v definici postupu.</span><span class="sxs-lookup"><span data-stu-id="0e3af-112">It is good programming practice to explicitly include the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword in the procedure definition.</span></span>  
  
-   <span data-ttu-id="0e3af-113">Pole parametrů je automaticky volitelné.</span><span class="sxs-lookup"><span data-stu-id="0e3af-113">The parameter array is automatically optional.</span></span> <span data-ttu-id="0e3af-114">Výchozí hodnota je prázdná jednorozměrné pole typu prvku pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="0e3af-114">Its default value is an empty one-dimensional array of the parameter array's element type.</span></span>  
  
-   <span data-ttu-id="0e3af-115">Všechny parametry předcházející pole parametrů je nutné zadat.</span><span class="sxs-lookup"><span data-stu-id="0e3af-115">All parameters preceding the parameter array must be required.</span></span> <span data-ttu-id="0e3af-116">Pole parametrů musí být pouze volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="0e3af-116">The parameter array must be the only optional parameter.</span></span>  
  
## <a name="calling-a-paramarray"></a><span data-ttu-id="0e3af-117">Volání metody ParamArray</span><span class="sxs-lookup"><span data-stu-id="0e3af-117">Calling a ParamArray</span></span>  
 <span data-ttu-id="0e3af-118">Při volání procedury, která definuje pole parametrů můžete zadat argument v některém z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="0e3af-118">When you call a procedure that defines a parameter array, you can supply the argument in any one of the following ways:</span></span>  
  
-   <span data-ttu-id="0e3af-119">Nothing – to znamená, můžete vynechat [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argument.</span><span class="sxs-lookup"><span data-stu-id="0e3af-119">Nothing — that is, you can omit the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argument.</span></span> <span data-ttu-id="0e3af-120">V takovém případě je prázdné pole předaný postupu.</span><span class="sxs-lookup"><span data-stu-id="0e3af-120">In this case, an empty array is passed to the procedure.</span></span> <span data-ttu-id="0e3af-121">Také můžete předat [nic](../../../../visual-basic/language-reference/nothing.md) – klíčové slovo pomocí stejného efektu.</span><span class="sxs-lookup"><span data-stu-id="0e3af-121">You can also pass the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, with the same effect.</span></span>  
  
-   <span data-ttu-id="0e3af-122">Seznam libovolný počet argumentů, oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="0e3af-122">A list of an arbitrary number of arguments, separated by commas.</span></span> <span data-ttu-id="0e3af-123">Datový typ jednotlivých argumentu musí být implicitně převést na `ParamArray` typ elementu.</span><span class="sxs-lookup"><span data-stu-id="0e3af-123">The data type of each argument must be implicitly convertible to the `ParamArray` element type.</span></span>  
  
-   <span data-ttu-id="0e3af-124">Pole s stejný typ elementu jako parametr pole typu elementu.</span><span class="sxs-lookup"><span data-stu-id="0e3af-124">An array with the same element type as the parameter array's element type.</span></span>  
  
 <span data-ttu-id="0e3af-125">Ve všech případech se kód v rámci procesu považuje za jednorozměrné pole s prvky stejný datový typ jako parametr pole `ParamArray` datového typu.</span><span class="sxs-lookup"><span data-stu-id="0e3af-125">In all cases, the code within the procedure treats the parameter array as a one-dimensional array with elements of the same data type as the `ParamArray` data type.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0e3af-126">Vždy, když budete pracovat s pole to může být velký, bez omezení, existuje riziko překročení některé interní kapacitu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="0e3af-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="0e3af-127">Pokud přijmete pole parametrů, měli byste otestovat pro velikost pole, které do ní předán volající kód.</span><span class="sxs-lookup"><span data-stu-id="0e3af-127">If you accept a parameter array, you should test for the size of the array that the calling code passed to it.</span></span> <span data-ttu-id="0e3af-128">Proveďte příslušné kroky, pokud je příliš velká pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0e3af-128">Take appropriate steps if it is too large for your application.</span></span> <span data-ttu-id="0e3af-129">Další informace najdete v tématu [pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="0e3af-129">For more information, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e3af-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="0e3af-130">Example</span></span>  
 <span data-ttu-id="0e3af-131">V následujícím příkladu definuje a volá funkci `calcSum`.</span><span class="sxs-lookup"><span data-stu-id="0e3af-131">The following example defines and calls the function `calcSum`.</span></span> <span data-ttu-id="0e3af-132">`ParamArray` Modifikátor pro parametr `args` umožňuje funkci tak, aby přijímal proměnný počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="0e3af-132">The `ParamArray` modifier for the parameter `args` enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](../../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-arrays_1.vb)]  
  
 <span data-ttu-id="0e3af-133">V následujícím příkladu definuje procedura se pole parametrů a výstupy hodnoty všechny elementy pole Předaný parametr pole.</span><span class="sxs-lookup"><span data-stu-id="0e3af-133">The following example defines a procedure with a parameter array, and outputs the values of all the array elements passed to the parameter array.</span></span>  
  
 [!code-vb[VbVbcnProcedures#48](./codesnippet/VisualBasic/parameter-arrays_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#49](./codesnippet/VisualBasic/parameter-arrays_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0e3af-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e3af-134">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>  
 [<span data-ttu-id="0e3af-135">Procedury</span><span class="sxs-lookup"><span data-stu-id="0e3af-135">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="0e3af-136">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="0e3af-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="0e3af-137">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="0e3af-137">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="0e3af-138">Předávání argumentů podle pozice a názvu</span><span class="sxs-lookup"><span data-stu-id="0e3af-138">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="0e3af-139">Nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="0e3af-139">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="0e3af-140">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="0e3af-140">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="0e3af-141">Pole</span><span class="sxs-lookup"><span data-stu-id="0e3af-141">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="0e3af-142">Optional</span><span class="sxs-lookup"><span data-stu-id="0e3af-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
