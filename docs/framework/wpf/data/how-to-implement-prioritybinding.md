---
title: 'Postupy: Implementace rozhraní PriorityBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: 343b0aca4736905f3a0cbff5a0f76b170da0c920
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459783"
---
# <a name="how-to-implement-prioritybinding"></a>Postupy: Implementace rozhraní PriorityBinding
<xref:System.Windows.Data.PriorityBinding> v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funguje tak, že se určí seznam vazeb. Seznam vazeb je seřazen od nejvyšší priority až po nejnižší prioritu. Pokud vazba s nejvyšší prioritou vrátí hodnotu úspěšně při zpracování, pak není nikdy nutné zpracovat ostatní vazby v seznamu. Může se jednat o případ, že je vyhodnocování vazby s nejvyšší prioritou trvat dlouhou dobu, bude použita další nejvyšší priorita, která vrátí hodnotu, dokud vazba s vyšší prioritou nevrátí hodnotu úspěšně.  
  
## <a name="example"></a>Příklad  
 Chcete-li předvést, jak <xref:System.Windows.Data.PriorityBinding> funguje, byl vytvořen objekt `AsyncDataSource` pomocí následujících tří vlastností: `FastDP`, `SlowerDP`a `SlowestDP`.  
  
 Přistupující objekt get pro `FastDP` vrací hodnotu datového členu `_fastDP`.  
  
 Přistupující objekt get pro `SlowerDP` čeká 3 sekundy před vrácením hodnoty datového členu `_slowerDP`.  
  
 Přistupující objekt get pro `SlowestDP` čeká 5 sekund před vrácením hodnoty datového členu `_slowestDP`.  
  
> [!NOTE]
> Tento příklad je určen pouze pro demonstrační účely. Pokyny pro rozhraní .NET doporučují před definováním vlastností, které jsou objednávkami s nižšími rozměry, než je sada polí. Další informace naleznete v tématu [Výběr mezi vlastnostmi a metodami](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100)).  
  
 [!code-csharp[PriorityBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 Vlastnost <xref:System.Windows.Controls.TextBlock.Text%2A> se váže k výše uvedenému `AsyncDS` pomocí <xref:System.Windows.Data.PriorityBinding>:  
  
 [!code-xaml[PriorityBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 Když modul vazby zpracovává objekty <xref:System.Windows.Data.Binding>, začíná prvním <xref:System.Windows.Data.Binding>, která je svázána s vlastností `SlowestDP`. Při zpracování tohoto <xref:System.Windows.Data.Binding> nevrátí hodnotu úspěšně, protože je v režimu spánku po dobu 5 sekund, takže se zpracuje další prvek <xref:System.Windows.Data.Binding>. Následující <xref:System.Windows.Data.Binding> nevrátí hodnotu úspěšně, protože je v režimu spánku po dobu 3 sekund. Modul vazby se pak přesune na další <xref:System.Windows.Data.Binding> element, který je svázán s vlastností `FastDP`. Tato <xref:System.Windows.Data.Binding> vrátí hodnotu "Rychlá hodnota". <xref:System.Windows.Controls.TextBlock> nyní zobrazí hodnotu "Rychlá hodnota".  
  
 Po 3 sekundách uplynou vlastnost `SlowerDP` vrátí hodnotu "pomalejší hodnota". <xref:System.Windows.Controls.TextBlock> pak zobrazí hodnotu "pomalejší hodnota".  
  
 Po uplynutí 5 sekund vrátí vlastnost `SlowestDP` hodnotu nejnižší hodnota. Tato vazba má nejvyšší prioritu, protože je uvedena jako první. <xref:System.Windows.Controls.TextBlock> nyní zobrazuje hodnotu nejpomalejších hodnot.  
  
 Informace o tom, co se považuje za úspěšnou návratovou hodnotu z vazby, najdete v tématu <xref:System.Windows.Data.PriorityBinding>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
