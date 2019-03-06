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
ms.openlocfilehash: f3fb2559510d85f6e55a4784f2b528f16737a2ab
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371109"
---
# <a name="staticresource-markup-extension"></a>StaticResource – rozšíření značek
Poskytuje hodnotu pro všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vlastnost atributu vyhledáním odkaz na prostředek už definované. Chování při vyhledávání pro daný prostředek je obdobou během načítání vyhledávání, která bude hledat prostředky, které byly dříve načteny z kódu aktuálního [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránek a jiných zdrojů aplikace a vygeneruje tuto hodnotu prostředků jako Hodnota vlastnosti objektů za běhu.  
  
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
|`key`|Klíč pro požadovaný prostředek. Tento klíč byl zpočátku přiřadil [x: Key – direktiva](../../xaml-services/x-key-directive.md) prostředek byl vytvořen v označení, zda byla poskytnuta jako `key` parametru při volání metody <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> Pokud prostředek se vytvořil v kódu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
>  A `StaticResource` nesmí se pokusit vytvořit dopředný odkaz na prostředek, který je definován v rámci lexikálně Další [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru. To pokusíte, není podporována, a i v případě selhání odkazu není pokusem dopředný odkaz se vám být naúčtovány snížení výkonu času zatížení při interní zatřiďovacích tabulek reprezentující <xref:System.Windows.ResourceDictionary> budou vyhledány. Nejlepších výsledků dosáhnete upravte tak, aby dopředné odkazy se lze vyvarovat složení zdrojové slovníky. Pokud se nelze vyhnout dopředný odkaz, použijte [– rozšíření značek DynamicResource](dynamicresource-markup-extension.md) místo.  
  
 Zadaný <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> by měl odpovídat existující prostředek, označena [x: Key – direktiva](../../xaml-services/x-key-directive.md) na určité úrovni v vaše stránka, aplikace, ovládací prvek k dispozici motivy a externí prostředky nebo systémové prostředky. Vyvolá se v tomto pořadí vyhledávání prostředků. Další informace o chování při vyhledávání prostředků pro statické a dynamické prostředky, najdete v části [prostředky XAML](xaml-resources.md).  
  
 Klíč prostředku může obsahovat libovolný řetězec podle [xamlname – gramatika](../../xaml-services/xamlname-grammar.md). Klíč prostředku může být také jinými typy objektů, například <xref:System.Type>. A <xref:System.Type> klíč je nezbytné k tom, jak můžete styl ovládací prvky podle motivy, prostřednictvím klíče k implicitní styl. Další informace najdete v tématu [Přehled vytváření ovládacího prvku](../controls/control-authoring-overview.md).  
  
 Alternativní deklarativní způsob odkazuje na prostředek je jako [– rozšíření značek DynamicResource](dynamicresource-markup-extension.md).  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Řetězec s tokenem uvedený za `StaticResource` řetězec identifikátoru je přiřazen jako <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> hodnoty základního <xref:System.Windows.StaticResourceExtension> rozšíření třídy.  
  
 `StaticResource` můžete použít v syntaxi elementu objektu. V takovém případě zadáte hodnotu <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> vlastnost je povinná.  
  
 `StaticResource` je také možné využití podrobné atribut, který určuje <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> vlastnost jako vlastnost = hodnota pár:  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné. Protože `StaticResource` má jen jednu nastavitelnou vlastnost, která je požadována, toto použití podrobné syntaxe není typické.  
  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementace procesoru, zpracování tohoto rozšíření značek definováno <xref:System.Windows.StaticResourceExtension> třídy.  
  
 `StaticResource` je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] použít {a} znaků v syntaxi atributu, což je konvence, podle kterého [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru rozpozná, že rozšíření značek musí zpracovat atribut. Další informace najdete v tématu [– rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také:
- [Styly a šablony](../controls/styling-and-templating.md)
- [Přehled XAML (WPF)](xaml-overview-wpf.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Prostředky XAML](xaml-resources.md)
- [Prostředky a kód](resources-and-code.md)
