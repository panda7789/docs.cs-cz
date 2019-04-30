---
title: Auto (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: e4beb320b3aa0cadb790dd3ab92255496bc32f05
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802697"
---
# <a name="auto-visual-basic"></a><span data-ttu-id="4a212-102">Auto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a212-102">Auto (Visual Basic)</span></span>
<span data-ttu-id="4a212-103">Určuje, že by měl Visual Basic zařazovat řetězce podle pravidel rozhraní .NET Framework, které jsou založené na externí název externí procedury byl deklarován.</span><span class="sxs-lookup"><span data-stu-id="4a212-103">Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="4a212-104">Při volání procedury definován vně vašeho projektu, kompilátor jazyka Visual Basic nemá přístup k informacím musí mít k voláním procedury správně.</span><span class="sxs-lookup"><span data-stu-id="4a212-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly.</span></span> <span data-ttu-id="4a212-105">Tyto informace zahrnují, kde se nachází postup, jak je identifikovaný, jeho volací sekvence a návratový typ a řetězec znakové sady, ji používá.</span><span class="sxs-lookup"><span data-stu-id="4a212-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="4a212-106">[Deklaraci příkazu](../../../visual-basic/language-reference/statements/declare-statement.md) vytvoří odkaz na externí procedura a poskytuje tyto nezbytné informace.</span><span class="sxs-lookup"><span data-stu-id="4a212-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="4a212-107">`charsetmodifier` Část v `Declare` příkaz poskytuje informace o znakových sadách pro zařazování řetězce při volání do externí procedury.</span><span class="sxs-lookup"><span data-stu-id="4a212-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="4a212-108">Také ovlivní, jak Visual Basic vyhledá externí soubor pro název externí procedury.</span><span class="sxs-lookup"><span data-stu-id="4a212-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="4a212-109">`Auto` Modifikátor Určuje, že by měl Visual Basic zařazovat řetězce podle pravidel rozhraní .NET Framework a, že ho měli určit základní znakové sady běhovou platformu a případně upravit název externí procedury úvodním vyhledávání se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="4a212-109">The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails.</span></span> <span data-ttu-id="4a212-110">Další informace najdete v tématu "Znakových sadách" [deklaraci příkazu](../../../visual-basic/language-reference/statements/declare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4a212-110">For more information, see "Character Sets" in [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md).</span></span>  
  
 <span data-ttu-id="4a212-111">Pokud není zadána žádná modifikátor sady znaků, `Ansi` je výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="4a212-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a212-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4a212-112">Remarks</span></span>  
 <span data-ttu-id="4a212-113">`Auto` Modifikátor lze použít v tomto kontextu:</span><span class="sxs-lookup"><span data-stu-id="4a212-113">The `Auto` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="4a212-114">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="4a212-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="4a212-115">Poznámky pro vývojáře inteligentního zařízení</span><span class="sxs-lookup"><span data-stu-id="4a212-115">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="4a212-116">Toto klíčové slovo se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="4a212-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a212-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a212-117">See also</span></span>

- [<span data-ttu-id="4a212-118">ANSI</span><span class="sxs-lookup"><span data-stu-id="4a212-118">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)
- [<span data-ttu-id="4a212-119">Unicode</span><span class="sxs-lookup"><span data-stu-id="4a212-119">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)
- [<span data-ttu-id="4a212-120">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="4a212-120">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
