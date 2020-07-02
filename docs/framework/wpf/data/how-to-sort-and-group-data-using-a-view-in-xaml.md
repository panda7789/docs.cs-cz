---
title: 'Postupy: Řazení a seskupení dat použitím zobrazení XAML'
description: Naučte se vytvořit zobrazení shromažďování dat pro seskupování, řazení a filtrování v Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: a4f8e2de9345dba8e4ea0d3a16a32d57a9adb55c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621675"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a>Postupy: Řazení a seskupení dat použitím zobrazení XAML
Tento příklad ukazuje, jak vytvořit zobrazení shromažďování dat v nástroji [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] . Zobrazení umožňují funkce seskupování, řazení, filtrování a pojmu aktuální položky.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je statický prostředek s názvem *místa* definován jako kolekce objektů typu *místo* , kde každý objekt *umístit* je sestávat z názvu města a stavu. Předpona *Src* je namapována na obor názvů, ve kterém je definováno zdrojové *umístění* zdrojů dat. Předpona *SCM* mapuje na `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` a *dat* mapuje na `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"` .  
  
 Následující příklad vytvoří zobrazení kolekce dat, která je seřazena podle názvu města a seskupena podle stavu.  
  
 [!code-xaml[CollectionViewSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 Zobrazení může být pak zdrojem vazby, jak je znázorněno v následujícím příkladu:  
  
 [!code-xaml[CollectionViewSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 Pro vazby na data XML definovaná v <xref:System.Windows.Data.XmlDataProvider> prostředku předchází název XML symbolem @.  
  
 [!code-xaml[CollectionViewSource#XDPChunk](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.CollectionViewSource>
- [Získat výchozí zobrazení shromažďování dat](how-to-get-the-default-view-of-a-data-collection.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [– postupy](data-binding-how-to-topics.md)
