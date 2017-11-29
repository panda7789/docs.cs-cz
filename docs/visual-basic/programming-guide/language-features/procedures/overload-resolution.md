---
title: "Rozlišení přetěžování (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- overload resolution
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedure overloading [Visual Basic], overload resolution
- signatures [Visual Basic], procedure
- overloads [Visual Basic], resolution
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7eb71b69496e27b664fe297e9e5f105b360ce01d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="overload-resolution-visual-basic"></a><span data-ttu-id="8e4e8-102">Rozlišení přetěžování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e4e8-102">Overload Resolution (Visual Basic)</span></span>
<span data-ttu-id="8e4e8-103">Když [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilátoru zaznamená volání procedury, která je definována v několika verzích přetížené, kompilátor musíte rozhodnout, které přetížení volání.</span><span class="sxs-lookup"><span data-stu-id="8e4e8-103">When the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler encounters a call to a procedure that is defined in several overloaded versions, the compiler must decide which of the overloads to call.</span></span> <span data-ttu-id="8e4e8-104">Dělá to pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="8e4e8-104">It does this by performing the following steps:</span></span>  
  
1.  <span data-ttu-id="8e4e8-105">**Usnadnění přístupu.**</span><span class="sxs-lookup"><span data-stu-id="8e4e8-105">**Accessibility.**</span></span> <span data-ttu-id="8e4e8-106">Eliminuje žádné přetížení s úroveň přístupu, která brání jeho volání volající kód.</span><span class="sxs-lookup"><span data-stu-id="8e4e8-106">It eliminates any overload with an access level that prevents the calling code from calling it.</span></span>  
  
2.  <span data-ttu-id="8e4e8-107">**Počet parametrů.**</span><span class="sxs-lookup"><span data-stu-id="8e4e8-107">**Number of Parameters.**</span></span> <span data-ttu-id="8e4e8-108">Eliminuje žádné přetížení, které definuje jiný počet parametrů, než se zadávají ve volání.</span><span class="sxs-lookup"><span data-stu-id="8e4e8-108">It eliminates any overload that defines a different number of parameters than are supplied in the call.</span></span>  
  
3.  <span data-ttu-id="8e4e8-109">**Datové typy parametrů.**</span><span class="sxs-lookup"><span data-stu-id="8e4e8-109">**Parameter Data Types.**</span></span> <span data-ttu-id="8e4e8-110">Kompilátor poskytuje instance metody předvoleb nad rozšiřující metody.</span><span class="sxs-lookup"><span data-stu-id="8e4e8-110">The compiler gives instance methods preference over extension methods.</span></span> <span data-ttu-id="8e4e8-111">Pokud se najde libovolné metody instance, který vyžaduje pouze rozšiřující převody tak, aby odpovídaly volání procedury, všechny rozšiřující metody jsou vyřazen a kompilátor pokračuje pouze kandidáty metoda instance.</span><span class="sxs-lookup"><span data-stu-id="8e4e8-111">If any instance method is found that requires only widening conversions to match the procedure call, all extension methods are dropped and the compiler continues with only the instance method candidates.</span></span> <span data-ttu-id="8e4e8-112">Pokud se žádná instance metoda nenajde, pokračuje v instanci a rozšiřující metody.</span><span class="sxs-lookup"><span data-stu-id="8e4e8-112">If no such instance method is found, it continues with both instance and extension methods.</span></span>  
  
     <span data-ttu-id="8e4e8-113">V tomto kroku eliminuje žádné přetížení, pro který datové typy argumentů volání nelze převést na typy parametrů, které jsou definované v přetížení.</span><span class="sxs-lookup"><span data-stu-id="8e4e8-113">In this step, it eliminates any overload for which the data types of the calling arguments cannot be converted to the parameter types defined in the overload.</span></span>  
  
4.  <span data-ttu-id="8e4e8-114">**Zužující převody.**</span><span class="sxs-lookup"><span data-stu-id="8e4e8-114">**Narrowing Conversions.**</span></span> <span data-ttu-id="8e4e8-115">Eliminuje žádné přetížení, které vyžaduje zužující převod z volání typy argumentů pro typy definované parametrů.</span><span class="sxs-lookup"><span data-stu-id="8e4e8-115">It eliminates any overload that requires a narrowing conversion from the calling argument types to the defined parameter types.</span></span> <span data-ttu-id="8e4e8-116">To platí určení, zda kontrola typu přepnout ([Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) je `On` nebo `Off`.</span><span class="sxs-lookup"><span data-stu-id="8e4e8-116">This is true whether the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `On` or `Off`.</span></span>  
  
5.  <span data-ttu-id="8e4e8-117">**Minimálně rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="8e4e8-117">**Least Widening.**</span></span> <span data-ttu-id="8e4e8-118">Kompilátor zvažuje zbývající přetížení v párech.</span><span class="sxs-lookup"><span data-stu-id="8e4e8-118">The compiler considers the remaining overloads in pairs.</span></span> <span data-ttu-id="8e4e8-119">Pro každý pár porovná datové typy definovaných parametrů.</span><span class="sxs-lookup"><span data-stu-id="8e4e8-119">For each pair, it compares the data types of the defined parameters.</span></span> <span data-ttu-id="8e4e8-120">Pokud typy v jednom z přetížení všechny rozšířit na odpovídající typy v dalších, kompilátor eliminuje ty druhé.</span><span class="sxs-lookup"><span data-stu-id="8e4e8-120">If the types in one of the overloads all widen to the corresponding types in the other, the compiler eliminates the latter.</span></span> <span data-ttu-id="8e4e8-121">To znamená zachová přetížení, která vyžaduje nejnižší možné rozšíření.</span><span class="sxs-lookup"><span data-stu-id="8e4e8-121">That is, it retains the overload that requires the least amount of widening.</span></span>  
  
6.  <span data-ttu-id="8e4e8-122">**Na jednom uchazeči.**</span><span class="sxs-lookup"><span data-stu-id="8e4e8-122">**Single Candidate.**</span></span> <span data-ttu-id="8e4e8-123">Pokračuje considering přetížení v párech dokud jenom jeden přetížení zůstane a jeho přeloží volání této přetížení.</span><span class="sxs-lookup"><span data-stu-id="8e4e8-123">It continues considering overloads in pairs until only one overload remains, and it resolves the call to that overload.</span></span> <span data-ttu-id="8e4e8-124">Pokud kompilátor nelze zmenšit přetížení do jediného kandidáta, vygeneruje se chyba.</span><span class="sxs-lookup"><span data-stu-id="8e4e8-124">If the compiler cannot reduce the overloads to a single candidate, it generates an error.</span></span>  
  
 <span data-ttu-id="8e4e8-125">Následující obrázek znázorňuje proces, který určuje, které sady přetížené verze volat.</span><span class="sxs-lookup"><span data-stu-id="8e4e8-125">The following illustration shows the process that determines which of a set of overloaded versions to call.</span></span>  
  
 <span data-ttu-id="8e4e8-126">![Vývojový diagram procesu rozlišení přetěžování](./media/overloadres.gif "OverloadRes")</span><span class="sxs-lookup"><span data-stu-id="8e4e8-126">![Flow diagram of overload resolution process](./media/overloadres.gif "OverloadRes")</span></span>  
<span data-ttu-id="8e4e8-127">Řešení mezi přetížené verze</span><span class="sxs-lookup"><span data-stu-id="8e4e8-127">Resolving among overloaded versions</span></span>  
  
 <span data-ttu-id="8e4e8-128">Následující příklad znázorňuje tento proces rozlišení přetížení.</span><span class="sxs-lookup"><span data-stu-id="8e4e8-128">The following example illustrates this overload resolution process.</span></span>  
  
 [!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/overload-resolution_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/overload-resolution_2.vb)]  
  
 <span data-ttu-id="8e4e8-129">Při prvním volání do kompilátoru eliminuje první přetížení, protože typ prvního argumentu (`Short`) zmenší tak, aby typ odpovídající parametru (`Byte`).</span><span class="sxs-lookup"><span data-stu-id="8e4e8-129">In the first call, the compiler eliminates the first overload because the type of the first argument (`Short`) narrows to the type of the corresponding parameter (`Byte`).</span></span> <span data-ttu-id="8e4e8-130">Protože každý argument typ v druhé přetížení pak eliminuje třetí přetížení (`Short` a `Single`) rozšiřuje odpovídající typ v třetí přetížení (`Integer` a `Single`).</span><span class="sxs-lookup"><span data-stu-id="8e4e8-130">It then eliminates the third overload because each argument type in the second overload (`Short` and `Single`) widens to the corresponding type in the third overload (`Integer` and `Single`).</span></span> <span data-ttu-id="8e4e8-131">Druhý přetížení vyžaduje méně rozšíření, kompilátor použije pro volání.</span><span class="sxs-lookup"><span data-stu-id="8e4e8-131">The second overload requires less widening, so the compiler uses it for the call.</span></span>  
  
 <span data-ttu-id="8e4e8-132">V druhé volání do kompilátoru nelze eliminovat žádné přetížení na základě zužující.</span><span class="sxs-lookup"><span data-stu-id="8e4e8-132">In the second call, the compiler cannot eliminate any of the overloads on the basis of narrowing.</span></span> <span data-ttu-id="8e4e8-133">Eliminuje třetí přetížení ze stejného důvodu jako první volání, protože ji můžete volat druhý přetížení s menší rozšiřující s typy argumentů.</span><span class="sxs-lookup"><span data-stu-id="8e4e8-133">It eliminates the third overload for the same reason as in the first call, because it can call the second overload with less widening of the argument types.</span></span> <span data-ttu-id="8e4e8-134">Kompilátor však nelze vyřešit mezi prvním a druhém přetížení.</span><span class="sxs-lookup"><span data-stu-id="8e4e8-134">However, the compiler cannot resolve between the first and second overloads.</span></span> <span data-ttu-id="8e4e8-135">Každá z nich má jeden typ definované parametru, která rozšiřuje odpovídající typ v dalších (`Byte` k `Short`, ale `Single` k `Double`).</span><span class="sxs-lookup"><span data-stu-id="8e4e8-135">Each has one defined parameter type that widens to the corresponding type in the other (`Byte` to `Short`, but `Single` to `Double`).</span></span> <span data-ttu-id="8e4e8-136">Kompilátor proto vygeneruje chybu rozlišení přetížení.</span><span class="sxs-lookup"><span data-stu-id="8e4e8-136">The compiler therefore generates an overload resolution error.</span></span>  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a><span data-ttu-id="8e4e8-137">Přetížený volitelné a ParamArray – argumenty</span><span class="sxs-lookup"><span data-stu-id="8e4e8-137">Overloaded Optional and ParamArray Arguments</span></span>  
 <span data-ttu-id="8e4e8-138">Pokud dva přetížení procedury mít identické podpisy s tím rozdílem, že je deklarovaná poslední parametr [volitelné](../../../../visual-basic/language-reference/modifiers/optional.md) v jednom a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) do druhé kompilátor přeloží volání této procedury jako následovně:</span><span class="sxs-lookup"><span data-stu-id="8e4e8-138">If two overloads of a procedure have identical signatures except that the last parameter is declared [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) in one and [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) in the other, the compiler resolves a call to that procedure as follows:</span></span>  
  
