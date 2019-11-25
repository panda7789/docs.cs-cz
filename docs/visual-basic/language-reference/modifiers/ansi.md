---
title: Ansi
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: 0c38c2b81af7b4cb8fd1723853a09c5413f805af
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344743"
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="f3f4e-102">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3f4e-102">Ansi (Visual Basic)</span></span>
<span data-ttu-id="f3f4e-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span><span class="sxs-lookup"><span data-stu-id="f3f4e-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="f3f4e-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span><span class="sxs-lookup"><span data-stu-id="f3f4e-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="f3f4e-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span><span class="sxs-lookup"><span data-stu-id="f3f4e-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="f3f4e-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span><span class="sxs-lookup"><span data-stu-id="f3f4e-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="f3f4e-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span><span class="sxs-lookup"><span data-stu-id="f3f4e-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="f3f4e-108">It also affects how Visual Basic searches the external file for the external procedure name.</span><span class="sxs-lookup"><span data-stu-id="f3f4e-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="f3f4e-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span><span class="sxs-lookup"><span data-stu-id="f3f4e-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="f3f4e-110">If no character set modifier is specified, `Ansi` is the default.</span><span class="sxs-lookup"><span data-stu-id="f3f4e-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3f4e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3f4e-111">Remarks</span></span>  
 <span data-ttu-id="f3f4e-112">The `Ansi` modifier can be used in this context:</span><span class="sxs-lookup"><span data-stu-id="f3f4e-112">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="f3f4e-113">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="f3f4e-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="f3f4e-114">Poznámky pro vývojáře inteligentního zařízení</span><span class="sxs-lookup"><span data-stu-id="f3f4e-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="f3f4e-115">This keyword is not supported.</span><span class="sxs-lookup"><span data-stu-id="f3f4e-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3f4e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3f4e-116">See also</span></span>

- [<span data-ttu-id="f3f4e-117">Auto</span><span class="sxs-lookup"><span data-stu-id="f3f4e-117">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)
- [<span data-ttu-id="f3f4e-118">Unicode</span><span class="sxs-lookup"><span data-stu-id="f3f4e-118">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)
- [<span data-ttu-id="f3f4e-119">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="f3f4e-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
