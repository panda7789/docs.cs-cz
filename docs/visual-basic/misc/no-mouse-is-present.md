---
title: Není připojena myš
ms.date: 07/20/2015
f1_keywords:
- vbrMouse_NoMouseIsPresent
ms.assetid: 4472fd57-4217-4463-9d3c-dc4a8fe88f1b
ms.openlocfilehash: c0e4e2a8cb0aa641b179d8b2608af384d7d4181e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61944934"
---
# <a name="no-mouse-is-present"></a><span data-ttu-id="9900e-102">Není připojena myš</span><span class="sxs-lookup"><span data-stu-id="9900e-102">No mouse is present</span></span>
<span data-ttu-id="9900e-103">Jedna z vlastností objektu `My.Computer.Mouse` byla volána objektu, ale počítač nemá žádné myši a portem myši nainstalované.</span><span class="sxs-lookup"><span data-stu-id="9900e-103">One of the properties of the `My.Computer.Mouse` object was called, but the computer has no mouse or mouse port installed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9900e-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="9900e-104">To correct this error</span></span>  
  
- <span data-ttu-id="9900e-105">Přidat `Try...Catch` blok po volání na vlastnost `My.Computer.Mouse` objektu.</span><span class="sxs-lookup"><span data-stu-id="9900e-105">Add a `Try...Catch` block around the call to the property of the `My.Computer.Mouse` object.</span></span>  
  
     <span data-ttu-id="9900e-106">– nebo –</span><span class="sxs-lookup"><span data-stu-id="9900e-106">— or —</span></span>  
  
- <span data-ttu-id="9900e-107">Nainstalujte do počítače myši.</span><span class="sxs-lookup"><span data-stu-id="9900e-107">Install a mouse on the computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9900e-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9900e-108">See also</span></span>

- [<span data-ttu-id="9900e-109">My.Computer.Mouse</span><span class="sxs-lookup"><span data-stu-id="9900e-109">My.Computer.Mouse</span></span>](xref:Microsoft.VisualBasic.Devices.Mouse)
- [<span data-ttu-id="9900e-110">Zpracování a vyvolání výjimek v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="9900e-110">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="9900e-111">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="9900e-111">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
