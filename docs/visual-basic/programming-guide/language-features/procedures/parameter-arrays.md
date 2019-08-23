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
ms.openlocfilehash: 5a2813b81490e7c2fcf1abcf5fd36ca89d9d7929
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933860"
---
# <a name="parameter-arrays-visual-basic"></a><span data-ttu-id="f17e4-102">Pole parametrů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f17e4-102">Parameter Arrays (Visual Basic)</span></span>
<span data-ttu-id="f17e4-103">Obvykle nemůžete volat proceduru s více argumenty, než určuje deklarace procedury.</span><span class="sxs-lookup"><span data-stu-id="f17e4-103">Usually, you cannot call a procedure with more arguments than the procedure declaration specifies.</span></span> <span data-ttu-id="f17e4-104">Pokud potřebujete nekonečný počet argumentů, můžete deklarovat *pole parametrů*, které umožňuje proceduře přijmout pole hodnot pro parametr.</span><span class="sxs-lookup"><span data-stu-id="f17e4-104">When you need an indefinite number of arguments, you can declare a *parameter array*, which allows a procedure to accept an array of values for a parameter.</span></span> <span data-ttu-id="f17e4-105">Při definování procedury není nutné znát počet prvků v poli parametrů.</span><span class="sxs-lookup"><span data-stu-id="f17e4-105">You do not have to know the number of elements in the parameter array when you define the procedure.</span></span> <span data-ttu-id="f17e4-106">Velikost pole je určena jednotlivě každým voláním procedury.</span><span class="sxs-lookup"><span data-stu-id="f17e4-106">The array size is determined individually by each call to the procedure.</span></span>  
  
## <a name="declaring-a-paramarray"></a><span data-ttu-id="f17e4-107">Deklarace ParamArray</span><span class="sxs-lookup"><span data-stu-id="f17e4-107">Declaring a ParamArray</span></span>  
 <span data-ttu-id="f17e4-108">Použijete klíčové slovo [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) k označení pole parametrů v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="f17e4-108">You use the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) keyword to denote a parameter array in the parameter list.</span></span> <span data-ttu-id="f17e4-109">Platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="f17e4-109">The following rules apply:</span></span>  
  
- <span data-ttu-id="f17e4-110">Procedura může definovat pouze jedno pole parametrů a musí se jednat o poslední parametr v definici procedury.</span><span class="sxs-lookup"><span data-stu-id="f17e4-110">A procedure can define only one parameter array, and it must be the last parameter in the procedure definition.</span></span>  
  
- <span data-ttu-id="f17e4-111">Pole parametrů musí být předáno hodnotou.</span><span class="sxs-lookup"><span data-stu-id="f17e4-111">The parameter array must be passed by value.</span></span> <span data-ttu-id="f17e4-112">Je dobrým postupem, jak explicitně do definice procedury přidat klíčové slovo [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) .</span><span class="sxs-lookup"><span data-stu-id="f17e4-112">It is good programming practice to explicitly include the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword in the procedure definition.</span></span>  
  
- <span data-ttu-id="f17e4-113">Pole parametrů je automaticky volitelné.</span><span class="sxs-lookup"><span data-stu-id="f17e4-113">The parameter array is automatically optional.</span></span> <span data-ttu-id="f17e4-114">Výchozí hodnota je prázdné jednorozměrné pole typu elementu pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="f17e4-114">Its default value is an empty one-dimensional array of the parameter array's element type.</span></span>  
  
- <span data-ttu-id="f17e4-115">Musí být požadovány všechny parametry předcházející poli parametrů.</span><span class="sxs-lookup"><span data-stu-id="f17e4-115">All parameters preceding the parameter array must be required.</span></span> <span data-ttu-id="f17e4-116">Pole parametrů musí být jediným volitelným parametrem.</span><span class="sxs-lookup"><span data-stu-id="f17e4-116">The parameter array must be the only optional parameter.</span></span>  
  
## <a name="calling-a-paramarray"></a><span data-ttu-id="f17e4-117">Volání ParamArray</span><span class="sxs-lookup"><span data-stu-id="f17e4-117">Calling a ParamArray</span></span>  
 <span data-ttu-id="f17e4-118">Když zavoláte proceduru, která definuje pole parametrů, můžete dodat argument jedním z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="f17e4-118">When you call a procedure that defines a parameter array, you can supply the argument in any one of the following ways:</span></span>  
  
