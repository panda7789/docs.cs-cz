---
title: ComponentResourceKey – rozšíření značek
ms.date: 03/30/2017
f1_keywords:
- ComponentResourceKey
- ComponentResourceKeyExtension
helpviewer_keywords:
- ComponentResourceKey markup extension [WPF]
- XAML [WPF], ComponentResourceKey markup extension
ms.assetid: d6bcdbe6-61b3-40a7-b381-4e02185b5a85
ms.openlocfilehash: d11c26add084165eaa9fd0b319a375c4b98c7fb9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540407"
---
# <a name="componentresourcekey-markup-extension"></a>ComponentResourceKey – rozšíření značek
Definuje a klíče pro prostředky, které jsou načteny z externí sestavení odkazuje. To umožňuje vyhledávání prostředků zadat typ cíle v sestavení, nikoli slovníku explicitní prostředků v sestavení nebo na třídu.  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>Použití atributu XAML (nastavení klíč, compact)  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>Použití atributu XAML (nastavení klíč, verbose)  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>Použití atributu XAML (žádajícího prostředků, compact)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a>Použití atributu XAML (žádajícího prostředků, verbose)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`targetTypeName`|Název veřejnosti [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] typu, která je definována v sestavení prostředků.|  
|`targetID`|Klíč pro prostředek. Když jsou vyhledávat prostředky, `targetID` se podobá [x: Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md) prostředku.|  
  
## <a name="remarks"></a>Poznámky  
 Jak je vidět v použití výše uvedeného {`ComponentResourceKey`} využití rozšíření značek nachází na dvou místech:  
  
-   Definice klíč v rámci slovník prostředků motiv, jaké poskytovala autorem ovládací prvek.  
  
-   Přístup k prostředku motiv ze sestavení, když jsou retemplating ovládací prvek ale chcete použít hodnoty vlastností, které pocházejí z prostředků poskytovaných motivy ovládacího prvku.  
  
 Pro odkazování na komponenty zdroje, které pocházejí z motivy, obvykle doporučujeme používat `{DynamicResource}` místo `{StaticResource}`. Můžete se podívat na využití. `{DynamicResource}` doporučuje se, protože uživatel může změnit motiv sám sebe. Pokud chcete součást prostředků, která nejvíce odpovídá implementované záměr autora ovládacího prvku pro podporu motiv, měli byste povolit odkaz prostředků vaší součásti také být dynamické.  
  
 <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> Určuje typ, který existuje v cílové sestavení, kde je ve skutečnosti definován prostředek. A `ComponentResourceKey` můžete definovaný a použít nezávisle na přesně vědět, kde <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> je definován, ale server se musí přeložit typ prostřednictvím odkazované sestavení.  
  
 Použití běžných pro <xref:System.Windows.ComponentResourceKey> je definovat klíče, které jsou pak zveřejněné jako členové třídy. Pro toto použití, můžete použít <xref:System.Windows.ComponentResourceKey> konstruktoru třídy, ne rozšíření značek. Další informace najdete v tématu <xref:System.Windows.ComponentResourceKey>, nebo "definování a odkazování na klíče pro motiv části zdroje tématu" [vytváření – Přehled ovládacího prvku](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 Pro vytvoření klíče i odkazy na s klíči prostředky, se běžně používá pro atribut syntaxe `ComponentResourceKey` – rozšíření značek.  
  
 Využívá compact syntaxi uvedenou <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> konstruktor podpisu a poziční parametr využití rozšíření značek. V jakém pořadí `targetTypeName` a `targetID` mají je důležité. Podrobná syntaxe spoléhá na <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> výchozí konstruktor a poté nastaví <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> a <xref:System.Windows.ComponentResourceKey.ResourceId%2A> způsobem, který je obdobou syntaxe true atributu v objektu elementu. V podrobná syntaxe není důležité pořadí, ve kterém jsou nastaveny vlastnosti. Relace a mechanismy tyto dvě možnosti (compact a podrobné) je podrobně popsaná v další v tématu [rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 Technicky hodnota `targetID` může být jakýkoli objekt, nemusí být řetězec. Nejběžnější využití v grafickém subsystému WPF je ale, chcete-li zarovnat `targetID` hodnotu s formuláři řetězce, které jsou a kde jsou platné v takové řetězce [XamlName – gramatika](../../../../docs/framework/xaml-services/xamlname-grammar.md).  
  
 `ComponentResourceKey` lze použít v syntaxi objekt elementu. V takovém případě zadáte hodnotu i <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> a <xref:System.Windows.ComponentResourceKey.ResourceId%2A> vlastnosti je potřeba správně inicializovat rozšíření.  
  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] čtečky implementace je definována zpracování pro toto rozšíření značek <xref:System.Windows.ComponentResourceKey> třídy.  
  
 `ComponentResourceKey` je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] použít {a} znaků v jejich syntaxi atributů, což je konvence, podle kterého [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor rozpozná, že rozšíření značek musí zpracovat atribut. Další informace najdete v tématu [rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.ComponentResourceKey>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Přehled vytváření ovládacích prvků](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
