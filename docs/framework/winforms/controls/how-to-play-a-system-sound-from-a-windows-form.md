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
ms.workload: dotnet
ms.openlocfilehash: 7b620b7386752e531a8d5252159c5f172176890a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-play-a-system-sound-from-a-windows-form"></a>Postupy: Přehrávání systémového zvuku z formuláře Windows
Následující kód například plní `Exclamation` systémového zvuku za běhu. Další informace o systémové zvuky najdete v tématu <xref:System.Media.SystemSounds>.  
  
## <a name="example"></a>Příklad  
  
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
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkaz na <xref:System.Media?displayProperty=nameWithType> oboru názvů.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Media.SoundPlayer>  
 <xref:System.Media.SystemSounds>  
 [Postupy: Přehrání zvukového signálu z formuláře Windows Forms](../../../../docs/framework/winforms/controls/how-to-play-a-beep-from-a-windows-form.md)  
 [Postupy: Přehrávání zvuku z formuláře Windows Forms](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
