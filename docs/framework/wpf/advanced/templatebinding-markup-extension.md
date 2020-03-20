---
title: TemplateBinding – rozšíření značek
ms.date: 03/30/2017
f1_keywords:
- TemplateBinding
- TemplateBindingExtension
helpviewer_keywords:
- XAML [WPF], TemplateBinding markup extension
- TemplateBinding markup extensions [WPF]
ms.assetid: 1d25bbfc-dbc2-499d-9f12-419d23d4ac6a
ms.openlocfilehash: 8cebbf717f66b072bc84b2068193ff2fe76ea87b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187283"
---
# <a name="templatebinding-markup-extension"></a>TemplateBinding – rozšíření značek
Propojuje hodnotu vlastnosti v šabloně ovládacího prvku s hodnotou jiné vlastnosti ovládacího prvku bez vizuálního vzhledu.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xml  
<object property="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a>Použití atributu XAML (pro vlastnost Setter v šabloně nebo stylu)  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`propertyName`|<xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>vlastnosti nastavené v syntaxi setteru.|  
|`sourceProperty`|Další vlastnost závislosti, která existuje u typu, který <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>je šablonován, určená jeho .<br /><br /> - nebo -<br /><br /> Název vlastnosti specifikovaný s použitím teček, který je definován jiným typem než cílovým typem bez vizuálního vzhledu. To je <xref:System.Windows.PropertyPath>vlastně . Viz [PropertyPath XAML Syntaxe](propertypath-xaml-syntax.md).|  
  
## <a name="remarks"></a>Poznámky  
 A `TemplateBinding` je optimalizovaná forma [vazby](binding-markup-extension.md) pro scénáře šablony, podobně jako `Binding` k vyrobeno s `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=OneWay}`. A `TemplateBinding` je vždy jednosměrná vazba, i v případě, že vlastnosti účastní výchozí obousměrné vazby. Obě vlastnosti musejí být vlastnosti závislostí. Chcete-li dosáhnout obousměrné vazby na šablonovaný nadřazený použít následující příkaz vazby místo `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`.
  
 [RelativeSource](relativesource-markupextension.md) je další rozšíření značky, které se `TemplateBinding` někdy používá ve spojení s nebo místo, aby bylo možné provést relativní vazby vlastností v rámci šablony.  
  
 Popis šablon ovládacích prvku jako koncept zde není popsán; Další informace naleznete [v tématu Ovládací styly a šablony](../controls/control-styles-and-templates.md).  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Token řetězce zadaný `TemplateBinding` po přidělení řetězce <xref:System.Windows.TemplateBindingExtension.Property%2A> identifikátoru jako <xref:System.Windows.TemplateBindingExtension> hodnota základní třídy rozšíření.  
  
 Je možné použít syntaxi elementu objektu, kterou ale neuvádíme, protože nemá žádné reálné použití. `TemplateBinding`se používá k vyplnění hodnot v rámci setters, pomocí `TemplateBinding` vyhodnocených výrazů a pomocí syntaxe elementu objektu pro vyplnění `<Setter.Property>` syntaxe prvku vlastnosti je zbytečně podrobné.  
  
 `TemplateBinding`lze také použít v podrobném použití atributu, který určuje <xref:System.Windows.TemplateBindingExtension.Property%2A> vlastnost jako dvojici vlastností=hodnota:  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné. Protože `TemplateBinding` má pouze jednu vlastnost settable, která je vyžadována, toto podrobné použití není typické.  
  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementaci procesoru XAML zpracování pro toto rozšíření <xref:System.Windows.TemplateBindingExtension> značky je definováno třídou.  
  
 `TemplateBinding`je rozšíření značky. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek v XAML `{` `}` používají znaky a v syntaxi jejich atributu, což je konvence, podle které procesor XAML rozpozná, že rozšíření značek musí atribut zpracovat. Další informace naleznete [v tématu Markup Extensions a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styly a šablony](../controls/styling-and-templating.md)
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
- [RelativeSource MarkupExtension](relativesource-markupextension.md)
- [Rozšíření značek datové vazby](binding-markup-extension.md)
