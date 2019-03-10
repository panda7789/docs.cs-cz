---
title: 'Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms GroupBox'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: 14c832251a76eaff21611c88179c4d2ffa7ab738
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708536"
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
- [Ovládací prvek GroupBox](groupbox-control-windows-forms.md)
