---
title: Přehled ovládacího prvku StatusBar
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: b0b97bc3cb0291871e1fd113d82d0b480b53cdba
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742874"
---
# <a name="statusbar-control-overview-windows-forms"></a>StatusBar – přehled ovládacího prvku (Windows Forms)
> [!IMPORTANT]
> Ovládací prvky <xref:System.Windows.Forms.StatusStrip> a <xref:System.Windows.Forms.ToolStripStatusLabel> nahrazují a přidávají funkce ovládacím prvkům <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel>; ovládací prvky <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> se však uchovávají pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.  
  
 [Ovládací prvek](statusbar-control-windows-forms.md) model Windows Forms stavový řádek se používá ve formulářích jako oblast, obvykle se zobrazuje v dolní části okna, kde aplikace může zobrazit různé druhy informací o stavu. ovládací prvky <xref:System.Windows.Forms.StatusBar> mohou mít panely na stavovém řádku, které zobrazují text nebo ikony k označení stavu, nebo řadu ikon v animaci, která indikuje, že proces pracuje. například Microsoft Word značí, že se dokument ukládá.  
  
## <a name="using-the-statusbar-control"></a>Použití ovládacího prvku stavový řádek  
 Internet Explorer používá stavový řádek k označení adresy URL stránky, když se ukazatel myši přesune na hypertextový odkaz. V aplikaci Microsoft Word získáte informace o umístění stránky, umístění oddílu a režimech úprav, například přepisu a sledování revizí. a Visual Studio používá stavový řádek k poskytnutí kontextově citlivých informací, jako je například oznámení, jak pracovat s ukotvit okny buď jako docked, nebo float.  
  
 Můžete zobrazit jednu zprávu na stavovém řádku nastavením vlastnosti <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> na `false` (výchozí nastavení) a nastavením vlastnosti <xref:System.Windows.Forms.StatusBar.Text%2A> stavového řádku na text, který se má zobrazit ve stavovém řádku. Stavový řádek můžete rozdělit na panely a zobrazit tak více než jeden typ informací nastavením vlastnosti <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> na `true` a pomocí metody <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím](determine-which-panel-wf-statusbar-control-was-clicked.md)
