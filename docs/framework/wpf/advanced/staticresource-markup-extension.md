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
ms.openlocfilehash: 518a85c158c9a4472689d3c236b84278114cf3ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547196"
---
# <a name="staticresource-markup-extension"></a>StaticResource – rozšíření značek
Poskytuje hodnotu pro všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vlastnost atribut vyhledáním odkaz na prostředek už definované. Chování vyhledávání pro tento prostředek je obdobou čas načítání vyhledávání, který bude hledat prostředky, které byly dříve načteny z kódu aktuální [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky a také další aplikace zdroje a vygeneruje tuto hodnotu prostředků, jako Hodnota vlastnosti v objektech spuštění.  
  
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
|`key`|Klíč pro požadovaný prostředek. Tento klíč původně přiřazený pomocí [x: Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md) prostředek byl vytvořen v značek, zda byla poskytnuta jako `key` parametr při volání metody <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> Pokud prostředek se vytvořil v kódu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
>  A `StaticResource` nesmí pokus o spuštění dopředného odkazu na prostředek, který je definován v rámci lexikálně Další [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru. Pokusili, není podporován, a i v případě odkazu neselže, pokusu o odkaz na dopředného zpoplatněná snížení výkonu času zatížení při interní hodnota hash tabulky představující <xref:System.Windows.ResourceDictionary> vyhledávají. Nejlepších výsledků dosáhnete upravte složení vaší slovnících prostředků tak, aby se vyhnout dopředného odkazy. Pokud se nelze vyhnout dopředného odkaz, použijte [DynamicResource – rozšíření značek](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) místo.  
  
 Zadaný <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> by měla odpovídat existující prostředek, označeny [x: Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md) na určité úrovni v stránku, aplikace, k dispozici řízení motivy a externím prostředkům nebo systémové prostředky. K vyhledávání prostředků v tomto pořadí. Další informace o chování vyhledávání prostředků pro statické a dynamické prostředky najdete v tématu [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Klíč prostředku může být libovolný řetězec definovaný v [XamlName – gramatika](../../../../docs/framework/xaml-services/xamlname-grammar.md). Klíč prostředku může být také další typy objektů, jako například <xref:System.Type>. A <xref:System.Type> klíč je nezbytné, aby jak můžete ve ovládací prvky podle motivy, prostřednictvím klíčem implicitní stylu. Další informace najdete v tématu [vytváření – Přehled ovládacího prvku](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 Odkazování na prostředek alternativní deklarativní způsob je jako [DynamicResource – rozšíření značek](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md).  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Token řetězec zadaný po `StaticResource` řetězec identifikátoru je přiřazen jako <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> hodnotu základní <xref:System.Windows.StaticResourceExtension> rozšíření třídy.  
  
 `StaticResource` lze použít v syntaxi objekt elementu. V takovém případě určující hodnotu <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> vlastnost je povinná.  
  
 `StaticResource` Můžete také použít využití podrobné atribut, který určuje <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> vlastnost jako vlastnost = dvojice hodnota:  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné. Protože `StaticResource` má jenom jednu nastavit vlastnost, který je vyžadován, toto podrobné použití není Typická.  
  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementace procesor je definovaný zpracování pro toto rozšíření značek <xref:System.Windows.StaticResourceExtension> třídy.  
  
 `StaticResource` je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] použít {a} znaků v jejich syntaxi atributů, což je konvence, podle kterého [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor rozpozná, že rozšíření značek musí zpracovat atribut. Další informace najdete v tématu [rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [Prostředky XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Prostředky a kód](../../../../docs/framework/wpf/advanced/resources-and-code.md)
