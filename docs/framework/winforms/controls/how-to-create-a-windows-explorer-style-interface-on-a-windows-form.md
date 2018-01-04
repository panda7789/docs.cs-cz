---
title: "Postupy: Vytváření rozhraní ve stylu Průzkumníku Windows ve formuláři Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c30dd18e7303cf9fe913760da3f9dad7bca3c95
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a>Postupy: Vytváření rozhraní ve stylu Průzkumníku Windows ve formuláři Windows
Průzkumník Windows je běžné volbou uživatelského rozhraní pro aplikace z důvodu jeho připravené znalosti.  
  
 Průzkumník Windows je v podstatě <xref:System.Windows.Forms.TreeView> řízení a <xref:System.Windows.Forms.ListView> ovládací prvek v samostatných panelů. Panely jsou vytvářeny podle rozdělovač umožňující změnu velikosti. Uspořádání ovládacích prvků je velmi efektivní pro zobrazení a procházení informace.  
  
 Následující kroky ukazují, jak k uspořádání ovládacích prvků ve formuláři stylu Průzkumníka Windows. Nezobrazovat jak přidat funkce procházení souborů aplikace Windows Explorer.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-a-windows-explorer-style-windows-form"></a>K vytvoření formuláře Windows stylu Průzkumníku Windows  
  
1.  Vytvořte nový projekt aplikace Windows. Podrobnosti najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Z **sada nástrojů**:  
  
    1.  Přetáhněte <xref:System.Windows.Forms.SplitContainer> ovládacího prvku do formuláře.  
  
    2.  Přetáhněte <xref:System.Windows.Forms.TreeView> řízení do **SplitterPanel1** (na panelu <xref:System.Windows.Forms.SplitContainer> řízení označena **Panel1**).  
  
    3.  Přetáhněte <xref:System.Windows.Forms.ListView> řízení do **SplitterPanel2** (na panelu <xref:System.Windows.Forms.SplitContainer> řízení označena **Panel2**).  
  
3.  Všechny tři ovládací prvky pro výběr stisknete klávesu CTRL a kliknutím na je naopak. Když vyberete <xref:System.Windows.Forms.SplitContainer> řídit, klikněte na tento panel, nikoli panely.  
  
    > [!NOTE]
    >  Nepoužívejte **Vybrat vše** příkaz na **upravit** nabídky. Pokud tak učiníte, vlastnost potřeba v dalším kroku se nebude zobrazovat na **vlastnosti** okno.  
  
4.  V **vlastnosti** nastavte <xref:System.Windows.Forms.SplitContainer.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.  
  
5.  Stisknutím klávesy F5 spusťte aplikaci.  
  
     Formulář zobrazí dvě části uživatelské rozhraní, podobně jako u Průzkumníka Windows.  
  
    > [!NOTE]
    >  Při přetažení rozdělovače změnit velikost panely sami.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.SplitContainer>  
 [Postupy: Vytváření uživatelského rozhraní s více podokny pomocí Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 [Postupy: Definování chování změny velikosti a polohování v rozděleném okně](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 [Postupy: Vodorovné rozdělení okna](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)  
 [Ovládací prvek SplitContainer](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
