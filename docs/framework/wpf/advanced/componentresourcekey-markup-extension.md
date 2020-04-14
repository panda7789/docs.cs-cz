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
ms.openlocfilehash: 4cdba2a61be4e9686cd2120fd90a213534c222c8
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243359"
---
# <a name="componentresourcekey-markup-extension"></a>ComponentResourceKey – rozšíření značek
Definuje a odkazuje na klíče pro prostředky, které jsou načteny z externích sestavení. To umožňuje vyhledávání prostředků určit cílový typ v sestavení, nikoli explicitní slovník prostředků v sestavení nebo ve třídě.  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>Použití atributu XAML (klíč nastavení, kompaktní)  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>Použití atributu XAML (nastavení klíče, podrobné)  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>Využití atributů XAML (vyžádání prostředku, komprimace)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a>Využití atributů XAML (vyžádání prostředku, podrobné)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`targetTypeName`|Název typu clr (public common language language) , který je definován v sestavení prostředku.|  
|`targetID`|Klíč pro prostředek. Při vyhlédnout zdroje, `targetID` bude obdobou [x:Key směrnice](../../../desktop-wpf/xaml-services/xkey-directive.md) prostředku.|  
  
## <a name="remarks"></a>Poznámky  
 Jak je vidět ve výše`ComponentResourceKey`uvedených použitích, použití rozšíření značek { } se nachází na dvou místech:  
  
- Definice klíče v rámci slovníku prostředků motivu, jak je k dispozici autor ovládacího prvku.  
  
- Přístup k prostředku motivu ze sestavení, když retemplating ovládacího prvku, ale chcete použít hodnoty vlastností, které pocházejí z prostředků poskytovaných motivy ovládacího prvku.  
  
 Pro odkazování na zdroje komponent, které pocházejí z `{DynamicResource}` motivů, se obecně doporučuje použít spíše než `{StaticResource}`. To je zobrazeno v použití. `{DynamicResource}`doporučuje, protože samotný motiv může být změněn uživatelem. Pokud chcete, aby prostředek komponenty, který nejvíce odpovídá záměru autora ovládacího prvku pro podporu motivu, měli byste povolit, aby byl odkaz na prostředek komponenty také dynamický.  
  
 Identifikuje <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> typ, který existuje v cílovém sestavení, kde je prostředek skutečně definován. A `ComponentResourceKey` lze definovat a použít nezávisle na <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> tom, přesně vědět, kde je definován, ale nakonec musí vyřešit typ prostřednictvím odkazovaných sestavení.  
  
 Běžné použití <xref:System.Windows.ComponentResourceKey> pro je definovat klíče, které jsou pak vystaveny jako členové třídy. Pro toto použití <xref:System.Windows.ComponentResourceKey> použijete konstruktor třídy, nikoli rozšíření značek. Další informace naleznete <xref:System.Windows.ComponentResourceKey>v tématu Definování a odkazování klíčů pro prostředky motivu v tématu [Přehled vytváření ovládacího prvku](../controls/control-authoring-overview.md).  
  
 Pro vytváření klíčů a odkazování na klíče prostředky, syntaxe `ComponentResourceKey` atributu se běžně používá pro rozšíření značky.  
  
 Zobrazená kompaktní syntaxe <xref:System.Windows.ComponentResourceKey.%23ctor%2A> závisí na podpisu konstruktoru a použití pozičního parametru rozšíření značek. Pořadí, ve `targetTypeName` kterém `targetID` a jsou uvedeny, je důležité. Podrobná syntaxe spoléhá na <xref:System.Windows.ComponentResourceKey.%23ctor%2A> konstruktor bez parametrů a <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> <xref:System.Windows.ComponentResourceKey.ResourceId%2A> pak nastaví a způsobem, který je obdobou syntaxe true atributu na elementu objektu. V podrobné syntaxi není důležité pořadí, ve kterém jsou nastaveny vlastnosti. Vztah a mechanismy těchto dvou alternativ (kompaktní a podrobné) jsou podrobněji popsány v tématu [Markup Extensions a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
 Technicky hodnota pro `targetID` může být libovolný objekt, nemusí být řetězec. Nejběžnější použití v WPF je však `targetID` zarovnat hodnotu s formuláři, které jsou řetězce a kde tyto řetězce jsou platné v [XamlName gramatiky](../../../desktop-wpf/xaml-services/xamlname-grammar.md).  
  
 `ComponentResourceKey`lze použít v syntaxi prvku objektu. V tomto případě je nutné zadat <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> <xref:System.Windows.ComponentResourceKey.ResourceId%2A> hodnotu vlastnosti a správně inicializovat rozšíření.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] V implementaci čtečky zpracování pro toto rozšíření <xref:System.Windows.ComponentResourceKey> značky je definována třídy.  
  
 `ComponentResourceKey`je rozšíření značky. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používají znaky { a } v syntaxi atributu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] což je konvence, podle které procesor rozpozná, že rozšíření značek musí atribut zpracovat. Další informace naleznete [v tématu Markup Extensions a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [Přehled vytváření ovládacích prvků](../controls/control-authoring-overview.md)
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
