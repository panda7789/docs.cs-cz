---
title: "Postupy: Kontrola stavu připojení v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Web connections [Visual Basic]
- IsAvailable property [Visual Basic], about IsAvailable
- connections [Visual Basic], checking status
- connection status [Visual Basic]
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 31a8bb72e3b5cdc5ddee626a377c70640facb81d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-check-connection-status-in-visual-basic"></a><span data-ttu-id="25b46-102">Postupy: Kontrola stavu připojení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="25b46-102">How to: Check Connection Status in Visual Basic</span></span>
<span data-ttu-id="25b46-103"><xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> Vlastnost lze použít k určení, zda má počítač funkční síť nebo připojení k Internetu.</span><span class="sxs-lookup"><span data-stu-id="25b46-103">The <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> property can be used to determine whether the computer has a working network or Internet connection.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a><span data-ttu-id="25b46-104">Zkontrolujte, zda má počítač připojení k pracovní</span><span class="sxs-lookup"><span data-stu-id="25b46-104">To check whether a computer has a working connection</span></span>  
  
-   <span data-ttu-id="25b46-105">Určit, zda `IsAvailable` vlastnost je `True` nebo `False`.</span><span class="sxs-lookup"><span data-stu-id="25b46-105">Determine whether the `IsAvailable` property is `True` or `False`.</span></span> <span data-ttu-id="25b46-106">Následující kód kontroluje stav vlastnosti a ohlásí ji:</span><span class="sxs-lookup"><span data-stu-id="25b46-106">The following code checks the property's status and reports it:</span></span>  
  
     [!code-vb[VbResourceTasks#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-check-connection-status_1.vb)]  
  
     <span data-ttu-id="25b46-107">Tento příklad kódu je také k dispozici jako IntelliSense fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="25b46-107">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="25b46-108">V Sběrač fragmentů kódu je umístěn v **připojení a sítě**.</span><span class="sxs-lookup"><span data-stu-id="25b46-108">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="25b46-109">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="25b46-109">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25b46-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="25b46-110">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
