---
title: 'Postupy: Přiřazení existujících ovládacích prvků jinému nadřazenému prvku'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1767fcff1742f4ad630b4b996c709b7ded53a129
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459196"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a>Postupy: Změna přiřazení existujících ovládacích prvků jinému nadřazenému prvku

Ovládací prvky, které existují na formuláři, můžete přiřadit k novému ovládacímu prvku kontejneru.

1. V sadě Visual Studio přetáhněte ze **sady nástrojů** do formuláře tři ovládací prvky <xref:System.Windows.Forms.Button>. Umístěte je blízko k sobě, ale nechte je nezarovnané.

2. Na **panelu nástrojů**klikněte na ikonu ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel>. (Nepřetáhněte ikonu do formuláře.)

3. Přesuňte ukazatel myši blízko k třem ovládacím prvkům <xref:System.Windows.Forms.Button>.

   Ukazatel se změní na vlasovou čáru s připojenou ikonou ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel>.

4. Klikněte a podržte tlačítko myši.

5. Přetažením ukazatele myši nakreslete obrys ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel>.

6. Vykreslete obrys kolem tří <xref:System.Windows.Forms.Button>ch ovládacích prvků.

7. Uvolněte tlačítko myši.

   Tři ovládací prvky <xref:System.Windows.Forms.Button> jsou nyní vloženy do ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel>.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Postupy: Uspořádání ovládacích prvků na Windows Forms s použitím ovládacího prvku TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
