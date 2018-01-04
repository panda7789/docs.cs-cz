---
title: "Postupy: Ukotvování ovládacích prvků ve Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fcc672dea63bc74980b4829129f530de9cc72ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-anchor-controls-on-windows-forms"></a>Postupy: Ukotvování ovládacích prvků ve Windows Forms
Při návrhu formuláře, který uživatel může změnit velikost za běhu, ovládací prvky na formuláři by měla velikost a změnit umístění správně. Změna velikosti ovládacích prvků dynamicky pomocí formuláře, můžete použít <xref:System.Windows.Forms.Control.Anchor%2A> vlastnosti ovládacích prvků Windows Forms. <xref:System.Windows.Forms.Control.Anchor%2A> Vlastnost definuje pozice ukotvení pro ovládací prvek. Když je ukotven ovládacího prvku na formulář a formulář se změnila velikost, ovládacího prvku udržuje vzdálenost mezi ovládacího prvku a pozice ukotvení. Pokud máte například <xref:System.Windows.Forms.TextBox> ovládací prvek, který je ukotven k levé, pravé a dolního okraje formuláře, při změně velikosti formuláře <xref:System.Windows.Forms.TextBox> vodorovně řízení změní velikost tak, aby udržuje stejnou vzdálenost od pravé a levé straně formuláře. Kromě toho ovládacího prvku umisťuje samotné svisle tak, aby jeho umístění je vždy stejnou vzdálenost od dolní části formuláře. Pokud není ukotven ovládacího prvku a formuláře, dojde ke změně pozice ovládacího prvku vůči okrajům formuláře.  
  
 <xref:System.Windows.Forms.Control.Anchor%2A> Vlastnost komunikuje s <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost. Další informace najdete v tématu [přehled vlastnosti AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-anchor-a-control-on-a-form"></a>Ukotvení ovládacího prvku ve formuláři  
  
1.  Vyberte ovládací prvek, který chcete ukotvení.  
  
    > [!NOTE]
    >  Stisknutím klávesy CTRL, klepnutím na každý ovládací prvek a vyberte ji a potom následující zbytek tohoto postupu můžete více ovládacích prvků ukotvení současně.  
  
2.  V **vlastnosti** okně klikněte na šipku napravo <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost.  
  
     Zobrazí se editoru, který ukazuje na křížek.  
  
3.  Pokud chcete nastavit anchor, klikněte na tlačítko levému hornímu, pravé nebo dolní části křížek.  
  
     Ovládací prvky jsou ukotven k horní a levé ve výchozím nastavení.  
  
4.  Zrušte straně ovládací prvek, který není ukotven, klikněte na tlačítko této arm křížek.  
  
5.  Zavřete <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost editor, klikněte <xref:System.Windows.Forms.Control.Anchor%2A> znovu název vlastnosti.  
  
 Při svého formuláře se zobrazí v době běhu, změní velikost zůstat umístěného ve stejné vzdálenosti od levého okraje formuláře ovládacího prvku. Vzdálenost od levého okraje ukotvené vždy nezmění definovaným vzdálenost, když je ovládací prvek umístěn v Návrháři formulářů.  
  
> [!NOTE]
>  Některé ovládací prvky, jako například <xref:System.Windows.Forms.ComboBox> řídit, omezení pro jejich výšku. Ukotvení ovládacího prvku k dolnímu okraji jeho formuláře nebo kontejner nemůže vynutit překročení limitu výška ovládacího prvku.  
  
 Musí být zděděné ovládací prvky `Protected` mohli být pevnou. Chcete-li změnit úroveň přístupu tohoto ovládacího prvku, nastavte jeho `Modifiers` vlastnost **vlastnosti** okno.  
  
## <a name="see-also"></a>Viz také  
 [Windows Forms – ovládací prvky](../../../../docs/framework/winforms/controls/index.md)  
 [Uspořádávání ovládacích prvků ve Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Přehled vlastnosti AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [Postupy: Vložení ovládacích prvků ve Windows Forms do doku](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [Postupy: Uspořádání ovládacích prvků na formuláři Windows Forms s použitím ovládacího prvku FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Postupy: Uspořádání ovládacích prvků na Windows Forms s použitím ovládacího prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Návod: Rozvrhování ovládacích prvků Windows Forms s odsazením, okraji a s vlastností AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
