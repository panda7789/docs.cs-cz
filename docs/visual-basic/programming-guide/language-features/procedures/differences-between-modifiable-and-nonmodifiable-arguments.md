---
title: "Rozdíly mezi upravitelnými a neupravitelnými argumenty (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ab108d064f5c6740f80328a9b6db4785334550ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a><span data-ttu-id="b588a-102">Rozdíly mezi upravitelnými a neupravitelnými argumenty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b588a-102">Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)</span></span>
<span data-ttu-id="b588a-103">Při volání procedury, obvykle předání jeden nebo více argumentů do ní.</span><span class="sxs-lookup"><span data-stu-id="b588a-103">When you call a procedure, you typically pass one or more arguments to it.</span></span> <span data-ttu-id="b588a-104">Každý argument odpovídá základní programovací element.</span><span class="sxs-lookup"><span data-stu-id="b588a-104">Each argument corresponds to an underlying programming element.</span></span> <span data-ttu-id="b588a-105">Základní elementy a argumenty sami může být upravitelnými a neupravitelnými.</span><span class="sxs-lookup"><span data-stu-id="b588a-105">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span></span>  
  
## <a name="modifiable-and-nonmodifiable-elements"></a><span data-ttu-id="b588a-106">Upravitelnými a Neupravitelnými elementy</span><span class="sxs-lookup"><span data-stu-id="b588a-106">Modifiable and Nonmodifiable Elements</span></span>  
 <span data-ttu-id="b588a-107">Programovací element může být buď *upravitelnými element*, která může mít jeho hodnota změněna, nebo *neupravitelnými element*, který má pevnou hodnotu, po vytvoření.</span><span class="sxs-lookup"><span data-stu-id="b588a-107">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span></span>  
  
 <span data-ttu-id="b588a-108">Následující tabulka uvádí upravitelnými a neupravitelnými elementům programování.</span><span class="sxs-lookup"><span data-stu-id="b588a-108">The following table lists modifiable and nonmodifiable programming elements.</span></span>  
  
|<span data-ttu-id="b588a-109">Upravitelnými elementy</span><span class="sxs-lookup"><span data-stu-id="b588a-109">Modifiable elements</span></span>|<span data-ttu-id="b588a-110">Neupravitelnými elementy</span><span class="sxs-lookup"><span data-stu-id="b588a-110">Nonmodifiable elements</span></span>|  
|-------------------------|----------------------------|  
|<span data-ttu-id="b588a-111">Lokální proměnné (deklarované uvnitř procedury), včetně objektové proměnné, s výjimkou jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b588a-111">Local variables (declared inside procedures), including object variables, except for read-only</span></span>|<span data-ttu-id="b588a-112">Proměnné jen pro čtení, polí a vlastností</span><span class="sxs-lookup"><span data-stu-id="b588a-112">Read-only variables, fields, and properties</span></span>|  
|<span data-ttu-id="b588a-113">Pole (členské proměnné modulů, třídy a struktury), s výjimkou jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b588a-113">Fields (member variables of modules, classes, and structures), except for read-only</span></span>|<span data-ttu-id="b588a-114">Konstanty a literály</span><span class="sxs-lookup"><span data-stu-id="b588a-114">Constants and literals</span></span>|  
|<span data-ttu-id="b588a-115">Vlastnosti, s výjimkou jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b588a-115">Properties, except for read-only</span></span>|<span data-ttu-id="b588a-116">Členové výčtu</span><span class="sxs-lookup"><span data-stu-id="b588a-116">Enumeration members</span></span>|  
|<span data-ttu-id="b588a-117">Elementy pole</span><span class="sxs-lookup"><span data-stu-id="b588a-117">Array elements</span></span>|<span data-ttu-id="b588a-118">Výrazy (i když jsou jejich elementů upravitelnými)</span><span class="sxs-lookup"><span data-stu-id="b588a-118">Expressions (even if their elements are modifiable)</span></span>|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a><span data-ttu-id="b588a-119">Upravitelnými a Neupravitelnými argumenty</span><span class="sxs-lookup"><span data-stu-id="b588a-119">Modifiable and Nonmodifiable Arguments</span></span>  
 <span data-ttu-id="b588a-120">A *upravitelnými argument* je jedním s upravitelnými základní elementem.</span><span class="sxs-lookup"><span data-stu-id="b588a-120">A *modifiable argument* is one with a modifiable underlying element.</span></span> <span data-ttu-id="b588a-121">Volání kódu můžete uložit novou hodnotu kdykoli, a Pokud předáte argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), kód v postupu můžete také upravit základní elementu v kódu volání.</span><span class="sxs-lookup"><span data-stu-id="b588a-121">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="b588a-122">A *neupravitelnými argument* má neupravitelnými základní element nebo je předán [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="b588a-122">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="b588a-123">Postup nelze upravit základní element v kód volání, i když je upravitelnými element.</span><span class="sxs-lookup"><span data-stu-id="b588a-123">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span></span> <span data-ttu-id="b588a-124">Pokud je element neupravitelnými, nelze jej upravovat volání samotný kód.</span><span class="sxs-lookup"><span data-stu-id="b588a-124">If it is a nonmodifiable element, the calling code itself cannot modify it.</span></span>  
  
 <span data-ttu-id="b588a-125">Volané procedury může změnit jeho místní kopii neupravitelnými argument, ale tato změna nemá vliv na základní elementu v kódu volání.</span><span class="sxs-lookup"><span data-stu-id="b588a-125">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b588a-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="b588a-126">See Also</span></span>  
 [<span data-ttu-id="b588a-127">Postupy</span><span class="sxs-lookup"><span data-stu-id="b588a-127">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="b588a-128">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="b588a-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="b588a-129">Postupy: předání argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="b588a-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="b588a-130">Předávání argumentů podle hodnoty a podle Reference</span><span class="sxs-lookup"><span data-stu-id="b588a-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="b588a-131">Rozdíly mezi předáním argumentu podle hodnoty a podle Reference</span><span class="sxs-lookup"><span data-stu-id="b588a-131">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [<span data-ttu-id="b588a-132">Postupy: Změna hodnoty argumentu procedury</span><span class="sxs-lookup"><span data-stu-id="b588a-132">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)  
 [<span data-ttu-id="b588a-133">Postupy: ochrana argumentu procedury proti změnám hodnoty</span><span class="sxs-lookup"><span data-stu-id="b588a-133">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [<span data-ttu-id="b588a-134">Postupy: vynucení předání hodnotou argumentu</span><span class="sxs-lookup"><span data-stu-id="b588a-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [<span data-ttu-id="b588a-135">Předávání argumentů podle pozice a názvu</span><span class="sxs-lookup"><span data-stu-id="b588a-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="b588a-136">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="b588a-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
