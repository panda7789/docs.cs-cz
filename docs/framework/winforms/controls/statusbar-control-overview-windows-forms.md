---
title: StatusBar – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: c3e52a91a31eb898d0176bc35a97cda7de9a8368
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491347"
---
# <a name="statusbar-control-overview-windows-forms"></a>StatusBar – přehled ovládacího prvku (Windows Forms)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> a <xref:System.Windows.Forms.ToolStripStatusLabel> ovládací prvky nahradit a přidání funkce, které <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> řídí; však <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> ovládací prvky se zachovají pro zpětnou kompatibilitu a budoucí použití, pokud jste Zvolte.  
  
 Windows Forms [ovládacího prvku StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) se používá ve formulářích jako oblast, obvykle se zobrazí v dolní části okna, ve kterém může aplikace zobrazit různé druhy informací o stavu. <xref:System.Windows.Forms.StatusBar> ovládací prvky můžete mít stav panelu na nich zobrazit panely text nebo ikony k označení stavu nebo řady ikony animace, který indikuje, že proces funguje; například [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] označující, že je dokument uložen.  
  
## <a name="using-the-statusbar-control"></a>Použití ovládacího prvku StatusBar  
 Aplikace Internet Explorer stavový řádek používá k označení adresy URL stránky při umístění ukazatele myši nad hypertextový odkaz. [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] poskytuje informace o umístění stránky, umístění oddílu a úpravy v režimu, jako je přepisování a sledování revizí; a sady Visual Studio využívá stavového řádku, abychom zajistili kontextové informace, například o tom, jak pracovat s ukotvitelných oken jako ukotvené nebo plovoucí.  
  
 Do jedné zprávy ve stavovém řádku můžete zobrazit tak, že nastavíte <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> vlastnost `false` (výchozí) a nastavení <xref:System.Windows.Forms.StatusBar.Text%2A> vlastnost stavový řádek textu, které se mají zobrazit ve stavovém řádku. Stavový řádek lze rozdělit do panelů k zobrazení více než jeden typ informací tak, že nastavíte <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> vlastnost `true` a použití <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> metoda <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)
