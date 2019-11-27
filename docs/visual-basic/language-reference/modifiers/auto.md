---
title: Autom.
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: 7ea46e5f8b882bb986f23e792b240bad0c5be7a5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351620"
---
# <a name="auto-visual-basic"></a><span data-ttu-id="9909d-102">Auto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9909d-102">Auto (Visual Basic)</span></span>
<span data-ttu-id="9909d-103">Určuje, že by Visual Basic měla zařazovat řetězce podle .NET Framework pravidla na základě vnějšího názvu deklarované externí procedury.</span><span class="sxs-lookup"><span data-stu-id="9909d-103">Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="9909d-104">Při volání procedury definované mimo projekt, kompilátor Visual Basic nemá přístup k informacím, které musí splňovat správné volání procedury.</span><span class="sxs-lookup"><span data-stu-id="9909d-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly.</span></span> <span data-ttu-id="9909d-105">Tyto informace zahrnují, kde se nachází postup, jak se identifikuje, jeho volající sekvence a návratový typ a znaková sada, kterou používá.</span><span class="sxs-lookup"><span data-stu-id="9909d-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="9909d-106">[Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md) vytvoří odkaz na externí proceduru a poskytne tyto nezbytné informace.</span><span class="sxs-lookup"><span data-stu-id="9909d-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="9909d-107">Část `charsetmodifier` v příkazu `Declare` poskytuje znakovou sadu informace pro zařazování řetězců během volání do externí procedury.</span><span class="sxs-lookup"><span data-stu-id="9909d-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="9909d-108">Ovlivňuje také způsob, jakým Visual Basic hledá Externí soubor pro název externí procedury.</span><span class="sxs-lookup"><span data-stu-id="9909d-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="9909d-109">Modifikátor `Auto` určuje, že Visual Basic by měl zařazovat řetězce podle pravidel .NET Framework a že by měl určit základní znakovou sadu běhové platformy a případně upravit název externí procedury, pokud se nepovede počáteční vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="9909d-109">The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails.</span></span> <span data-ttu-id="9909d-110">Další informace naleznete v tématu "znakové sady" v [příkazu Declare](../../../visual-basic/language-reference/statements/declare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9909d-110">For more information, see "Character Sets" in [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md).</span></span>  
  
 <span data-ttu-id="9909d-111">Pokud není zadán žádný modifikátor znakové sady, je `Ansi` výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="9909d-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9909d-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9909d-112">Remarks</span></span>  
 <span data-ttu-id="9909d-113">V tomto kontextu lze použít modifikátor `Auto`:</span><span class="sxs-lookup"><span data-stu-id="9909d-113">The `Auto` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="9909d-114">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="9909d-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="9909d-115">Poznámky pro vývojáře inteligentního zařízení</span><span class="sxs-lookup"><span data-stu-id="9909d-115">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="9909d-116">Toto klíčové slovo není podporováno.</span><span class="sxs-lookup"><span data-stu-id="9909d-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9909d-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9909d-117">See also</span></span>

- [<span data-ttu-id="9909d-118">ANSI</span><span class="sxs-lookup"><span data-stu-id="9909d-118">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)
- [<span data-ttu-id="9909d-119">Unicode</span><span class="sxs-lookup"><span data-stu-id="9909d-119">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)
- [<span data-ttu-id="9909d-120">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="9909d-120">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
