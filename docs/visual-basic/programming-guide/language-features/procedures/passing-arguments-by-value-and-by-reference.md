---
title: Předávání argumentů podle hodnoty a odkazu (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- passing arguments [Visual Basic], by value or by reference
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing [Visual Basic], by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f10e0e582e060c1305a9c0fe922620cb4da2c215
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a><span data-ttu-id="20737-102">Předávání argumentů podle hodnoty a odkazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20737-102">Passing Arguments by Value and by Reference (Visual Basic)</span></span>
<span data-ttu-id="20737-103">V jazyce Visual Basic, můžete předat argument proceduře *hodnotou* nebo *odkazem*.</span><span class="sxs-lookup"><span data-stu-id="20737-103">In Visual Basic, you can pass an argument to a procedure *by value* or *by reference*.</span></span> <span data-ttu-id="20737-104">To se označuje jako *předávání mechanismus*, a určuje, zda postupu můžete upravit programovací element základní argument ve volání kódu.</span><span class="sxs-lookup"><span data-stu-id="20737-104">This is known as the *passing mechanism*, and it determines whether the procedure can modify the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="20737-105">Deklarace procedury určuje předávání mechanismus pro každý parametr zadáním [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="20737-105">The procedure declaration determines the passing mechanism for each parameter by specifying the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword.</span></span>  
  
## <a name="distinctions"></a><span data-ttu-id="20737-106">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="20737-106">Distinctions</span></span>  
 <span data-ttu-id="20737-107">Při předávání argumentu procedury, nezapomeňte několik různých rozdíly, které spolupracují mezi sebou:</span><span class="sxs-lookup"><span data-stu-id="20737-107">When passing an argument to a procedure, be aware of several different distinctions that interact with each other:</span></span>  
  
-   <span data-ttu-id="20737-108">Jestli je základní programovací element upravitelnými a neupravitelnými</span><span class="sxs-lookup"><span data-stu-id="20737-108">Whether the underlying programming element is modifiable or nonmodifiable</span></span>  
  
-   <span data-ttu-id="20737-109">Jestli je samotného argumentu upravitelnými a neupravitelnými</span><span class="sxs-lookup"><span data-stu-id="20737-109">Whether the argument itself is modifiable or nonmodifiable</span></span>  
  
-   <span data-ttu-id="20737-110">Jestli argument je předávána hodnotou nebo odkazem</span><span class="sxs-lookup"><span data-stu-id="20737-110">Whether the argument is being passed by value or by reference</span></span>  
  
-   <span data-ttu-id="20737-111">Jestli datový typ argumentu je hodnota typu nebo typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="20737-111">Whether the argument data type is a value type or a reference type</span></span>  
  
 <span data-ttu-id="20737-112">Další informace najdete v tématu [rozdíly mezi upravitelnými a Neupravitelnými argumenty](./differences-between-modifiable-and-nonmodifiable-arguments.md) a [rozdíly mezi předáním argumentu podle hodnoty a podle Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span><span class="sxs-lookup"><span data-stu-id="20737-112">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) and [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
## <a name="choice-of-passing-mechanism"></a><span data-ttu-id="20737-113">Volba předávání mechanismus</span><span class="sxs-lookup"><span data-stu-id="20737-113">Choice of Passing Mechanism</span></span>  
 <span data-ttu-id="20737-114">Měli byste vybrat mechanismus předávání pečlivě pro každý argument.</span><span class="sxs-lookup"><span data-stu-id="20737-114">You should choose the passing mechanism carefully for each argument.</span></span>  
  
-   <span data-ttu-id="20737-115">**Ochrana**.</span><span class="sxs-lookup"><span data-stu-id="20737-115">**Protection**.</span></span> <span data-ttu-id="20737-116">Ve výběru mezi dvěma předávání mechanismy, je nejdůležitější kritérium ohrožení volání proměnné, které chcete změnit.</span><span class="sxs-lookup"><span data-stu-id="20737-116">In choosing between the two passing mechanisms, the most important criterion is the exposure of calling variables to change.</span></span> <span data-ttu-id="20737-117">Výhodou předáním argumentu `ByRef` je, že postup můžete vrátit hodnotu volání kódu pomocí tohoto argumentu.</span><span class="sxs-lookup"><span data-stu-id="20737-117">The advantage of passing an argument `ByRef` is that the procedure can return a value to the calling code through that argument.</span></span> <span data-ttu-id="20737-118">Výhodou předáním argumentu `ByVal` je chrání proměnné před změnou procedurou.</span><span class="sxs-lookup"><span data-stu-id="20737-118">The advantage of passing an argument `ByVal` is that it protects a variable from being changed by the procedure.</span></span>  
  
-   <span data-ttu-id="20737-119">**Výkon**.</span><span class="sxs-lookup"><span data-stu-id="20737-119">**Performance**.</span></span> <span data-ttu-id="20737-120">I když tento mechanismus předávání mohou ovlivnit výkon kódu, je obvykle zanedbatelný rozdíl.</span><span class="sxs-lookup"><span data-stu-id="20737-120">Although the passing mechanism can affect the performance of your code, the difference is usually insignificant.</span></span> <span data-ttu-id="20737-121">Jedinou výjimkou je typu hodnota předaná `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="20737-121">One exception to this is a value type passed `ByVal`.</span></span> <span data-ttu-id="20737-122">V takovém případě jazyka Visual Basic zkopíruje obsah celého datového argumentu.</span><span class="sxs-lookup"><span data-stu-id="20737-122">In this case, Visual Basic copies the entire data contents of the argument.</span></span> <span data-ttu-id="20737-123">Proto na typ velké hodnoty, které by bylo třeba strukturou, může být efektivnější předáváme `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="20737-123">Therefore, for a large value type such as a structure, it can be more efficient to pass it `ByRef`.</span></span>  
  
     <span data-ttu-id="20737-124">Pro odkazové typy pouze má ukazatel na data je zkopírovaný (čtyři bajtů na platformách 32-bit, osm bajtů na 64bitových platformách).</span><span class="sxs-lookup"><span data-stu-id="20737-124">For reference types, only the pointer to the data is copied (four bytes on 32-bit platforms, eight bytes on 64-bit platforms).</span></span> <span data-ttu-id="20737-125">Proto můžete předat argumenty typu `String` nebo `Object` hodnotou bez poškozování výkonu.</span><span class="sxs-lookup"><span data-stu-id="20737-125">Therefore, you can pass arguments of type `String` or `Object` by value without harming performance.</span></span>  
  
## <a name="determination-of-the-passing-mechanism"></a><span data-ttu-id="20737-126">Stanovení mechanismus předávání</span><span class="sxs-lookup"><span data-stu-id="20737-126">Determination of the Passing Mechanism</span></span>  
 <span data-ttu-id="20737-127">Deklarace procedury určuje předávání mechanismus pro jednotlivé parametry.</span><span class="sxs-lookup"><span data-stu-id="20737-127">The procedure declaration specifies the passing mechanism for each parameter.</span></span> <span data-ttu-id="20737-128">Volání kódu nejde přepsat `ByVal` mechanismus.</span><span class="sxs-lookup"><span data-stu-id="20737-128">The calling code can't override a `ByVal` mechanism.</span></span>  
  
 <span data-ttu-id="20737-129">Pokud je parametr deklarovat s `ByRef`, volající kód můžete vynutit mechanismus `ByVal` uzavřením argument názvu v závorkách ve volání.</span><span class="sxs-lookup"><span data-stu-id="20737-129">If a parameter is declared with `ByRef`, the calling code can force the mechanism to `ByVal` by enclosing the argument name in parentheses in the call.</span></span> <span data-ttu-id="20737-130">Další informace najdete v tématu [postupy: vynucení předání hodnotou argumentu](./how-to-force-an-argument-to-be-passed-by-value.md).</span><span class="sxs-lookup"><span data-stu-id="20737-130">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
 <span data-ttu-id="20737-131">Ve výchozím nastavení v jazyce Visual Basic se předání argumentů hodnotou.</span><span class="sxs-lookup"><span data-stu-id="20737-131">The default in Visual Basic is to pass arguments by value.</span></span>  
  
## <a name="when-to-pass-an-argument-by-value"></a><span data-ttu-id="20737-132">Když k předání argumentu podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="20737-132">When to Pass an Argument by Value</span></span>  
  
-   <span data-ttu-id="20737-133">Pokud volání kód element základní argument je neupravitelnými, deklarovat s odpovídajícím parametrem [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="20737-133">If the calling code element underlying the argument is a nonmodifiable element, declare the corresponding parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="20737-134">Žádný kód můžete změnit hodnotu neupravitelnými elementu.</span><span class="sxs-lookup"><span data-stu-id="20737-134">No code can change the value of a nonmodifiable element.</span></span>  
  
-   <span data-ttu-id="20737-135">Pokud je základní element upravitelnými, ale nechcete, aby postup nebudete moct změnit jeho hodnotu, deklarovat parametr `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="20737-135">If the underlying element is modifiable, but you do not want the procedure to be able to change its value, declare the parameter `ByVal`.</span></span> <span data-ttu-id="20737-136">Pouze volací kód můžete změnit hodnotu upravitelnými elementu předaná hodnota.</span><span class="sxs-lookup"><span data-stu-id="20737-136">Only the calling code can change the value of a modifiable element passed by value.</span></span>  
  
## <a name="when-to-pass-an-argument-by-reference"></a><span data-ttu-id="20737-137">Když k předání argumentu podle Reference</span><span class="sxs-lookup"><span data-stu-id="20737-137">When to Pass an Argument by Reference</span></span>  
  
-   <span data-ttu-id="20737-138">Pokud má procedura originální potřeba změnit základní elementu v kódu volání, deklarovat s odpovídajícím parametrem [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span><span class="sxs-lookup"><span data-stu-id="20737-138">If the procedure has a genuine need to change the underlying element in the calling code, declare the corresponding parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span></span>  
  
-   <span data-ttu-id="20737-139">Pokud správné spuštění kódu závisí na procesu Změna základní elementu v kódu volání, deklarovat parametr `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="20737-139">If the correct execution of the code depends on the procedure changing the underlying element in the calling code, declare the parameter `ByRef`.</span></span> <span data-ttu-id="20737-140">Pokud předáte hodnotu, nebo pokud volací kód přepíše `ByRef` předávání mechanismus uzavřením argument do závorek, volání procedury může vést k neočekávaným výsledkům.</span><span class="sxs-lookup"><span data-stu-id="20737-140">If you pass it by value, or if the calling code overrides the `ByRef` passing mechanism by enclosing the argument in parentheses, the procedure call might produce unexpected results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20737-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="20737-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="20737-142">Popis</span><span class="sxs-lookup"><span data-stu-id="20737-142">Description</span></span>  
 <span data-ttu-id="20737-143">Následující příklad ilustruje, kdy předání argumentů hodnotou a kdy se mají předat je odkazem.</span><span class="sxs-lookup"><span data-stu-id="20737-143">The following example illustrates when to pass arguments by value and when to pass them by reference.</span></span> <span data-ttu-id="20737-144">Postup `Calculate` má oba `ByVal` a `ByRef` parametr.</span><span class="sxs-lookup"><span data-stu-id="20737-144">Procedure `Calculate` has both a `ByVal` and a `ByRef` parameter.</span></span> <span data-ttu-id="20737-145">Zadané úrokové sazby, `rate`a součet hodnot peníze, `debt`, úloha procedury je k výpočtu nové hodnoty pro `debt` který je výsledkem použití úrokové sazby na původní hodnotu `debt`.</span><span class="sxs-lookup"><span data-stu-id="20737-145">Given an interest rate, `rate`, and a sum of money, `debt`, the task of the procedure is to calculate a new value for `debt` that is the result of applying the interest rate to the original value of `debt`.</span></span> <span data-ttu-id="20737-146">Protože `debt` je `ByRef` parametr nové celkem se odrazí v hodnota argumentu v volací kód, který odpovídá `debt`.</span><span class="sxs-lookup"><span data-stu-id="20737-146">Because `debt` is a `ByRef` parameter, the new total is reflected in the value of the argument in the calling code that corresponds to `debt`.</span></span> <span data-ttu-id="20737-147">Parametr `rate` je `ByVal` parametr protože `Calculate` neměli měnit jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="20737-147">Parameter `rate` is a `ByVal` parameter because `Calculate` should not change its value.</span></span>  
  
### <a name="code"></a><span data-ttu-id="20737-148">Kód</span><span class="sxs-lookup"><span data-stu-id="20737-148">Code</span></span>  
 [!code-vb[VbVbcnProcedures#74](./codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="20737-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="20737-149">See Also</span></span>  
 [<span data-ttu-id="20737-150">Procedury</span><span class="sxs-lookup"><span data-stu-id="20737-150">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="20737-151">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="20737-151">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="20737-152">Postupy: Předání argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="20737-152">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="20737-153">Postupy: Změna hodnoty argumentu procedury</span><span class="sxs-lookup"><span data-stu-id="20737-153">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)  
 [<span data-ttu-id="20737-154">Postupy: Ochrana argumentu procedury před změnami hodnoty</span><span class="sxs-lookup"><span data-stu-id="20737-154">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [<span data-ttu-id="20737-155">Postupy: Vynucení předání argumentu podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="20737-155">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [<span data-ttu-id="20737-156">Předávání argumentů podle pozice a názvu</span><span class="sxs-lookup"><span data-stu-id="20737-156">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="20737-157">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="20737-157">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
