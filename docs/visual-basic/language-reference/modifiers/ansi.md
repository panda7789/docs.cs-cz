---
title: Ansi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: 98dafab3e524ea371bba228eb231e28d46cc3b4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802554"
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="24877-102">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24877-102">Ansi (Visual Basic)</span></span>
<span data-ttu-id="24877-103">Určuje, že by měl Visual Basic zařazovat všechny řetězce na hodnoty American National Standards Institute (ANSI) bez ohledu na název externí procedury byl deklarován.</span><span class="sxs-lookup"><span data-stu-id="24877-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="24877-104">Při volání procedury definován vně vašeho projektu, kompilátor jazyka Visual Basic nemá přístup k informacím, které potřebuje k voláním procedury správně.</span><span class="sxs-lookup"><span data-stu-id="24877-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="24877-105">Tyto informace zahrnují, kde se nachází postup, jak je identifikovaný, jeho volací sekvence a návratový typ a řetězec znakové sady, ji používá.</span><span class="sxs-lookup"><span data-stu-id="24877-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="24877-106">[Deklaraci příkazu](../../../visual-basic/language-reference/statements/declare-statement.md) vytvoří odkaz na externí procedura a poskytuje tyto nezbytné informace.</span><span class="sxs-lookup"><span data-stu-id="24877-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="24877-107">`charsetmodifier` Část v `Declare` příkaz poskytuje informace o znakových sadách pro zařazování řetězce při volání do externí procedury.</span><span class="sxs-lookup"><span data-stu-id="24877-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="24877-108">Také ovlivní, jak Visual Basic vyhledá externí soubor pro název externí procedury.</span><span class="sxs-lookup"><span data-stu-id="24877-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="24877-109">`Ansi` Modifikátor Určuje, že jazyka Visual Basic by měla zařazovat všechny řetězce na hodnoty ANSI a by měl vyhledávat proceduru bez úpravy jejího názvu během vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="24877-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="24877-110">Pokud není zadána žádná modifikátor sady znaků, `Ansi` je výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="24877-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24877-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="24877-111">Remarks</span></span>  
 <span data-ttu-id="24877-112">`Ansi` Modifikátor lze použít v tomto kontextu:</span><span class="sxs-lookup"><span data-stu-id="24877-112">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="24877-113">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="24877-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="24877-114">Poznámky pro vývojáře inteligentního zařízení</span><span class="sxs-lookup"><span data-stu-id="24877-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="24877-115">Toto klíčové slovo se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="24877-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24877-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="24877-116">See also</span></span>

- [<span data-ttu-id="24877-117">Auto</span><span class="sxs-lookup"><span data-stu-id="24877-117">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)
- [<span data-ttu-id="24877-118">Unicode</span><span class="sxs-lookup"><span data-stu-id="24877-118">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)
- [<span data-ttu-id="24877-119">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="24877-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
