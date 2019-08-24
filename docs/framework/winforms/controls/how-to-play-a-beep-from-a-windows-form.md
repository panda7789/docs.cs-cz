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
ms.openlocfilehash: 7fecc5d5b7259b743926713f87d9303596803582
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015814"
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a><span data-ttu-id="8e8fc-102">Postupy: Přehrávání zvukového signálu z formuláře Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8e8fc-102">How to: Play a Beep from a Windows Form</span></span>
<span data-ttu-id="8e8fc-103">Tento příklad hraje zvukový signál za běhu.</span><span class="sxs-lookup"><span data-stu-id="8e8fc-103">This example plays a beep at run time.</span></span>

## <a name="example"></a><span data-ttu-id="8e8fc-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e8fc-104">Example</span></span>

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
> <span data-ttu-id="8e8fc-105">Zvuk přehrávaný v ukázce C# kódu je určen <xref:System.Media.SystemSounds.Beep%2A> nastavením zvuk systému.</span><span class="sxs-lookup"><span data-stu-id="8e8fc-105">The sound played in the C# code sample is determined by the <xref:System.Media.SystemSounds.Beep%2A> system sound setting.</span></span> <span data-ttu-id="8e8fc-106">Další informace naleznete v tématu <xref:System.Media.SystemSounds>.</span><span class="sxs-lookup"><span data-stu-id="8e8fc-106">For more information, see <xref:System.Media.SystemSounds>.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="8e8fc-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="8e8fc-107">Compiling the Code</span></span>
 <span data-ttu-id="8e8fc-108">C#V tomto příkladu vyžaduje odkaz na <xref:System.Media?displayProperty=nameWithType> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="8e8fc-108">For C#, this example requires  a reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e8fc-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e8fc-109">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Beep%2A>
- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="8e8fc-110">Postupy: Přehrání systémového zvuku z formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="8e8fc-110">How to: Play a System Sound from a Windows Form</span></span>](how-to-play-a-system-sound-from-a-windows-form.md)
- [<span data-ttu-id="8e8fc-111">Postupy: Přehrání zvuku z formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="8e8fc-111">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
