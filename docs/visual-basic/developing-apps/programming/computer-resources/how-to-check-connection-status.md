---
title: 'Postupy: Kontrola stavu připojení v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- Web connections [Visual Basic]
- IsAvailable property [Visual Basic], about IsAvailable
- connections [Visual Basic], checking status
- connection status [Visual Basic]
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
ms.openlocfilehash: 1a03b181c2e363c3380c4f9858b629713641f2c2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64620678"
---
# <a name="how-to-check-connection-status-in-visual-basic"></a><span data-ttu-id="dc4af-102">Postupy: Kontrola stavu připojení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dc4af-102">How to: Check Connection Status in Visual Basic</span></span>
<span data-ttu-id="dc4af-103"><xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> Vlastnost lze použít k určení, zda má počítač funkční síť a připojení k Internetu.</span><span class="sxs-lookup"><span data-stu-id="dc4af-103">The <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> property can be used to determine whether the computer has a working network or Internet connection.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a><span data-ttu-id="dc4af-104">Zkontrolujte, zda počítač má připojení k práci</span><span class="sxs-lookup"><span data-stu-id="dc4af-104">To check whether a computer has a working connection</span></span>  
  
- <span data-ttu-id="dc4af-105">Určení, zda `IsAvailable` vlastnost `True` nebo `False`.</span><span class="sxs-lookup"><span data-stu-id="dc4af-105">Determine whether the `IsAvailable` property is `True` or `False`.</span></span> <span data-ttu-id="dc4af-106">Následující kód kontroluje stav vlastnosti a ohlásí ji:</span><span class="sxs-lookup"><span data-stu-id="dc4af-106">The following code checks the property's status and reports it:</span></span>  
  
     [!code-vb[VbResourceTasks#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#3)]  
  
     <span data-ttu-id="dc4af-107">Tento příklad kódu je také dostupný jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="dc4af-107">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="dc4af-108">V dialogu pro výběr fragmentu kódu je umístěn v **připojení a sítě**.</span><span class="sxs-lookup"><span data-stu-id="dc4af-108">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="dc4af-109">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="dc4af-109">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc4af-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dc4af-110">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
