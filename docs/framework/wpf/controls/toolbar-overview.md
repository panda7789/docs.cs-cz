---
title: "ToolBar – přehled"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f00597d48ff100325c1fb2884f64169164415a50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="toolbar-overview"></a>ToolBar – přehled
<xref:System.Windows.Controls.ToolBar>ovládací prvky jsou kontejnery pro skupinu příkazy nebo ovládací prvky, které jsou obvykle spojené v jejich funkce. A <xref:System.Windows.Controls.ToolBar> obvykle obsahuje tlačítka, pomocí kterých volat příkazy.  
  
  
<a name="ToolBarControl"></a>   
## <a name="toolbar-control"></a>ToolBar – ovládací prvek  
 <xref:System.Windows.Controls.ToolBar> Řízení trvá jeho název z panelu jako uspořádání tlačítek a jiných ovládacích prvků do jednoho řádku nebo sloupce. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.ToolBar> ovládací prvky poskytují mechanismus přetečení, který nahradí všechny položky, které se přirozeně nevejdou v rámci velikost omezené <xref:System.Windows.Controls.ToolBar> do oblasti speciální přetečení. Navíc [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> ovládací prvky se obvykle používají s související <xref:System.Windows.Controls.ToolBarTray> řízení, které poskytuje chování zvláštní rozložení, stejně jako podporu pro uživatel spustil velikost a uspořádání panelů nástrojů.  
  
<a name="Creating_ToolBars"></a>   
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a>Určení v ToolBarTray pozici panelů nástrojů  
 Použití <xref:System.Windows.Controls.ToolBar.Band%2A> a <xref:System.Windows.Controls.ToolBar.BandIndex%2A> vlastnosti, které chcete umístit <xref:System.Windows.Controls.ToolBar> v <xref:System.Windows.Controls.ToolBarTray>. <xref:System.Windows.Controls.ToolBar.Band%2A>Určuje pozici, ve kterém <xref:System.Windows.Controls.ToolBar> je umístěn v rámci nadřazené <xref:System.Windows.Controls.ToolBarTray>. <xref:System.Windows.Controls.ToolBar.BandIndex%2A>Určuje, v jakém pořadí <xref:System.Windows.Controls.ToolBar> je umístěn v rámci jeho vzdálené správy. Následující příklad ukazuje, jak použít tuto vlastnost umístit <xref:System.Windows.Controls.ToolBar> uvnitř ovládací prvky <xref:System.Windows.Controls.ToolBarTray>.  
  
 [!code-xaml[ToolBarExample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>   
## <a name="toolbars-with-overflow-items"></a>Panely nástrojů s položkami přetečení  
 Často <xref:System.Windows.Controls.ToolBar> ovládací prvky obsahují více položek, než můžete začlenit do velikosti panelu nástrojů. V takovém případě <xref:System.Windows.Controls.ToolBar> zobrazí tlačítko přetečení. Zobrazit položky přetečení, uživatel klikne na tlačítko přetečení a položky, které se zobrazí v místním okně níže <xref:System.Windows.Controls.ToolBar>. Následující grafické ukazuje <xref:System.Windows.Controls.ToolBar> s položkami přetečení.  
  
 ![Panel nástrojů s přetečení](../../../../docs/framework/wpf/controls/media/toolbarwithoverflowitem.png "ToolbarWithOverflowItem")  
Panel nástrojů s položkami přetečení  
  
 Můžete zadat, pokud je uskutečněn položku na panelu nástrojů na panelu přetečení nastavením <xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType> přidružená vlastnost k <xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>, <xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>, nebo <xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>. Následující příklad určuje, že poslední čtyři tlačítek na panelu nástrojů by měla být vždy na panelu přetečení.  
  
 [!code-xaml[ToolBarExample#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 <xref:System.Windows.Controls.ToolBar> Používá <xref:System.Windows.Controls.Primitives.ToolBarPanel> a <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> v jeho <xref:System.Windows.Controls.ControlTemplate>.  <xref:System.Windows.Controls.Primitives.ToolBarPanel> Zodpovídá za rozložení položek na panelu nástrojů.  <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> Zodpovídá za rozložení položek, které se nehodí na <xref:System.Windows.Controls.ToolBar>. Příklad <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.ToolBar>, najdete v části  
  
 [ToolBar – styly prvků a šablony](../../../../docs/framework/wpf/controls/toolbar-styles-and-templates.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
 <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
 [Ovládací prvky stylu na prvku ToolBar](../../../../docs/framework/wpf/controls/how-to-style-controls-on-a-toolbar.md)  
 [Ukázka galerie ovládacích prvků grafického subsystému WPF](http://go.microsoft.com/fwlink/?LinkID=160053)
