---
title: StaticResource – rozšíření značek
ms.date: 03/30/2017
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
ms.openlocfilehash: 5c0bb247bae525658d89d53f1672e57b87aba7bc
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646216"
---
# <a name="staticresource-markup-extension"></a>StaticResource – rozšíření značek
Poskytuje hodnotu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pro všechny atributy vlastnosti vyhledáním odkaz na již definovaný prostředek. Chování vyhledávání pro tento prostředek je analogické vyhledávání v době načítání, které bude hledat prostředky, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] které byly dříve načteny ze značek aktuální stránky a jiných zdrojů aplikace, a vygeneruje tuto hodnotu prostředku jako hodnotu vlastnosti v objektech za běhu.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xml  
<object property="{StaticResource key}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>Použití elementu objektu XAML  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`key`|Klíč pro požadovaný prostředek. Tento klíč byl původně přiřazen [x:Key směrnice,](../../../desktop-wpf/xaml-services/xkey-directive.md) pokud prostředek byl vytvořen `key` ve značkách nebo byl poskytnut jako parametr při volání, <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> pokud prostředek byl vytvořen v kódu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
> Nesmí `StaticResource` se pokoušet o odkaz dopředné na prostředek, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] který je definován lexikálně dále v souboru. Pokus o to není podporována a i v případě, že takový odkaz neselže, pokus o odkaz dopředné bude <xref:System.Windows.ResourceDictionary> mít za následek snížení výkonu doby načítání při prohledávání vnitřních tabulek hash představujících a. Nejlepších výsledků dosáhnete, když upravíte složení slovníků prostředků tak, aby se předkládaly odkazy dopředu. Pokud se nemůžete vyhnout dopředný odkaz, použijte [dynamicResource Markup Extension](dynamicresource-markup-extension.md) místo.  
  
 Zadaný <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> by měl odpovídat existujícímu prostředku označenému [direktivou x:Key](../../../desktop-wpf/xaml-services/xkey-directive.md) na určité úrovni na stránce, aplikaci, dostupných tématech ovládacích prvku a externích prostředcích nebo systémových prostředcích. Vyhledávání prostředků probíhá v tomto pořadí. Další informace o chování vyhledávání prostředků pro statické a dynamické prostředky naleznete v [tématu XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 Klíč prostředku může být libovolný řetězec definovaný v [gramatice XamlName](../../../desktop-wpf/xaml-services/xamlname-grammar.md). Klíč prostředku může být také jiné typy <xref:System.Type>objektů, například . Klíč <xref:System.Type> je zásadní pro to, jak lze ovládací prvky stylovat podle motivů, prostřednictvím implicitního klíče stylu. Další informace naleznete [v tématu Přehled vytváření ovládacích prvku](../controls/control-authoring-overview.md).  
  
 Alternativní deklarativní prostředky odkazování na prostředek je jako [dynamicResource Markup Extension](dynamicresource-markup-extension.md).  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Token řetězce zadaný `StaticResource` po přidělení řetězce <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> identifikátoru jako <xref:System.Windows.StaticResourceExtension> hodnota základní třídy rozšíření.  
  
 `StaticResource`lze použít v syntaxi prvku objektu. V tomto případě je vyžadováno <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> zadání hodnoty vlastnosti.  
  
 `StaticResource`lze také použít v podrobném použití atributu, který určuje <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> vlastnost jako dvojici vlastností=hodnota:  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné. Protože `StaticResource` má pouze jednu vlastnost settable, která je vyžadována, toto podrobné použití není typické.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] V implementaci procesoru zpracování pro toto rozšíření <xref:System.Windows.StaticResourceExtension> značky je definována třídy.  
  
 `StaticResource`je rozšíření značky. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používají znaky { a } v syntaxi atributu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] což je konvence, podle které procesor rozpozná, že rozšíření značek musí atribut zpracovat. Další informace naleznete [v tématu Markup Extensions a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také

- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Zdroje XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Zdroje a kód](resources-and-code.md)
