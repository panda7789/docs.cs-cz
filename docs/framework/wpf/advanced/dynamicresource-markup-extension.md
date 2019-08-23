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
ms.openlocfilehash: 06355c64d36d2688ef027c1940688d4c87e51ec8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964800"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource – rozšíření značek
Poskytuje hodnotu pro libovolný [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atribut vlastnosti odložením této hodnoty jako odkaz na definovaný prostředek. Chování vyhledávání pro tento prostředek je analogické pro vyhledávání za běhu.  
  
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
|`key`|Klíč pro požadovaný prostředek. Tento klíč byl původně přiřazen direktivou [x:Key –](../../xaml-services/x-key-directive.md) , pokud byl prostředek vytvořen v kódu, nebo byl zadán jako `key` parametr při volání <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> , pokud byl prostředek vytvořen v kódu.|  
  
## <a name="remarks"></a>Poznámky  
 Vytvoří `DynamicResource` během počáteční kompilace dočasný výraz, čímž se odloží vyhledávání prostředků, dokud není požadovaná hodnota prostředku skutečně potřebná k vytvoření objektu. To může být potenciálně po [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] načtení stránky. Hodnota prostředku bude nalezena na základě hledání klíčů proti všem aktivním slovníkům prostředků počínaje aktuálním rozsahem stránky a je nahrazena zástupným výrazem z kompilace.  
  
> [!IMPORTANT]
> V souladu s prioritou vlastnosti závislosti je `DynamicResource` výraz ekvivalentem pozice, kde je použit odkaz na dynamický prostředek. Pokud nastavíte místní hodnotu pro vlastnost, která dříve obsahovala `DynamicResource` výraz jako místní hodnotu, dojde k `DynamicResource` úplnému odebrání. Podrobnosti najdete v tématu [Priorita hodnoty vlastností závislosti](dependency-property-value-precedence.md).  
  
 Některé scénáře přístupu k prostředkům jsou zvláště vhodné `DynamicResource` pro [rozšíření značek StaticResource](staticresource-markup-extension.md). Diskuzi o relativních aspektech a vlivech `DynamicResource` na výkon a `StaticResource`najdete v tématu [zdroje XAML](xaml-resources.md) .  
  
 Zadaný <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> parametr by měl odpovídat existujícímu prostředku, který je stanoven [direktivou x:Key –](../../xaml-services/x-key-directive.md) na některé úrovni stránky, aplikaci, dostupných motivech ovládacích prvků a externích prostředků nebo systémových prostředků, a vyhledávání prostředků se stane. v tomto pořadí. Další informace o vyhledávání prostředků pro statické a dynamické prostředky naleznete v tématu [prostředky XAML](xaml-resources.md).  
  
 Klíč prostředku může být libovolný řetězec definovaný v gramatice v kódu [XAML](../../xaml-services/xamlname-grammar.md). Klíč prostředku může být také jiné typy objektů, jako je <xref:System.Type>například. <xref:System.Type> Klíč je zásadní pro to, jak lze ovládací prvky stylovat pomocí motivů. Další informace najdete v tématu [Přehled tvorby řízení](../controls/control-authoring-overview.md).  
  
 Rozhraní API pro vyhledávání hodnot prostředků, <xref:System.Windows.FrameworkElement.FindResource%2A>jako je, sledují stejnou logiku vyhledávání prostředků jako `DynamicResource`používá.  
  
 Alternativním deklarativním způsobem, který odkazuje na prostředek, je [rozšíření značek StaticResource](staticresource-markup-extension.md).  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Token řetězce poskytnutý po `DynamicResource` řetězci identifikátoru je přiřazen <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> jako hodnota základní <xref:System.Windows.DynamicResourceExtension> třídy rozšíření.  
  
 `DynamicResource`lze použít v syntaxi elementu Object. V takovém případě je nutné zadat hodnotu <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> vlastnosti.  
  
 `DynamicResource`lze také použít v podrobném použití atributu, které určuje <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> vlastnost jako dvojici vlastnost = hodnota:  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné. Protože `DynamicResource` má pouze jednu nastavitelnou vlastnost, která je povinná, toto podrobné použití není typické.  
  
 V implementaci procesoru je zpracování tohoto <xref:System.Windows.DynamicResourceExtension> rozšíření značek definováno třídou. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
 `DynamicResource`je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek používají znaky {a} v jejich syntaxi atributu, což je konvence, podle [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] které procesor rozpozná, že je nutné zpracovat atribut v rozšíření značek. Další informace naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také:

- [Prostředky XAML](xaml-resources.md)
- [Prostředky a kód](resources-and-code.md)
- [x:Key – direktiva](../../xaml-services/x-key-directive.md)
- [Přehled XAML (WPF)](xaml-overview-wpf.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Rozšíření značek StaticResource](staticresource-markup-extension.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
