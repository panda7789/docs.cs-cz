---
title: Unicode (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: b3c9452f8d144fb18ea3efcb35b85caed80e8692
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819343"
---
# <a name="unicode-visual-basic"></a><span data-ttu-id="92b71-102">Unicode (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92b71-102">Unicode (Visual Basic)</span></span>
<span data-ttu-id="92b71-103">Určuje, že by měl Visual Basic zařazovat všechny řetězce k hodnotám Unicode bez ohledu na název externí procedury byl deklarován.</span><span class="sxs-lookup"><span data-stu-id="92b71-103">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="92b71-104">Při volání procedury definován vně vašeho projektu, kompilátor jazyka Visual Basic nemá přístup k informacím, musíte mít k voláním procedury správně.</span><span class="sxs-lookup"><span data-stu-id="92b71-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span></span> <span data-ttu-id="92b71-105">Tyto informace zahrnují, kde se nachází postup, jak je identifikovaný, jeho volací sekvence a návratový typ a řetězec znakové sady, ji používá.</span><span class="sxs-lookup"><span data-stu-id="92b71-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="92b71-106">[Deklaraci příkazu](../../../visual-basic/language-reference/statements/declare-statement.md) vytvoří odkaz na externí procedura a poskytuje tyto nezbytné informace.</span><span class="sxs-lookup"><span data-stu-id="92b71-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="92b71-107">`charsetmodifier` Část v `Declare` příkaz poskytuje informace o sadě znak k zařazování řetězců v kódu při volání do externí procedury.</span><span class="sxs-lookup"><span data-stu-id="92b71-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span></span> <span data-ttu-id="92b71-108">Také ovlivní, jak Visual Basic vyhledá externí soubor pro název externí procedury.</span><span class="sxs-lookup"><span data-stu-id="92b71-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="92b71-109">`Unicode` Modifikátor Určuje, že jazyka Visual Basic by měla zařazovat všechny řetězce k hodnotám Unicode a by měl vyhledávat proceduru bez úpravy jejího názvu během vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="92b71-109">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="92b71-110">Pokud není zadána žádná modifikátor sady znaků, `Ansi` je výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="92b71-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92b71-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="92b71-111">Remarks</span></span>  
 <span data-ttu-id="92b71-112">`Unicode` Modifikátor lze použít v tomto kontextu:</span><span class="sxs-lookup"><span data-stu-id="92b71-112">The `Unicode` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="92b71-113">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="92b71-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="92b71-114">Poznámky pro vývojáře inteligentního zařízení</span><span class="sxs-lookup"><span data-stu-id="92b71-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="92b71-115">Toto klíčové slovo se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="92b71-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92b71-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92b71-116">See also</span></span>

- [<span data-ttu-id="92b71-117">ANSI</span><span class="sxs-lookup"><span data-stu-id="92b71-117">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)
- [<span data-ttu-id="92b71-118">Auto</span><span class="sxs-lookup"><span data-stu-id="92b71-118">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)
- [<span data-ttu-id="92b71-119">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="92b71-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
