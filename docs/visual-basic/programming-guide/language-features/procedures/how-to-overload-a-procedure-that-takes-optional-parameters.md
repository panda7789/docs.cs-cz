---
title: 'Postupy: Přetížení procedury, která přebírá volitelné parametry'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
ms.openlocfilehash: 9ae6818b1e03ccd00ed554e98690e02ffa45de99
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387839"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a><span data-ttu-id="17d57-102">Postupy: Přetížení procedury, která přebírá volitelné parametry (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17d57-102">How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="17d57-103">Pokud má procedura jeden nebo více [volitelných](../../../language-reference/modifiers/optional.md) parametrů, nelze definovat přetíženou verzi odpovídající jakémukoli z jeho implicitních přetížení.</span><span class="sxs-lookup"><span data-stu-id="17d57-103">If a procedure has one or more [Optional](../../../language-reference/modifiers/optional.md) parameters, you cannot define an overloaded version matching any of its implicit overloads.</span></span> <span data-ttu-id="17d57-104">Další informace naleznete v části "implicitní přetížení pro volitelné parametry" v tématu Co je [třeba v postupech přetížení](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="17d57-104">For more information, see "Implicit Overloads for Optional Parameters" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="one-optional-parameter"></a><span data-ttu-id="17d57-105">Jeden volitelný parametr</span><span class="sxs-lookup"><span data-stu-id="17d57-105">One Optional Parameter</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a><span data-ttu-id="17d57-106">Přetížení procedury, která přijímá jeden volitelný parametr</span><span class="sxs-lookup"><span data-stu-id="17d57-106">To overload a procedure that takes one optional parameter</span></span>  
  
1. <span data-ttu-id="17d57-107">Napsat `Sub` `Function` příkaz deklarace nebo, který obsahuje volitelný parametr v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="17d57-107">Write a `Sub` or `Function` declaration statement that includes the optional parameter in the parameter list.</span></span> <span data-ttu-id="17d57-108">Nepoužívejte `Optional` klíčové slovo v této přetížené verzi.</span><span class="sxs-lookup"><span data-stu-id="17d57-108">Do not use the `Optional` keyword in this overloaded version.</span></span>  
  
2. <span data-ttu-id="17d57-109">Předchází `Sub` klíčové slovo or `Function` s klíčovým slovem [přetížení](../../../language-reference/modifiers/overloads.md) .</span><span class="sxs-lookup"><span data-stu-id="17d57-109">Precede the `Sub` or `Function` keyword with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span>  
  
3. <span data-ttu-id="17d57-110">Napište kód procedury, který by měl být proveden, když volající kód dodá volitelný argument.</span><span class="sxs-lookup"><span data-stu-id="17d57-110">Write the procedure code that should execute when the calling code supplies the optional argument.</span></span>  
  
4. <span data-ttu-id="17d57-111">V případě potřeby postup ukončete `End Sub` pomocí `End Function` příkazu nebo.</span><span class="sxs-lookup"><span data-stu-id="17d57-111">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
5. <span data-ttu-id="17d57-112">Napište druhý příkaz deklarace, který je totožný s první deklarací s tím rozdílem, že nezahrnuje volitelný parametr v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="17d57-112">Write a second declaration statement that is identical to the first declaration except that it does not include the optional parameter in the parameter list.</span></span>  
  
6. <span data-ttu-id="17d57-113">Napište kód procedury, který by měl být proveden, když volající kód nedodá nepovinný argument.</span><span class="sxs-lookup"><span data-stu-id="17d57-113">Write the procedure code that should execute when the calling code does not supply the optional argument.</span></span> <span data-ttu-id="17d57-114">V případě potřeby postup ukončete `End Sub` pomocí `End Function` příkazu nebo.</span><span class="sxs-lookup"><span data-stu-id="17d57-114">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
     <span data-ttu-id="17d57-115">Následující příklad ukazuje proceduru, která je definována s volitelným parametrem, ekvivalentní sadou dvou přetížených procedur a nakonec příklady obou neplatných a platných přetížených verzí.</span><span class="sxs-lookup"><span data-stu-id="17d57-115">The following example shows a procedure defined with an optional parameter,  an equivalent set of two overloaded procedures, and finally examples of both invalid and valid overloaded versions.</span></span>  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a><span data-ttu-id="17d57-116">Několik volitelných parametrů</span><span class="sxs-lookup"><span data-stu-id="17d57-116">Multiple Optional Parameters</span></span>  
 <span data-ttu-id="17d57-117">Postup s více než jedním volitelným parametrem obvykle vyžaduje více než dvě přetížené verze.</span><span class="sxs-lookup"><span data-stu-id="17d57-117">For a procedure with more than one optional parameter, you normally need more than two overloaded versions.</span></span> <span data-ttu-id="17d57-118">Například pokud existují dva volitelné parametry a volající kód může dodat nebo vynechat každou z nich nezávisle na sobě, potřebujete čtyři přetížené verze, jednu pro každou možnou kombinaci zadaných argumentů.</span><span class="sxs-lookup"><span data-stu-id="17d57-118">For example, if there are two optional parameters, and the calling code can supply or omit each one independently of the other, you need four overloaded versions, one for each possible combination of supplied arguments.</span></span>  
  
 <span data-ttu-id="17d57-119">Jak se zvyšuje počet nepovinných parametrů, složitost přetížení se zvyšuje.</span><span class="sxs-lookup"><span data-stu-id="17d57-119">As the number of optional parameters increases, the complexity of the overloading increases.</span></span> <span data-ttu-id="17d57-120">Pokud nejsou některé kombinace dodaných argumentů přijatelné, pro N nepovinné parametry potřebujete 2 ^ N přetížené verze.</span><span class="sxs-lookup"><span data-stu-id="17d57-120">Unless some combinations of supplied arguments are not acceptable, for N optional parameters you need 2 ^ N overloaded versions.</span></span> <span data-ttu-id="17d57-121">V závislosti na povaze postupu se můžete setkat s tím, že jasnost logiky odůvodňuje další úsilí o definování všech přetížených verzí.</span><span class="sxs-lookup"><span data-stu-id="17d57-121">Depending on the nature of the procedure, you might find that the clarity of logic justifies the extra effort of defining all the overloaded versions.</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a><span data-ttu-id="17d57-122">Přetížení procedury, která přijímá více než jeden volitelný parametr</span><span class="sxs-lookup"><span data-stu-id="17d57-122">To overload a procedure that takes more than one optional parameter</span></span>  
  
1. <span data-ttu-id="17d57-123">Určete, které kombinace dodaných volitelných argumentů jsou přijatelné pro logiku procedury.</span><span class="sxs-lookup"><span data-stu-id="17d57-123">Determine which combinations of supplied optional arguments are acceptable to the logic of the procedure.</span></span> <span data-ttu-id="17d57-124">Pokud jeden volitelný parametr závisí na jiném, může dojít k nepřijatelné kombinaci.</span><span class="sxs-lookup"><span data-stu-id="17d57-124">An unacceptable combination might arise if one optional parameter depends on another.</span></span> <span data-ttu-id="17d57-125">Například pokud jeden parametr akceptuje jméno osoby a druhý akceptuje stáří osoby, kombinace argumentů, které poskytují věk, ale vynechání názvu je nepřijatelná.</span><span class="sxs-lookup"><span data-stu-id="17d57-125">For example, if one parameter accepts a person's name and another accepts the person's age, a combination of arguments supplying the age but omitting the name is unacceptable.</span></span>  
  
2. <span data-ttu-id="17d57-126">Pro každou přijatelnou kombinaci dodaných volitelných argumentů napište `Sub` `Function` příkaz nebo deklaraci příkazu, který definuje odpovídající seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="17d57-126">For each acceptable combination of supplied optional arguments, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="17d57-127">Nepoužívejte `Optional` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="17d57-127">Do not use the `Optional` keyword.</span></span>  
  
3. <span data-ttu-id="17d57-128">V každé deklaraci uveďte klíčové slovo `Sub` OR `Function` s klíčovým slovem [Overloads](../../../language-reference/modifiers/overloads.md) .</span><span class="sxs-lookup"><span data-stu-id="17d57-128">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span>  
  
4. <span data-ttu-id="17d57-129">Po každé deklaraci zapište kód procedury, která by měla být provedena, když volající kód dodá seznam argumentů odpovídajících tomuto seznamu parametrů deklarace.</span><span class="sxs-lookup"><span data-stu-id="17d57-129">Following each declaration, write the procedure code that should execute when the calling code supplies an argument list corresponding to that declaration's parameter list.</span></span>  
  
5. <span data-ttu-id="17d57-130">V případě potřeby ukončete jednotlivé postupy pomocí `End Sub` `End Function` příkazu nebo.</span><span class="sxs-lookup"><span data-stu-id="17d57-130">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17d57-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="17d57-131">See also</span></span>

- [<span data-ttu-id="17d57-132">Procedury</span><span class="sxs-lookup"><span data-stu-id="17d57-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="17d57-133">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="17d57-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="17d57-134">Volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="17d57-134">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="17d57-135">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="17d57-135">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="17d57-136">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="17d57-136">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="17d57-137">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="17d57-137">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="17d57-138">Postupy: Definice více verzí procedury</span><span class="sxs-lookup"><span data-stu-id="17d57-138">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="17d57-139">Postupy: Volání přetížené procedury</span><span class="sxs-lookup"><span data-stu-id="17d57-139">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="17d57-140">Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů.</span><span class="sxs-lookup"><span data-stu-id="17d57-140">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="17d57-141">Rozlišení přetěžování</span><span class="sxs-lookup"><span data-stu-id="17d57-141">Overload Resolution</span></span>](./overload-resolution.md)
