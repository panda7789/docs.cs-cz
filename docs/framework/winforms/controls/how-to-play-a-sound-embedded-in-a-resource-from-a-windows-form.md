---
title: 'Postupy: Přehrávání zvuku vestavěného v prostředku z formuláře Windows Forms'
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
ms.openlocfilehash: 49235f9cb035c5a09c26b427f855fc00e818fe1c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078574"
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a>Postupy: Přehrávání zvuku vestavěného v prostředku z formuláře Windows Forms
Můžete použít <xref:System.Media.SoundPlayer> třídy přehraje zvuk ze vloženého prostředku.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.Sound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
 Import <xref:System.Media?displayProperty=nameWithType> oboru názvů.  
  
 Včetně zvukový soubor jako vložený prostředek ve vašem projektu.  
  
 Nahraďte "\<AssemblyName >" s názvem sestavení, ve kterém se vloží zvukový soubor. Tuto službu nezahrnuje příponu ".dll".  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Media.SoundPlayer>
- [Postupy: Přehrávání zvuku z formuláře Windows](how-to-play-a-sound-from-a-windows-form.md)
- [Postupy: Smyčka přehrávání zvuku ve formuláři Windows](how-to-loop-a-sound-playing-on-a-windows-form.md)
