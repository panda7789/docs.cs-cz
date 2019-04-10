---
title: Modifikátor 'Custom' není platný pro události deklarované bez explicitních typů delegátů.
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 169cb49cc5abc76b7c52785392d0083b81a99450
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300941"
---
# <a name="custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="3223c-102">Modifikátor 'Custom' není platný pro události deklarované bez explicitních typů delegátů.</span><span class="sxs-lookup"><span data-stu-id="3223c-102">'Custom' modifier is not valid on events declared without explicit delegate types</span></span>
<span data-ttu-id="3223c-103">Na rozdíl od jiných vlastních událostí `Custom Event` deklarace vyžaduje `As` klauzule podle název události, které explicitně určuje typ delegáta pro událost.</span><span class="sxs-lookup"><span data-stu-id="3223c-103">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>  
  
 <span data-ttu-id="3223c-104">Non vlastní události může být definována buď pomocí `As` klauzule a explicitní typ delegáta nebo s parametrem seznamu bezprostředně za název události.</span><span class="sxs-lookup"><span data-stu-id="3223c-104">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>  
  
 <span data-ttu-id="3223c-105">**ID chyby:** BC31122</span><span class="sxs-lookup"><span data-stu-id="3223c-105">**Error ID:** BC31122</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3223c-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="3223c-106">To correct this error</span></span>  
  
1. <span data-ttu-id="3223c-107">Definujte delegáta se stejným seznamem parametrů jako vlastní událost.</span><span class="sxs-lookup"><span data-stu-id="3223c-107">Define a delegate with the same parameter list as the custom event.</span></span>  
  
     <span data-ttu-id="3223c-108">Například pokud `Custom Event` byl definovaný souborem `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, pak odpovídající delegáta by byl následující.</span><span class="sxs-lookup"><span data-stu-id="3223c-108">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>  
  
     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]  
  
2. <span data-ttu-id="3223c-109">Nahraďte parametr seznam vlastních událostí pomocí `As` klauzule určující typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="3223c-109">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>  
  
     <span data-ttu-id="3223c-110">Pokračujte v tomto příkladu `Custom Event` deklarace by být přepsán následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="3223c-110">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>  
  
     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]  
  
## <a name="example"></a><span data-ttu-id="3223c-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="3223c-111">Example</span></span>  
 <span data-ttu-id="3223c-112">V tomto příkladu deklaruje `Custom Event` a určuje požadované `As` klauzule s typem delegáta.</span><span class="sxs-lookup"><span data-stu-id="3223c-112">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>  
  
 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="3223c-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3223c-113">See also</span></span>

- [<span data-ttu-id="3223c-114">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="3223c-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="3223c-115">Delegate – příkaz</span><span class="sxs-lookup"><span data-stu-id="3223c-115">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="3223c-116">Události</span><span class="sxs-lookup"><span data-stu-id="3223c-116">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
