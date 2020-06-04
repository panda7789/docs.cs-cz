---
title: Rozdíly mezi upravitelnými a neupravitelnými argumenty
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: 733f92cc2cdaa6e923c57649774ceb64de172c18
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403340"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a><span data-ttu-id="33039-102">Rozdíly mezi upravitelnými a neupravitelnými argumenty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33039-102">Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)</span></span>
<span data-ttu-id="33039-103">Při volání procedury obvykle předáte jeden nebo více argumentů.</span><span class="sxs-lookup"><span data-stu-id="33039-103">When you call a procedure, you typically pass one or more arguments to it.</span></span> <span data-ttu-id="33039-104">Každý argument odpovídá základnímu programovacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="33039-104">Each argument corresponds to an underlying programming element.</span></span> <span data-ttu-id="33039-105">Základní prvky i samotné argumenty mohou být buď upravitelné, nebo neupravitelné.</span><span class="sxs-lookup"><span data-stu-id="33039-105">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span></span>  
  
## <a name="modifiable-and-nonmodifiable-elements"></a><span data-ttu-id="33039-106">Upravitelné a neupravitelné elementy</span><span class="sxs-lookup"><span data-stu-id="33039-106">Modifiable and Nonmodifiable Elements</span></span>  
 <span data-ttu-id="33039-107">Programovací element může být buď *upravitelný prvek*, který může mít změněnou hodnotu, nebo *neupravitelný prvek*, který má pevnou hodnotu po vytvoření.</span><span class="sxs-lookup"><span data-stu-id="33039-107">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span></span>  
  
 <span data-ttu-id="33039-108">V následující tabulce je uveden seznam upravitelných a neupravitelných programovacích prvků.</span><span class="sxs-lookup"><span data-stu-id="33039-108">The following table lists modifiable and nonmodifiable programming elements.</span></span>  
  
|<span data-ttu-id="33039-109">Upravitelné elementy</span><span class="sxs-lookup"><span data-stu-id="33039-109">Modifiable elements</span></span>|<span data-ttu-id="33039-110">Neupravitelné elementy</span><span class="sxs-lookup"><span data-stu-id="33039-110">Nonmodifiable elements</span></span>|  
|-------------------------|----------------------------|  
|<span data-ttu-id="33039-111">Lokální proměnné (deklarované uvnitř procedur), včetně proměnných objektů, s výjimkou pouze pro čtení</span><span class="sxs-lookup"><span data-stu-id="33039-111">Local variables (declared inside procedures), including object variables, except for read-only</span></span>|<span data-ttu-id="33039-112">Proměnné, pole a vlastnosti jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="33039-112">Read-only variables, fields, and properties</span></span>|  
|<span data-ttu-id="33039-113">Pole (členské proměnné modulů, tříd a struktur), s výjimkou jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="33039-113">Fields (member variables of modules, classes, and structures), except for read-only</span></span>|<span data-ttu-id="33039-114">Konstanty a literály</span><span class="sxs-lookup"><span data-stu-id="33039-114">Constants and literals</span></span>|  
|<span data-ttu-id="33039-115">Vlastnosti, s výjimkou pouze pro čtení</span><span class="sxs-lookup"><span data-stu-id="33039-115">Properties, except for read-only</span></span>|<span data-ttu-id="33039-116">Členové výčtu</span><span class="sxs-lookup"><span data-stu-id="33039-116">Enumeration members</span></span>|  
|<span data-ttu-id="33039-117">Prvky pole</span><span class="sxs-lookup"><span data-stu-id="33039-117">Array elements</span></span>|<span data-ttu-id="33039-118">Výrazy (i když jejich prvky lze upravovat)</span><span class="sxs-lookup"><span data-stu-id="33039-118">Expressions (even if their elements are modifiable)</span></span>|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a><span data-ttu-id="33039-119">Upravitelné a neupravitelné argumenty</span><span class="sxs-lookup"><span data-stu-id="33039-119">Modifiable and Nonmodifiable Arguments</span></span>  
 <span data-ttu-id="33039-120">*Upravitelný argument* je jeden s upravitelným podkladovým elementem.</span><span class="sxs-lookup"><span data-stu-id="33039-120">A *modifiable argument* is one with a modifiable underlying element.</span></span> <span data-ttu-id="33039-121">Volající kód může uložit novou hodnotu kdykoli, a Pokud předáte argument [ByRef](../../../language-reference/modifiers/byref.md), kód v proceduře může také upravit podkladový prvek v kódu volajícího.</span><span class="sxs-lookup"><span data-stu-id="33039-121">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="33039-122">*Neupravitelný argument* má buď neupravitelný základní prvek, nebo je předán jako [ByVal](../../../language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="33039-122">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="33039-123">Procedura nemůže změnit podkladový prvek v kódu volání, i když se jedná o upravitelný prvek.</span><span class="sxs-lookup"><span data-stu-id="33039-123">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span></span> <span data-ttu-id="33039-124">Pokud se jedná o neupravitelný prvek, samotný volající kód ho nemůže změnit.</span><span class="sxs-lookup"><span data-stu-id="33039-124">If it is a nonmodifiable element, the calling code itself cannot modify it.</span></span>  
  
 <span data-ttu-id="33039-125">Volaná procedura může změnit svou místní kopii neupravitelného argumentu, ale tato změna nemá vliv na základní prvek v kódu volajícího.</span><span class="sxs-lookup"><span data-stu-id="33039-125">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33039-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="33039-126">See also</span></span>

- [<span data-ttu-id="33039-127">Procedury</span><span class="sxs-lookup"><span data-stu-id="33039-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="33039-128">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="33039-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="33039-129">Postupy: Předání argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="33039-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="33039-130">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="33039-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="33039-131">Rozdíly mezi předáním argumentu podle hodnoty a podle reference</span><span class="sxs-lookup"><span data-stu-id="33039-131">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="33039-132">Postupy: Změna hodnoty argumentu procedury</span><span class="sxs-lookup"><span data-stu-id="33039-132">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="33039-133">Postupy: Ochrana argumentu procedury před změnami hodnoty</span><span class="sxs-lookup"><span data-stu-id="33039-133">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="33039-134">Postupy: Vynucení předání argumentu podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="33039-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="33039-135">Předávání argumentů podle pozice a názvu</span><span class="sxs-lookup"><span data-stu-id="33039-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="33039-136">Typy hodnot a typy odkazu</span><span class="sxs-lookup"><span data-stu-id="33039-136">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
