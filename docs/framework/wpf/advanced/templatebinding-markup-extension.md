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
ms.openlocfilehash: 399e4ac223d2fcb728ece2c92d25a087990992f2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458667"
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
|`propertyName`|<xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> vlastnosti nastavené v syntaxi setter.|  
|`sourceProperty`|Další vlastnost závislosti, která existuje pro typ se šablonou, určená jeho <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.<br /><br /> ani<br /><br /> Název vlastnosti specifikovaný s použitím teček, který je definován jiným typem než cílovým typem bez vizuálního vzhledu. Toto je ve skutečnosti <xref:System.Windows.PropertyPath>. Viz [syntaxe jazyka XAML pro PropertyPath](propertypath-xaml-syntax.md).|  
  
## <a name="remarks"></a>Poznámky  
 `TemplateBinding` je optimalizovaná forma [vazby](binding-markup-extension.md) pro scénáře šablon, která je podobná `Binding` vytvořená pomocí `{Binding RelativeSource={RelativeSource TemplatedParent}}`. `TemplateBinding` je vždy jednosměrná vazba, a to i v případě, že vlastnosti použité jako výchozí jsou obousměrné vazby. Obě vlastnosti musejí být vlastnosti závislostí. Aby bylo možné dosáhnout obousměrné vazby k nadřazenému objektu, použijte následující příkaz vazby místo `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`. 
  
 [RelativeSource](relativesource-markupextension.md) je další rozšíření značek, které se někdy používá ve spojení s nebo místo `TemplateBinding`, aby bylo možné provést relativní vazbu vlastnosti v rámci šablony.  
  
 Popis šablon ovládacích prvků v rámci konceptu se zde nezabývá; Další informace najdete v tématu [styly a šablony ovládacích prvků](../controls/control-styles-and-templates.md).  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Token řetězce poskytnutý po řetězci `TemplateBinding` identifikátoru je přiřazen jako hodnota <xref:System.Windows.TemplateBindingExtension.Property%2A> základní třídy rozšíření <xref:System.Windows.TemplateBindingExtension>.  
  
 Je možné použít syntaxi elementu objektu, kterou ale neuvádíme, protože nemá žádné reálné použití. `TemplateBinding` slouží k vyplňování hodnot v rámci setter, pomocí vyhodnocených výrazů a použití syntaxe elementů objektu pro `TemplateBinding` k vyplnění `<Setter.Property>` syntaxe elementu vlastnosti není nutně podrobná.  
  
 `TemplateBinding` lze také použít v podrobném použití atributu, které určuje vlastnost <xref:System.Windows.TemplateBindingExtension.Property%2A> jako dvojici vlastnost = hodnota:  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné. Protože `TemplateBinding` má pouze jednu nastavitelnou vlastnost, která je povinná, toto podrobné použití není typické.  
  
 V implementaci procesoru [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML je zpracování tohoto rozšíření značek definováno třídou <xref:System.Windows.TemplateBindingExtension>.  
  
 `TemplateBinding` je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek v jazyce XAML používají ve své syntaxi atributu `{` a `}` znaky, což je konvence, pomocí níž procesor XAML rozpozná, že musí zpracovat atribut rozšíření značek. Další informace naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styly a šablony](../controls/styling-and-templating.md)
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Rozšíření značek RelativeSource](relativesource-markupextension.md)
- [Rozšíření značek datové vazby](binding-markup-extension.md)
