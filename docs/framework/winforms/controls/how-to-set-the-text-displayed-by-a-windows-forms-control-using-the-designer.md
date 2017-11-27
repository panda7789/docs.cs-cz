---
title: "Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], setting caption
- Windows Forms, setting the text displayed
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 59d66df2c6f18ad28ad4b912c00e35f786d773da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer"></a>Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms pomocí Návrháře
Ovládací prvky Windows Forms obvykle zobrazí text související s primární funkce ovládacího prvku. Například <xref:System.Windows.Forms.Button> obvykle zobrazí popisek, který určuje, jaká akce se provede při kliknutí na tlačítko. Pro všechny ovládací prvky, můžete nastavit nebo vrátí text s použitím <xref:System.Windows.Forms.Control.Text%2A> vlastnost. Písmo můžete změnit pomocí <xref:System.Windows.Forms.Control.Font%2A> vlastnost.  
  
### <a name="to-set-the-text-and-font-with-the-designer"></a>Chcete-li nastavit text a písma pomocí návrháře  
  
1.  V okně vlastnosti nastavit <xref:System.Windows.Forms.Control.Text%2A> vlastnost ovládacího prvku na odpovídající řetězec.  
  
     Chcete-li vytvořit podtržené klávesová obsahuje znak ampersand (&) před písmeno, které bude klávesovou zkratku.  
  
2.  V okně vlastností klikněte na tlačítko se třemi tečkami (![– snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.Control.Font%2A> vlastnost.  
  
     V dialogovém okně standardní písma vyberte písmo, styl písma, velikost, efekty (například přeškrtnutí nebo podtržení) a skriptu které chcete.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: nastavení textu zobrazovaného prvku Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [Použití písem a textu](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [Popisování jednotlivých Windows Forms – ovládací prvky a zajišťování zástupců pro tyto](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