|<span data-ttu-id="8e4e8-139">Pokud poskytuje poslední argument jako volání</span><span class="sxs-lookup"><span data-stu-id="8e4e8-139">If the call supplies the last argument as</span></span>|<span data-ttu-id="8e4e8-140">Kompilátor přeloží volání přetížení poslední argument jako deklarace</span><span class="sxs-lookup"><span data-stu-id="8e4e8-140">The compiler resolves the call to the overload declaring the last argument as</span></span>|  
|---|---|  
|<span data-ttu-id="8e4e8-141">Žádná hodnota (argument vynechán)</span><span class="sxs-lookup"><span data-stu-id="8e4e8-141">No value (argument omitted)</span></span>|`Optional`|  
|<span data-ttu-id="8e4e8-142">jednu hodnotu</span><span class="sxs-lookup"><span data-stu-id="8e4e8-142">A single value</span></span>|`Optional`|  
|<span data-ttu-id="8e4e8-143">Dvě nebo více hodnot v seznamu odděleném čárkami</span><span class="sxs-lookup"><span data-stu-id="8e4e8-143">Two or more values in a comma-separated list</span></span>|`ParamArray`|  
|<span data-ttu-id="8e4e8-144">Pole s žádné délkou (včetně prázdné pole)</span><span class="sxs-lookup"><span data-stu-id="8e4e8-144">An array of any length (including an empty array)</span></span>|`ParamArray`|  
  
