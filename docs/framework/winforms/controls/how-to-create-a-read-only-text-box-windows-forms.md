---
title: 'Postupy: Vytvoření textového pole určeného jen pro čtení (Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 06e03f67bd1f084b30bce85c3d81ad7b8c97a1b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530143"
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
 [Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Postupy: Vkládání uvozovek do řetězce](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [Ovládací prvek TextBox](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
