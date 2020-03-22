---
title: 'Postupy: Kontrola stavu připojení'
ms.date: 07/20/2015
helpviewer_keywords:
- Web connections [Visual Basic]
- IsAvailable property [Visual Basic], about IsAvailable
- connections [Visual Basic], checking status
- connection status [Visual Basic]
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
ms.openlocfilehash: 89ef431759dac25bd213fd954db0712ad95434b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345883"
---
# <a name="how-to-check-connection-status-in-visual-basic"></a><span data-ttu-id="cd768-102">Postupy: Kontrola stavu připojení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cd768-102">How to: Check Connection Status in Visual Basic</span></span>

<span data-ttu-id="cd768-103">Vlastnost <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> lze použít k určení, zda má počítač funkční síť nebo připojení k Internetu.</span><span class="sxs-lookup"><span data-stu-id="cd768-103">The <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> property can be used to determine whether the computer has a working network or Internet connection.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a><span data-ttu-id="cd768-104">Kontrola, zda má počítač funkční připojení</span><span class="sxs-lookup"><span data-stu-id="cd768-104">To check whether a computer has a working connection</span></span>  
  
- <span data-ttu-id="cd768-105">Zjistěte, `IsAvailable` zda `True` `False`je vlastnost nebo .</span><span class="sxs-lookup"><span data-stu-id="cd768-105">Determine whether the `IsAvailable` property is `True` or `False`.</span></span> <span data-ttu-id="cd768-106">Následující kód zkontroluje stav vlastnosti a hlásí ji:</span><span class="sxs-lookup"><span data-stu-id="cd768-106">The following code checks the property's status and reports it:</span></span>  
  
     [!code-vb[VbResourceTasks#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#3)]  
  
     <span data-ttu-id="cd768-107">Tento příklad kódu je také k dispozici jako fragment kódu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="cd768-107">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="cd768-108">Ve výběru fragmentu kódu je umístěn v **konektivitě a síti**.</span><span class="sxs-lookup"><span data-stu-id="cd768-108">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="cd768-109">Další informace naleznete v [tématu Fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="cd768-109">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd768-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd768-110">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
