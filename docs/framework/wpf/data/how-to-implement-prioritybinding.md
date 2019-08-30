---
title: 'Postupy: Implementace rozhraní PriorityBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: 4be1ce434eb1e169e8a19b56c92ca1efb48773d2
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169090"
---
# <a name="how-to-implement-prioritybinding"></a>Postupy: Implementace rozhraní PriorityBinding
<xref:System.Windows.Data.PriorityBinding>v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sadě Works zadáním seznamu vazeb. Seznam vazeb je seřazen od nejvyšší priority až po nejnižší prioritu. Pokud vazba s nejvyšší prioritou vrátí hodnotu úspěšně při zpracování, pak není nikdy nutné zpracovat ostatní vazby v seznamu. Může se jednat o případ, že je vyhodnocování vazby s nejvyšší prioritou trvat dlouhou dobu, bude použita další nejvyšší priorita, která vrátí hodnotu, dokud vazba s vyšší prioritou nevrátí hodnotu úspěšně.  
  
## <a name="example"></a>Příklad  
 Chcete-li <xref:System.Windows.Data.PriorityBinding> předvést `AsyncDataSource` , jak funguje, objekt byl vytvořen pomocí následujících tří vlastností `FastDP`: `SlowerDP`, a `SlowestDP`.  
  
 Přístupový objekt get objektu `FastDP` vrací hodnotu `_fastDP` datového členu.  
  
 Přístupový objekt `SlowerDP` get pro čeká 3 sekundy před vrácením hodnoty `_slowerDP` datového členu.  
  
 Přístupový objekt `SlowestDP` Get čeká po dobu 5 sekund, než vrátí hodnotu `_slowestDP` datového členu.  
  
> [!NOTE]
> Tento příklad je určen pouze pro demonstrační účely. Pokyny pro rozhraní .NET doporučují před definováním vlastností, které jsou objednávkami s nižšími rozměry, než je sada polí. Další informace naleznete v tématu [Výběr mezi vlastnostmi a metodami](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100)).  
  
 [!code-csharp[PriorityBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 Vlastnost se váže k výše uvedenému `AsyncDS` pomocí <xref:System.Windows.Data.PriorityBinding>: <xref:System.Windows.Controls.TextBlock.Text%2A>  
  
 [!code-xaml[PriorityBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 Když modul vazby zpracovává <xref:System.Windows.Data.Binding> objekty, začíná prvním <xref:System.Windows.Data.Binding>, `SlowestDP` který je vázán na vlastnost. Když je <xref:System.Windows.Data.Binding> tato hodnota zpracována, nevrátí hodnotu úspěšně, protože je pozastavena po dobu 5 sekund, takže <xref:System.Windows.Data.Binding> je zpracován další prvek. Další <xref:System.Windows.Data.Binding> nevrátí hodnotu úspěšně, protože je v režimu spánku po dobu 3 sekund. Modul vazby se pak přesune na další <xref:System.Windows.Data.Binding> prvek, který je svázán `FastDP` s vlastností. <xref:System.Windows.Data.Binding> Vrátí hodnotu "Rychlá hodnota". <xref:System.Windows.Controls.TextBlock> Nyní zobrazí hodnotu "Rychlá hodnota".  
  
 Po 3 sekundách uběhlá `SlowerDP` vlastnost vrátí hodnotu "pomalejší hodnota". <xref:System.Windows.Controls.TextBlock> Pak zobrazí hodnotu "pomalejší hodnota".  
  
 Po uplynutí `SlowestDP` 5 sekund vrátí vlastnost hodnotu nejnižší hodnota. Tato vazba má nejvyšší prioritu, protože je uvedena jako první. <xref:System.Windows.Controls.TextBlock> Nyní zobrazí hodnotu nejnižší hodnota.  
  
 Informace <xref:System.Windows.Data.PriorityBinding> o tom, co se považuje za úspěšnou návratovou hodnotu z vazby, najdete v tématu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>
- [Přehled datových vazeb](data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
