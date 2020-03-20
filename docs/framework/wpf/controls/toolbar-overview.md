---
title: ToolBar – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
ms.openlocfilehash: b5498b8b88c7403ffe51256a57544261de3ace08
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186616"
---
# <a name="toolbar-overview"></a>ToolBar – přehled
<xref:System.Windows.Controls.ToolBar>ovládací prvky jsou kontejnery pro skupinu příkazů nebo ovládacích prvků, které jsou obvykle související v jejich funkci. Obvykle <xref:System.Windows.Controls.ToolBar> obsahuje tlačítka, která vyvolávají příkazy.  

<a name="ToolBarControl"></a>
## <a name="toolbar-control"></a>ToolBar – ovládací prvek  
 Ovládací <xref:System.Windows.Controls.ToolBar> prvek přenese svůj název z bar-jako uspořádání tlačítek nebo jiných ovládacích prvků do jednoho řádku nebo sloupce. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.ToolBar> ovládací prvky poskytují mechanismus přetečení, který umísťuje <xref:System.Windows.Controls.ToolBar> všechny položky, které se přirozeně nevejdou do velikosti omezené, do zvláštní oblasti přetečení. Ovládací prvky se také <xref:System.Windows.Controls.ToolBarTray> obvykle používají s souvisejícím ovládacím prvkem, který poskytuje speciální chování rozložení, stejně jako podporu pro uživatelem iniciované změny velikosti a uspořádání panelů nástrojů. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar>  
  
<a name="Creating_ToolBars"></a>
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a>Určení umístění panelů nástrojů v panelu nástrojů  
 Pomocí <xref:System.Windows.Controls.ToolBar.Band%2A> vlastností a <xref:System.Windows.Controls.ToolBar.BandIndex%2A> <xref:System.Windows.Controls.ToolBar> umístěte <xref:System.Windows.Controls.ToolBarTray>v . <xref:System.Windows.Controls.ToolBar.Band%2A>označuje pozici, ve <xref:System.Windows.Controls.ToolBar> které je <xref:System.Windows.Controls.ToolBarTray>umístěn v rámci svého mateřského . <xref:System.Windows.Controls.ToolBar.BandIndex%2A>označuje pořadí, ve <xref:System.Windows.Controls.ToolBar> kterém je umístěn v jeho pásmu. Následující příklad ukazuje, jak použít <xref:System.Windows.Controls.ToolBar> tuto <xref:System.Windows.Controls.ToolBarTray>vlastnost k umístění ovládacích prvků uvnitř .  
  
 [!code-xaml[ToolBarExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>
## <a name="toolbars-with-overflow-items"></a>Panely nástrojů s položkami přetečení  
 Ovládací <xref:System.Windows.Controls.ToolBar> prvky často obsahují více položek, než se vejde do velikosti panelu nástrojů. V takovém případě <xref:System.Windows.Controls.ToolBar> se zobrazí tlačítko přetečení. Chcete-li zobrazit položky přetečení, uživatel klepne na tlačítko přetečení a <xref:System.Windows.Controls.ToolBar>položky jsou zobrazeny v rozbalovacím okně pod . Následující obrázek <xref:System.Windows.Controls.ToolBar> znázorňuje položky s přetečením:  
  
 ![Snímek obrazovky, který zobrazuje panel nástrojů s přetečením položek.](./media/toolbar-overview/toolbar-overflow-items.png)  
  
 Můžete určit, kdy bude položka na panelu nástrojů umístěna <xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType> na panelu přetečení, nastavením připojené vlastnosti na <xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>, <xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>, nebo <xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>. Následující příklad určuje, že poslední čtyři tlačítka na panelu nástrojů by měla být vždy na panelu přetečení.  
  
 [!code-xaml[ToolBarExample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 Použití <xref:System.Windows.Controls.ToolBar> <xref:System.Windows.Controls.Primitives.ToolBarPanel> a a <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> v <xref:System.Windows.Controls.ControlTemplate>jeho .  Je <xref:System.Windows.Controls.Primitives.ToolBarPanel> zodpovědný za rozložení položek na panelu nástrojů.  Je <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> zodpovědný za rozložení položek, které se <xref:System.Windows.Controls.ToolBar>nevejdou na rozhraní . Příklad <xref:System.Windows.Controls.ControlTemplate> a <xref:System.Windows.Controls.ToolBar>for , viz  
  
 [Styly a šablony panelu nástrojů](toolbar-styles-and-templates.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.Primitives.ToolBarPanel>
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>
- [Ovládací prvky stylu na prvku ToolBar](how-to-style-controls-on-a-toolbar.md)
- [Ukázka galerie ovládacích prvků WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
