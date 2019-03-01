---
title: 'Postupy: Vynucení argumentu být předána podle hodnoty (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
ms.openlocfilehash: 7bd78772b35e3f336f49c1d39b5f56a3a2076c30
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970282"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="602d7-102">Postupy: Vynucení argumentu být předána podle hodnoty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="602d7-102">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>
<span data-ttu-id="602d7-103">Deklarace procedury určuje předávání.</span><span class="sxs-lookup"><span data-stu-id="602d7-103">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="602d7-104">Pokud parametr je deklarován [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic se očekává, že odpovídající argument předávání odkazem.</span><span class="sxs-lookup"><span data-stu-id="602d7-104">If a parameter is declared [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="602d7-105">To umožňuje postup, chcete-li změnit hodnotu programovací element základní argumentu ve volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="602d7-105">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="602d7-106">Pokud chcete chránit základní prvek proti takové změny, můžete přepsat `ByRef` předávání mechanismus v postupu pro volání uzavření název argumentu do závorek.</span><span class="sxs-lookup"><span data-stu-id="602d7-106">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="602d7-107">Tyto závorky jsou kromě závorky uzavírající seznamu argumentů ve volání.</span><span class="sxs-lookup"><span data-stu-id="602d7-107">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="602d7-108">Volající kód nelze přepsat [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mechanismus.</span><span class="sxs-lookup"><span data-stu-id="602d7-108">The calling code cannot override a [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="602d7-109">K vynucení argumentu být předána podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="602d7-109">To force an argument to be passed by value</span></span>  
  
-   <span data-ttu-id="602d7-110">Pokud je deklarován odpovídajícího parametru `ByVal` v postupu, nepotřebujete žádné další kroky.</span><span class="sxs-lookup"><span data-stu-id="602d7-110">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> <span data-ttu-id="602d7-111">Visual Basic již očekává, že k předání argumentu podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="602d7-111">Visual Basic already expects to pass the argument by value.</span></span>  
  
-   <span data-ttu-id="602d7-112">Pokud je deklarován odpovídajícího parametru `ByRef` v postupu, uzavřete jej do závorek ve volání procedury.</span><span class="sxs-lookup"><span data-stu-id="602d7-112">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="602d7-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="602d7-113">Example</span></span>  
 <span data-ttu-id="602d7-114">Následující příklad přepisuje `ByRef` deklarace parametru.</span><span class="sxs-lookup"><span data-stu-id="602d7-114">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="602d7-115">Při volání funkce, která vynutí `ByVal`, Všimněte si dvě úrovně závorky.</span><span class="sxs-lookup"><span data-stu-id="602d7-115">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 <span data-ttu-id="602d7-116">Když `str` není uzavřen v závorkách navíc v rámci seznamu argumentů `setNewString` procedury nelze změnit jeho hodnotu ve volajícím kódu a `MsgBox` zobrazí "Nelze nahradit, pokud předaná ByVal".</span><span class="sxs-lookup"><span data-stu-id="602d7-116">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="602d7-117">Když `str` není uzavřen v závorkách navíc, můžete změnit podle postupu, a `MsgBox` zobrazí "Toto je nová hodnota pro inString argument."</span><span class="sxs-lookup"><span data-stu-id="602d7-117">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="602d7-118">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="602d7-118">Compiling the Code</span></span>  
 <span data-ttu-id="602d7-119">Při předání proměnné podle odkazu, je nutné použít `ByRef` – klíčové slovo k určení tento mechanismus.</span><span class="sxs-lookup"><span data-stu-id="602d7-119">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="602d7-120">Ve výchozím nastavení v jazyce Visual Basic je předání argumentů podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="602d7-120">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="602d7-121">Ale při programování je dobrým zvykem zahrnout buď [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) – klíčové slovo s každou deklarovaný parametr.</span><span class="sxs-lookup"><span data-stu-id="602d7-121">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="602d7-122">Díky tomu váš kód lépe čitelný.</span><span class="sxs-lookup"><span data-stu-id="602d7-122">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="602d7-123">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="602d7-123">Robust Programming</span></span>  
 <span data-ttu-id="602d7-124">Pokud postup deklaruje parametr [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), správné spuštění kódu může záviset na schopnost změnit základní prvek ve volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="602d7-124">If a procedure declares a parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="602d7-125">Pokud volající kód přepíše tento mechanismus volání uzavřením argument v závorkách nebo v případě úspěšného neupravitelnými argumentu, nelze změnit postup základního elementu.</span><span class="sxs-lookup"><span data-stu-id="602d7-125">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="602d7-126">To může vést k neočekávaným výsledkům ve volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="602d7-126">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="602d7-127">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="602d7-127">.NET Framework Security</span></span>  
 <span data-ttu-id="602d7-128">Je vždycky představuje potenciální riziko postup, chcete-li změnit hodnotu argumentu ve volajícím kódu základní, kterému je povoleno.</span><span class="sxs-lookup"><span data-stu-id="602d7-128">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="602d7-129">Ujistěte se, že očekáváte, že tuto hodnotu změnit a připravit tak zkontrolovat, že platnost před jeho použitím.</span><span class="sxs-lookup"><span data-stu-id="602d7-129">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="602d7-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="602d7-130">See also</span></span>
- [<span data-ttu-id="602d7-131">Procedury</span><span class="sxs-lookup"><span data-stu-id="602d7-131">Procedures</span></span>](./index.md)
- [<span data-ttu-id="602d7-132">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="602d7-132">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="602d7-133">Postupy: Předání argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="602d7-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="602d7-134">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="602d7-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="602d7-135">Rozdíly mezi upravitelnými a neupravitelnými argumenty</span><span class="sxs-lookup"><span data-stu-id="602d7-135">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="602d7-136">Rozdíly mezi předáním argumentu podle hodnoty a podle reference</span><span class="sxs-lookup"><span data-stu-id="602d7-136">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="602d7-137">Postupy: Změna hodnoty argumentu procedury</span><span class="sxs-lookup"><span data-stu-id="602d7-137">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="602d7-138">Postupy: Ochrana argumentu procedury proti změnám hodnoty</span><span class="sxs-lookup"><span data-stu-id="602d7-138">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="602d7-139">Předávání argumentů podle pozice a názvu</span><span class="sxs-lookup"><span data-stu-id="602d7-139">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="602d7-140">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="602d7-140">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
