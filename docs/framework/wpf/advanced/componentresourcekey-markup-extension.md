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
ms.openlocfilehash: 2ccc4f3154996a4e442a4092833f5c9ed9c8938a
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559458"
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
|`targetTypeName`|Název veřejného typu modulu CLR (Common Language Runtime), který je definován v sestavení prostředků.|  
|`targetID`|Klíč pro prostředek Po vyhledání prostředků se `targetID` podobá [direktivě x:Key –](../../../desktop-wpf/xaml-services/xkey-directive.md) prostředku.|  
  
## <a name="remarks"></a>Poznámky  
 Jak je vidět výše, použití rozšíření značek {`ComponentResourceKey`} se nachází na dvou místech:  
  
- Definice klíče v rámci slovníku prostředků motivu, jak poskytuje autor ovládacího prvku.  
  
- Přístup k prostředku motivu ze sestavení, když jste retemplating ovládací prvek, ale chcete použít hodnoty vlastností, které pocházejí z prostředků poskytovaných motivy ovládacího prvku.  
  
 Pro odkazování na prostředky komponent, které pocházejí z motivů, se obecně doporučuje použít `{DynamicResource}` místo `{StaticResource}`. To se zobrazuje v části použití. `{DynamicResource}` se doporučuje, protože vlastní motiv může změnit uživatel. Chcete-li, aby prostředek součásti, který nejlépe odpovídá záměru autora ovládacího prvku, podporoval motiv, měli byste povolit, aby byl odkaz na prostředek komponenty také dynamický.  
  
 <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> identifikuje typ, který existuje v cílovém sestavení, kde je prostředek skutečně definován. `ComponentResourceKey` lze definovat a použít nezávisle na tom, kde je <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> definována, ale nakonec musí vyřešit typ prostřednictvím odkazovaných sestavení.  
  
 Běžné použití <xref:System.Windows.ComponentResourceKey> je definování klíčů, které jsou pak zveřejněny jako členové třídy. Pro účely tohoto použití použijte konstruktor <xref:System.Windows.ComponentResourceKey> třídy, nikoli příponu označení. Další informace najdete v tématu <xref:System.Windows.ComponentResourceKey>nebo v části Definování a odkazování klíčů pro prostředky motivů v tématu [Přehled vytváření ovládacích prvků](../controls/control-authoring-overview.md).  
  
 Pro vytváření klíčů a odkazujících se na prostředky s klíčem se běžně používá syntaxe atributu `ComponentResourceKey` rozšíření značek.  
  
 Uvedená syntaxe komprimace spoléhá na signaturu konstruktoru <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> a použití pozičního parametru rozšíření značek. Pořadí, ve kterém jsou předány `targetTypeName` a `targetID`, je důležité. Podrobná syntaxe spoléhá na <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> konstruktor bez parametrů a poté nastaví <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> a <xref:System.Windows.ComponentResourceKey.ResourceId%2A> způsobem, který je podobný syntaxi true atributu v elementu Object. V podrobné syntaxi není pořadí, ve kterém jsou vlastnosti nastaveny, důležité. Vztah a mechanismy těchto dvou alternativ (Compact a verbose) jsou podrobněji popsány v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
 Technicky, hodnota pro `targetID` může být libovolný objekt, nemusí se jednat o řetězec. Nejběžnějším využitím v subsystému WPF je však zarovnat `targetID` hodnoty pomocí formulářů, které jsou řetězcem, a kde jsou tyto řetězce platné v [gramatice gramatiky](../../../desktop-wpf/xaml-services/xamlname-grammar.md).  
  
 `ComponentResourceKey` lze použít v syntaxi elementu Object. V takovém případě je nutné zadat hodnotu vlastností <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> a <xref:System.Windows.ComponentResourceKey.ResourceId%2A>, aby bylo možné správně inicializovat rozšíření.  
  
 V implementaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Reader je zpracování tohoto rozšíření značek definováno třídou <xref:System.Windows.ComponentResourceKey>.  
  
 `ComponentResourceKey` je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používají znaky {a} v jejich syntaxi atributu, což je konvence, podle které procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] rozpoznává, že rozšíření značek musí zpracovat atribut. Další informace naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [Přehled vytváření ovládacích prvků](../controls/control-authoring-overview.md)
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
