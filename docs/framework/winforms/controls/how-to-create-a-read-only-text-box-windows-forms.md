---
title: 'Postupy: Vytvoření textového pole určeného jen pro čtení'
description: Přečtěte si informace o transformaci upravitelný model Windows Forms textového pole do textového pole model Windows Forms jen pro čtení.
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 5baa7c66d5f16560a4ea23861d563b099592957f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619361"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>Postupy: Vytvoření textového pole určeného jen pro čtení (Windows Forms)

Můžete transformovat upravitelný model Windows Forms textové pole na ovládací prvek jen pro čtení. Například v textovém poli se může zobrazit hodnota, která je obvykle upravována, ale nemusí být v současné době způsobena stavem aplikace.

## <a name="to-create-a-read-only-text-box"></a>Vytvoření textového pole určeného jen pro čtení

1. Nastavte <xref:System.Windows.Forms.TextBox> vlastnost ovládacího prvku <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> na `true` . Když je vlastnost nastavena na hodnotu `true` , uživatelé mohou v textovém poli přesouvat a zvýrazňovat text bez povolení změn. Příkaz pro **kopírování** je funkční v textovém poli, ale příkazy pro **vyjmutí** a **vložení** nejsou.

    > [!NOTE]
    > <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>Vlastnost ovlivňuje pouze interakci uživatele v době běhu. Změnou vlastnosti textového pole můžete i nadále měnit obsah textového pole programově za běhu <xref:System.Windows.Forms.TextBox.Text%2A> .

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.TextBox>
- [Přehled ovládacího prvku TextBox](textbox-control-overview-windows-forms.md)
- [Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Postupy: Vkládání uvozovek do řetězce](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox – ovládací prvek](textbox-control-windows-forms.md)
