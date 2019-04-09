---
title: 'Postupy: Přiřazení existujících ovládacích prvků jinému nadřazenému prvku'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
ms.openlocfilehash: 113afc642ca313f10062a496d2f170e3666d5043
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162238"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a>Postupy: Přiřazení existujících ovládacích prvků jinému nadřazenému prvku
Můžete přiřadit ovládací prvky, které existují ve formuláři pro nový ovládací prvek kontejneru.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-reassign-existing-controls-to-a-different-parent"></a>K přiřazení existujících ovládacích prvků jinému nadřazenému prvku  
  
1.  Přetáhněte tři <xref:System.Windows.Forms.Button> ovládacích prvků z **nástrojů** do formuláře.  
  
     Umístěte blízko sobě navzájem, ale nechat nezarovnaných.  
  
2.  V **nástrojů**, klikněte na tlačítko <xref:System.Windows.Forms.FlowLayoutPanel> ikonu ovládacího prvku.  
  
     Není přetáhněte ikonu na formuláři.  
  
3.  Přesuňte ukazatel myši blízko tři <xref:System.Windows.Forms.Button> ovládacích prvků.  
  
     Ukazatel se změní na křížek s <xref:System.Windows.Forms.FlowLayoutPanel> ikonu ovládací prvek připojen.  
  
4.  Klepněte a podržte tlačítko myši.  
  
5.  Přetažením ukazatele myši nakreslete obrysu <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.  
  
6.  Nakreslit obrys kolem tři <xref:System.Windows.Forms.Button> ovládacích prvků.  
  
7.  Uvolněte tlačítko myši.  
  
     Tři <xref:System.Windows.Forms.Button> ovládací prvky jsou vloženy do <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Uspořádávání ovládacích prvků ve Windows Forms](arranging-controls-on-windows-forms.md)
- [Návod: Uspořádání ovládacích prvků ve Windows Forms s použitím ovládacího prvku TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
