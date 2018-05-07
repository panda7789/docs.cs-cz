---
title: 'Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms GroupBox'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: 718367e9da9efda20c79fbff3bd2f14f11c96ee1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a>Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms GroupBox
Windows Forms <xref:System.Windows.Forms.GroupBox> ovládací prvky slouží k seskupení další ovládací prvky. Existují tři důvodů, proč seskupování ovládacích prvků:  
  
-   Chcete-li vytvořit visual seskupení prvků související formuláře pro zrušte uživatelské rozhraní.  
  
-   Chcete-li vytvořit programový seskupení (přepínačů, např.).  
  
-   Pro přesun ovládací prvky jako jednotku v době návrhu.  
  
### <a name="to-create-a-group-of-controls"></a>Chcete-li vytvořit skupinu ovládacích prvků  
  
1.  Kreslení <xref:System.Windows.Forms.GroupBox> prvek na formuláři.  
  
2.  Přidání dalších ovládacích prvků do pole skupiny kreslení každý uvnitř pole skupiny.  
  
     Pokud máte stávající ovládací prvky, které chcete uzavřete ve skupinovém rámečku, můžete vybrat všechny ovládací prvky, je vyjmout data do schránky, vyberte <xref:System.Windows.Forms.GroupBox> řízení a pak je vložte do pole skupiny. Můžete je také přetáhnout do pole skupiny.  
  
3.  Nastavte <xref:System.Windows.Forms.GroupBox.Text%2A> vlastnost pole skupiny do příslušné titulek.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.GroupBox>  
 [Ovládací prvek GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)
