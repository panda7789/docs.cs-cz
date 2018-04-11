---
title: Auto (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1e32c4c910567829a4f5c59b48020db4dfbbeb7b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="auto-visual-basic"></a><span data-ttu-id="078b6-102">Auto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="078b6-102">Auto (Visual Basic)</span></span>
<span data-ttu-id="078b6-103">Určuje, že jazyka Visual Basic by měl zařazování řetězců podle rozhraní .NET Framework pravidla založená na externí název externí procedura se deklarovat.</span><span class="sxs-lookup"><span data-stu-id="078b6-103">Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="078b6-104">Při volání procedury definované mimo projekt Visual Basic – kompilátor nemá přístup k informacím musí mít voláním procedury správně.</span><span class="sxs-lookup"><span data-stu-id="078b6-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly.</span></span> <span data-ttu-id="078b6-105">Tyto informace zahrnují, kde se nachází postup, jak je identifikovat, jeho volací sekvence a návratový typ a řetězec znaková sada, se používá.</span><span class="sxs-lookup"><span data-stu-id="078b6-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="078b6-106">[Deklarovat příkaz](../../../visual-basic/language-reference/statements/declare-statement.md) vytvoří odkaz na externí procedura a poskytuje tyto nezbytné informace.</span><span class="sxs-lookup"><span data-stu-id="078b6-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="078b6-107">`charsetmodifier` Část v `Declare` příkaz poskytuje informace o znakových sadách pro zařazování řetězců během volání externí procedura.</span><span class="sxs-lookup"><span data-stu-id="078b6-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="078b6-108">Ovlivní také jak jazyka Visual Basic prohledává externí soubor pro externí procedura název.</span><span class="sxs-lookup"><span data-stu-id="078b6-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="078b6-109">`Auto` Modifikátor Určuje, že by měl jazyka Visual Basic zařazování řetězců podle pravidel rozhraní .NET Framework a se musí určit základní znakovou sadu platformy spuštění a případně upravit název externí procedura pokud počáteční vyhledávání se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="078b6-109">The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails.</span></span> <span data-ttu-id="078b6-110">Další informace najdete v tématu "Sady znaků" v [deklarovat příkaz](../../../visual-basic/language-reference/statements/declare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="078b6-110">For more information, see "Character Sets" in [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md).</span></span>  
  
 <span data-ttu-id="078b6-111">Pokud není zadaný žádný modifikátor sady znaků, `Ansi` je výchozí.</span><span class="sxs-lookup"><span data-stu-id="078b6-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="078b6-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="078b6-112">Remarks</span></span>  
 <span data-ttu-id="078b6-113">`Auto` Modifikátor můžete v tomto kontextu použít:</span><span class="sxs-lookup"><span data-stu-id="078b6-113">The `Auto` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="078b6-114">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="078b6-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="078b6-115">Poznámky pro vývojáře inteligentního zařízení</span><span class="sxs-lookup"><span data-stu-id="078b6-115">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="078b6-116">This – klíčové slovo není podporováno.</span><span class="sxs-lookup"><span data-stu-id="078b6-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="078b6-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="078b6-117">See Also</span></span>  
 [<span data-ttu-id="078b6-118">ANSI</span><span class="sxs-lookup"><span data-stu-id="078b6-118">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [<span data-ttu-id="078b6-119">Kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="078b6-119">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [<span data-ttu-id="078b6-120">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="078b6-120">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
