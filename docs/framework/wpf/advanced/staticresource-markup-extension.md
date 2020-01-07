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
ms.openlocfilehash: aa7f69e8871295006c3c5a9c7d0a70d0ecbd6d7e
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559817"
---
# <a name="staticresource-markup-extension"></a>StaticResource – rozšíření značek
Poskytuje hodnotu pro libovolný atribut [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vlastnosti vyhledáním odkazu na již definovaný prostředek. Chování vyhledávání pro tento prostředek je obdobou vyhledávání při načítání, což bude hledat prostředky, které byly dříve načteny ze značky aktuální [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky a také do jiných zdrojů aplikace, a vygeneruje hodnotu tohoto prostředku jako hodnotu vlastnosti v objektech modulu runtime.  
  
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
|`key`|Klíč pro požadovaný prostředek. Tento klíč byl původně přiřazen [direktivou x:Key –](../../../desktop-wpf/xaml-services/xkey-directive.md) , pokud byl prostředek vytvořen v kódu, nebo byl zadán jako parametr `key` při volání <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>, pokud byl prostředek vytvořen v kódu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
> `StaticResource` se nesmí pokusit vytvořit dopředný odkaz na prostředek, který je v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru definován lexikálním. Pokus o provedení této akce není podporován a i v případě, že takový odkaz neselže, bude při pokusu o přemístění v případě, že se prohledávají vnitřní tabulky hash reprezentující <xref:System.Windows.ResourceDictionary>, vyhledána pokuta výkonu při načítání. Pro dosažení nejlepších výsledků upravte složení svých slovníků prostředků tak, aby bylo možné vyhnout se odkazům na dopředné odkazy. Pokud se vám nedaří dopředný odkaz, použijte místo toho [rozšíření značek DynamicResource](dynamicresource-markup-extension.md) .  
  
 Zadaný <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> by měl odpovídat existujícímu prostředku identifikovanému pomocí [direktivy x:Key –](../../../desktop-wpf/xaml-services/xkey-directive.md) na některé úrovni stránky, aplikaci, dostupných motivech ovládacích prvků a externích prostředků nebo systémových prostředků. K vyhledávání prostředků dochází v tomto pořadí. Další informace o chování vyhledávání prostředků pro statické a dynamické prostředky naleznete v tématu [prostředky XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 Klíč prostředků může být libovolný řetězec definovaný v gramatice v kódu [XAML](../../../desktop-wpf/xaml-services/xamlname-grammar.md). Klíč prostředků může být také jiné typy objektů, například <xref:System.Type>. <xref:System.Type> klíč je zásadní pro to, jak lze ovládací prvky stylovat pomocí motivů pomocí implicitního klíče stylu. Další informace najdete v tématu [Přehled tvorby řízení](../controls/control-authoring-overview.md).  
  
 Alternativním deklarativním způsobem, který odkazuje na prostředek, je [rozšíření značek DynamicResource](dynamicresource-markup-extension.md).  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Token řetězce poskytnutý po řetězci `StaticResource` identifikátoru je přiřazen jako hodnota <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> základní třídy rozšíření <xref:System.Windows.StaticResourceExtension>.  
  
 `StaticResource` lze použít v syntaxi elementu Object. V takovém případě je nutné zadat hodnotu vlastnosti <xref:System.Windows.StaticResourceExtension.ResourceKey%2A>.  
  
 `StaticResource` lze také použít v podrobném použití atributu, které určuje vlastnost <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> jako dvojici vlastnost = hodnota:  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné. Protože `StaticResource` má pouze jednu nastavitelnou vlastnost, která je povinná, toto podrobné použití není typické.  
  
 V implementaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru je zpracování tohoto rozšíření značek definováno třídou <xref:System.Windows.StaticResourceExtension>.  
  
 `StaticResource` je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používají znaky {a} v jejich syntaxi atributu, což je konvence, podle které procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] rozpoznává, že rozšíření značek musí zpracovat atribut. Další informace naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také:

- [Styly a šablony](../controls/styling-and-templating.md)
- [Přehled XAML (WPF)](xaml-overview-wpf.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Prostředky XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Prostředky a kód](resources-and-code.md)
