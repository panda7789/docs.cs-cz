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
ms.openlocfilehash: 5f72d6c3273cfda4276383cfe72f90196e5d4340
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169751"
---
# <a name="componentresourcekey-markup-extension"></a>ComponentResourceKey – rozšíření značek
Definuje a klíče pro prostředky, které jsou načteny z externího sestavení odkazuje. To umožňuje vyhledávání prostředků zadat typ cíle v sestavení, nikoli slovníku explicitní prostředků v sestavení nebo třídy.  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>Použití atributu XAML (klíč nastavení, compact)  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>Použití atributu XAML (nastavení klíče, verbose)  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>Použití atributu XAML (žádost o prostředek, compact)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a>Použití atributu XAML (žádost o prostředek, verbose)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`targetTypeName`|Název veřejně [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] typ, který je definovaný v sestavení prostředků.|  
|`targetID`|Klíč prostředku. Když jsou vyhledány prostředky `targetID` bude obdobná [x: Key – direktiva](../../xaml-services/x-key-directive.md) prostředku.|  
  
## <a name="remarks"></a>Poznámky  
 Jak je znázorněno výše, použití {`ComponentResourceKey`} použití rozšíření značky se nachází na dvou místech:  
  
-   Definice klíče ve slovníku prostředků motivu, podle autora ovládacího prvku.  
  
-   Přístup k prostředku motiv ze sestavení, když jsou retemplating ovládací prvek ale chcete použít hodnoty vlastností, které pocházejí z prostředků poskytované motivy ovládacího prvku.  
  
 Pro odkazování na komponenty prostředky, které pocházejí z motivy, obecně doporučujeme používat `{DynamicResource}` spíše než `{StaticResource}`. To je ukázáno uplatňovány na. `{DynamicResource}` je doporučeno, protože samotný motivu lze změnit uživatelem. Pokud chcete, aby komponenta prostředek, který nejlépe odpovídá ovládacího prvku Autor záměr pro podporu motiv, byste měli povolit odkaz na prostředek vaše komponenta také být dynamická.  
  
 <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> Identifikuje typ, který existuje v cílové sestavení, ve kterém je prostředek ve skutečnosti definovány. A `ComponentResourceKey` možné definovat a používat nezávisle na přesně vědět, kde <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> je definován, ale nakonec musí rozpoznat typ prostřednictvím odkazovaných sestavení.  
  
 Společné využití pro <xref:System.Windows.ComponentResourceKey> je definovat klíče, které jsou poté vystavena jako členy třídy. Pro toto použití je použít <xref:System.Windows.ComponentResourceKey> konstruktoru třídy, není rozšíření značek. Další informace najdete v tématu <xref:System.Windows.ComponentResourceKey>, nebo definování a odkazování na klíče pro motiv část "Resources v tématu" [Přehled vytváření ovládacího prvku](../controls/control-authoring-overview.md).  
  
 Pro vytvoření klíče i odkazující na označenými prostředky, syntaxe atributu se běžně používá pro `ComponentResourceKey` – rozšíření značek.  
  
 Nejúspornější syntaxí, zobrazí se může spolehnout <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> podpis konstruktoru a pozičních parametrů více dopředu používání rozšíření značek. Pořadí, ve kterém `targetTypeName` a `targetID` disponují je důležité. Podrobná syntaxe se může spolehnout <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> výchozí konstruktor a nastaví <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> a <xref:System.Windows.ComponentResourceKey.ResourceId%2A> způsobem, který je obdobou syntaxe true atributu na elementu objektu. V podrobné syntaxi není důležité pořadí, ve kterém jsou nastavené vlastnosti. Relace a mechanismy tyto dvě možnosti (compact a podrobné) je popsána podrobněji vysvětlený v tématu [– rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
 Technicky vzato hodnota `targetID` může být libovolný objekt, nemusí být řetězec. Nejběžnější použití v subsystému WPF je však zarovnat `targetID` hodnotu s formuláři, které jsou řetězce, a kde jsou platné v těchto řetězců [xamlname – gramatika](../../xaml-services/xamlname-grammar.md).  
  
 `ComponentResourceKey` můžete použít v syntaxi elementu objektu. V takovém případě určující hodnotu i <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> a <xref:System.Windows.ComponentResourceKey.ResourceId%2A> vlastnosti je potřeba správně inicializovat rozšíření.  
  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] čtečky implementace zpracování tohoto rozšíření značek definováno <xref:System.Windows.ComponentResourceKey> třídy.  
  
 `ComponentResourceKey` je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] použít {a} znaků v syntaxi atributu, což je konvence, podle kterého [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru rozpozná, že rozšíření značek musí zpracovat atribut. Další informace najdete v tématu [– rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [Přehled řízeného vytváření](../controls/control-authoring-overview.md)
- [Přehled XAML (WPF)](xaml-overview-wpf.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
