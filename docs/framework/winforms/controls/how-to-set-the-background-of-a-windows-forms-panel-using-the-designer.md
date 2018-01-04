---
title: "Postupy: Nastavení pozadí panelu Windows Forms pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 995dd5982601ba92a2ec23b82acd7131db183835
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a>Postupy: Nastavení pozadí panelu Windows Forms pomocí Návrháře
Windows Forms <xref:System.Windows.Forms.Panel> ovládací prvek může zobrazit barvu pozadí a obrázek na pozadí. <xref:System.Windows.Forms.Control.BackColor%2A> Vlastnost nastaví barvu pozadí pro ovládací prvky, které jsou obsaženy v panelu, jako je například popisky a přepínač tlačítka. Pokud <xref:System.Windows.Forms.Control.BackgroundImage%2A> není vlastnost nastavena, <xref:System.Windows.Forms.Control.BackColor%2A> výběr naplní všechny panelu. Pokud <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost nastavena, zobrazí se obrázek za ovládacích prvků, které jsou obsaženy v panelu.  
  
 Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře, který obsahuje <xref:System.Windows.Forms.Panel> ovládacího prvku. Informace o tom, jak nastavit tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-the-background-in-the-windows-forms-designer"></a>Chcete-li nastavit na pozadí v Návrháři formulářů Windows  
  
1.  Vyberte <xref:System.Windows.Forms.Panel> ovládacího prvku.  
  
2.  V **vlastnosti** klikněte na šipku vedle <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost zobrazit okno s tři karty.  
  
3.  Vyberte **vlastní** zobrazíte paletu barev.  
  
4.  Vyberte **webové** nebo **systému** můžete zobrazit seznam předdefinovaných názvů pro barvy a pak vyberte barvu.  
  
5.  V **vlastnosti** klikněte na šipku vedle <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost.  
  
6.  V **otevřete** dialogové okno, vyberte soubor, který chcete zobrazit.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Control.BackColor%2A>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>  
 [Ovládací prvek Panel](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [Přehled ovládacího prvku Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí Návrháře](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)
