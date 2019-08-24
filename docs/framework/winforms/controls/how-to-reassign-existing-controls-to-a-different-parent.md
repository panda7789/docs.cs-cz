---
title: 'Postupy: Přiřazení existujících ovládacích prvků jinému nadřazenému prvku'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 84e662e0bd2689115abe128c6442e4462eed3e18
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987033"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a>Postupy: Opětovné přiřazení existujících ovládacích prvků jinému nadřazenému prvku

Ovládací prvky, které existují na formuláři, můžete přiřadit k novému ovládacímu prvku kontejneru.

1. V sadě Visual Studio přetáhněte tři <xref:System.Windows.Forms.Button> ovládací prvky z **panelu nástrojů** do formuláře. Umístěte je blízko k sobě, ale nechte je nezarovnané.

2. Na **panelu nástrojů**klikněte <xref:System.Windows.Forms.FlowLayoutPanel> na ikonu ovládacího prvku. (Nepřetáhněte ikonu do formuláře.)

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
- [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí zarovnávacím čárám](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
