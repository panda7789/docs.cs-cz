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
ms.openlocfilehash: 765021875767a754e62e3ec11e56487e4de91e93
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602780"
---
# <a name="how-to-play-a-system-sound-from-a-windows-form"></a><span data-ttu-id="51df0-102">Postupy: Přehrávání systémového zvuku z formuláře Windows Forms</span><span class="sxs-lookup"><span data-stu-id="51df0-102">How to: Play a System Sound from a Windows Form</span></span>
<span data-ttu-id="51df0-103">Následující kód například jde skvěle dohromady `Exclamation` systémového zvuku v době běhu.</span><span class="sxs-lookup"><span data-stu-id="51df0-103">The following code example plays the `Exclamation` system sound at run time.</span></span> <span data-ttu-id="51df0-104">Další informace o systémové zvuky, naleznete v tématu <xref:System.Media.SystemSounds>.</span><span class="sxs-lookup"><span data-stu-id="51df0-104">For more information about system sounds, see <xref:System.Media.SystemSounds>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51df0-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="51df0-105">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="51df0-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="51df0-106">Compiling the Code</span></span>  
 <span data-ttu-id="51df0-107">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="51df0-107">This example requires:</span></span>  
  
- <span data-ttu-id="51df0-108">Odkaz na <xref:System.Media?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="51df0-108">A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51df0-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51df0-109">See also</span></span>

- <xref:System.Media.SoundPlayer>
- <xref:System.Media.SystemSounds>
- [<span data-ttu-id="51df0-110">Postupy: Přehrání zvukového signálu z formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="51df0-110">How to: Play a Beep from a Windows Form</span></span>](how-to-play-a-beep-from-a-windows-form.md)
- [<span data-ttu-id="51df0-111">Postupy: Přehrávání zvuku z formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="51df0-111">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
