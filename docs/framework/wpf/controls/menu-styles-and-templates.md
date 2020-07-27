---
title: Styly a šablony nabídky
description: Přečtěte si o stylech a šablonách Windows Presentation Foundation ovládacím prvku nabídky. Upravte ControlTemplate tak, aby měl ovládací prvek jedinečný vzhled.
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Menu
- ControlTemplate [WPF], Menu
- Menu [WPF], styles and templates
- states [WPF], Menu
- templates [WPF], Menu
- parts [WPF], Menu
ms.assetid: b89da183-9b87-42c6-ac53-731a42c7b09e
ms.openlocfilehash: 5187e4a479609686e39e043808931141ca52078c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164546"
---
# <a name="menu-styles-and-templates"></a>Styly a šablony nabídky
Toto téma popisuje styly a šablony pro <xref:System.Windows.Controls.Menu> ovládací prvek. Můžete změnit výchozí nastavení <xref:System.Windows.Controls.ControlTemplate> a dát ovládacímu prvku jedinečný vzhled. Další informace najdete v tématu [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="menu-parts"></a>Části nabídky  
 <xref:System.Windows.Controls.Menu>Ovládací prvek nemá žádné pojmenované části.  
  
 Když vytvoříte <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Menu> , může vaše šablona obsahovat <xref:System.Windows.Controls.ItemsPresenter> v <xref:System.Windows.Controls.ScrollViewer> . ( <xref:System.Windows.Controls.ItemsPresenter> Zobrazí všechny položky v <xref:System.Windows.Controls.Menu> ; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v rámci ovládacího prvku).  Pokud <xref:System.Windows.Controls.ItemsPresenter> není přímým podřízeným prvku, je <xref:System.Windows.Controls.ScrollViewer> nutné zadat <xref:System.Windows.Controls.ItemsPresenter> název, `ItemsPresenter` .  
  
## <a name="menu-states"></a>Stavy nabídky  
 V následující tabulce jsou uvedeny vizuální stavy <xref:System.Windows.Controls.Menu> ovládacího prvku.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídu a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojenou vlastnost je `false` .|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Připojená vlastnost má `true` fokus na ovládací prvek.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Připojená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="menuitem-parts"></a>Části MenuItem  
 V následující tabulce jsou uvedeny pojmenované části <xref:System.Windows.Controls.Menu> ovládacího prvku.  
  
|Část|Typ|Popis|  
|-|-|-|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|Oblast pro podnabídku|  
  
 Když vytvoříte <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.MenuItem> , může vaše šablona obsahovat <xref:System.Windows.Controls.ItemsPresenter> v <xref:System.Windows.Controls.ScrollViewer> . ( <xref:System.Windows.Controls.ItemsPresenter> Zobrazí všechny položky v <xref:System.Windows.Controls.MenuItem> ; <xref:System.Windows.Controls.ScrollViewer> umožňuje posouvání v rámci ovládacího prvku).  Pokud <xref:System.Windows.Controls.ItemsPresenter> není přímým podřízeným prvku, je <xref:System.Windows.Controls.ScrollViewer> nutné zadat <xref:System.Windows.Controls.ItemsPresenter> název, `ItemsPresenter` .  
  
## <a name="menuitem-states"></a>Stavy MenuItem  
 V následující tabulce jsou uvedeny vizuální stavy <xref:System.Windows.Controls.MenuItem> ovládacího prvku.  
  
|Název VisualState|Název VisualStateGroup|Popis|  
|-|-|-|  
|Platné|ValidationStates|Ovládací prvek používá <xref:System.Windows.Controls.Validation> třídu a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojenou vlastnost je `false` .|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Připojená vlastnost má `true` fokus na ovládací prvek.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Připojená vlastnost `true` má ovládací prvek nemá fokus.|  
  
## <a name="menu-and-menuitem-controltemplate-example"></a>Příklad nabídky a nabídky MenuItem ControlTemplate  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.Menu> ovládací prvek.  
  
 [!code-xaml[ControlTemplateExamples#Menu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menu)]  
  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.MenuItem> ovládací prvek.  
  
 [!code-xaml[ControlTemplateExamples#MenuItem](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuitem)]  
  
 Následující příklad definuje `MenuScrollViewer` , který je použit v předchozím příkladu.  
  
 [!code-xaml[ControlTemplateExamples#MenuScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuscrollviewer)]  
  
 V <xref:System.Windows.Controls.ControlTemplate> příkladech se používá jeden nebo více následujících zdrojů.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Úplnou ukázku najdete v tématu [stylování s ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styly a šablony ovládacích prvků](control-styles-and-templates.md)
- [Přizpůsobení ovládacího prvku](control-customization.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Vytvoření šablony pro ovládací prvek](../../../desktop-wpf/themes/how-to-create-apply-template.md)
