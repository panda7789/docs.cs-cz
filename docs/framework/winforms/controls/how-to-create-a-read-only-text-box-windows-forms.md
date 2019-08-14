---
title: 'Postupy: Vytvoření textového pole určeného jen pro čtení (model Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 18d2f5ed2530957487ac25c3eb6240f8bc50a938
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971947"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>Postupy: Vytvoření textového pole určeného jen pro čtení (model Windows Forms)

Můžete transformovat upravitelný model Windows Forms textové pole na ovládací prvek jen pro čtení. Například v textovém poli se může zobrazit hodnota, která je obvykle upravována, ale nemusí být v současné době způsobena stavem aplikace.

## <a name="to-create-a-read-only-text-box"></a>Vytvoření textového pole určeného jen pro čtení

1. <xref:System.Windows.Forms.TextBox> Nastavte vlastnost<xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> ovládacího prvku na `true`. Když je vlastnost nastavena na `true`hodnotu, uživatelé mohou v textovém poli přesouvat a zvýrazňovat text bez povolení změn. Příkaz pro **kopírování** je funkční v textovém poli, ale příkazy pro vyjmutí a **vložení** nejsou.

    > [!NOTE]
    > <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> Vlastnost ovlivňuje pouze interakci uživatele v době běhu. Změnou <xref:System.Windows.Forms.TextBox.Text%2A> vlastnosti textového pole můžete i nadále měnit obsah textového pole programově za běhu.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.TextBox>
- [Přehled ovládacího prvku TextBox](textbox-control-overview-windows-forms.md)
- [Postupy: Řízení místa vložení v ovládacím prvku TextBox model Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Postupy: Textové pole pro vytvoření hesla pomocí ovládacího prvku model Windows Forms TextBox](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Postupy: Vložení uvozovek do řetězce](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Postupy: Výběr textu v ovládacím prvku model Windows Forms TextBox](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Postupy: Zobrazit více řádků v ovládacím prvku model Windows Forms TextBox](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [Ovládací prvek TextBox](textbox-control-windows-forms.md)
