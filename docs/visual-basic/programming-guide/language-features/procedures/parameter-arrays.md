---
title: Pole parametrů
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
ms.openlocfilehash: dac0575d73ffd4159e89bff344915a33b9d0e5d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364276"
---
# <a name="parameter-arrays-visual-basic"></a><span data-ttu-id="0d478-102">Pole parametrů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d478-102">Parameter Arrays (Visual Basic)</span></span>
<span data-ttu-id="0d478-103">Obvykle nemůžete volat proceduru s více argumenty, než určuje deklarace procedury.</span><span class="sxs-lookup"><span data-stu-id="0d478-103">Usually, you cannot call a procedure with more arguments than the procedure declaration specifies.</span></span> <span data-ttu-id="0d478-104">Pokud potřebujete nekonečný počet argumentů, můžete deklarovat *pole parametrů*, které umožňuje proceduře přijmout pole hodnot pro parametr.</span><span class="sxs-lookup"><span data-stu-id="0d478-104">When you need an indefinite number of arguments, you can declare a *parameter array*, which allows a procedure to accept an array of values for a parameter.</span></span> <span data-ttu-id="0d478-105">Při definování procedury není nutné znát počet prvků v poli parametrů.</span><span class="sxs-lookup"><span data-stu-id="0d478-105">You do not have to know the number of elements in the parameter array when you define the procedure.</span></span> <span data-ttu-id="0d478-106">Velikost pole je určena jednotlivě každým voláním procedury.</span><span class="sxs-lookup"><span data-stu-id="0d478-106">The array size is determined individually by each call to the procedure.</span></span>  
  
## <a name="declaring-a-paramarray"></a><span data-ttu-id="0d478-107">Deklarace ParamArray</span><span class="sxs-lookup"><span data-stu-id="0d478-107">Declaring a ParamArray</span></span>  
 <span data-ttu-id="0d478-108">Použijete klíčové slovo [ParamArray](../../../language-reference/modifiers/paramarray.md) k označení pole parametrů v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="0d478-108">You use the [ParamArray](../../../language-reference/modifiers/paramarray.md) keyword to denote a parameter array in the parameter list.</span></span> <span data-ttu-id="0d478-109">Platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="0d478-109">The following rules apply:</span></span>  
  
- <span data-ttu-id="0d478-110">Procedura může definovat pouze jedno pole parametrů a musí se jednat o poslední parametr v definici procedury.</span><span class="sxs-lookup"><span data-stu-id="0d478-110">A procedure can define only one parameter array, and it must be the last parameter in the procedure definition.</span></span>  
  
- <span data-ttu-id="0d478-111">Pole parametrů musí být předáno hodnotou.</span><span class="sxs-lookup"><span data-stu-id="0d478-111">The parameter array must be passed by value.</span></span> <span data-ttu-id="0d478-112">Je dobrým postupem, jak explicitně do definice procedury přidat klíčové slovo [ByVal](../../../language-reference/modifiers/byval.md) .</span><span class="sxs-lookup"><span data-stu-id="0d478-112">It is good programming practice to explicitly include the [ByVal](../../../language-reference/modifiers/byval.md) keyword in the procedure definition.</span></span>  
  
- <span data-ttu-id="0d478-113">Pole parametrů je automaticky volitelné.</span><span class="sxs-lookup"><span data-stu-id="0d478-113">The parameter array is automatically optional.</span></span> <span data-ttu-id="0d478-114">Výchozí hodnota je prázdné jednorozměrné pole typu elementu pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="0d478-114">Its default value is an empty one-dimensional array of the parameter array's element type.</span></span>  
  
- <span data-ttu-id="0d478-115">Musí být požadovány všechny parametry předcházející poli parametrů.</span><span class="sxs-lookup"><span data-stu-id="0d478-115">All parameters preceding the parameter array must be required.</span></span> <span data-ttu-id="0d478-116">Pole parametrů musí být jediným volitelným parametrem.</span><span class="sxs-lookup"><span data-stu-id="0d478-116">The parameter array must be the only optional parameter.</span></span>  
  
## <a name="calling-a-paramarray"></a><span data-ttu-id="0d478-117">Volání ParamArray</span><span class="sxs-lookup"><span data-stu-id="0d478-117">Calling a ParamArray</span></span>  
 <span data-ttu-id="0d478-118">Když zavoláte proceduru, která definuje pole parametrů, můžete dodat argument jedním z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="0d478-118">When you call a procedure that defines a parameter array, you can supply the argument in any one of the following ways:</span></span>  
  
