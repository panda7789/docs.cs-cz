---
title: 'Postupy: Přiřazení existujících ovládacích prvků jinému nadřazenému prvku'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
ms.openlocfilehash: a65b3c2b596a2d88ce4236aeadd86993bb268aa6
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039791"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a>Postupy: Přiřazení existujících ovládacích prvků jinému nadřazenému prvku
Ovládací prvky, které existují na formuláři, můžete přiřadit k novému ovládacímu prvku kontejneru.

## <a name="to-reassign-existing-controls-to-a-different-parent"></a>Změna přiřazení existujících ovládacích prvků jinému nadřazenému prvku

1. Přetáhněte tři <xref:System.Windows.Forms.Button> ovládací prvky z **panelu nástrojů** do formuláře.

     Umístěte je blízko k sobě, ale nechte je nezarovnané.

2. Na **panelu nástrojů**klikněte <xref:System.Windows.Forms.FlowLayoutPanel> na ikonu ovládacího prvku.

     Nepřetáhněte ikonu do formuláře.

3. Přesuňte ukazatel myši blízko k třem <xref:System.Windows.Forms.Button> ovládacím prvkům.

     Ukazatel se změní na vlasovou čáru s <xref:System.Windows.Forms.FlowLayoutPanel> připojenou ikonou ovládacího prvku.

4. Klikněte a podržte tlačítko myši.

5. Přetažením ukazatele myši nakreslete obrys <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.

6. Vykreslete obrys kolem tří <xref:System.Windows.Forms.Button> ovládacích prvků.

7. Uvolněte tlačítko myši.

     Tři <xref:System.Windows.Forms.Button> ovládací prvky jsou nyní vloženy <xref:System.Windows.Forms.FlowLayoutPanel> do ovládacího prvku.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Uspořádávání ovládacích prvků ve Windows Forms](arranging-controls-on-windows-forms.md)
- [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí zarovnávacím čárám](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
