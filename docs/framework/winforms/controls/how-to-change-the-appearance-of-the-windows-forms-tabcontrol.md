---
title: 'Postupy: Změna vzhledu ovládacího prvku Windows Forms TabControl'
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
ms.openlocfilehash: 05df05a52914f27a4b62cf7bde92e5d942b6ea06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904264"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a>Postupy: Změna vzhledu ovládacího prvku Windows Forms TabControl
Můžete změnit vzhled karty ve Windows Forms pomocí vlastnosti <xref:System.Windows.Forms.TabControl> a <xref:System.Windows.Forms.TabPage> objekty, které tvoří jednotlivé karty na ovládacím prvku. Nastavením těchto vlastností můžete zobrazit obrázky na karty, zobrazení karet svisle namísto vodorovně, zobrazit více řádků karet a povolit nebo zakázat karty prostřednictvím kódu programu.  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a>Chcete-li zobrazit ikonu v části popisek karty  
  
1. Přidat <xref:System.Windows.Forms.ImageList> ovládacího prvku na formuláři.  
  
2. Přidání obrázků do seznamu obrázků.  
  
     Další informace o seznamech image, najdete v části [komponenty ImageList](imagelist-component-windows-forms.md) a [jak: Přidání a odebrání obrázků se Windows Forms ImageList – komponenta](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
3. Nastavte <xref:System.Windows.Forms.TabControl.ImageList%2A> vlastnost <xref:System.Windows.Forms.TabControl> k <xref:System.Windows.Forms.ImageList> ovládacího prvku.  
  
4. Nastavte <xref:System.Windows.Forms.TabPage.ImageIndex%2A> vlastnost <xref:System.Windows.Forms.TabPage> do indexu v seznamu odpovídající image.  
  
### <a name="to-create-multiple-rows-of-tabs"></a>Chcete-li vytvořit více řádků karet  
  
1. Číslo stránky karet, které chcete přidáte.  
  
2. Nastavte <xref:System.Windows.Forms.TabControl.Multiline%2A> vlastnost <xref:System.Windows.Forms.TabControl> k `true`.  
  
3. Pokud na kartách se už nezobrazují v více řádků, nastavte <xref:System.Windows.Forms.Control.Width%2A> vlastnost <xref:System.Windows.Forms.TabControl> bude užší než všechny karty.  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a>Uspořádání karet Toolbar ovládacího prvku  
  
- Nastavte <xref:System.Windows.Forms.TabControl.Alignment%2A> vlastnost <xref:System.Windows.Forms.TabControl> k <xref:System.Windows.Forms.TabAlignment.Left> nebo <xref:System.Windows.Forms.TabAlignment.Right>.  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a>Prostřednictvím kódu programu povolit nebo zakázat všechny ovládací prvky na kartě  
  
1. Nastavte <xref:System.Windows.Forms.TabPage.Enabled%2A> vlastnost <xref:System.Windows.Forms.TabPage> k `true` nebo `false`.  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a>Chcete-li zobrazit karty jako tlačítka  
  
- Nastavte <xref:System.Windows.Forms.TabControl.Appearance%2A> vlastnost <xref:System.Windows.Forms.TabControl> k <xref:System.Windows.Forms.TabAppearance.Buttons> nebo <xref:System.Windows.Forms.TabAppearance.FlatButtons>.  
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvek TabControl](tabcontrol-control-windows-forms.md)
- [Přehled ovládacího prvku TabControl](tabcontrol-control-overview-windows-forms.md)
- [Postupy: Přidání ovládacího prvku do stránky karty](how-to-add-a-control-to-a-tab-page.md)
- [Postupy: Zákaz stránek karet](how-to-disable-tab-pages.md)
- [Postupy: Přidání a odebrání karet pomocí ovládacího prvku Windows Forms TabControl](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