- <span data-ttu-id="0d478-119">Nothing – argument [ParamArray](../../../language-reference/modifiers/paramarray.md) můžete vynechat.</span><span class="sxs-lookup"><span data-stu-id="0d478-119">Nothing — that is, you can omit the [ParamArray](../../../language-reference/modifiers/paramarray.md) argument.</span></span> <span data-ttu-id="0d478-120">V tomto případě je do procedury předáno prázdné pole.</span><span class="sxs-lookup"><span data-stu-id="0d478-120">In this case, an empty array is passed to the procedure.</span></span> <span data-ttu-id="0d478-121">Pokud explicitně předáte klíčové slovo [Nothing](../../../language-reference/nothing.md) , je do procedury předáno pole s hodnotou null a výsledkem volání NullReferenceException je, že volaná procedura tuto podmínku nekontroluje.</span><span class="sxs-lookup"><span data-stu-id="0d478-121">If you explicitly pass the [Nothing](../../../language-reference/nothing.md) keyword, a null array is passed to the procedure and may result in a NullReferenceException if the called procedure does not check for this condition.</span></span>
  
- <span data-ttu-id="0d478-122">Seznam libovolného počtu argumentů oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="0d478-122">A list of an arbitrary number of arguments, separated by commas.</span></span> <span data-ttu-id="0d478-123">Datový typ každého argumentu musí být implicitně převoditelné na `ParamArray` typ elementu.</span><span class="sxs-lookup"><span data-stu-id="0d478-123">The data type of each argument must be implicitly convertible to the `ParamArray` element type.</span></span>  
  
- <span data-ttu-id="0d478-124">Pole se stejným typem prvku jako typ elementu pole parametru.</span><span class="sxs-lookup"><span data-stu-id="0d478-124">An array with the same element type as the parameter array's element type.</span></span>  
  
 <span data-ttu-id="0d478-125">Ve všech případech kód v proceduře zpracovává pole parametrů jako jednorozměrné pole s prvky stejného datového typu jako `ParamArray` datový typ.</span><span class="sxs-lookup"><span data-stu-id="0d478-125">In all cases, the code within the procedure treats the parameter array as a one-dimensional array with elements of the same data type as the `ParamArray` data type.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0d478-126">Kdykoli budete pracovat s polem, které může být neomezeně velké, existuje riziko, že dojde k přeběhu některé interní kapacity vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="0d478-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="0d478-127">Pokud přijmete pole parametrů, měli byste otestovat velikost pole, do kterého se předává volající kód.</span><span class="sxs-lookup"><span data-stu-id="0d478-127">If you accept a parameter array, you should test for the size of the array that the calling code passed to it.</span></span> <span data-ttu-id="0d478-128">Pokud je pro vaši aplikaci moc velká, proveďte příslušné kroky.</span><span class="sxs-lookup"><span data-stu-id="0d478-128">Take appropriate steps if it is too large for your application.</span></span> <span data-ttu-id="0d478-129">Další informace naleznete v tématu [pole](../arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="0d478-129">For more information, see [Arrays](../arrays/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d478-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="0d478-130">Example</span></span>  
 <span data-ttu-id="0d478-131">V následujícím příkladu je definována a volána funkce `calcSum` .</span><span class="sxs-lookup"><span data-stu-id="0d478-131">The following example defines and calls the function `calcSum`.</span></span> <span data-ttu-id="0d478-132">`ParamArray`Modifikátor pro parametr `args` umožňuje funkci přijmout proměnlivý počet argumentů.</span><span class="sxs-lookup"><span data-stu-id="0d478-132">The `ParamArray` modifier for the parameter `args` enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 <span data-ttu-id="0d478-133">Následující příklad definuje proceduru s polem parametrů a vytvoří výstup hodnot všech prvků pole předaných do pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="0d478-133">The following example defines a procedure with a parameter array, and outputs the values of all the array elements passed to the parameter array.</span></span>  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a><span data-ttu-id="0d478-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d478-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="0d478-135">Procedury</span><span class="sxs-lookup"><span data-stu-id="0d478-135">Procedures</span></span>](./index.md)
- [<span data-ttu-id="0d478-136">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="0d478-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="0d478-137">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="0d478-137">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="0d478-138">Předávání argumentů podle pozice a názvu</span><span class="sxs-lookup"><span data-stu-id="0d478-138">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="0d478-139">Volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="0d478-139">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="0d478-140">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="0d478-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="0d478-141">Pole</span><span class="sxs-lookup"><span data-stu-id="0d478-141">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="0d478-142">Volitelné</span><span class="sxs-lookup"><span data-stu-id="0d478-142">Optional</span></span>](../../../language-reference/modifiers/optional.md)
