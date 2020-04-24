---
title: DynamicResource – rozšíření značek
ms.date: 03/30/2017
f1_keywords:
- DynamicResource
- DynamicResourceExtension
helpviewer_keywords:
- XAML [WPF], DynamicResource markup extension
- DynamicResource markup extensions [WPF]
ms.assetid: 7324f243-03af-4c2b-b0db-26ac6cdfcbe4
ms.openlocfilehash: 5ccda8ba8f41a30e0ce1c832a6d3176b7fb8e8c2
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646265"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource – rozšíření značek
Poskytuje hodnotu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro libovolný atribut vlastnosti odložením této hodnoty jako odkaz na definovaný prostředek. Chování vyhledávání pro tento prostředek je analogické vyhledávání za běhu.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xml  
<object property="{DynamicResource key}" .../>  
```  
  
## <a name="xaml-property-element-usage"></a>Použití elementu vlastnosti XAML  
  
```xml  
<object>  
  <object.property>  
    <DynamicResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`key`|Klíč pro požadovaný prostředek. Tento klíč byl původně přiřazen [x:Key směrnice,](../../../desktop-wpf/xaml-services/xkey-directive.md) pokud prostředek byl vytvořen `key` ve značkách nebo byl poskytnut jako parametr při volání, <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> pokud prostředek byl vytvořen v kódu.|  
  
## <a name="remarks"></a>Poznámky  
 A `DynamicResource` vytvoří dočasný výraz během počáteční kompilace a tedy odložit vyhledávání prostředků, dokud požadovaná hodnota prostředku je skutečně požadováno pro vytvoření objektu. To může být potenciálně po načtení [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky. Hodnota prostředku bude nalezena na základě hledání klíčů proti všem aktivním slovníkům prostředků počínaje aktuálním rozsahem stránky a je nahrazena zástupným výrazem z kompilace.  
  
> [!IMPORTANT]
> Z hlediska priority vlastnosti závislosti `DynamicResource` je výraz ekvivalentní pozici, kde je použit odkaz dynamického prostředku. Pokud nastavíte místní hodnotu pro `DynamicResource` vlastnost, která dříve `DynamicResource` měla výraz jako místní hodnotu, je zcela odebrán. Podrobnosti naleznete v [tématu Priorita hodnoty vlastnosti závislostí](dependency-property-value-precedence.md).  
  
 Některé scénáře přístupu k `DynamicResource` prostředkům jsou zvláště vhodné pro na rozdíl od [staticresource markup extension](staticresource-markup-extension.md). Informace [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) o relativních výhodách a důsledcích `DynamicResource` výkonu aplikace `StaticResource`a .  
  
 Zadaný <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> by měl odpovídat existujícímu prostředku určenému [direktivou x:Key](../../../desktop-wpf/xaml-services/xkey-directive.md) na určité úrovni na stránce, aplikaci, dostupných řídicích tématech a externích prostředcích nebo systémových prostředcích a vyhledávání prostředků proběhne v tomto pořadí. Další informace o vyhledávání prostředků pro statické a dynamické prostředky naleznete v [tématu XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 Klíčem prostředku může být libovolný řetězec definovaný v [gramatice XamlName](../../../desktop-wpf/xaml-services/xamlname-grammar.md). Klíč prostředku může být také jiné typy <xref:System.Type>objektů, například . Klíč <xref:System.Type> je zásadní pro to, jak mohou být ovládací prvky stylizovány podle motivů. Další informace naleznete [v tématu Přehled vytváření ovládacích prvku](../controls/control-authoring-overview.md).  
  
 Api pro vyhledávání hodnot prostředků, <xref:System.Windows.FrameworkElement.FindResource%2A>například podle logiky vyhledávání prostředků, jakou `DynamicResource`používá aplikace .  
  
 Alternativní deklarativní prostředky odkazování na prostředek je jako [rozšíření značky staticresource](staticresource-markup-extension.md).  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Token řetězce zadaný `DynamicResource` po přidělení řetězce <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> identifikátoru jako <xref:System.Windows.DynamicResourceExtension> hodnota základní třídy rozšíření.  
  
 `DynamicResource`lze použít v syntaxi prvku objektu. V tomto případě je vyžadováno <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> zadání hodnoty vlastnosti.  
  
 `DynamicResource`lze také použít v podrobném použití atributu, který určuje <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> vlastnost jako dvojici vlastností=hodnota:  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné. Protože `DynamicResource` má pouze jednu vlastnost settable, která je vyžadována, toto podrobné použití není typické.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] V implementaci procesoru zpracování pro toto rozšíření <xref:System.Windows.DynamicResourceExtension> značky je definována třídy.  
  
 `DynamicResource`je rozšíření značky. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používají znaky { a } v syntaxi atributu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] což je konvence, podle které procesor rozpozná, že rozšíření značek musí atribut zpracovat. Další informace naleznete [v tématu Markup Extensions a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také

- [Zdroje XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Zdroje a kód](resources-and-code.md)
- [x:Key – direktiva](../../../desktop-wpf/xaml-services/xkey-directive.md)
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
- [StaticResource – rozšíření značek](staticresource-markup-extension.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
