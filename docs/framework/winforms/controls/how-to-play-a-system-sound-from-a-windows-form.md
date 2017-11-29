---
title: "Postupy: Přehrávání systémového zvuku z formuláře Windows"
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
- sounds [Windows Forms], playing for system events
- playing sounds [Windows Forms], Windows Forms
- system sounds [Windows Forms], playing from Windows Forms
- playing sounds [Windows Forms], system
- SoundPlayer class [Windows Forms], system sounds
- sounds [Windows Forms], playing
- examples [Windows Forms], sounds
ms.assetid: afb206ff-4824-4804-a8d4-185bf5ad8e7c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 51de367f2558abfc28be740409d8a0d394065acf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-play-a-system-sound-from-a-windows-form"></a><span data-ttu-id="aa49e-102">Postupy: Přehrávání systémového zvuku z formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="aa49e-102">How to: Play a System Sound from a Windows Form</span></span>
<span data-ttu-id="aa49e-103">Následující kód například plní `Exclamation` systémového zvuku za běhu.</span><span class="sxs-lookup"><span data-stu-id="aa49e-103">The following code example plays the `Exclamation` system sound at run time.</span></span> <span data-ttu-id="aa49e-104">Další informace o systémové zvuky najdete v tématu <xref:System.Media.SystemSounds>.</span><span class="sxs-lookup"><span data-stu-id="aa49e-104">For more information about system sounds, see <xref:System.Media.SystemSounds>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa49e-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="aa49e-105">Example</span></span>  
  
```vb  
Public Sub PlayExclamation()  
    SystemSounds.Exclamation.Play()  
End Sub  
```  
  
```csharp  
public void playExclamation()  
{  
    SystemSounds.Exclamation.Play();  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aa49e-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="aa49e-106">Compiling the Code</span></span>  
 <span data-ttu-id="aa49e-107">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="aa49e-107">This example requires:</span></span>  
  
-   <span data-ttu-id="aa49e-108">Odkaz na <xref:System.Media?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="aa49e-108">A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa49e-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa49e-109">See Also</span></span>  
 <xref:System.Media.SoundPlayer>  
 <xref:System.Media.SystemSounds>  
 [<span data-ttu-id="aa49e-110">Postupy: přehrání zvukového signálu z formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="aa49e-110">How to: Play a Beep from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-beep-from-a-windows-form.md)  
 [<span data-ttu-id="aa49e-111">Postupy: přehrávání zvuku z formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="aa49e-111">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
