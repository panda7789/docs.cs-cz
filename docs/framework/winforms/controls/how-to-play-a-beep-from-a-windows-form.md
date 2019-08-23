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
ms.openlocfilehash: 1a72f88c05fb21c11864058ffbe81c1957525375
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966512"
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a>Postupy: Přehrávání zvukového signálu z formuláře Windows Forms
Tento příklad hraje zvukový signál za běhu.  
  
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
> Zvuk přehrávaný v ukázce C# kódu je určen <xref:System.Media.SystemSounds.Beep%2A> nastavením zvuk systému. Další informace naleznete v tématu <xref:System.Media.SystemSounds>.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 C#V tomto příkladu vyžaduje odkaz na <xref:System.Media?displayProperty=nameWithType> obor názvů.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Interaction.Beep%2A>
- <xref:System.Media.SoundPlayer>
- [Postupy: Přehrání systémového zvuku z formuláře Windows](how-to-play-a-system-sound-from-a-windows-form.md)
- [Postupy: Přehrání zvuku z formuláře Windows](how-to-play-a-sound-from-a-windows-form.md)
