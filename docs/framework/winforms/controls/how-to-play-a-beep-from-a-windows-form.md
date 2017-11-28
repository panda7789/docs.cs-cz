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
ms.openlocfilehash: e214b368b65797100722cb41ad6a77ecd16424de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a>Postupy: Přehrání zvukového signálu z formuláře Windows
Tento příklad hraje zvukového signálu za běhu.  
  
## <a name="example"></a>Příklad  
  
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
>  Je dáno zvuk přehrávají v ukázce kódu C# <xref:System.Media.SystemSounds.Beep%2A> zvukové nastavení systému. Další informace naleznete v tématu <xref:System.Media.SystemSounds>.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Pro jazyk C#, tento příklad vyžaduje odkaz na <xref:System.Media?displayProperty=nameWithType> oboru názvů.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Interaction.Beep%2A>  
 <xref:System.Media.SoundPlayer>  
 [Postupy: přehrávání systémového zvuku z formuláře Windows](../../../../docs/framework/winforms/controls/how-to-play-a-system-sound-from-a-windows-form.md)  
 [Postupy: přehrávání zvuku z formuláře Windows](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
