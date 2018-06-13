---
title: 'Postupy: Implementace rozhraní PriorityBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: cf0ed5c2b55358d3a583ac89e307b23b3ab08a9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557755"
---
# <a name="how-to-implement-prioritybinding"></a>Postupy: Implementace rozhraní PriorityBinding
<xref:System.Windows.Data.PriorityBinding> v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funguje tak, že zadáte seznam vazeb. Seznam vazeb je nejnižší priorita seřazena z nejvyšší prioritou. Jestliže nejvyšší prioritou vazby vrací hodnotu úspěšně při zpracování nejsou nikdy potřeba zpracovat vazby v seznamu. Může to být případě, že nejvyšší prioritou vazby trvá dlouhou dobu k vyhodnocení, další nejvyšší prioritou, která vrátí hodnotu úspěšně bude používat, dokud vazbu s vyšší prioritou vrací hodnotu úspěšně.  
  
## <a name="example"></a>Příklad  
 K předvedení způsobu <xref:System.Windows.Data.PriorityBinding> funguje, `AsyncDataSource` objekt byl vytvořen s následujícími třemi vlastnostmi: `FastDP`, `SlowerDP`, a `SlowestDP`.  
  
 Přistupující objekt get z `FastDP` vrací hodnotu `_fastDP` – datový člen.  
  
 Přistupující objekt get z `SlowerDP` čeká 3 sekund před vrácením hodnotu `_slowerDP` – datový člen.  
  
 Přistupující objekt get z `SlowestDP` čeká na 5 sekund před vrácením hodnotu `_slowestDP` – datový člen.  
  
> [!NOTE]
>  V tomto příkladu je pouze pro demonstrační účely. [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] Pokyny nedoporučujeme definování vlastností, které jsou pořadí podle velikosti pomalejší, než by bylo pole sady. Další informace najdete v tématu [NIB: výběr mezi vlastnosti a metody](http://msdn.microsoft.com/library/55825e8f-7e2e-448a-9505-7217cc91b1af).  
  
 [!code-csharp[PriorityBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <xref:System.Windows.Controls.TextBlock.Text%2A> Vlastnost váže k výše `AsyncDS` pomocí <xref:System.Windows.Data.PriorityBinding>:  
  
 [!code-xaml[PriorityBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 Když modul vazby zpracovává <xref:System.Windows.Data.Binding> objekty, začíná prvním <xref:System.Windows.Data.Binding>, která je vázána `SlowestDP` vlastnost. Pokud to <xref:System.Windows.Data.Binding> je zpracování nevrátí hodnotu úspěšně vzhledem k tomu, že ho je v režimu spánku po dobu 5 sekund, takže další <xref:System.Windows.Data.Binding> zpracování elementu. Další <xref:System.Windows.Data.Binding> nevrátí hodnotu úspěšně vzhledem k tomu, že je pozastaveno pro 3 sekund. Modul vazby pak se posouvá do další <xref:System.Windows.Data.Binding> element, který je vázána `FastDP` vlastnost. To <xref:System.Windows.Data.Binding> vrátí hodnotu "Rychlé hodnota". <xref:System.Windows.Controls.TextBlock> Teď zobrazuje hodnotu "Rychlé hodnota".  
  
 Po uplynutí 3 sekund `SlowerDP` vlastnost vrací hodnotu "Nižší hodnota". <xref:System.Windows.Controls.TextBlock> Pak zobrazí hodnotu "Nižší hodnota".  
  
 Po uplynutí 5 sekund `SlowestDP` vlastnost vrací hodnotu "Nejpomalejší hodnota". Této vazby má nejvyšší prioritu, protože je uvedená jako první. <xref:System.Windows.Controls.TextBlock> Teď zobrazuje hodnotu "Nejpomalejší hodnota".  
  
 V tématu <xref:System.Windows.Data.PriorityBinding> informace o co se považuje za úspěšné vrácená hodnota z vazbu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
