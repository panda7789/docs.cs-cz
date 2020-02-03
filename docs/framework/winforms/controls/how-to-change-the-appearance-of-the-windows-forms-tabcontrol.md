---
title: Změna vzhledu TabControl
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- icons [Windows Forms], displaying on tabs
- TabControl control [Windows Forms], changing page appearance
- tabs [Windows Forms], controlling appearance
- buttons [Windows Forms], displaying tabs as
ms.assetid: 7c6cc443-ed62-4d26-b94d-b8913b44f773
ms.openlocfilehash: 056070177e6bbaba0c93c7b94f5adfd7887be6a8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746609"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a>Postupy: Změna vzhledu Windows Forms TabControl
Můžete změnit vzhled karet v model Windows Forms pomocí vlastností <xref:System.Windows.Forms.TabControl> a objektů <xref:System.Windows.Forms.TabPage>, které tvoří jednotlivé karty na ovládacím prvku. Nastavením těchto vlastností můžete zobrazit obrázky na kartách, zobrazit karty svisle namísto horizontálně, Zobrazit více řádků karet a povolit nebo zakázat karty programově.  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a>Zobrazení ikony v části popisku na kartě  
  
1. Přidejte ovládací prvek <xref:System.Windows.Forms.ImageList> do formuláře.  
  
2. Přidejte obrázky do seznamu obrázků.  
  
     Další informace o seznamech obrázků naleznete v tématu [Komponenta ImageList](imagelist-component-windows-forms.md) a [Postupy: Přidání nebo odebrání obrázků s komponentou model Windows Forms ImageList](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
3. Nastavte vlastnost <xref:System.Windows.Forms.TabControl.ImageList%2A> <xref:System.Windows.Forms.TabControl> na ovládací prvek <xref:System.Windows.Forms.ImageList>.  
  
4. Nastavte vlastnost <xref:System.Windows.Forms.TabPage.ImageIndex%2A> <xref:System.Windows.Forms.TabPage> na index příslušného obrázku v seznamu.  
  
### <a name="to-create-multiple-rows-of-tabs"></a>Vytvoření více řádků karet  
  
1. Přidejte požadovaný počet stránek karty.  
  
2. Nastavte vlastnost <xref:System.Windows.Forms.TabControl.Multiline%2A> <xref:System.Windows.Forms.TabControl> na `true`.  
  
3. Pokud se karty ještě neobjevují v několika řádcích, nastavte vlastnost <xref:System.Windows.Forms.Control.Width%2A> <xref:System.Windows.Forms.TabControl> tak, aby byla užší než všechny karty.  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a>Uspořádání karet na straně ovládacího prvku  
  
- Vlastnost <xref:System.Windows.Forms.TabControl.Alignment%2A> <xref:System.Windows.Forms.TabControl> nastavte na <xref:System.Windows.Forms.TabAlignment.Left> nebo <xref:System.Windows.Forms.TabAlignment.Right>.  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a>Programové povolení nebo zakázání všech ovládacích prvků na kartě  
  
1. Vlastnost <xref:System.Windows.Forms.TabPage.Enabled%2A> <xref:System.Windows.Forms.TabPage> nastavte na `true` nebo `false`.  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a>Zobrazení karet jako tlačítek  
  
- Vlastnost <xref:System.Windows.Forms.TabControl.Appearance%2A> <xref:System.Windows.Forms.TabControl> nastavte na <xref:System.Windows.Forms.TabAppearance.Buttons> nebo <xref:System.Windows.Forms.TabAppearance.FlatButtons>.  
  
## <a name="see-also"></a>Viz také

- [Ovládací prvek TabControl](tabcontrol-control-windows-forms.md)
- [Přehled ovládacího prvku TabControl](tabcontrol-control-overview-windows-forms.md)
- [Postupy: Přidání ovládacího prvku na kartu](how-to-add-a-control-to-a-tab-page.md)
- [Postupy: Zákaz karet](how-to-disable-tab-pages.md)
- [Postupy: Přidání a odebrání karet pomocí ovládacího prvku Windows Forms TabControl](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
