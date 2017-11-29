---
title: "Postupy: Přehrávání zvuku vestavěného v prostředku z formuláře Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], playing from resources
- resources [Windows Forms], playing sounds
- playing sounds [Windows Forms], from resources
- SoundPlayer class [Windows Forms], playing sounds from resources
ms.assetid: 7d148bb6-8a1e-47d7-a08d-35828d2e688f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 82e143a6c405d4f3065c18a1a118891e0e692b93
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a><span data-ttu-id="bb6e8-102">Postupy: Přehrávání zvuku vestavěného v prostředku z formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="bb6e8-102">How to: Play a Sound Embedded in a Resource from a Windows Form</span></span>
<span data-ttu-id="bb6e8-103">Můžete použít <xref:System.Media.SoundPlayer> třída pro přehrávání zvuku z vložený prostředek.</span><span class="sxs-lookup"><span data-stu-id="bb6e8-103">You can use the <xref:System.Media.SoundPlayer> class to play a sound from an embedded resource.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb6e8-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="bb6e8-104">Example</span></span>  
 [!code-csharp[System.Windows.Forms.Sound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bb6e8-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="bb6e8-105">Compiling the Code</span></span>  
 <span data-ttu-id="bb6e8-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="bb6e8-106">This example requires:</span></span>  
  
 <span data-ttu-id="bb6e8-107">Import <xref:System.Media?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="bb6e8-107">Importing the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="bb6e8-108">Zvukový soubor včetně jako vložený prostředek ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="bb6e8-108">Including the sound file as an embedded resource in your project.</span></span>  
  
 <span data-ttu-id="bb6e8-109">Nahrazení "\<AssemblyName >" s název sestavení, ve kterém se vloží zvukový soubor.</span><span class="sxs-lookup"><span data-stu-id="bb6e8-109">Replacing "\<AssemblyName>" with the name of the assembly in which the sound file is embedded.</span></span> <span data-ttu-id="bb6e8-110">Neuvádějte příponu ".dll".</span><span class="sxs-lookup"><span data-stu-id="bb6e8-110">Do not include the ".dll" suffix.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb6e8-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb6e8-111">See Also</span></span>  
 <xref:System.Media.SoundPlayer>  
 [<span data-ttu-id="bb6e8-112">Postupy: přehrávání zvuku z formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="bb6e8-112">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)  
 [<span data-ttu-id="bb6e8-113">Postupy: cykly přehrávání zvuku ve formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="bb6e8-113">How to: Loop a Sound Playing on a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-loop-a-sound-playing-on-a-windows-form.md)
