---
title: 'Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms GroupBox'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: 44f0116511165c021f8e3dc35fb14e5cfb6f619e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686917"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a>Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms GroupBox
Windows Forms <xref:System.Windows.Forms.GroupBox> ovládací prvky se používají k seskupování další ovládací prvky. Existují tři hlavní důvody k seskupování ovládacích prvků:  
  
-   Chcete-li vytvořit vizuální seskupení elementů související formuláře pro jasné uživatelské rozhraní.  
  
-   Chcete-li vytvořit programový seskupení (přepínačů, například).  
  
-   K přesunutí ovládacích prvků jako jednotka v době návrhu.  
  
### <a name="to-create-a-group-of-controls"></a>Chcete-li vytvořit skupinu ovládacích prvků  
  
1.  Vykreslení <xref:System.Windows.Forms.GroupBox> ovládací prvek na formuláři.  
  
2.  Přidejte další ovládací prvky do pole skupiny, kreslení každý uvnitř skupinového rámečku.  
  
     Pokud máte existující ovládací prvky, které chcete uzavřít do skupinového rámečku, můžete vybrat všechny ovládací prvky, vyjmout data do schránky, vyberte <xref:System.Windows.Forms.GroupBox> ovládací prvek a pak je vložte do pole pro skupiny. Můžete také přetáhnout do pole skupiny.  
  
3.  Nastavte <xref:System.Windows.Forms.GroupBox.Text%2A> vlastnost skupinový rámeček pro příslušný popisek.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.GroupBox>
- [Ovládací prvek GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)
