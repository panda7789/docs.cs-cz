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
ms.openlocfilehash: c4286ed9e9d5fd768ae29b7050b3d1505ccca9dd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344225"
---
# <a name="unicode-visual-basic"></a><span data-ttu-id="6c9d9-102">Unicode (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6c9d9-102">Unicode (Visual Basic)</span></span>
<span data-ttu-id="6c9d9-103">Určuje, že Visual Basic by měly zařazovat všechny řetězce do hodnot Unicode bez ohledu na název externí procedury, která je deklarována.</span><span class="sxs-lookup"><span data-stu-id="6c9d9-103">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="6c9d9-104">Při volání procedury definované mimo projekt, kompilátor Visual Basic nemá přístup k informacím, které musí mít, aby mohl správně zavolat proceduru.</span><span class="sxs-lookup"><span data-stu-id="6c9d9-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span></span> <span data-ttu-id="6c9d9-105">Tyto informace zahrnují, kde se nachází postup, jak se identifikuje, jeho volající sekvence a návratový typ a znaková sada, kterou používá.</span><span class="sxs-lookup"><span data-stu-id="6c9d9-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="6c9d9-106">[Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md) vytvoří odkaz na externí proceduru a poskytne tyto nezbytné informace.</span><span class="sxs-lookup"><span data-stu-id="6c9d9-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="6c9d9-107">Část `charsetmodifier` v příkazu `Declare` poskytuje znakovou sadu informace pro zařazování řetězců během volání do externí procedury.</span><span class="sxs-lookup"><span data-stu-id="6c9d9-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span></span> <span data-ttu-id="6c9d9-108">Ovlivňuje také způsob, jakým Visual Basic hledá Externí soubor pro název externí procedury.</span><span class="sxs-lookup"><span data-stu-id="6c9d9-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="6c9d9-109">Modifikátor `Unicode` určuje, že Visual Basic by měly zařazovat všechny řetězce do hodnot Unicode a měly by Hledat postup beze změny jeho názvu během hledání.</span><span class="sxs-lookup"><span data-stu-id="6c9d9-109">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="6c9d9-110">Pokud není zadán žádný modifikátor znakové sady, je `Ansi` výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="6c9d9-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c9d9-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c9d9-111">Remarks</span></span>  
 <span data-ttu-id="6c9d9-112">V tomto kontextu lze použít modifikátor `Unicode`:</span><span class="sxs-lookup"><span data-stu-id="6c9d9-112">The `Unicode` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="6c9d9-113">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="6c9d9-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="6c9d9-114">Poznámky pro vývojáře inteligentního zařízení</span><span class="sxs-lookup"><span data-stu-id="6c9d9-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="6c9d9-115">Toto klíčové slovo není podporováno.</span><span class="sxs-lookup"><span data-stu-id="6c9d9-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c9d9-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c9d9-116">See also</span></span>

- [<span data-ttu-id="6c9d9-117">ANSI</span><span class="sxs-lookup"><span data-stu-id="6c9d9-117">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)
- [<span data-ttu-id="6c9d9-118">Auto</span><span class="sxs-lookup"><span data-stu-id="6c9d9-118">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)
- [<span data-ttu-id="6c9d9-119">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="6c9d9-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
