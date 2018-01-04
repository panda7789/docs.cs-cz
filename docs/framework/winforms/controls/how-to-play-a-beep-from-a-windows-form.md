---
title: "Postupy: Přehrání zvukového signálu z formuláře Windows"
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
- sounds [Windows Forms], beep
- Windows Forms, sounds
- sounds [Windows Forms], playing
- forms [Windows Forms], sounds
- examples [Windows Forms], sounds
ms.assetid: 7ea5cded-4888-4f35-8f28-5cab1a55c973
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c0c0c369756547231c0f8171bdfa940cb353544b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a><span data-ttu-id="0c414-102">Postupy: Přehrání zvukového signálu z formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="0c414-102">How to: Play a Beep from a Windows Form</span></span>
<span data-ttu-id="0c414-103">Tento příklad hraje zvukového signálu za běhu.</span><span class="sxs-lookup"><span data-stu-id="0c414-103">This example plays a beep at run time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c414-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="0c414-104">Example</span></span>  
  
```vb  
Public Sub OnePing()  
    Beep()  
End Sub  
```  
  
```csharp  
public void onePing()  
{  
    SystemSounds.Beep.Play();  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="0c414-105">Je dáno zvuk přehrávají v ukázce kódu C# <xref:System.Media.SystemSounds.Beep%2A> zvukové nastavení systému.</span><span class="sxs-lookup"><span data-stu-id="0c414-105">The sound played in the C# code sample is determined by the <xref:System.Media.SystemSounds.Beep%2A> system sound setting.</span></span> <span data-ttu-id="0c414-106">Další informace naleznete v tématu <xref:System.Media.SystemSounds>.</span><span class="sxs-lookup"><span data-stu-id="0c414-106">For more information, see <xref:System.Media.SystemSounds>.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0c414-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="0c414-107">Compiling the Code</span></span>  
 <span data-ttu-id="0c414-108">Pro jazyk C#, tento příklad vyžaduje odkaz na <xref:System.Media?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0c414-108">For C#, this example requires  a reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c414-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c414-109">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Beep%2A>  
 <xref:System.Media.SoundPlayer>  
 [<span data-ttu-id="0c414-110">Postupy: Přehrávání systémového zvuku z formuláře Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0c414-110">How to: Play a System Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-system-sound-from-a-windows-form.md)  
 [<span data-ttu-id="0c414-111">Postupy: Přehrávání zvuku z formuláře Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0c414-111">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
