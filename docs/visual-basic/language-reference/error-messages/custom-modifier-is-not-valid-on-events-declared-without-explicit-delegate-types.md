---
title: '&#39;Vlastní&#39; modifikátor není platný pro události deklarované bez explicitních typů delegátů.'
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 3f08bbbbbac4a01dfbac8d15cf9285c01262618a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587516"
---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="809f1-102">&#39;Vlastní&#39; modifikátor není platný pro události deklarované bez explicitních typů delegátů.</span><span class="sxs-lookup"><span data-stu-id="809f1-102">&#39;Custom&#39; modifier is not valid on events declared without explicit delegate types</span></span>
<span data-ttu-id="809f1-103">Na rozdíl od jiných vlastní události `Custom Event` deklarace vyžaduje `As` klauzule následující název události, které explicitně určuje typ delegát pro událost.</span><span class="sxs-lookup"><span data-stu-id="809f1-103">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>  
  
 <span data-ttu-id="809f1-104">Bez vlastní události může být definována buď pomocí `As` klauzule a explicitního delegovat typ, nebo pomocí parametru seznamu okamžitě následující název události.</span><span class="sxs-lookup"><span data-stu-id="809f1-104">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>  
  
 <span data-ttu-id="809f1-105">**ID chyby:** BC31122</span><span class="sxs-lookup"><span data-stu-id="809f1-105">**Error ID:** BC31122</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="809f1-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="809f1-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="809f1-107">Definujte delegáta s stejný seznam parametrů jako vlastní události.</span><span class="sxs-lookup"><span data-stu-id="809f1-107">Define a delegate with the same parameter list as the custom event.</span></span>  
  
     <span data-ttu-id="809f1-108">Například pokud `Custom Event` byl definován pomocí `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, pak odpovídající delegát by byl následující.</span><span class="sxs-lookup"><span data-stu-id="809f1-108">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>  
  
     [!code-vb[VbVbalrEventError#18](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]  
  
2.  <span data-ttu-id="809f1-109">Nahradit seznam parametrů vlastní události s `As` klauzule určení typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="809f1-109">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>  
  
     <span data-ttu-id="809f1-110">Pokračování příkladu, s `Custom Event` deklarace by takto přepsána.</span><span class="sxs-lookup"><span data-stu-id="809f1-110">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>  
  
     [!code-vb[VbVbalrEventError#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="809f1-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="809f1-111">Example</span></span>  
 <span data-ttu-id="809f1-112">Tento příklad deklaruje `Custom Event` a určuje požadované `As` klauzule s typem delegáta.</span><span class="sxs-lookup"><span data-stu-id="809f1-112">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>  
  
 [!code-vb[VbVbalrEventError#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="809f1-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="809f1-113">See Also</span></span>  
 [<span data-ttu-id="809f1-114">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="809f1-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="809f1-115">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="809f1-115">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="809f1-116">Události</span><span class="sxs-lookup"><span data-stu-id="809f1-116">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
