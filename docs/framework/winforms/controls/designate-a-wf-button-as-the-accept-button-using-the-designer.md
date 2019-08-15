---
title: 'Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: 27ecb26c493232bcfb996d012f9760b7ef91e5b2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039660"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a>Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout pomocí Návrháře
V jakémkoli formuláři Windows můžete určit <xref:System.Windows.Forms.Button> ovládací prvek, který bude tlačítko přijmout, označované také jako výchozí tlačítko. Pokaždé, když uživatel stiskne klávesu ENTER, klikne na tlačítko výchozí, a to bez ohledu na to, který jiný ovládací prvek ve formuláři má fokus. Výjimkou je, když je ovládací prvek s fokusem jiný tlačítko – v takovém případě se na tlačítko s fokusem klikne – nebo na víceřádkové textové pole nebo na vlastní ovládací prvek, který zachytávání klíče ENTER.

## <a name="to-designate-the-accept-button"></a>Označení tlačítka přijmout

1. Vyberte formulář, na kterém se nachází tlačítko.

2. V okně **vlastnosti** nastavte <xref:System.Windows.Forms.Form.AcceptButton%2A> vlastnost formuláře na <xref:System.Windows.Forms.Button> název ovládacího prvku.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Přehled ovládacího prvku Button](button-control-overview-windows-forms.md)
- [Metody výběru ovládacího prvku Windows Forms Button](ways-to-select-a-windows-forms-button-control.md)
- [Postupy: Reakce na model Windows Forms kliknutí na tlačítko](how-to-respond-to-windows-forms-button-clicks.md)
- [Postupy: Označení tlačítka model Windows Forms jako tlačítka Storno pomocí návrháře](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Ovládací prvek Button](button-control-windows-forms.md)