## <a name="see-also"></a><span data-ttu-id="8e4e8-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e4e8-145">See Also</span></span>  
 [<span data-ttu-id="8e4e8-146">Volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="8e4e8-146">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="8e4e8-147">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="8e4e8-147">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="8e4e8-148">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="8e4e8-148">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="8e4e8-149">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="8e4e8-149">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="8e4e8-150">Postupy: definice více verzí procedury</span><span class="sxs-lookup"><span data-stu-id="8e4e8-150">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="8e4e8-151">Postupy: volání přetížené procedury</span><span class="sxs-lookup"><span data-stu-id="8e4e8-151">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)  
 [<span data-ttu-id="8e4e8-152">Postupy: přetížení procedury, která přebírá volitelné parametry</span><span class="sxs-lookup"><span data-stu-id="8e4e8-152">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="8e4e8-153">Postupy: přetížení procedury, která přebírá nekonečný počet parametrů</span><span class="sxs-lookup"><span data-stu-id="8e4e8-153">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="8e4e8-154">Aspekty přetížení procedur</span><span class="sxs-lookup"><span data-stu-id="8e4e8-154">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)  
 [<span data-ttu-id="8e4e8-155">Přetížení</span><span class="sxs-lookup"><span data-stu-id="8e4e8-155">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [<span data-ttu-id="8e4e8-156">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="8e4e8-156">Extension Methods</span></span>](./extension-methods.md)
