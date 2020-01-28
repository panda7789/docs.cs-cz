---
title: 'Postupy: Vytvoření textového pole určeného jen pro čtení'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 17ae9524009c687cd62fb315f842e188e120ac68
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731268"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>Postupy: Vytvoření textového pole určeného jen pro čtení (Windows Forms)

Můžete transformovat upravitelný model Windows Forms textové pole na ovládací prvek jen pro čtení. Například v textovém poli se může zobrazit hodnota, která je obvykle upravována, ale nemusí být v současné době způsobena stavem aplikace.

## <a name="to-create-a-read-only-text-box"></a>Vytvoření textového pole určeného jen pro čtení

1. Nastavte vlastnost <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> <xref:System.Windows.Forms.TextBox>ho ovládacího prvku na hodnotu `true`. Když je vlastnost nastavená na `true`, můžou uživatelé pořád přesouvat a zvýrazňovat text v textovém poli bez povolení změn. Příkaz pro **kopírování** je funkční v textovém poli, ale příkazy pro **vyjmutí** a **vložení** nejsou.

    > [!NOTE]
    > Vlastnost <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> má vliv na interakci uživatele v době běhu. Změnou vlastnosti <xref:System.Windows.Forms.TextBox.Text%2A> v textovém poli můžete i nadále měnit obsah textového pole programově v době běhu.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.TextBox>
- [Přehled ovládacího prvku TextBox](textbox-control-overview-windows-forms.md)
- [Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Postupy: Vkládání uvozovek do řetězce](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [Ovládací prvek TextBox](textbox-control-windows-forms.md)
