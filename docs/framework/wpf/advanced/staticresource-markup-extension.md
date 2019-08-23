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
ms.openlocfilehash: 7392be182aedeeebe6b7092f9868c1fabfaafcb7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963458"
---
# <a name="staticresource-markup-extension"></a>StaticResource – rozšíření značek
Poskytuje hodnotu pro libovolný [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atribut vlastnosti vyhledáním odkazu na již definovaný prostředek. Chování vyhledávání pro tento prostředek je analogické k vyhledávání při načítání, což bude hledat prostředky, které byly dříve načteny ze značky aktuální [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky, i z jiných zdrojů aplikací a vygeneruje tuto hodnotu prostředku jako hodnota vlastnosti v běhových objektech.  
  
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
|`key`|Klíč pro požadovaný prostředek. Tento klíč byl původně přiřazen direktivou [x:Key –](../../xaml-services/x-key-directive.md) , pokud byl prostředek vytvořen v kódu, nebo byl zadán jako `key` parametr při volání <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> , pokud byl prostředek vytvořen v kódu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
> Nesmí se pokoušet o vytvoření dopředný odkaz na prostředek, který je [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] v souboru definován lexikálním. `StaticResource` Pokus o provedení této akce není podporován a i v případě, že takový odkaz neselže, bude při pokusu o dopředné odkazu účtována pokuta výkonu zatížení, když <xref:System.Windows.ResourceDictionary> jsou prohledány vnitřní tabulky hash reprezentující. Pro dosažení nejlepších výsledků upravte složení svých slovníků prostředků tak, aby bylo možné vyhnout se odkazům na dopředné odkazy. Pokud se vám nedaří dopředný odkaz, použijte místo toho [rozšíření značek DynamicResource](dynamicresource-markup-extension.md) .  
  
 Zadaný parametr <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> by měl odpovídat existujícímu prostředku, který je identifikovaný pomocí [direktivy x:Key –](../../xaml-services/x-key-directive.md) na určité úrovni stránky, aplikace, dostupných motivů ovládacích prvků a externích prostředků nebo systémových prostředků. K vyhledávání prostředků dochází v tomto pořadí. Další informace o chování vyhledávání prostředků pro statické a dynamické prostředky naleznete v tématu [prostředky XAML](xaml-resources.md).  
  
 Klíč prostředků může být libovolný řetězec definovaný v gramatice v kódu [XAML](../../xaml-services/xamlname-grammar.md). Klíč prostředků může být také jiné typy objektů, jako je <xref:System.Type>například. <xref:System.Type> Klíč je zásadní pro to, jak lze ovládací prvky stylovat pomocí motivů pomocí implicitního klíče stylu. Další informace najdete v tématu [Přehled tvorby řízení](../controls/control-authoring-overview.md).  
  
 Alternativním deklarativním způsobem, který odkazuje na prostředek, je [rozšíření značek DynamicResource](dynamicresource-markup-extension.md).  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Token řetězce poskytnutý po `StaticResource` řetězci identifikátoru je přiřazen <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> jako hodnota základní <xref:System.Windows.StaticResourceExtension> třídy rozšíření.  
  
 `StaticResource`lze použít v syntaxi elementu Object. V takovém případě je nutné zadat hodnotu <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> vlastnosti.  
  
 `StaticResource`lze také použít v podrobném použití atributu, které určuje <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> vlastnost jako dvojici vlastnost = hodnota:  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné. Protože `StaticResource` má pouze jednu nastavitelnou vlastnost, která je povinná, toto podrobné použití není typické.  
  
 V implementaci procesoru je zpracování tohoto <xref:System.Windows.StaticResourceExtension> rozšíření značek definováno třídou. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
 `StaticResource`je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek používají znaky {a} v jejich syntaxi atributu, což je konvence, podle [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] které procesor rozpozná, že je nutné zpracovat atribut v rozšíření značek. Další informace naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také:

- [Styly a šablony](../controls/styling-and-templating.md)
- [Přehled XAML (WPF)](xaml-overview-wpf.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Prostředky XAML](xaml-resources.md)
- [Prostředky a kód](resources-and-code.md)
