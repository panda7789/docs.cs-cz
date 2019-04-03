---
title: Rozdíly mezi upravitelnými a neupravitelnými argumenty (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: a880ae8c13eebd5d9d325468098e058f58d3fa71
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826662"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a><span data-ttu-id="f741a-102">Rozdíly mezi upravitelnými a neupravitelnými argumenty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f741a-102">Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)</span></span>
<span data-ttu-id="f741a-103">Při volání procedury, typicky pass jeden nebo více argumentů do něj.</span><span class="sxs-lookup"><span data-stu-id="f741a-103">When you call a procedure, you typically pass one or more arguments to it.</span></span> <span data-ttu-id="f741a-104">Každý argument odpovídá základní programovací element.</span><span class="sxs-lookup"><span data-stu-id="f741a-104">Each argument corresponds to an underlying programming element.</span></span> <span data-ttu-id="f741a-105">Základní elementy a argumenty, sami může být upravitelnými a neupravitelnými.</span><span class="sxs-lookup"><span data-stu-id="f741a-105">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span></span>  
  
## <a name="modifiable-and-nonmodifiable-elements"></a><span data-ttu-id="f741a-106">Upravitelnými a Neupravitelnými elementy</span><span class="sxs-lookup"><span data-stu-id="f741a-106">Modifiable and Nonmodifiable Elements</span></span>  
 <span data-ttu-id="f741a-107">Programovací element může být buď *upravitelná element*, svou hodnotu mění, která může mít nebo *neupravitelnými element*, který má pevnou hodnotu, po jejím vytvoření.</span><span class="sxs-lookup"><span data-stu-id="f741a-107">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span></span>  
  
 <span data-ttu-id="f741a-108">V následující tabulce jsou uvedeny upravitelnými a neupravitelnými programovací prvky.</span><span class="sxs-lookup"><span data-stu-id="f741a-108">The following table lists modifiable and nonmodifiable programming elements.</span></span>  
  
|<span data-ttu-id="f741a-109">Upravitelná elementy</span><span class="sxs-lookup"><span data-stu-id="f741a-109">Modifiable elements</span></span>|<span data-ttu-id="f741a-110">Neupravitelnými elementy</span><span class="sxs-lookup"><span data-stu-id="f741a-110">Nonmodifiable elements</span></span>|  
|-------------------------|----------------------------|  
|<span data-ttu-id="f741a-111">Lokální proměnné (deklarované uvnitř procedury), včetně objektových proměnných, s výjimkou jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f741a-111">Local variables (declared inside procedures), including object variables, except for read-only</span></span>|<span data-ttu-id="f741a-112">Proměnné určené jen pro čtení, polí a vlastností</span><span class="sxs-lookup"><span data-stu-id="f741a-112">Read-only variables, fields, and properties</span></span>|  
|<span data-ttu-id="f741a-113">Pole (členské proměnné modulů, třídy a struktury), s výjimkou jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f741a-113">Fields (member variables of modules, classes, and structures), except for read-only</span></span>|<span data-ttu-id="f741a-114">Konstanty a literály</span><span class="sxs-lookup"><span data-stu-id="f741a-114">Constants and literals</span></span>|  
|<span data-ttu-id="f741a-115">Vlastnosti, s výjimkou jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f741a-115">Properties, except for read-only</span></span>|<span data-ttu-id="f741a-116">Členy výčtu</span><span class="sxs-lookup"><span data-stu-id="f741a-116">Enumeration members</span></span>|  
|<span data-ttu-id="f741a-117">Prvky pole</span><span class="sxs-lookup"><span data-stu-id="f741a-117">Array elements</span></span>|<span data-ttu-id="f741a-118">Výrazy (i když jsou jejich prvky upravitelná)</span><span class="sxs-lookup"><span data-stu-id="f741a-118">Expressions (even if their elements are modifiable)</span></span>|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a><span data-ttu-id="f741a-119">Upravitelnými a Neupravitelnými argumenty</span><span class="sxs-lookup"><span data-stu-id="f741a-119">Modifiable and Nonmodifiable Arguments</span></span>  
 <span data-ttu-id="f741a-120">A *upravitelná argument* s upravitelná základního elementu.</span><span class="sxs-lookup"><span data-stu-id="f741a-120">A *modifiable argument* is one with a modifiable underlying element.</span></span> <span data-ttu-id="f741a-121">Volající kód může ukládat novou hodnotu v okamžiku, a pokud předat argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), kód v postupu můžete také upravit základní prvek ve volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="f741a-121">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="f741a-122">A *neupravitelnými argument* má element neupravitelnými základní nebo je předán [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="f741a-122">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="f741a-123">Postup nelze upravovat základní prvek v volající kód, i v případě, že je lze měnit element.</span><span class="sxs-lookup"><span data-stu-id="f741a-123">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span></span> <span data-ttu-id="f741a-124">Pokud je element neupravitelnými, nelze jej upravovat volání samotný kód.</span><span class="sxs-lookup"><span data-stu-id="f741a-124">If it is a nonmodifiable element, the calling code itself cannot modify it.</span></span>  
  
 <span data-ttu-id="f741a-125">Volané procedury může upravovat jeho místní kopii neupravitelnými argument, ale tato změna nemá vliv na základní element ve volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="f741a-125">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f741a-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f741a-126">See also</span></span>

- [<span data-ttu-id="f741a-127">Procedury</span><span class="sxs-lookup"><span data-stu-id="f741a-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="f741a-128">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="f741a-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="f741a-129">Postupy: Předání argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="f741a-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="f741a-130">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="f741a-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="f741a-131">Rozdíly mezi předáním argumentu podle hodnoty a podle reference</span><span class="sxs-lookup"><span data-stu-id="f741a-131">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="f741a-132">Postupy: Změna hodnoty argumentu procedury</span><span class="sxs-lookup"><span data-stu-id="f741a-132">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="f741a-133">Postupy: Ochrana argumentu procedury proti změnám hodnoty</span><span class="sxs-lookup"><span data-stu-id="f741a-133">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="f741a-134">Postupy: Vynucení argumentu být předána podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="f741a-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="f741a-135">Předávání argumentů podle pozice a názvu</span><span class="sxs-lookup"><span data-stu-id="f741a-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="f741a-136">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="f741a-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
