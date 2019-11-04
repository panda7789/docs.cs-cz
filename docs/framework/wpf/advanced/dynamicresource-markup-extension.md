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
ms.openlocfilehash: a04e1569f77fed73a480fda3d63cabf6dbc30664
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460518"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource – rozšíření značek
Poskytuje hodnotu pro jakýkoliv [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atribut vlastnosti odložením této hodnoty jako odkaz na definovaný prostředek. Chování vyhledávání pro tento prostředek je analogické pro vyhledávání za běhu.  
  
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
|`key`|Klíč pro požadovaný prostředek. Tento klíč byl původně přiřazen [direktivou x:Key –](../../xaml-services/x-key-directive.md) , pokud byl prostředek vytvořen v kódu, nebo byl zadán jako parametr `key` při volání <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>, pokud byl prostředek vytvořen v kódu.|  
  
## <a name="remarks"></a>Poznámky  
 `DynamicResource` vytvoří dočasný výraz při počáteční kompilaci, čímž se odloží vyhledávání prostředků, dokud se ve skutečnosti nevyžaduje požadovaná hodnota prostředku, aby bylo možné vytvořit objekt. To může být potenciálně po načtení stránky [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Hodnota prostředku bude nalezena na základě hledání klíčů proti všem aktivním slovníkům prostředků počínaje aktuálním rozsahem stránky a je nahrazena zástupným výrazem z kompilace.  
  
> [!IMPORTANT]
> V souladu s prioritou vlastnosti závislosti je výraz `DynamicResource` ekvivalentní pozici, kde se používá odkaz na dynamický prostředek. Pokud nastavíte místní hodnotu pro vlastnost, která dříve obsahovala výraz `DynamicResource` jako místní hodnotu, `DynamicResource` je zcela odebrán. Podrobnosti najdete v tématu [Priorita hodnoty vlastností závislosti](dependency-property-value-precedence.md).  
  
 Některé scénáře přístupu k prostředkům jsou zvláště vhodné pro `DynamicResource` na rozdíl od [rozšíření značek StaticResource](staticresource-markup-extension.md). Diskuzi o relativních aspektech a dopadu na výkon `DynamicResource` a `StaticResource`najdete v tématu [zdroje XAML](xaml-resources.md) .  
  
 Zadaný <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> by měl odpovídat stávajícímu prostředku určenému [direktivou x:Key –](../../xaml-services/x-key-directive.md) na určité úrovni stránky, aplikaci, dostupných motivech řízení a externích prostředcích nebo systémových prostředků a vyhledávání prostředků se stane v dané pořadí. Další informace o vyhledávání prostředků pro statické a dynamické prostředky naleznete v tématu [prostředky XAML](xaml-resources.md).  
  
 Klíč prostředku může být libovolný řetězec definovaný v gramatice v kódu [XAML](../../xaml-services/xamlname-grammar.md). Klíč prostředku může být také jiné typy objektů, například <xref:System.Type>. <xref:System.Type> klíč je zásadní pro to, jak lze ovládací prvky stylovat pomocí motivů. Další informace najdete v tématu [Přehled tvorby řízení](../controls/control-authoring-overview.md).  
  
 Rozhraní API pro vyhledávání hodnot prostředků, jako je například <xref:System.Windows.FrameworkElement.FindResource%2A>, sledují stejnou logiku vyhledávání prostředků, jakou používá `DynamicResource`.  
  
 Alternativním deklarativním způsobem, který odkazuje na prostředek, je [rozšíření značek StaticResource](staticresource-markup-extension.md).  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Token řetězce poskytnutý po řetězci `DynamicResource` identifikátoru je přiřazen jako hodnota <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> základní třídy rozšíření <xref:System.Windows.DynamicResourceExtension>.  
  
 `DynamicResource` lze použít v syntaxi elementu Object. V takovém případě je nutné zadat hodnotu vlastnosti <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>.  
  
 `DynamicResource` lze také použít v podrobném použití atributu, které určuje vlastnost <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> jako dvojici vlastnost = hodnota:  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné. Protože `DynamicResource` má pouze jednu nastavitelnou vlastnost, která je povinná, toto podrobné použití není typické.  
  
 V implementaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru je zpracování tohoto rozšíření značek definováno třídou <xref:System.Windows.DynamicResourceExtension>.  
  
 `DynamicResource` je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používají znaky {a} v jejich syntaxi atributu, což je konvence, podle které procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] rozpoznává, že rozšíření značek musí zpracovat atribut. Další informace naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také:

- [Prostředky XAML](xaml-resources.md)
- [Prostředky a kód](resources-and-code.md)
- [x:Key – direktiva](../../xaml-services/x-key-directive.md)
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Rozšíření značek StaticResource](staticresource-markup-extension.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
