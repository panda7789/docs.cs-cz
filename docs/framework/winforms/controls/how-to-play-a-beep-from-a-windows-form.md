---
title: 'Postupy: Přehrání zvukového signálu z formuláře Windows'
ms.date: 03/30/2017
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
ms.openlocfilehash: 460309d853f2b3b423d14a820771e0230358e3c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
 [Postupy: Přehrávání systémového zvuku z formuláře Windows Forms](../../../../docs/framework/winforms/controls/how-to-play-a-system-sound-from-a-windows-form.md)  
 [Postupy: Přehrávání zvuku z formuláře Windows Forms](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
