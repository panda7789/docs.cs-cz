---
title: Kódování Unicode
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: 9b1bc40bb52244deefc0486d3a40c4b961ad1ee5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402678"
---
# <a name="unicode-visual-basic"></a><span data-ttu-id="63f38-102">Unicode (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63f38-102">Unicode (Visual Basic)</span></span>
<span data-ttu-id="63f38-103">Určuje, že Visual Basic by měly zařazovat všechny řetězce do hodnot Unicode bez ohledu na název externí procedury, která je deklarována.</span><span class="sxs-lookup"><span data-stu-id="63f38-103">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="63f38-104">Při volání procedury definované mimo projekt, kompilátor Visual Basic nemá přístup k informacím, které musí mít, aby mohl správně zavolat proceduru.</span><span class="sxs-lookup"><span data-stu-id="63f38-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span></span> <span data-ttu-id="63f38-105">Tyto informace zahrnují, kde se nachází postup, jak se identifikuje, jeho volající sekvence a návratový typ a znaková sada, kterou používá.</span><span class="sxs-lookup"><span data-stu-id="63f38-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="63f38-106">[Příkaz Declare](../statements/declare-statement.md) vytvoří odkaz na externí proceduru a poskytne tyto nezbytné informace.</span><span class="sxs-lookup"><span data-stu-id="63f38-106">The [Declare Statement](../statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="63f38-107">`charsetmodifier`Část v `Declare` příkazu poskytuje znakovou sadu informace pro zařazování řetězců během volání externí procedury.</span><span class="sxs-lookup"><span data-stu-id="63f38-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span></span> <span data-ttu-id="63f38-108">Ovlivňuje také způsob, jakým Visual Basic hledá Externí soubor pro název externí procedury.</span><span class="sxs-lookup"><span data-stu-id="63f38-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="63f38-109">`Unicode`Modifikátor určuje, že Visual Basic by měl zařazovat všechny řetězce do hodnot Unicode a by měl vyhledat proceduru bez úpravy jejího názvu během hledání.</span><span class="sxs-lookup"><span data-stu-id="63f38-109">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="63f38-110">Pokud není zadán modifikátor znakové sady, `Ansi` je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="63f38-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63f38-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="63f38-111">Remarks</span></span>  
 <span data-ttu-id="63f38-112">`Unicode`V tomto kontextu lze použít modifikátor:</span><span class="sxs-lookup"><span data-stu-id="63f38-112">The `Unicode` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="63f38-113">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="63f38-113">Declare Statement</span></span>](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="63f38-114">Poznámky pro vývojáře inteligentního zařízení</span><span class="sxs-lookup"><span data-stu-id="63f38-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="63f38-115">Toto klíčové slovo není podporováno.</span><span class="sxs-lookup"><span data-stu-id="63f38-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63f38-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="63f38-116">See also</span></span>

- [<span data-ttu-id="63f38-117">Ansi</span><span class="sxs-lookup"><span data-stu-id="63f38-117">Ansi</span></span>](ansi.md)
- [<span data-ttu-id="63f38-118">Automaticky</span><span class="sxs-lookup"><span data-stu-id="63f38-118">Auto</span></span>](auto.md)
- [<span data-ttu-id="63f38-119">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="63f38-119">Keywords</span></span>](../keywords/index.md)
