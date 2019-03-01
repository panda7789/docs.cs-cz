---
title: 'Postupy: Přetížení procedury, která přebírá volitelné parametry (Visual Basic)'
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
ms.openlocfilehash: 52e31ba2f9d2f5cf87a5597a3c8d639816a75535
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972661"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a><span data-ttu-id="72f49-102">Postupy: Přetížení procedury, která přebírá volitelné parametry (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72f49-102">How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="72f49-103">Pokud procedura má jeden nebo více [volitelné](../../../../visual-basic/language-reference/modifiers/optional.md) parametry, nelze definovat přetížený verzi, která odpovídá některé z jeho implicitní přetížení.</span><span class="sxs-lookup"><span data-stu-id="72f49-103">If a procedure has one or more [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameters, you cannot define an overloaded version matching any of its implicit overloads.</span></span> <span data-ttu-id="72f49-104">Další informace najdete v tématu "Implicitní přetížení pro volitelné parametry" [aspekty přetížení procedur](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="72f49-104">For more information, see "Implicit Overloads for Optional Parameters" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="one-optional-parameter"></a><span data-ttu-id="72f49-105">Jeden volitelný parametr</span><span class="sxs-lookup"><span data-stu-id="72f49-105">One Optional Parameter</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a><span data-ttu-id="72f49-106">Přetížení procedury, která přijímá jeden volitelný parametr</span><span class="sxs-lookup"><span data-stu-id="72f49-106">To overload a procedure that takes one optional parameter</span></span>  
  
1.  <span data-ttu-id="72f49-107">Zápis `Sub` nebo `Function` příkazu deklarace, která obsahuje volitelný parametr v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="72f49-107">Write a `Sub` or `Function` declaration statement that includes the optional parameter in the parameter list.</span></span> <span data-ttu-id="72f49-108">Nepoužívejte `Optional` – klíčové slovo v této verzi přetížená.</span><span class="sxs-lookup"><span data-stu-id="72f49-108">Do not use the `Optional` keyword in this overloaded version.</span></span>  
  
2.  <span data-ttu-id="72f49-109">Předcházet `Sub` nebo `Function` – klíčové slovo se [přetížení](../../../../visual-basic/language-reference/modifiers/overloads.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="72f49-109">Precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
3.  <span data-ttu-id="72f49-110">Napište kód postup, který by se měl spustit, když volající kód poskytuje nepovinný argument.</span><span class="sxs-lookup"><span data-stu-id="72f49-110">Write the procedure code that should execute when the calling code supplies the optional argument.</span></span>  
  
4.  <span data-ttu-id="72f49-111">Ukončí proceduru s `End Sub` nebo `End Function` příkaz podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="72f49-111">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
5.  <span data-ttu-id="72f49-112">Zápis druhého příkazu deklarace, která je stejná jako první deklarace s tím rozdílem, že neobsahuje volitelný parametr v seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="72f49-112">Write a second declaration statement that is identical to the first declaration except that it does not include the optional parameter in the parameter list.</span></span>  
  
6.  <span data-ttu-id="72f49-113">Napište kód postup, který by se měl spustit, když volající kód neposkytuje nepovinný argument.</span><span class="sxs-lookup"><span data-stu-id="72f49-113">Write the procedure code that should execute when the calling code does not supply the optional argument.</span></span> <span data-ttu-id="72f49-114">Ukončí proceduru s `End Sub` nebo `End Function` příkaz podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="72f49-114">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
     <span data-ttu-id="72f49-115">Následující příklad ukazuje definované s volitelným parametrem, ekvivalentní sadu dvě přetížení procedury a nakonec příkladem neplatné a platný přetížené verze procedury.</span><span class="sxs-lookup"><span data-stu-id="72f49-115">The following example shows a procedure defined with an optional parameter,  an equivalent set of two overloaded procedures, and finally examples of both invalid and valid overloaded versions.</span></span>  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a><span data-ttu-id="72f49-116">Více volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="72f49-116">Multiple Optional Parameters</span></span>  
 <span data-ttu-id="72f49-117">Pro proceduru s více než jeden volitelný parametr musíte obvykle více než dvě přetížené verze.</span><span class="sxs-lookup"><span data-stu-id="72f49-117">For a procedure with more than one optional parameter, you normally need more than two overloaded versions.</span></span> <span data-ttu-id="72f49-118">Například pokud existují dva volitelné parametry a volající kód můžete zadat nebo vynechat, nechte každé z nich nezávisle na druhém, je třeba čtyři přetížené verze, jeden pro jednotlivých možných kombinací zadaným argumentům.</span><span class="sxs-lookup"><span data-stu-id="72f49-118">For example, if there are two optional parameters, and the calling code can supply or omit each one independently of the other, you need four overloaded versions, one for each possible combination of supplied arguments.</span></span>  
  
 <span data-ttu-id="72f49-119">Jak se zvyšuje počet volitelné parametry, zvyšuje složitost přetížení.</span><span class="sxs-lookup"><span data-stu-id="72f49-119">As the number of optional parameters increases, the complexity of the overloading increases.</span></span> <span data-ttu-id="72f49-120">Není-li některá kombinace zadané argumenty nejsou přípustné, nepovinných parametrů. N potřebujete 2 ^ N přetížené verze.</span><span class="sxs-lookup"><span data-stu-id="72f49-120">Unless some combinations of supplied arguments are not acceptable, for N optional parameters you need 2 ^ N overloaded versions.</span></span> <span data-ttu-id="72f49-121">V závislosti na povaze postup můžete zjistit, že srozumitelnost logiky odůvodňuje další úsilí definice přetížené verze.</span><span class="sxs-lookup"><span data-stu-id="72f49-121">Depending on the nature of the procedure, you might find that the clarity of logic justifies the extra effort of defining all the overloaded versions.</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a><span data-ttu-id="72f49-122">Přetížení procedury, která má více než jeden volitelný parametr</span><span class="sxs-lookup"><span data-stu-id="72f49-122">To overload a procedure that takes more than one optional parameter</span></span>  
  
1.  <span data-ttu-id="72f49-123">Určete, jaké kombinace zadaná volitelné argumenty jsou přijatelné logiku podle postupu.</span><span class="sxs-lookup"><span data-stu-id="72f49-123">Determine which combinations of supplied optional arguments are acceptable to the logic of the procedure.</span></span> <span data-ttu-id="72f49-124">Nepřijatelné kombinaci může nastat, pokud jeden volitelný parametr, závisí na jiném.</span><span class="sxs-lookup"><span data-stu-id="72f49-124">An unacceptable combination might arise if one optional parameter depends on another.</span></span> <span data-ttu-id="72f49-125">Například pokud jeden parametr přijímá název manželem a jiné přijímá stáří partnera, kombinace argumentů poskytnutí stáří, ale bez názvu nepřijatelné.</span><span class="sxs-lookup"><span data-stu-id="72f49-125">For example, if one parameter accepts a spouse's name and another accepts the spouse's age, a combination of arguments supplying the age but omitting the name is unacceptable.</span></span>  
  
2.  <span data-ttu-id="72f49-126">Pro každý přijatelné kombinace zadaná volitelné argumenty zapisovat `Sub` nebo `Function` příkazu deklarace, která definuje odpovídající seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="72f49-126">For each acceptable combination of supplied optional arguments, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="72f49-127">Nepoužívejte `Optional` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="72f49-127">Do not use the `Optional` keyword.</span></span>  
  
3.  <span data-ttu-id="72f49-128">V deklaraci, předcházet `Sub` nebo `Function` – klíčové slovo se [přetížení](../../../../visual-basic/language-reference/modifiers/overloads.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="72f49-128">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
4.  <span data-ttu-id="72f49-129">Po deklaraci psát kód postup, který by se měl spustit, když volající kód poskytuje seznam argumentů odpovídající této deklarace seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="72f49-129">Following each declaration, write the procedure code that should execute when the calling code supplies an argument list corresponding to that declaration's parameter list.</span></span>  
  
5.  <span data-ttu-id="72f49-130">Ukončit každý postup s `End Sub` nebo `End Function` příkaz podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="72f49-130">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72f49-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72f49-131">See also</span></span>
- [<span data-ttu-id="72f49-132">Procedury</span><span class="sxs-lookup"><span data-stu-id="72f49-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="72f49-133">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="72f49-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="72f49-134">Nepovinné parametry</span><span class="sxs-lookup"><span data-stu-id="72f49-134">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="72f49-135">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="72f49-135">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="72f49-136">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="72f49-136">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="72f49-137">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="72f49-137">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="72f49-138">Postupy: Definice více verzí procedury</span><span class="sxs-lookup"><span data-stu-id="72f49-138">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="72f49-139">Postupy: Volání přetížené procedury</span><span class="sxs-lookup"><span data-stu-id="72f49-139">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="72f49-140">Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů</span><span class="sxs-lookup"><span data-stu-id="72f49-140">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="72f49-141">Řešení přetížení</span><span class="sxs-lookup"><span data-stu-id="72f49-141">Overload Resolution</span></span>](./overload-resolution.md)
