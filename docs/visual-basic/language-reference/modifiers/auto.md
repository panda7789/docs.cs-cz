---
title: Auto
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: b9bdeed55788252c71b8fb1c995c140cbfdf60eb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373125"
---
# <a name="auto-visual-basic"></a><span data-ttu-id="fc6f6-102">Auto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc6f6-102">Auto (Visual Basic)</span></span>
<span data-ttu-id="fc6f6-103">Určuje, že by Visual Basic měla zařazovat řetězce podle .NET Framework pravidla na základě vnějšího názvu deklarované externí procedury.</span><span class="sxs-lookup"><span data-stu-id="fc6f6-103">Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="fc6f6-104">Při volání procedury definované mimo projekt, kompilátor Visual Basic nemá přístup k informacím, které musí splňovat správné volání procedury.</span><span class="sxs-lookup"><span data-stu-id="fc6f6-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly.</span></span> <span data-ttu-id="fc6f6-105">Tyto informace zahrnují, kde se nachází postup, jak se identifikuje, jeho volající sekvence a návratový typ a znaková sada, kterou používá.</span><span class="sxs-lookup"><span data-stu-id="fc6f6-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="fc6f6-106">[Příkaz Declare](../statements/declare-statement.md) vytvoří odkaz na externí proceduru a poskytne tyto nezbytné informace.</span><span class="sxs-lookup"><span data-stu-id="fc6f6-106">The [Declare Statement](../statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="fc6f6-107">`charsetmodifier`Část v `Declare` příkazu poskytuje znakovou sadu informace pro zařazování řetězců během volání externí procedury.</span><span class="sxs-lookup"><span data-stu-id="fc6f6-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="fc6f6-108">Ovlivňuje také způsob, jakým Visual Basic hledá Externí soubor pro název externí procedury.</span><span class="sxs-lookup"><span data-stu-id="fc6f6-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="fc6f6-109">`Auto`Modifikátor určuje, že Visual Basic by měl zařazovat řetězce v souladu s pravidly .NET Framework a že by měl určit základní znakovou sadu běhové platformy a případně upravit název externí procedury, pokud se nepovede počáteční vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="fc6f6-109">The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails.</span></span> <span data-ttu-id="fc6f6-110">Další informace naleznete v tématu "znakové sady" v [příkazu Declare](../statements/declare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fc6f6-110">For more information, see "Character Sets" in [Declare Statement](../statements/declare-statement.md).</span></span>  
  
 <span data-ttu-id="fc6f6-111">Pokud není zadán modifikátor znakové sady, `Ansi` je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="fc6f6-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc6f6-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fc6f6-112">Remarks</span></span>  
 <span data-ttu-id="fc6f6-113">`Auto`V tomto kontextu lze použít modifikátor:</span><span class="sxs-lookup"><span data-stu-id="fc6f6-113">The `Auto` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="fc6f6-114">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="fc6f6-114">Declare Statement</span></span>](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="fc6f6-115">Poznámky pro vývojáře inteligentního zařízení</span><span class="sxs-lookup"><span data-stu-id="fc6f6-115">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="fc6f6-116">Toto klíčové slovo není podporováno.</span><span class="sxs-lookup"><span data-stu-id="fc6f6-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc6f6-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc6f6-117">See also</span></span>

- [<span data-ttu-id="fc6f6-118">Ansi</span><span class="sxs-lookup"><span data-stu-id="fc6f6-118">Ansi</span></span>](ansi.md)
- [<span data-ttu-id="fc6f6-119">Kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="fc6f6-119">Unicode</span></span>](unicode.md)
- [<span data-ttu-id="fc6f6-120">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="fc6f6-120">Keywords</span></span>](../keywords/index.md)
