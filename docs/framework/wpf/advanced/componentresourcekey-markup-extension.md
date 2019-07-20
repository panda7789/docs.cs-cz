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
ms.openlocfilehash: 93735d12426042fd6517c10a55d1a9bd32f906bb
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363057"
---
# <a name="componentresourcekey-markup-extension"></a>ComponentResourceKey – rozšíření značek
Definuje a odkazuje na klíče pro prostředky, které jsou načteny z externích sestavení. Díky tomu může vyhledávání prostředků určovat cílový typ v sestavení, nikoli explicitní slovník prostředků v sestavení nebo třídě.  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>Použití atributu XAML (nastavení klíče, komprimace)  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>Použití atributu XAML (nastavení klíče, verbose)  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>Použití atributu XAML (vyžádání prostředku, kompaktní)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a>Použití atributu XAML (vyžádání prostředku, verbose)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`targetTypeName`|Název veřejného [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] typu, který je definován v sestavení prostředků.|  
|`targetID`|Klíč pro prostředek Při vyhledání `targetID` prostředků se bude považovat za analogku s [direktivou x:Key –](../../xaml-services/x-key-directive.md) prostředku.|  
  
## <a name="remarks"></a>Poznámky  
 Jak je vidět výše, použití rozšíření značek {`ComponentResourceKey`} se nachází na dvou místech:  
  
- Definice klíče v rámci slovníku prostředků motivu, jak poskytuje autor ovládacího prvku.  
  
- Přístup k prostředku motivu ze sestavení, když jste retemplating ovládací prvek, ale chcete použít hodnoty vlastností, které pocházejí z prostředků poskytovaných motivy ovládacího prvku.  
  
 Pro odkazování na prostředky komponent, které pocházejí z motivů, se obecně doporučuje použít `{DynamicResource}` `{StaticResource}`místo. To se zobrazuje v části použití. `{DynamicResource}`se doporučuje, protože daný motiv může změnit uživatel. Chcete-li, aby prostředek součásti, který nejlépe odpovídá záměru autora ovládacího prvku, podporoval motiv, měli byste povolit, aby byl odkaz na prostředek komponenty také dynamický.  
  
 <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> Identifikuje typ, který existuje v cílovém sestavení, kde je prostředek skutečně definován. Lze definovat a použít nezávisle na <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> tom, kde je definována, ale nakonec musí vyřešit typ prostřednictvím odkazovaných sestavení. `ComponentResourceKey`  
  
 Běžné použití pro <xref:System.Windows.ComponentResourceKey> je definování klíčů, které jsou pak zveřejněny jako členové třídy. Pro toto použití použijte <xref:System.Windows.ComponentResourceKey> konstruktor třídy, nikoli rozšíření značek. Další informace najdete v <xref:System.Windows.ComponentResourceKey>části nebo v části Definování a odkazování klíčů pro prostředky motivů v tématu [Přehled vytváření ovládacích prvků](../controls/control-authoring-overview.md).  
  
 Pro vytváření klíčů a odkazujících se na prostředky s klíčem se běžně používá syntaxe atributu pro `ComponentResourceKey` rozšíření značek.  
  
 Uvedená syntaxe komprimace spoléhá na <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> signaturu konstruktoru a použití pozičního parametru rozšíření značek. Pořadí, ve kterém `targetTypeName` jsou uvedeny a `targetID` jsou důležité. Podrobná syntaxe se spoléhá na <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> konstruktor bez parametrů a pak <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> nastaví a <xref:System.Windows.ComponentResourceKey.ResourceId%2A> způsobem, který je podobný syntaxi true atributu v elementu Object. V podrobné syntaxi není pořadí, ve kterém jsou vlastnosti nastaveny, důležité. Vztah a mechanismy těchto dvou alternativ (Compact a verbose) jsou podrobněji popsány v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
 Technicky, hodnota pro `targetID` může být libovolný objekt, nemusí se jednat o řetězec. Nejběžnějším využitím v subsystému WPF je však zarovnání `targetID` hodnoty pomocí formulářů, které jsou řetězce a kde jsou tyto řetězce platné v gramatice v kódu [XAML](../../xaml-services/xamlname-grammar.md).  
  
 `ComponentResourceKey`lze použít v syntaxi elementu Object. V takovém případě je nutné zadat hodnotu <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> vlastností a <xref:System.Windows.ComponentResourceKey.ResourceId%2A> , aby bylo rozšíření správně inicializováno.  
  
 V implementaci čtecího modulu je zpracování tohoto <xref:System.Windows.ComponentResourceKey> rozšíření značek definováno třídou. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
 `ComponentResourceKey`je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek používají znaky {a} v jejich syntaxi atributu, což je konvence, podle [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] které procesor rozpozná, že je nutné zpracovat atribut v rozšíření značek. Další informace naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [Přehled vytváření ovládacích prvků](../controls/control-authoring-overview.md)
- [Přehled XAML (WPF)](xaml-overview-wpf.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
