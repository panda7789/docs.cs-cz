---
title: Modifikátor 'Custom' není platný pro události deklarované bez explicitních typů delegátů.
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 0c5a4188fedf9685afdd1cde4c1de93a0b43b919
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409777"
---
# <a name="custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="b1088-102">Modifikátor 'Custom' není platný pro události deklarované bez explicitních typů delegátů.</span><span class="sxs-lookup"><span data-stu-id="b1088-102">'Custom' modifier is not valid on events declared without explicit delegate types</span></span>
<span data-ttu-id="b1088-103">Na rozdíl od nevlastní události `Custom Event` deklarace vyžaduje `As` klauzuli za názvem události, která explicitně určuje typ delegáta pro událost.</span><span class="sxs-lookup"><span data-stu-id="b1088-103">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>  
  
 <span data-ttu-id="b1088-104">Nevlastní události lze definovat buď pomocí `As` klauzule, explicitního typu delegáta, nebo se seznamem parametrů hned za názvem události.</span><span class="sxs-lookup"><span data-stu-id="b1088-104">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>  
  
 <span data-ttu-id="b1088-105">**ID chyby:** BC31122</span><span class="sxs-lookup"><span data-stu-id="b1088-105">**Error ID:** BC31122</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b1088-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b1088-106">To correct this error</span></span>  
  
1. <span data-ttu-id="b1088-107">Definujte delegáta se stejným seznamem parametrů jako vlastní událost.</span><span class="sxs-lookup"><span data-stu-id="b1088-107">Define a delegate with the same parameter list as the custom event.</span></span>  
  
     <span data-ttu-id="b1088-108">Například, pokud `Custom Event` byla definována uživatelem `Custom Event Test(ByVal sender As Object, ByVal i As Integer)` , pak odpovídající delegát bude následující.</span><span class="sxs-lookup"><span data-stu-id="b1088-108">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>  
  
     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]  
  
2. <span data-ttu-id="b1088-109">Nahraďte seznam parametrů vlastní události `As` klauzulí určující typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="b1088-109">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>  
  
     <span data-ttu-id="b1088-110">Pokračování v příkladu `Custom Event` deklarace by se přepsala takto.</span><span class="sxs-lookup"><span data-stu-id="b1088-110">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>  
  
     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]  
  
## <a name="example"></a><span data-ttu-id="b1088-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="b1088-111">Example</span></span>  
 <span data-ttu-id="b1088-112">Tento příklad deklaruje `Custom Event` a Určuje požadovanou `As` klauzuli s typem delegáta.</span><span class="sxs-lookup"><span data-stu-id="b1088-112">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>  
  
 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="b1088-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1088-113">See also</span></span>

- [<span data-ttu-id="b1088-114">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="b1088-114">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="b1088-115">Delegate – příkaz</span><span class="sxs-lookup"><span data-stu-id="b1088-115">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="b1088-116">Události</span><span class="sxs-lookup"><span data-stu-id="b1088-116">Events</span></span>](../../programming-guide/language-features/events/index.md)
