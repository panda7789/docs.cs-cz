---
title: 'Postupy: Přehrávání zvukového signálu z formuláře Windows Forms'
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
ms.openlocfilehash: 0aa01f600873dd8853e1c33d5443448835e11455
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913429"
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a>Postupy: Přehrávání zvukového signálu z formuláře Windows Forms
V tomto příkladu přehraje pípnutí v době běhu.  
  
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
>  Zvuk v C# vzorový kód závisí <xref:System.Media.SystemSounds.Beep%2A> zvukový nastavení systému. Další informace naleznete v tématu <xref:System.Media.SystemSounds>.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Pro C#, v tomto příkladu vyžaduje přidání odkazu na <xref:System.Media?displayProperty=nameWithType> oboru názvů.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Interaction.Beep%2A>
- <xref:System.Media.SoundPlayer>
- [Postupy: Přehrávání systémového zvuku z formuláře Windows](how-to-play-a-system-sound-from-a-windows-form.md)
- [Postupy: Přehrávání zvuku z formuláře Windows](how-to-play-a-sound-from-a-windows-form.md)
