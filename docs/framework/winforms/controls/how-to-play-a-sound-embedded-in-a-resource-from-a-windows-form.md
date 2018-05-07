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
ms.openlocfilehash: c9dc8499e2d12ed17f9b409a805148d08da894fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a>Postupy: Přehrávání zvuku vestavěného v prostředku z formuláře Windows
Můžete použít <xref:System.Media.SoundPlayer> třída pro přehrávání zvuku z vložený prostředek.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.Sound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
 Import <xref:System.Media?displayProperty=nameWithType> oboru názvů.  
  
 Zvukový soubor včetně jako vložený prostředek ve vašem projektu.  
  
 Nahrazení "\<AssemblyName >" s název sestavení, ve kterém se vloží zvukový soubor. Neuvádějte příponu ".dll".  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Media.SoundPlayer>  
 [Postupy: Přehrávání zvuku z formuláře Windows Forms](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)  
 [Postupy: Opakované přehrávání zvuku ve formuláři Windows Forms](../../../../docs/framework/winforms/controls/how-to-loop-a-sound-playing-on-a-windows-form.md)
