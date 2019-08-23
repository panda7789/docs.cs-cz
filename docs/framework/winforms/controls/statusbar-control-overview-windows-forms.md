---
title: StatusBar – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: bd58d4c70e3a3c88e57fe242957f669d1944fd71
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964426"
---
# <a name="statusbar-control-overview-windows-forms"></a>StatusBar – přehled ovládacího prvku (Windows Forms)
> [!IMPORTANT]
> <xref:System.Windows.Forms.ToolStripStatusLabel> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel> <xref:System.Windows.Forms.StatusBarPanel> Ovládací prvky <xref:System.Windows.Forms.StatusStrip> a nahrazují<xref:System.Windows.Forms.StatusBar> a přidávají funkce ovládacím prvkům a; ovládací prvky a jsou však uchovávány pro zpětnou kompatibilitu i pro budoucí použití, pokud výběrem.  
  
 [Ovládací prvek](statusbar-control-windows-forms.md) model Windows Forms stavový řádek se používá ve formulářích jako oblast, obvykle se zobrazuje v dolní části okna, kde aplikace může zobrazit různé druhy informací o stavu. <xref:System.Windows.Forms.StatusBar>ovládací prvky mohou mít panely na stavovém řádku, které zobrazují text nebo ikony k označení stavu nebo řady ikon v animaci, která indikuje, že proces pracuje. například Microsoft Word značí, že se dokument ukládá.  
  
## <a name="using-the-statusbar-control"></a>Použití ovládacího prvku stavový řádek  
 Internet Explorer používá stavový řádek k označení adresy URL stránky, když se ukazatel myši přesune na hypertextový odkaz. V aplikaci Microsoft Word získáte informace o umístění stránky, umístění oddílu a režimech úprav, například přepisu a sledování revizí. a Visual Studio používá stavový řádek k poskytnutí kontextově citlivých informací, jako je například oznámení, jak pracovat s ukotvit okny buď jako docked, nebo float.  
  
 Můžete zobrazit jednu zprávu na stavovém řádku <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> nastavením vlastnosti na `false` ( <xref:System.Windows.Forms.StatusBar.Text%2A> výchozí) a nastavením vlastnosti stavového řádku na text, který se má zobrazit ve stavovém řádku. Stavový řádek můžete rozdělit na panely, aby se zobrazil více než jeden <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> typ informací nastavením vlastnosti na `true` <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>a pomocí <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> metody.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Postupy: Určete, na který panel model Windows Forms ovládací prvek stavový řádek.](determine-which-panel-wf-statusbar-control-was-clicked.md)
