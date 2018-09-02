---
title: ToolBar – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
ms.openlocfilehash: 816ac0d81ddcaa461a842c0f69fe5ed5b21a32d1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43466281"
---
# <a name="toolbar-overview"></a>ToolBar – přehled
<xref:System.Windows.Controls.ToolBar> ovládací prvky jsou kontejnery pro skupinu příkazů nebo ovládacích prvků, které jsou obvykle související funkce. A <xref:System.Windows.Controls.ToolBar> obvykle obsahuje tlačítka, pomocí kterých vyvolat příkazy.  
  
  
<a name="ToolBarControl"></a>   
## <a name="toolbar-control"></a>ToolBar – ovládací prvek  
 <xref:System.Windows.Controls.ToolBar> Ovládací prvek získá jeho název z panelu jako uspořádání tlačítek nebo jiných ovládacích prvků do jednoho řádku nebo sloupce. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> ovládací prvky poskytují přetečení mechanismus, který nahradí všechny položky, které se přirozeně nevejdou do velikosti omezen <xref:System.Windows.Controls.ToolBar> do oblasti speciální přetečení. Navíc [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> se obvykle používají ovládací prvky s související <xref:System.Windows.Controls.ToolBarTray> ovládací prvek, který poskytuje chování zvláštní rozložení, jakož i podporu pro uživatelem iniciované velikost a uspořádání panelů nástrojů.  
  
<a name="Creating_ToolBars"></a>   
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a>V ToolBarTray určující pozici panelů nástrojů  
 Použití <xref:System.Windows.Controls.ToolBar.Band%2A> a <xref:System.Windows.Controls.ToolBar.BandIndex%2A> vlastnosti, které chcete umístit <xref:System.Windows.Controls.ToolBar> v <xref:System.Windows.Controls.ToolBarTray>. <xref:System.Windows.Controls.ToolBar.Band%2A> Určuje umístění, ve kterém <xref:System.Windows.Controls.ToolBar> je umístěn v rámci svého nadřazeného objektu <xref:System.Windows.Controls.ToolBarTray>. <xref:System.Windows.Controls.ToolBar.BandIndex%2A> Určuje pořadí, ve kterém <xref:System.Windows.Controls.ToolBar> je umístěn v rámci jeho obsluhy vzdálené správy. Následující příklad ukazuje, jak použít tuto vlastnost umístit <xref:System.Windows.Controls.ToolBar> ovládací prvky uvnitř <xref:System.Windows.Controls.ToolBarTray>.  
  
 [!code-xaml[ToolBarExample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>   
## <a name="toolbars-with-overflow-items"></a>Panely nástrojů s položkami přetečení  
 Často <xref:System.Windows.Controls.ToolBar> ovládací prvky obsahovat více položek, než se vejde do velikosti panelu nástrojů. Pokud k tomu dojde, <xref:System.Windows.Controls.ToolBar> zobrazí tlačítku přetečení. Chcete-li zobrazit položky přetečení, uživatel klikne na tlačítko přetečení a položky jsou uvedeny v následující automaticky otevírané okno <xref:System.Windows.Controls.ToolBar>. Následující grafické ukazuje <xref:System.Windows.Controls.ToolBar> s položkami přetečení.  
  
 ![Panel nástrojů s přetečením](../../../../docs/framework/wpf/controls/media/toolbarwithoverflowitem.png "ToolbarWithOverflowItem")  
Panel nástrojů s položkami přetečení  
  
 Můžete zadat, pokud je uskutečněn položky na panelu nástrojů na panelu přetečení tak, že nastavíte <xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType> připojené vlastnosti <xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>, <xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>, nebo <xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>. Následující příklad určuje, že poslední čtyři tlačítka na panelu nástrojů by měla být vždy v panelu přetečení.  
  
 [!code-xaml[ToolBarExample#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 <xref:System.Windows.Controls.ToolBar> Používá <xref:System.Windows.Controls.Primitives.ToolBarPanel> a <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> v jeho <xref:System.Windows.Controls.ControlTemplate>.  <xref:System.Windows.Controls.Primitives.ToolBarPanel> Zodpovídá za rozložení položek na panelu nástrojů.  <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> Je zodpovědná za položky, které se nevejdou na rozložení <xref:System.Windows.Controls.ToolBar>. Příklad <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ToolBar>, naleznete v tématu  
  
 [ToolBar – styly a šablony](../../../../docs/framework/wpf/controls/toolbar-styles-and-templates.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
 <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
 [Ovládací prvky stylu na prvku ToolBar](../../../../docs/framework/wpf/controls/how-to-style-controls-on-a-toolbar.md)  
 [Ukázková galerie ovládacích prvků WPF](https://go.microsoft.com/fwlink/?LinkID=160053)
