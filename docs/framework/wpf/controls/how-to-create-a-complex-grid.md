---
title: 'Postupy: Vytvoření komplexní mřížky'
ms.date: 03/30/2017
helpviewer_keywords:
- calendar [WPF], creating
- monthly calendar [WPF], creating
- Grid control [WPF], creating [WPF], complex grid
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
ms.openlocfilehash: 49bf9781d56b93fd4529f3c9b62deb171e69155f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553592"
---
# <a name="how-to-create-a-complex-grid"></a>Postupy: Vytvoření komplexní mřížky
Tento příklad ukazuje, jak používat <xref:System.Windows.Controls.Grid> pro vytvoření rozložení, který může vypadat měsíční kalendář.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje osm řádků a sloupců osm pomocí <xref:System.Windows.Controls.RowDefinition> a <xref:System.Windows.Controls.ColumnDefinition> třídy. Použije <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> a <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> přidružené vlastnosti, společně s <xref:System.Windows.Shapes.Rectangle> prvky, které výplně pozadí různých sloupců a řádků. Tento návrh je možné, protože může existovat více než jeden element v jednotlivých buněk <xref:System.Windows.Controls.Grid>, Princip rozdíl mezi <xref:System.Windows.Controls.Grid> a <xref:System.Windows.Documents.Table>.  
  
 Tento příklad používá přechody vertikální k <xref:System.Windows.Shapes.Shape.Fill%2A> sloupců a řádků za účelem zlepšení vizuální prezentaci a čitelnost kalendáře. Ve <xref:System.Windows.Controls.TextBlock> elementy reprezentují kalendářních dat a dny v týdnu. <xref:System.Windows.Controls.TextBlock> elementy jsou absolutně umístěny v rámci své buňky pomocí <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost a zarovnání vlastnosti, které jsou definovány v rámci styl pro aplikaci.  
  
 [!code-xaml[GridComplex#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Documents.TableCell>  
 [Přehled malování plnými barvami a přechody](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Přehled panelu](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Přehled tabulky](../../../../docs/framework/wpf/advanced/table-overview.md)
