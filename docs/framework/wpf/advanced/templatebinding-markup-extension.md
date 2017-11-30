---
title: "TemplateBinding – rozšíření značek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TemplateBinding
- TemplateBindingExtension
helpviewer_keywords:
- XAML [WPF], TemplateBinding markup extension
- TemplateBinding markup extensions [WPF]
ms.assetid: 1d25bbfc-dbc2-499d-9f12-419d23d4ac6a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ab8645de78a79f4bd47fa436699af002db99b9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
|`propertyName`|<xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>vlastnosti se nastavuje v syntaxi setter.|  
|`sourceProperty`|Další závislosti vlastnost, která existuje v typu probíhá podle šablony, určeného jeho <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>.<br /><br /> - nebo -<br /><br /> Název vlastnosti specifikovaný s použitím teček, který je definován jiným typem než cílovým typem bez vizuálního vzhledu. Toto je ve skutečnosti <xref:System.Windows.PropertyPath>. V tématu [syntaxe PropertyPath XAML](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).|  
  
## <a name="remarks"></a>Poznámky  
 A `TemplateBinding` optimalizované formu [vazby](../../../../docs/framework/wpf/advanced/binding-markup-extension.md) pro scénáře šablon, podobá `Binding` zkonstruovat s `{Binding RelativeSource={RelativeSource TemplatedParent}}`. A `TemplateBinding` je vždy jednosměrný vazbu, i v případě, že vlastnosti podílejí výchozí nastavení vazba obousměrná. Obě vlastnosti musejí být vlastnosti závislostí.  
  
 [RelativeSource](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md) je jiné rozšíření značek, které se někdy používá ve spojení s nebo místo `TemplateBinding` za účelem provedení relativní vlastnost vazbu v rámci šablony.  
  
 Popisující šablon ovládacích prvků jako koncept neplatí zde; Další informace najdete v tématu [– styly ovládacích prvků a šablony](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Token řetězec zadaný po `TemplateBinding` řetězec identifikátoru je přiřazen jako <xref:System.Windows.TemplateBindingExtension.Property%2A> hodnotu základní <xref:System.Windows.TemplateBindingExtension> rozšíření třídy.  
  
 Je možné použít syntaxi elementu objektu, kterou ale neuvádíme, protože nemá žádné reálné použití. `TemplateBinding`slouží k vyplnění výrazy hodnot v rámci setter, pomocí vyhodnotit a pomocí syntaxe element objektu pro `TemplateBinding` k vyplnění `<Setter.Property>` vlastnost element syntaxe je zbytečně verbose.  
  
 `TemplateBinding`Můžete také použít využití podrobné atribut, který určuje <xref:System.Windows.TemplateBindingExtension.Property%2A> vlastnost jako vlastnost = dvojice hodnota:  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné. Protože `TemplateBinding` má jenom jednu nastavit vlastnost, který je vyžadován, toto podrobné použití není Typická.  
  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementace XAML procesor je definovaný zpracování pro toto rozšíření značek <xref:System.Windows.TemplateBindingExtension> třídy.  
  
 `TemplateBinding`je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek v XAML použití `{` a `}` znaků v jejich syntaxi atributů, což je konvence, podle kterého XAML procesor rozpozná, že rozšíření značek musí zpracovat atribut. Další informace najdete v tématu [rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Style>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [RelativeSource MarkupExtension](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md)  
 [Vazby – rozšíření značek](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)
