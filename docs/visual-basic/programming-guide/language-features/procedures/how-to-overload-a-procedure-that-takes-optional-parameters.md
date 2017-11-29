---
title: "Postupy: Přetížení procedury, která přebírá volitelné parametry (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b4a863944d4f9ab265aab52578fbb704ca376de5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a><span data-ttu-id="db132-102">Postupy: Přetížení procedury, která přebírá volitelné parametry (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db132-102">How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="db132-103">Pokud procedury má jeden nebo více [volitelné](../../../../visual-basic/language-reference/modifiers/optional.md) parametry, nelze definovat přetížené verze odpovídající některý z jeho implicitní přetížení.</span><span class="sxs-lookup"><span data-stu-id="db132-103">If a procedure has one or more [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameters, you cannot define an overloaded version matching any of its implicit overloads.</span></span> <span data-ttu-id="db132-104">Další informace najdete v tématu "Implicitní přetížení pro volitelné parametry" v [aspekty přetížení procedur](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="db132-104">For more information, see "Implicit Overloads for Optional Parameters" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="one-optional-parameter"></a><span data-ttu-id="db132-105">Jeden volitelný parametr</span><span class="sxs-lookup"><span data-stu-id="db132-105">One Optional Parameter</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a><span data-ttu-id="db132-106">Chcete-li přetížení procedury, která přijímá jeden parametr volitelný</span><span class="sxs-lookup"><span data-stu-id="db132-106">To overload a procedure that takes one optional parameter</span></span>  
  
1.  <span data-ttu-id="db132-107">Zápis `Sub` nebo `Function` deklarace příkaz, který obsahuje volitelný parametr v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="db132-107">Write a `Sub` or `Function` declaration statement that includes the optional parameter in the parameter list.</span></span> <span data-ttu-id="db132-108">Nepoužívejte `Optional` – klíčové slovo v této verzi přetížená.</span><span class="sxs-lookup"><span data-stu-id="db132-108">Do not use the `Optional` keyword in this overloaded version.</span></span>  
  
2.  <span data-ttu-id="db132-109">Předcházet `Sub` nebo `Function` – klíčové slovo s [přetížení](../../../../visual-basic/language-reference/modifiers/overloads.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="db132-109">Precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
3.  <span data-ttu-id="db132-110">Psaní kódu postup, který by měl být spuštěn při volání kód poskytuje nepovinný argument.</span><span class="sxs-lookup"><span data-stu-id="db132-110">Write the procedure code that should execute when the calling code supplies the optional argument.</span></span>  
  
4.  <span data-ttu-id="db132-111">Ukončení procesu se `End Sub` nebo `End Function` příkaz podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="db132-111">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
5.  <span data-ttu-id="db132-112">Zápis druhý příkaz deklaraci, která je stejná jako první deklaraci s tím rozdílem, že v seznamu parametrů neobsahoval volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="db132-112">Write a second declaration statement that is identical to the first declaration except that it does not include the optional parameter in the parameter list.</span></span>  
  
6.  <span data-ttu-id="db132-113">Psaní kódu postup, který by měl být spuštěn při volání kód neposkytuje nepovinný argument.</span><span class="sxs-lookup"><span data-stu-id="db132-113">Write the procedure code that should execute when the calling code does not supply the optional argument.</span></span> <span data-ttu-id="db132-114">Ukončení procesu se `End Sub` nebo `End Function` příkaz podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="db132-114">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
     <span data-ttu-id="db132-115">Následující příklad ukazuje postup definovaný s volitelný parametr ekvivalentní sadu přetížené dva postupy a nakonec příklady neplatný i platný přetížené verze.</span><span class="sxs-lookup"><span data-stu-id="db132-115">The following example shows a procedure defined with an optional parameter,  an equivalent set of two overloaded procedures, and finally examples of both invalid and valid overloaded versions.</span></span>  
  
     [!code-vb[VbVbcnProcedures#59](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_2.vb)]  
  
     [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_3.vb)]  
  
## <a name="multiple-optional-parameters"></a><span data-ttu-id="db132-116">Více volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="db132-116">Multiple Optional Parameters</span></span>  
 <span data-ttu-id="db132-117">Pro proceduru s více než jeden volitelný parametr musíte obvykle více než dvě přetížené verze.</span><span class="sxs-lookup"><span data-stu-id="db132-117">For a procedure with more than one optional parameter, you normally need more than two overloaded versions.</span></span> <span data-ttu-id="db132-118">Například pokud existují dvě volitelné parametry a volání kód můžete zadat nebo vynechejte každé z nich nezávisle na druhém, musíte čtyři přetížené verze, jeden pro jednotlivých možných kombinací zadané argumenty.</span><span class="sxs-lookup"><span data-stu-id="db132-118">For example, if there are two optional parameters, and the calling code can supply or omit each one independently of the other, you need four overloaded versions, one for each possible combination of supplied arguments.</span></span>  
  
 <span data-ttu-id="db132-119">Hodnota se zvyšuje počet volitelné parametry, zvyšuje složitost přetížení.</span><span class="sxs-lookup"><span data-stu-id="db132-119">As the number of optional parameters increases, the complexity of the overloading increases.</span></span> <span data-ttu-id="db132-120">Pokud některé kombinace zadané argumenty nejsou přijatelné, pro volitelné parametry N potřebujete 2 ^ N přetížený verze.</span><span class="sxs-lookup"><span data-stu-id="db132-120">Unless some combinations of supplied arguments are not acceptable, for N optional parameters you need 2 ^ N overloaded versions.</span></span> <span data-ttu-id="db132-121">V závislosti na povaze postup je možné, že přehlednost logiky opravňuje navíc úsilí definice všechny přetížené verze.</span><span class="sxs-lookup"><span data-stu-id="db132-121">Depending on the nature of the procedure, you might find that the clarity of logic justifies the extra effort of defining all the overloaded versions.</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a><span data-ttu-id="db132-122">Přetížení procedury, která má více než jeden nepovinný parametr</span><span class="sxs-lookup"><span data-stu-id="db132-122">To overload a procedure that takes more than one optional parameter</span></span>  
  
1.  <span data-ttu-id="db132-123">Určete, které kombinace zadaný volitelné argumenty jsou přijatelné pro logiku procedury.</span><span class="sxs-lookup"><span data-stu-id="db132-123">Determine which combinations of supplied optional arguments are acceptable to the logic of the procedure.</span></span> <span data-ttu-id="db132-124">Pokud jeden volitelný parametr závisí na jiném, mohou se vyskytnout nepřijatelné kombinaci.</span><span class="sxs-lookup"><span data-stu-id="db132-124">An unacceptable combination might arise if one optional parameter depends on another.</span></span> <span data-ttu-id="db132-125">Například pokud jméno partnera přijímá jeden parametr a jiné přijímá manžela stáří, kombinace argumentů zadávání stáří, ale bez názvu nepřijatelné.</span><span class="sxs-lookup"><span data-stu-id="db132-125">For example, if one parameter accepts a spouse's name and another accepts the spouse's age, a combination of arguments supplying the age but omitting the name is unacceptable.</span></span>  
  
2.  <span data-ttu-id="db132-126">Pro každou přijatelné kombinaci zadaný volitelné argumenty, zápisu `Sub` nebo `Function` deklarace příkaz, který definuje odpovídající seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="db132-126">For each acceptable combination of supplied optional arguments, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="db132-127">Nepoužívejte `Optional` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="db132-127">Do not use the `Optional` keyword.</span></span>  
  
3.  <span data-ttu-id="db132-128">V každé deklaraci předcházet `Sub` nebo `Function` – klíčové slovo s [přetížení](../../../../visual-basic/language-reference/modifiers/overloads.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="db132-128">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
4.  <span data-ttu-id="db132-129">Následující každá deklarace psát kód postup, který by měl spustit, když kód volání poskytuje seznam argumentů odpovídající seznam parametrů tohoto prohlášení.</span><span class="sxs-lookup"><span data-stu-id="db132-129">Following each declaration, write the procedure code that should execute when the calling code supplies an argument list corresponding to that declaration's parameter list.</span></span>  
  
5.  <span data-ttu-id="db132-130">Terminate – každý postup s `End Sub` nebo `End Function` příkaz podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="db132-130">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db132-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="db132-131">See Also</span></span>  
 [<span data-ttu-id="db132-132">Postupy</span><span class="sxs-lookup"><span data-stu-id="db132-132">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="db132-133">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="db132-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="db132-134">Volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="db132-134">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="db132-135">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="db132-135">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="db132-136">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="db132-136">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="db132-137">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="db132-137">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="db132-138">Postupy: definice více verzí procedury</span><span class="sxs-lookup"><span data-stu-id="db132-138">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="db132-139">Postupy: volání přetížené procedury</span><span class="sxs-lookup"><span data-stu-id="db132-139">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)  
 [<span data-ttu-id="db132-140">Postupy: přetížení procedury, která přebírá nekonečný počet parametrů</span><span class="sxs-lookup"><span data-stu-id="db132-140">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="db132-141">Řešení přetížení</span><span class="sxs-lookup"><span data-stu-id="db132-141">Overload Resolution</span></span>](./overload-resolution.md)
