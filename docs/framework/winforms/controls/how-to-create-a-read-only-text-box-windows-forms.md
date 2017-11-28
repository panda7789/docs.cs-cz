---
title: "Postupy: Vytvoření textového pole určeného jen pro čtení (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9cf6064442c3b648116f98f98f169dac12e5e88c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>Postupy: Vytvoření textového pole určeného jen pro čtení (Windows Forms)
Textového pole na upravitelné Windows Forms můžete převést do ovládacího prvku jen pro čtení. Textové pole může například zobrazí hodnotu, která je obvykle upravovat, ale nemusí být v současné době z důvodu stavu aplikace.  
  
### <a name="to-create-a-read-only-text-box"></a>Chcete-li vytvořit jen pro čtení textového pole  
  
1.  Nastavte <xref:System.Windows.Forms.TextBox> ovládacího prvku <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> vlastnost `true`. S vlastností nastavenou na `true`, uživatelé stále přejděte a zvýrazňování textu v textovém poli beze změny. A **kopie** příkaz je funkční v textovém poli, ale **Vyjmout** a **vložení** nejsou příkazy.  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> Vlastnost ovlivňuje pouze interakci s uživatelem v době běhu. Můžete je stále změnit obsahu textového pole prostřednictvím kódu programu v době běhu změnou <xref:System.Windows.Forms.TextBox.Text%2A> vlastnosti textového pole.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.TextBox>  
 [Přehled ovládacího prvku TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Postupy: řízení bodu pro vkládání v ovládacím prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Postupy: vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Postupy: vkládání uvozovek do řetězce](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Postupy: Výběr textu v systému Windows Forms TextBox – ovládací prvek](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [Postupy: zobrazení více řádků v systému Windows Forms TextBox – ovládací prvek](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [TextBox – ovládací prvek](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
