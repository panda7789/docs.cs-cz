---
title: 'Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů.'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: ddff8c8cd82593b7d89fb0847e56123c287e364b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387878"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="5fb29-102">Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="5fb29-102">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>
<span data-ttu-id="5fb29-103">Pokud má procedura parametr [ParamArray](../../../language-reference/modifiers/paramarray.md) , nemůžete definovat přetíženou verzi, která vezme jednorozměrné pole pro pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="5fb29-103">If a procedure has a [ParamArray](../../../language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="5fb29-104">Další informace naleznete v části "implicitní přetížení pro parametr ParamArray" v tématu Co je [třeba v postupech přetížení](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5fb29-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="5fb29-105">Přetížení procedury, která přebírá proměnný počet parametrů</span><span class="sxs-lookup"><span data-stu-id="5fb29-105">To overload a procedure that takes a variable number of parameters</span></span>  
  
1. <span data-ttu-id="5fb29-106">Zajistěte, aby procedura a volání logiky kódu byly přínosem z přetížených verzí více než z `ParamArray` parametru.</span><span class="sxs-lookup"><span data-stu-id="5fb29-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="5fb29-107">Viz "přetížení a ParamArray" v tématu Co je [třeba v postupech přetížení](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5fb29-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2. <span data-ttu-id="5fb29-108">Určete, která čísla zadaných hodnot má procedura přijmout v proměnné části seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="5fb29-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="5fb29-109">To může zahrnovat případ bez hodnoty a může obsahovat případ jednorozměrného pole.</span><span class="sxs-lookup"><span data-stu-id="5fb29-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3. <span data-ttu-id="5fb29-110">Pro každý přijatelný počet zadaných hodnot, zápis `Sub` nebo `Function` příkaz deklarace, který definuje odpovídající seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="5fb29-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="5fb29-111">V této přetížené verzi nepoužívejte `Optional` ani `ParamArray` klíčové slovo or.</span><span class="sxs-lookup"><span data-stu-id="5fb29-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4. <span data-ttu-id="5fb29-112">V každé deklaraci uveďte klíčové slovo `Sub` OR `Function` s klíčovým slovem [Overloads](../../../language-reference/modifiers/overloads.md) .</span><span class="sxs-lookup"><span data-stu-id="5fb29-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5. <span data-ttu-id="5fb29-113">Podle každé deklarace napište kód procedury, který by měl být proveden, když volající kód dodá hodnoty odpovídající seznamu parametrů dané deklarace.</span><span class="sxs-lookup"><span data-stu-id="5fb29-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6. <span data-ttu-id="5fb29-114">V případě potřeby ukončete jednotlivé postupy pomocí `End Sub` `End Function` příkazu nebo.</span><span class="sxs-lookup"><span data-stu-id="5fb29-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fb29-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="5fb29-115">Example</span></span>  
 <span data-ttu-id="5fb29-116">Následující příklad ukazuje proceduru, která je definována s parametrem [ParamArray](../../../language-reference/modifiers/paramarray.md) , a pak ekvivalentní sadu přetížených procedur.</span><span class="sxs-lookup"><span data-stu-id="5fb29-116">The following example shows a procedure defined with a [ParamArray](../../../language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="5fb29-117">Taková procedura se nedá přetížit se seznamem parametrů, který přebírá jednorozměrné pole pro pole parametrů.</span><span class="sxs-lookup"><span data-stu-id="5fb29-117">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="5fb29-118">Můžete však použít signatury dalších implicitních přetížení.</span><span class="sxs-lookup"><span data-stu-id="5fb29-118">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="5fb29-119">Tuto ilustraci ilustrují následující deklarace.</span><span class="sxs-lookup"><span data-stu-id="5fb29-119">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 <span data-ttu-id="5fb29-120">Kód v přetížených verzích nemusí testovat, zda volající kód zadal jednu nebo více hodnot pro `ParamArray` parametr, nebo pokud ano, kolik jich má.</span><span class="sxs-lookup"><span data-stu-id="5fb29-120">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> <span data-ttu-id="5fb29-121">Visual Basic předá řízení verzi, která odpovídá seznamu argumentů volání.</span><span class="sxs-lookup"><span data-stu-id="5fb29-121">Visual Basic passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="5fb29-122">Kompilovat kód</span><span class="sxs-lookup"><span data-stu-id="5fb29-122">Compile the code</span></span>  
 <span data-ttu-id="5fb29-123">Vzhledem k tomu, že procedura s `ParamArray` parametrem je ekvivalentem sady přetížených verzí, nelze takovou proceduru přetížit se seznamem parametrů odpovídajícím žádné z těchto implicitních přetížení.</span><span class="sxs-lookup"><span data-stu-id="5fb29-123">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="5fb29-124">Další informace najdete v tématu věnovaném [důležitým postupům při přetížení](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5fb29-124">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="5fb29-125">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5fb29-125">.NET Framework Security</span></span>  
 <span data-ttu-id="5fb29-126">Kdykoli budete pracovat s polem, které může být neomezeně velké, existuje riziko, že dojde k přeběhu některé interní kapacity vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="5fb29-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="5fb29-127">Pokud přijmete pole parametrů, měli byste otestovat délku pole, na které se předává volající kód, a provést příslušné kroky, pokud je pro vaši aplikaci příliš velká.</span><span class="sxs-lookup"><span data-stu-id="5fb29-127">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fb29-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="5fb29-128">See also</span></span>

- [<span data-ttu-id="5fb29-129">Procedury</span><span class="sxs-lookup"><span data-stu-id="5fb29-129">Procedures</span></span>](./index.md)
- [<span data-ttu-id="5fb29-130">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="5fb29-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="5fb29-131">Volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="5fb29-131">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="5fb29-132">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="5fb29-132">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="5fb29-133">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="5fb29-133">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="5fb29-134">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="5fb29-134">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="5fb29-135">Postupy: Definice více verzí procedury</span><span class="sxs-lookup"><span data-stu-id="5fb29-135">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="5fb29-136">Postupy: Volání přetížené procedury</span><span class="sxs-lookup"><span data-stu-id="5fb29-136">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="5fb29-137">Postupy: Přetížení procedury, která přebírá nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="5fb29-137">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="5fb29-138">Rozlišení přetěžování</span><span class="sxs-lookup"><span data-stu-id="5fb29-138">Overload Resolution</span></span>](./overload-resolution.md)
