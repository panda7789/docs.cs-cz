---
title: 'Postupy: Vynucení předání argumentu podle hodnoty'
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
ms.openlocfilehash: 48f7d7afebd76916cba11459532d89d71871c79b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387961"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="210b4-102">Postupy: Vynucení předání argumentu podle hodnoty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="210b4-102">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>
<span data-ttu-id="210b4-103">Deklarace procedury určuje mechanismus předávání.</span><span class="sxs-lookup"><span data-stu-id="210b4-103">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="210b4-104">Pokud je parametr deklarovaný jako [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic očekává předání odpovídajícího argumentu odkazem.</span><span class="sxs-lookup"><span data-stu-id="210b4-104">If a parameter is declared [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="210b4-105">To umožňuje proceduře změnit hodnotu programovacího prvku podkladu argumentu v volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="210b4-105">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="210b4-106">Pokud chcete chránit základní prvek proti takové změně, můžete přepsat `ByRef` mechanismus předávání v volání procedury uzavřením názvu argumentu do závorek.</span><span class="sxs-lookup"><span data-stu-id="210b4-106">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="210b4-107">Tyto kulaté závorky jsou kromě závorek ohraničujících seznam argumentů ve volání.</span><span class="sxs-lookup"><span data-stu-id="210b4-107">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="210b4-108">Volající kód nemůže přepsat mechanismus [ByVal](../../../language-reference/modifiers/byval.md) .</span><span class="sxs-lookup"><span data-stu-id="210b4-108">The calling code cannot override a [ByVal](../../../language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="210b4-109">Vynutit předání argumentu hodnotou</span><span class="sxs-lookup"><span data-stu-id="210b4-109">To force an argument to be passed by value</span></span>  
  
- <span data-ttu-id="210b4-110">Pokud je příslušný parametr deklarován `ByVal` v proceduře, není nutné provádět žádné další kroky.</span><span class="sxs-lookup"><span data-stu-id="210b4-110">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> <span data-ttu-id="210b4-111">Visual Basic již očekává předání argumentu hodnotou.</span><span class="sxs-lookup"><span data-stu-id="210b4-111">Visual Basic already expects to pass the argument by value.</span></span>  
  
- <span data-ttu-id="210b4-112">Pokud je odpovídající parametr deklarován `ByRef` v proceduře, uveďte argument do závorek v proceduře volání procedury.</span><span class="sxs-lookup"><span data-stu-id="210b4-112">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="210b4-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="210b4-113">Example</span></span>  
 <span data-ttu-id="210b4-114">Následující příklad přepisuje `ByRef` deklaraci parametru.</span><span class="sxs-lookup"><span data-stu-id="210b4-114">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="210b4-115">V volání, které vynucuje `ByVal` , si všimněte dvou úrovní závorek.</span><span class="sxs-lookup"><span data-stu-id="210b4-115">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 <span data-ttu-id="210b4-116">Když `str` je uzavřen v závorkách v seznamu argumentů, `setNewString` procedura nemůže změnit jeho hodnotu v kódu volajícího a `MsgBox` zobrazení "nemůže být nahrazeno, pokud bylo předáno" ByVal ".</span><span class="sxs-lookup"><span data-stu-id="210b4-116">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="210b4-117">Když není `str` uzavřen v závorkách navíc, procedura ho může změnit a `MsgBox` zobrazí "Toto je nová hodnota pro argument inString."</span><span class="sxs-lookup"><span data-stu-id="210b4-117">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="210b4-118">Kompilovat kód</span><span class="sxs-lookup"><span data-stu-id="210b4-118">Compile the code</span></span>  
 <span data-ttu-id="210b4-119">Pokud předáte proměnnou odkazem, je nutné použít `ByRef` klíčové slovo k určení tohoto mechanismu.</span><span class="sxs-lookup"><span data-stu-id="210b4-119">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="210b4-120">Výchozí hodnotou v Visual Basic je předání argumentů podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="210b4-120">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="210b4-121">Nicméně je dobrým programovacím postupem, jak zahrnout klíčové slovo [ByVal](../../../language-reference/modifiers/byval.md) nebo [ByRef](../../../language-reference/modifiers/byref.md) s každým deklarovaným parametrem.</span><span class="sxs-lookup"><span data-stu-id="210b4-121">However, it is good programming practice to include either the [ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="210b4-122">To usnadňuje čtení kódu.</span><span class="sxs-lookup"><span data-stu-id="210b4-122">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="210b4-123">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="210b4-123">Robust Programming</span></span>  
 <span data-ttu-id="210b4-124">Pokud procedura deklaruje parametr [ByRef](../../../language-reference/modifiers/byref.md), správné spuštění kódu může záviset na tom, zda je možné změnit podkladový prvek v kódu volajícího.</span><span class="sxs-lookup"><span data-stu-id="210b4-124">If a procedure declares a parameter [ByRef](../../../language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="210b4-125">Pokud volající kód přepíše tento volající mechanismus uzavřením argumentu do závorek nebo pokud předává argument, který není upraviteln, procedura nemůže změnit základní prvek.</span><span class="sxs-lookup"><span data-stu-id="210b4-125">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="210b4-126">To může vést k neočekávaným výsledkům při volání kódu.</span><span class="sxs-lookup"><span data-stu-id="210b4-126">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="210b4-127">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="210b4-127">.NET Framework Security</span></span>  
 <span data-ttu-id="210b4-128">V případě, že je možné změnit hodnotu podkladového typu argumentu v volajícím kódu, je vždy potenciálním rizikem.</span><span class="sxs-lookup"><span data-stu-id="210b4-128">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="210b4-129">Ujistěte se, že jste očekávali, že tato hodnota se má změnit, a je připravená ji před použitím ověřit.</span><span class="sxs-lookup"><span data-stu-id="210b4-129">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="210b4-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="210b4-130">See also</span></span>

- [<span data-ttu-id="210b4-131">Procedury</span><span class="sxs-lookup"><span data-stu-id="210b4-131">Procedures</span></span>](./index.md)
- [<span data-ttu-id="210b4-132">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="210b4-132">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="210b4-133">Postupy: Předání argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="210b4-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="210b4-134">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="210b4-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="210b4-135">Rozdíly mezi upravitelnými a neupravitelnými argumenty</span><span class="sxs-lookup"><span data-stu-id="210b4-135">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="210b4-136">Rozdíly mezi předáním argumentu podle hodnoty a podle reference</span><span class="sxs-lookup"><span data-stu-id="210b4-136">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="210b4-137">Postupy: Změna hodnoty argumentu procedury</span><span class="sxs-lookup"><span data-stu-id="210b4-137">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="210b4-138">Postupy: Ochrana argumentu procedury před změnami hodnoty</span><span class="sxs-lookup"><span data-stu-id="210b4-138">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="210b4-139">Předávání argumentů podle pozice a názvu</span><span class="sxs-lookup"><span data-stu-id="210b4-139">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="210b4-140">Typy hodnot a typy odkazu</span><span class="sxs-lookup"><span data-stu-id="210b4-140">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
