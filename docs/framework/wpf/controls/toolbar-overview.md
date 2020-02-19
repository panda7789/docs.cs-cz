---
title: ToolBar – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
ms.openlocfilehash: 460d4420d5faf849a8d05a94e0170aea384f69b4
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452692"
---
# <a name="toolbar-overview"></a>ToolBar – přehled
ovládací prvky <xref:System.Windows.Controls.ToolBar> jsou kontejnery pro skupinu příkazů nebo ovládacích prvků, které obvykle souvisejí s jejich funkcí. <xref:System.Windows.Controls.ToolBar> obvykle obsahuje tlačítka, která vyvolávají příkazy.  

<a name="ToolBarControl"></a>   
## <a name="toolbar-control"></a>ToolBar – ovládací prvek  
 Ovládací prvek <xref:System.Windows.Controls.ToolBar> přebírá svůj název z pruhu tlačítek nebo jiných ovládacích prvků na jeden řádek nebo sloupec. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> ovládací prvky poskytují mechanismus přetečení, který umístí všechny položky, které nejsou přirozeně v rámci omezené velikosti <xref:System.Windows.Controls.ToolBar> do speciální oblasti přetečení. Také [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> ovládací prvky se obvykle používají spolu se souvisejícím ovládacím prvkem <xref:System.Windows.Controls.ToolBarTray>, který poskytuje speciální chování rozložení a také podporu pro uživatele iniciující změny velikosti a uspořádání panelů nástrojů.  
  
<a name="Creating_ToolBars"></a>   
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a>Určení pozice panelů nástrojů v ovládacího prvku ToolBarTray  
 Pomocí vlastností <xref:System.Windows.Controls.ToolBar.Band%2A> a <xref:System.Windows.Controls.ToolBar.BandIndex%2A> umístěte <xref:System.Windows.Controls.ToolBar> do <xref:System.Windows.Controls.ToolBarTray>. <xref:System.Windows.Controls.ToolBar.Band%2A> určuje pozici, ve které je <xref:System.Windows.Controls.ToolBar> umístěn v rámci své nadřazené <xref:System.Windows.Controls.ToolBarTray>. <xref:System.Windows.Controls.ToolBar.BandIndex%2A> určuje pořadí, ve kterém se <xref:System.Windows.Controls.ToolBar> umístí do svého pásma. Následující příklad ukazuje, jak použít tuto vlastnost k umístění <xref:System.Windows.Controls.ToolBar> ovládacích prvků uvnitř <xref:System.Windows.Controls.ToolBarTray>.  
  
 [!code-xaml[ToolBarExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>   
## <a name="toolbars-with-overflow-items"></a>Panely nástrojů s položkami přetečení  
 Často <xref:System.Windows.Controls.ToolBar> ovládací prvky obsahují více položek, než lze umístit do velikosti panelu nástrojů. Pokud k tomu dojde, zobrazí <xref:System.Windows.Controls.ToolBar> tlačítko přetečení. Chcete-li zobrazit položky přetečení, uživatel klikne na tlačítko přetečení a položky se zobrazí v překryvném okně pod <xref:System.Windows.Controls.ToolBar>. Následující obrázek ukazuje <xref:System.Windows.Controls.ToolBar> s položkami přetečení:  
  
 ![Snímek obrazovky, který zobrazuje panel nástrojů s položkami přetečení.](./media/toolbar-overview/toolbar-overflow-items.png)  
  
 Můžete určit, kdy se má položka na panelu nástrojů umístit na panel přetečení, nastavením vlastnosti <xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType> připojeno na <xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>, <xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>nebo <xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>. Následující příklad určuje, že poslední čtyři tlačítka na panelu nástrojů by měla být vždy na panelu přetečení.  
  
 [!code-xaml[ToolBarExample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 <xref:System.Windows.Controls.ToolBar> v <xref:System.Windows.Controls.ControlTemplate>používá <xref:System.Windows.Controls.Primitives.ToolBarPanel> a <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>.  <xref:System.Windows.Controls.Primitives.ToolBarPanel> zodpovídá za rozložení položek na panelu nástrojů.  <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> zodpovídá za rozložení položek, které se nevejdou do <xref:System.Windows.Controls.ToolBar>. Příklad <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ToolBar>najdete v tématu.  
  
 [Styly a šablony panelů nástrojů](toolbar-styles-and-templates.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.Primitives.ToolBarPanel>
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>
- [Ovládací prvky stylu na prvku ToolBar](how-to-style-controls-on-a-toolbar.md)
- [Ukázka galerie ovládacích prvků WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
