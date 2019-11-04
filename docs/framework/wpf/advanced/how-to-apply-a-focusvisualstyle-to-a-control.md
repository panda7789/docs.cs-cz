---
title: 'Postupy: Použití FocusVisualStyle na ovládací prvek'
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: b44330ee7554f953389556bd62ff49db120b5db9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459817"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a>Postupy: Použití FocusVisualStyle na ovládací prvek
Tento příklad ukazuje, jak vytvořit vizuální styl fokusu v prostředcích a použít styl pro ovládací prvek pomocí vlastnosti <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje styl, který vytváří další skládání ovládacího prvku, který je použit pouze v případě, že je tento ovládací prvek zaměřen na [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. To je dosaženo definováním stylu pomocí <xref:System.Windows.Controls.ControlTemplate>a pak odkazem na tento styl jako prostředek při nastavení vlastnosti <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
 Vnější obdélník, který se podobá ohraničení, je umístěn mimo obdélníkovou oblast. Pokud není jinak změněno, velikost stylu používá <xref:System.Windows.FrameworkElement.ActualHeight%2A> a <xref:System.Windows.FrameworkElement.ActualWidth%2A> obdélníkového ovládacího prvku, kde je použit styl vizuálu fokusu. V tomto příkladu jsou nastaveny záporné hodnoty pro <xref:System.Windows.FrameworkElement.Margin%2A>, aby se ohraničení mírně vytvářely mimo ovládací prvek s fokusem.  
  
 [!code-xaml[FEFocusVisualStyle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> je aditivní pro libovolný styl šablony ovládacího prvku, který se nachází buď z explicitního stylu, nebo stylu motivu. primární styl ovládacího prvku lze stále vytvořit pomocí <xref:System.Windows.Controls.ControlTemplate> a nastavením tohoto stylu na vlastnost <xref:System.Windows.FrameworkElement.Style%2A>.  
  
 Vizuální styly fokusu by se měly používat konzistentně napříč motivem nebo uživatelským rozhraním namísto použití jiného pro každý prvek s fokusem. Podrobnosti najdete v tématu [styly pro fokus v ovládacích prvcích a FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Nastavení stylů pro fokus v ovládacích prvcích a FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md)
