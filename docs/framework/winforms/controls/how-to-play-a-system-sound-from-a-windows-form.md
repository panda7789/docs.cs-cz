---
title: 'Postupy: Přehrávání systémového zvuku z formuláře Windows Forms'
ms.date: 03/30/2017
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
ms.openlocfilehash: d85d8cd40ff2b32cb3f2a79cf9a8221964f186c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913286"
---
# <a name="how-to-play-a-system-sound-from-a-windows-form"></a>Postupy: Přehrávání systémového zvuku z formuláře Windows Forms
Následující kód například jde skvěle dohromady `Exclamation` systémového zvuku v době běhu. Další informace o systémové zvuky, naleznete v tématu <xref:System.Media.SystemSounds>.  
  
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
  
- Odkaz na <xref:System.Media?displayProperty=nameWithType> oboru názvů.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Media.SoundPlayer>
- <xref:System.Media.SystemSounds>
- [Postupy: Přehrání zvukového signálu z formuláře Windows](how-to-play-a-beep-from-a-windows-form.md)
- [Postupy: Přehrávání zvuku z formuláře Windows](how-to-play-a-sound-from-a-windows-form.md)
