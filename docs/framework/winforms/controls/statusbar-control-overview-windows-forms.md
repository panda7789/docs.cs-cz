---
title: "StatusBar – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: df8e6b8484cf3b35c684445445ddc41adc358698
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="statusbar-control-overview-windows-forms"></a>StatusBar – přehled ovládacího prvku (Windows Forms)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> a <xref:System.Windows.Forms.ToolStripStatusLabel> ovládací prvky nahradit a přidání funkcí do <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> řídí; však <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> ovládací prvky jsou uchovány pro zpětnou kompatibilitu a budoucí použití, pokud jste Vyberte.  
  
 Windows Forms [StatusBar – ovládací prvek](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) se používá ve formulářích jako oblast, obvykle zobrazují v dolní části okna, ve kterém aplikace můžete zobrazit různé typy informací o stavu. <xref:System.Windows.Forms.StatusBar>ovládací prvky může mít stav panely panelu na nich, které zobrazení textu nebo ikony, které označují stav nebo řadu ikony v animace, který indikuje, že proces je v provozu. například [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] označující, že dokument je uložen.  
  
## <a name="using-the-statusbar-control"></a>Použití ovládacího prvku StatusBar  
 Internet Explorer pomocí stavového řádku označuje adresu URL stránky při umístění ukazatele myši na hypertextový odkaz; [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] získáte informace na stránce umístění, část umístění a úpravy v režimu například přepisování a revize sledování; a [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] používá stavový řádek umožnit kontextové informace, například o tom, jak pracovat s lze ukotvit Windows jako ukotveného nebo plovoucí.  
  
 Do jedné zprávy můžete zobrazit na stavovém řádku nastavením <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> vlastnost `false` (výchozí) a nastavení <xref:System.Windows.Forms.StatusBar.Text%2A> vlastnost stavový řádek na text, který se má zobrazit ve stavovém řádku. Stavový řádek lze rozdělit do panelů zobrazíte víc než jeden typ informací nastavením <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> vlastnost, která má `true` a pomocí <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> metodu <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)
