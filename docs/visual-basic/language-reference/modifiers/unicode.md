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
# <a name="unicode-visual-basic"></a><span data-ttu-id="2399b-102">Unicode (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2399b-102">Unicode (Visual Basic)</span></span>
<span data-ttu-id="2399b-103">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span><span class="sxs-lookup"><span data-stu-id="2399b-103">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="2399b-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span><span class="sxs-lookup"><span data-stu-id="2399b-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span></span> <span data-ttu-id="2399b-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span><span class="sxs-lookup"><span data-stu-id="2399b-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="2399b-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span><span class="sxs-lookup"><span data-stu-id="2399b-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="2399b-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span><span class="sxs-lookup"><span data-stu-id="2399b-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span></span> <span data-ttu-id="2399b-108">It also affects how Visual Basic searches the external file for the external procedure name.</span><span class="sxs-lookup"><span data-stu-id="2399b-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="2399b-109">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span><span class="sxs-lookup"><span data-stu-id="2399b-109">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="2399b-110">If no character set modifier is specified, `Ansi` is the default.</span><span class="sxs-lookup"><span data-stu-id="2399b-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2399b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2399b-111">Remarks</span></span>  
 <span data-ttu-id="2399b-112">The `Unicode` modifier can be used in this context:</span><span class="sxs-lookup"><span data-stu-id="2399b-112">The `Unicode` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="2399b-113">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="2399b-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="2399b-114">Poznámky pro vývojáře inteligentního zařízení</span><span class="sxs-lookup"><span data-stu-id="2399b-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="2399b-115">This keyword is not supported.</span><span class="sxs-lookup"><span data-stu-id="2399b-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2399b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2399b-116">See also</span></span>

- [<span data-ttu-id="2399b-117">ANSI</span><span class="sxs-lookup"><span data-stu-id="2399b-117">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)
- [<span data-ttu-id="2399b-118">Auto</span><span class="sxs-lookup"><span data-stu-id="2399b-118">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)
- [<span data-ttu-id="2399b-119">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="2399b-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
