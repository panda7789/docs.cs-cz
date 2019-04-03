---
title: 'Postupy: Kontrola stavu připojení v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- Web connections [Visual Basic]
- IsAvailable property [Visual Basic], about IsAvailable
- connections [Visual Basic], checking status
- connection status [Visual Basic]
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
ms.openlocfilehash: fd618852c2d0650f168edf8dac53931216fc3a9b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826259"
---
# <a name="how-to-check-connection-status-in-visual-basic"></a><span data-ttu-id="4e254-102">Postupy: Kontrola stavu připojení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4e254-102">How to: Check Connection Status in Visual Basic</span></span>
<span data-ttu-id="4e254-103"><xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> Vlastnost lze použít k určení, zda má počítač funkční síť a připojení k Internetu.</span><span class="sxs-lookup"><span data-stu-id="4e254-103">The <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> property can be used to determine whether the computer has a working network or Internet connection.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a><span data-ttu-id="4e254-104">Zkontrolujte, zda počítač má připojení k práci</span><span class="sxs-lookup"><span data-stu-id="4e254-104">To check whether a computer has a working connection</span></span>  
  
-   <span data-ttu-id="4e254-105">Určení, zda `IsAvailable` vlastnost `True` nebo `False`.</span><span class="sxs-lookup"><span data-stu-id="4e254-105">Determine whether the `IsAvailable` property is `True` or `False`.</span></span> <span data-ttu-id="4e254-106">Následující kód kontroluje stav vlastnosti a ohlásí ji:</span><span class="sxs-lookup"><span data-stu-id="4e254-106">The following code checks the property's status and reports it:</span></span>  
  
     [!code-vb[VbResourceTasks#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#3)]  
  
     <span data-ttu-id="4e254-107">Tento příklad kódu je také dostupný jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="4e254-107">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="4e254-108">V dialogu pro výběr fragmentu kódu je umístěn v **připojení a sítě**.</span><span class="sxs-lookup"><span data-stu-id="4e254-108">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="4e254-109">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="4e254-109">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e254-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e254-110">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
