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
ms.openlocfilehash: 63cac0bcca0d9ce8e9f69aa8c9986cb5fa597a56
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590339"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource – rozšíření značek
Poskytuje hodnotu pro všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vlastnost atributu odložením tuto hodnotu jako odkaz na prostředek definovaný. Chování při vyhledávání pro daný prostředek je obdobou vyhledávání za běhu.  
  
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
|`key`|Klíč pro požadovaný prostředek. Tento klíč byl zpočátku přiřadil [x: Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md) prostředek byl vytvořen v označení, zda byla poskytnuta jako `key` parametru při volání metody <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> Pokud prostředek se vytvořil v kódu.|  
  
## <a name="remarks"></a>Poznámky  
 A `DynamicResource` vytvoří dočasné výraz během počáteční kompilace a vyhledávání prostředků tedy odložit, dokud hodnota požadovaný prostředek je skutečně potřeba, abyste mohli vytvořit objekt. To může být potenciálně po [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] načtení stránky. Hodnota prostředku se najít podle klíčových vyhledávání na všechny aktivní zdrojové slovníky od aktuální obor page a nahradí zástupný symbol výrazu z kompilace.  
  
> [!IMPORTANT]
>  Z hlediska Priorita vlastností závislosti `DynamicResource` výraz je ekvivalentní k umístění, kde použít odkaz na prostředek dynamické. Pokud nastavíte hodnotu místní vlastnosti, které dříve měly `DynamicResource` výraz jako místní hodnota `DynamicResource` úplně Odebereme. Podrobnosti najdete v tématu [Priorita hodnot závislých vlastností](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).  
  
 Jsou zvlášť vhodná pro určité scénáře přístupu prostředků `DynamicResource` nikoli [– rozšíření značek StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md). Zobrazit [prostředky XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md) diskuzi o relativní věci a rozbor aspektů výkonu `DynamicResource` a `StaticResource`.  
  
 Zadaný <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> určené existující prostředek, musí odpovídat [x: Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md) na určité úrovni v vaše stránka, aplikace, ovládací prvek dostupné motivy a externí prostředky nebo systémové prostředky a vyhledání prostředku se stane v tomto pořadí. Další informace o vyhledání prostředku pro statické a dynamické prostředky, najdete v části [prostředky XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Klíč prostředku může být libovolný řetězec podle [xamlname – gramatika](../../../../docs/framework/xaml-services/xamlname-grammar.md). Klíč prostředku může být také další typy objektů, například <xref:System.Type>. A <xref:System.Type> klíč je základní jak může být ovládací prvky ve stylu podle motivů. Další informace najdete v tématu [Přehled vytváření ovládacího prvku](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] pro vyhledávání hodnoty prostředků jako například <xref:System.Windows.FrameworkElement.FindResource%2A>, se řídí stejnou logikou vyhledávání prostředků jako používá `DynamicResource`.  
  
 Alternativní deklarativní způsob odkazuje na prostředek je jako [– rozšíření značek StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Řetězec s tokenem uvedený za `DynamicResource` řetězec identifikátoru je přiřazen jako <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> hodnoty základního <xref:System.Windows.DynamicResourceExtension> rozšíření třídy.  
  
 `DynamicResource` můžete použít v syntaxi elementu objektu. V takovém případě zadáte hodnotu <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> vlastnost je povinná.  
  
 `DynamicResource` je také možné využití podrobné atribut, který určuje <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> vlastnost jako vlastnost = hodnota pár:  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné. Protože `DynamicResource` má jen jednu nastavitelnou vlastnost, která je požadována, toto použití podrobné syntaxe není typické.  
  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementace procesoru, zpracování tohoto rozšíření značek definováno <xref:System.Windows.DynamicResourceExtension> třídy.  
  
 `DynamicResource` je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] použít {a} znaků v syntaxi atributu, což je konvence, podle kterého [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru rozpozná, že rozšíření značek musí zpracovat atribut. Další informace najdete v tématu [– rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také:
- [Prostředky XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)
- [Prostředky a kód](../../../../docs/framework/wpf/advanced/resources-and-code.md)
- [x:Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md)
- [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [Rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [Rozšíření značek StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)
- [Rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
