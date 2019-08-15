---
title: 'Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Zrušit pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: cc352f15fb1e8b531cd0f9b298b2db4ce649d3cf
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039639"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a>Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Zrušit pomocí Návrháře
V jakémkoli formuláři Windows můžete určit <xref:System.Windows.Forms.Button> ovládací prvek pro tlačítko Storno. Kliknutím na tlačítko Storno dojde vždy, když uživatel stiskne klávesu ESC bez ohledu na to, který jiný ovládací prvek ve formuláři má fokus. Toto tlačítko je obvykle naprogramováno, aby uživatel mohl rychle ukončit operaci bez nutnosti potvrzení akce.

## <a name="to-designate-the-cancel-button"></a>Chcete-li určit tlačítko Storno

1. Vyberte formulář, na kterém se nachází tlačítko.

2. V okně **vlastnosti** nastavte <xref:System.Windows.Forms.Form.CancelButton%2A> vlastnost formuláře na <xref:System.Windows.Forms.Button> název ovládacího prvku.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Přehled ovládacího prvku Button](button-control-overview-windows-forms.md)
- [Metody výběru ovládacího prvku Windows Forms Button](ways-to-select-a-windows-forms-button-control.md)
- [Postupy: Reakce na model Windows Forms kliknutí na tlačítko](how-to-respond-to-windows-forms-button-clicks.md)
- [Postupy: Označení tlačítka model Windows Forms jako tlačítka přijmout pomocí návrháře](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Ovládací prvek Button](button-control-windows-forms.md)
