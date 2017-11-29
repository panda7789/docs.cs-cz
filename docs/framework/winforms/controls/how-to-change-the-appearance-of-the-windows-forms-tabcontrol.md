---
title: "Postupy: Změna vzhledu Windows Forms TabControl"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b244930f0837d3b1d548e0f7a8c77dd80e1ce039
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a>Postupy: Změna vzhledu Windows Forms TabControl
Můžete změnit vzhled karet ve Windows Forms pomocí vlastnosti <xref:System.Windows.Forms.TabControl> a <xref:System.Windows.Forms.TabPage> objekty, které tvoří na jednotlivé karty na ovládací prvek. Pomocí nastavení těchto vlastností, můžete zobrazení obrázků na karty, zobrazení karet svisle místo vodorovně, zobrazit více řádků karet a povolit nebo zakázat karty prostřednictvím kódu programu.  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a>Zobrazit ikonu na část popisek karty  
  
1.  Přidat <xref:System.Windows.Forms.ImageList> ovládacího prvku do formuláře.  
  
2.  Přidání bitové kopie do seznamu obrázků.  
  
     Další informace o seznamech obrázků najdete v tématu [ImageList – komponenta](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) a [postupy: Přidání nebo odebrání obrázků s komponentou Windows Forms ImageList](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
3.  Nastavte <xref:System.Windows.Forms.TabControl.ImageList%2A> vlastnost <xref:System.Windows.Forms.TabControl> k <xref:System.Windows.Forms.ImageList> ovládacího prvku.  
  
4.  Nastavte <xref:System.Windows.Forms.TabPage.ImageIndex%2A> vlastnost <xref:System.Windows.Forms.TabPage> indexu příslušné bitové kopie v seznamu.  
  
### <a name="to-create-multiple-rows-of-tabs"></a>Chcete-li vytvořit více řádků karty  
  
1.  Číslo stránky karet, které chcete přidáte.  
  
2.  Nastavte <xref:System.Windows.Forms.TabControl.Multiline%2A> vlastnost <xref:System.Windows.Forms.TabControl> k `true`.  
  
3.  Pokud karty se již nezobrazují ve více řádků, nastavte <xref:System.Windows.Forms.Control.Width%2A> vlastnost <xref:System.Windows.Forms.TabControl> být užší než všechny karty.  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a>Chcete-li uspořádat karty stranu ovládacího prvku  
  
-   Nastavte <xref:System.Windows.Forms.TabControl.Alignment%2A> vlastnost <xref:System.Windows.Forms.TabControl> k <xref:System.Windows.Forms.TabAlignment.Left> nebo <xref:System.Windows.Forms.TabAlignment.Right>.  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a>Prostřednictvím kódu programu povolit nebo zakázat všechny ovládací prvky na kartě  
  
1.  Nastavte <xref:System.Windows.Forms.TabPage.Enabled%2A> vlastnost <xref:System.Windows.Forms.TabPage> k `true` nebo `false`.  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a>K zobrazení karet jako tlačítka  
  
-   Nastavte <xref:System.Windows.Forms.TabControl.Appearance%2A> vlastnost <xref:System.Windows.Forms.TabControl> k <xref:System.Windows.Forms.TabAppearance.Buttons> nebo <xref:System.Windows.Forms.TabAppearance.FlatButtons>.  
  
## <a name="see-also"></a>Viz také  
 [TabControl – ovládací prvek](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [Přehled ovládacího prvku TabControl](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [Postupy: Přidání ovládacího prvku do stránky karty](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [Postupy: zákaz stránek karet](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [Postupy: přidávání a odebírání karet s prvkem Windows Forms TabControl](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
