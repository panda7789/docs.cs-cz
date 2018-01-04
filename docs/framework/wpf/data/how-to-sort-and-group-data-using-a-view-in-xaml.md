---
title: "Postupy: Řazení a seskupení dat použitím zobrazení XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1bfa1941e6352372712debb5a5243bdd24810aac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
