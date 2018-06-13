---
title: 'Postupy: Řazení a seskupení dat použitím zobrazení XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], grouping data in views in XAML
- XAML [WPF], sorting data in views
- grouping data in views in XAML [WPF]
- data binding [WPF], sorting data in views in XAML
- sorting data in views in XAML [WPF]
- XAML [WPF], grouping data in views
- views [WPF], sorting data
- views [WPF], grouping data
ms.assetid: 145c8c3f-dbdd-4d0d-816f-90b35eba7eda
ms.openlocfilehash: 80529420bcc5fdca473313e164b3d096732953f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555825"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a>Postupy: Řazení a seskupení dat použitím zobrazení XAML
Tento příklad ukazuje, jak vytvořit zobrazení shromažďování dat v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Zobrazení umožňují funkce seskupování, řazení a filtrování a představu o aktuální položky.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu, statické prostředků s názvem *umístí* je definována jako kolekce *místní* objekty, kde každá *místní* objekt se skládal z název města a stav. Předpona *src* je namapovaný na obor názvů kde zdroj dat *místech* je definována. Předpona *scm* mapuje `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` a *dat* mapuje `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.  
  
 Následující příklad vytvoří zobrazení shromažďování dat, který je seřazené podle názvu města a seskupené podle stavu.  
  
 [!code-xaml[CollectionViewSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 Zobrazení pak může být zdrojem vazby, jako v následujícím příkladu:  
  
 [!code-xaml[CollectionViewSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 Pro vazby na data XML, které jsou definované v <xref:System.Windows.Data.XmlDataProvider> prostředků, zadejte před název XML @ symbol.  
  
 [!code-xaml[CollectionViewSource#XDPChunk](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Data.CollectionViewSource>  
 [Načtení výchozího zobrazení datové kolekce](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
