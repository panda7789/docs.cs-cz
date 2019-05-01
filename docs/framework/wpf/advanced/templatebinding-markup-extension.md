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
ms.openlocfilehash: c004560a0b7ab367fbf4fbb48b0e8d8b63f3d8f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053038"
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
|`propertyName`|<xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> vlastnosti, která je nastavena v syntaxi setter.|  
|`sourceProperty`|Další vlastnost závislosti, která existuje pro typ bez vizuálního vzhledu, určená jeho <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.<br /><br /> - nebo -<br /><br /> Název vlastnosti specifikovaný s použitím teček, který je definován jiným typem než cílovým typem bez vizuálního vzhledu. Ve skutečnosti se jedná <xref:System.Windows.PropertyPath>. Zobrazit [syntaxe PropertyPath XAML](propertypath-xaml-syntax.md).|  
  
## <a name="remarks"></a>Poznámky  
 A `TemplateBinding` je optimalizovaná forma [vazby](binding-markup-extension.md) pro šablony je analogická `Binding` zkonstruován pomocí `{Binding RelativeSource={RelativeSource TemplatedParent}}`. A `TemplateBinding` je vždy jednosměrná vazba, i když příslušné vlastnosti ve výchozím nastavení používají obousměrné vazby. Obě vlastnosti musejí být vlastnosti závislostí. Abyste dosáhli Obousměrná vazba nadřazenému prvku bez vizuálního vzhledu použijte následující příkaz vazby `{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`. 
  
 [RelativeSource](relativesource-markupextension.md) je další rozšíření značek, které se někdy používá ve spojení s nebo namísto něj `TemplateBinding` účelem vytvoření relativní vazby vlastností v rámci šablony.  
  
 Popis šablon ovládacích prvků jako koncept není součástí tohoto Další informace najdete v tématu [– styly ovládacích prvků a šablon](../controls/control-styles-and-templates.md).  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Řetězec s tokenem uvedený za `TemplateBinding` řetězec identifikátoru je přiřazen jako <xref:System.Windows.TemplateBindingExtension.Property%2A> hodnoty základního <xref:System.Windows.TemplateBindingExtension> rozšíření třídy.  
  
 Je možné použít syntaxi elementu objektu, kterou ale neuvádíme, protože nemá žádné reálné použití. `TemplateBinding` slouží k naplnění hodnot v rámci elementů setter pomocí vyhodnocení výrazů a použití syntaxe elementu objektu pro `TemplateBinding` tak, aby vyplnil `<Setter.Property>` syntax prvku vlastnosti je zbytečné.  
  
 `TemplateBinding` je také možné využití podrobné atribut, který určuje <xref:System.Windows.TemplateBindingExtension.Property%2A> vlastnost jako vlastnost = hodnota pár:  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné. Protože `TemplateBinding` má jen jednu nastavitelnou vlastnost, která je požadována, toto použití podrobné syntaxe není typické.  
  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementaci procesoru XAML je zpracování tohoto rozšíření značek je určené <xref:System.Windows.TemplateBindingExtension> třídy.  
  
 `TemplateBinding` je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek XAML používá `{` a `}` znaků v syntaxi atributu, což je konvence, podle kterého na procesor XAML rozpozná, že rozšíření značek musí zpracovat atribut. Další informace najdete v tématu [– rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styly a šablony](../controls/styling-and-templating.md)
- [Přehled XAML (WPF)](xaml-overview-wpf.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Rozšíření značek RelativeSource](relativesource-markupextension.md)
- [Rozšíření značek datové vazby](binding-markup-extension.md)
