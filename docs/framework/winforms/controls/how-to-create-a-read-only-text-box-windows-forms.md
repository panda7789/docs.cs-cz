---
title: 'Postupy: Vytvoření pole jen pro čtení textu (Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 72dc188993474ad4b39f0cfa74cadffdb99ff46f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61746819"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>Postupy: Vytvoření pole jen pro čtení textu (Windows Forms)
Upravitelné textové pole formulářů Windows můžete transformovat na ovládací prvek jen pro čtení. Do textového pole mohou například zobrazit hodnotu, která je obvykle upraven, ale nemusí být v současné době kvůli stavu aplikace.  
  
### <a name="to-create-a-read-only-text-box"></a>K vytvoření pole jen pro čtení textu  
  
1. Nastavte <xref:System.Windows.Forms.TextBox> ovládacího prvku <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> vlastnost `true`. Vlastnost nastavena na `true`, uživatelé stále můžete posunout a zvýrazňování textu v textovém poli bez povolení změn. A **kopírování** příkaz je funkční v textovém poli, ale **Vyjmout** a **vložit** nejsou příkazy.  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> Vlastnost ovlivňuje pouze interakci s uživatelem v době běhu. Můžete stále změnit obsahu textového pole prostřednictvím kódu programu za běhu pomocí změny <xref:System.Windows.Forms.TextBox.Text%2A> vlastnosti textového pole.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.TextBox>
- [Přehled ovládacího prvku TextBox](textbox-control-overview-windows-forms.md)
- [Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Postupy: Vkládání uvozovek do řetězce](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Postupy: Zobrazit více řádků v ovládacím prvku Windows Forms TextBox](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [Ovládací prvek TextBox](textbox-control-windows-forms.md)