- <span data-ttu-id="f17e4-119">Nothing – argument [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) můžete vynechat.</span><span class="sxs-lookup"><span data-stu-id="f17e4-119">Nothing — that is, you can omit the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argument.</span></span> <span data-ttu-id="f17e4-120">V tomto případě je do procedury předáno prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="f17e4-120">In this case, an empty array is passed to the procedure.</span></span> <span data-ttu-id="f17e4-121">Pomocí stejného efektu můžete také předat klíčové slovo [Nothing](../../../../visual-basic/language-reference/nothing.md) .</span><span class="sxs-lookup"><span data-stu-id="f17e4-121">You can also pass the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, with the same effect.</span></span>  
  
- <span data-ttu-id="f17e4-122">Seznam libovolného počtu argumentů oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="f17e4-122">A list of an arbitrary number of arguments, separated by commas.</span></span> <span data-ttu-id="f17e4-123">Datový typ každého argumentu musí být implicitně převoditelné na `ParamArray` typ elementu.</span><span class="sxs-lookup"><span data-stu-id="f17e4-123">The data type of each argument must be implicitly convertible to the `ParamArray` element type.</span></span>  
  
- <span data-ttu-id="f17e4-124">Pole se stejným typem prvku jako typ elementu pole parametru.</span><span class="sxs-lookup"><span data-stu-id="f17e4-124">An array with the same element type as the parameter array's element type.</span></span>  
  
 <span data-ttu-id="f17e4-125">Ve všech případech kód v proceduře zpracovává pole parametrů jako jednorozměrné pole s prvky stejného datového typu jako `ParamArray` datový typ.</span><span class="sxs-lookup"><span data-stu-id="f17e4-125">In all cases, the code within the procedure treats the parameter array as a one-dimensional array with elements of the same data type as the `ParamArray` data type.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f17e4-126">Kdykoli budete pracovat s polem, které může být neomezeně velké, existuje riziko, že dojde k přeběhu některé interní kapacity vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="f17e4-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="f17e4-127">Pokud přijmete pole parametrů, měli byste otestovat velikost pole, do kterého se předává volající kód.</span><span class="sxs-lookup"><span data-stu-id="f17e4-127">If you accept a parameter array, you should test for the size of the array that the calling code passed to it.</span></span> <span data-ttu-id="f17e4-128">Pokud je pro vaši aplikaci moc velká, proveďte příslušné kroky.</span><span class="sxs-lookup"><span data-stu-id="f17e4-128">Take appropriate steps if it is too large for your application.</span></span> <span data-ttu-id="f17e4-129">Další informace naleznete v tématu [pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="f17e4-129">For more information, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f17e4-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="f17e4-130">Example</span></span>  
 <span data-ttu-id="f17e4-131">V následujícím příkladu je definována a volána funkce `calcSum`.</span><span class="sxs-lookup"><span data-stu-id="f17e4-131">The following example defines and calls the function `calcSum`.</span></span> <span data-ttu-id="f17e4-132">Modifikátor pro parametr `args` umožňuje funkci přijmout proměnlivý počet argumentů. `ParamArray`</span><span class="sxs-lookup"><span data-stu-id="f17e4-132">The `ParamArray` modifier for the parameter `args` enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 <span data-ttu-id="f17e4-133">Následující příklad definuje proceduru s polem parametrů a vytvoří výstup hodnot všech prvků pole předaných do pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="f17e4-133">The following example defines a procedure with a parameter array, and outputs the values of all the array elements passed to the parameter array.</span></span>  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a><span data-ttu-id="f17e4-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f17e4-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="f17e4-135">Procedury</span><span class="sxs-lookup"><span data-stu-id="f17e4-135">Procedures</span></span>](./index.md)
- [<span data-ttu-id="f17e4-136">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="f17e4-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="f17e4-137">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="f17e4-137">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="f17e4-138">Předávání argumentů podle pozice a názvu</span><span class="sxs-lookup"><span data-stu-id="f17e4-138">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="f17e4-139">Nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="f17e4-139">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="f17e4-140">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="f17e4-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="f17e4-141">Pole</span><span class="sxs-lookup"><span data-stu-id="f17e4-141">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="f17e4-142">Optional</span><span class="sxs-lookup"><span data-stu-id="f17e4-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
