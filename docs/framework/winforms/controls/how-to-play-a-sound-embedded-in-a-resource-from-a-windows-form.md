---
title: 'Postupy: Přehrávání zvuku vestavěného v prostředku z formuláře Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], playing from resources
- resources [Windows Forms], playing sounds
- playing sounds [Windows Forms], from resources
- SoundPlayer class [Windows Forms], playing sounds from resources
ms.assetid: 7d148bb6-8a1e-47d7-a08d-35828d2e688f
ms.openlocfilehash: f52cac4ca16adee232fae6fe2c1540bf5d3cb8cf
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708181"
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a><span data-ttu-id="7f69e-102">Postupy: Přehrávání zvuku vestavěného v prostředku z formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="7f69e-102">How to: Play a Sound Embedded in a Resource from a Windows Form</span></span>
<span data-ttu-id="7f69e-103">Můžete použít <xref:System.Media.SoundPlayer> třídy přehraje zvuk ze vloženého prostředku.</span><span class="sxs-lookup"><span data-stu-id="7f69e-103">You can use the <xref:System.Media.SoundPlayer> class to play a sound from an embedded resource.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f69e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="7f69e-104">Example</span></span>  
 [!code-csharp[System.Windows.Forms.Sound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7f69e-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7f69e-105">Compiling the Code</span></span>  
 <span data-ttu-id="7f69e-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="7f69e-106">This example requires:</span></span>  
  
 <span data-ttu-id="7f69e-107">Import <xref:System.Media?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7f69e-107">Importing the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="7f69e-108">Včetně zvukový soubor jako vložený prostředek ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="7f69e-108">Including the sound file as an embedded resource in your project.</span></span>  
  
 <span data-ttu-id="7f69e-109">Nahraďte "\<AssemblyName >" s názvem sestavení, ve kterém se vloží zvukový soubor.</span><span class="sxs-lookup"><span data-stu-id="7f69e-109">Replacing "\<AssemblyName>" with the name of the assembly in which the sound file is embedded.</span></span> <span data-ttu-id="7f69e-110">Tuto službu nezahrnuje příponu ".dll".</span><span class="sxs-lookup"><span data-stu-id="7f69e-110">Do not include the ".dll" suffix.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f69e-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f69e-111">See also</span></span>
- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="7f69e-112">Postupy: Přehrávání zvuku z formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="7f69e-112">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
- [<span data-ttu-id="7f69e-113">Postupy: Smyčka přehrávání zvuku ve formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="7f69e-113">How to: Loop a Sound Playing on a Windows Form</span></span>](how-to-loop-a-sound-playing-on-a-windows-form.md)
