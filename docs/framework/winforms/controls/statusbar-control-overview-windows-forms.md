---
title: StatusBar – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: 4e1816ef221641f5ad54fb429442ed43289b592a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505421"
---
# <a name="statusbar-control-overview-windows-forms"></a>StatusBar – přehled ovládacího prvku (Windows Forms)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> a <xref:System.Windows.Forms.ToolStripStatusLabel> ovládací prvky nahradit a přidání funkce, které <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> řídí; však <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> ovládací prvky se zachovají pro zpětnou kompatibilitu a budoucí použití, pokud jste Zvolte.  
  
 Windows Forms [ovládacího prvku StatusBar](statusbar-control-windows-forms.md) se používá ve formulářích jako oblast, obvykle se zobrazí v dolní části okna, ve kterém může aplikace zobrazit různé druhy informací o stavu. <xref:System.Windows.Forms.StatusBar> ovládací prvky můžete mít stav panelu na nich zobrazit panely text nebo ikony k označení stavu nebo řady ikony animace, který indikuje, že proces funguje; například Microsoft Word označující, že dokument se ukládá.  
  
## <a name="using-the-statusbar-control"></a>Použití ovládacího prvku StatusBar  
 Aplikace Internet Explorer stavový řádek používá k označení adresy URL stránky při umístění ukazatele myši nad hypertextový odkaz. Aplikace Microsoft Word získáte informace o umístění stránky, umístění oddílu a úpravy režimech, např. přepisování a sledování; revizí a Visual Studio využívá stavového řádku, abychom zajistili kontextové informace, například o tom, jak k práci s jako ukotvené nebo plovoucí ukotvitelných oken.  
  
 Do jedné zprávy ve stavovém řádku můžete zobrazit tak, že nastavíte <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> vlastnost `false` (výchozí) a nastavení <xref:System.Windows.Forms.StatusBar.Text%2A> vlastnost stavový řádek textu, které se mají zobrazit ve stavovém řádku. Stavový řádek lze rozdělit do panelů k zobrazení více než jeden typ informací tak, že nastavíte <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> vlastnost `true` a použití <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> metoda <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím](determine-which-panel-wf-statusbar-control-was-clicked.md)
