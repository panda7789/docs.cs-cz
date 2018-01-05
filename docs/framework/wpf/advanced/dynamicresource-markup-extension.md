---
title: "DynamicResource – rozšíření značek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DynamicResource
- DynamicResourceExtension
helpviewer_keywords:
- XAML [WPF], DynamicResource markup extension
- DynamicResource markup extensions [WPF]
ms.assetid: 7324f243-03af-4c2b-b0db-26ac6cdfcbe4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f6c8500f9b9cd6d617789a2da3444519971ae81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource – rozšíření značek
Poskytuje hodnotu pro všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vlastnost atribut rozlišením tuto hodnotu jako odkaz na prostředek definované. Chování vyhledávání pro tento prostředek je analogická spuštění vyhledávání.  
  
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
|`key`|Klíč pro požadovaný prostředek. Tento klíč původně přiřazený pomocí [x: Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md) prostředek byl vytvořen v značek, zda byla poskytnuta jako `key` parametr při volání metody <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> Pokud prostředek se vytvořil v kódu.|  
  
## <a name="remarks"></a>Poznámky  
 A `DynamicResource` vytvoří dočasný výraz během počáteční kompilace a proto odložení vyhledávání pro prostředky, dokud hodnota požadovaný prostředek je ve skutečnosti vyžaduje, aby bylo možné vytvořit objekt. To může být potenciálně po [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] načtení stránky. Hodnota prostředků bude na základě nalezen klíč hledání u všech slovnících active prostředků od aktuální obor stránky a nahradí zástupný výraz ze kompilace.  
  
> [!IMPORTANT]
>  Z hlediska přednost před vlastností závislostí `DynamicResource` výraz je ekvivalentní pozice, kdy se používá odkaz dynamické prostředků. Pokud nastavíte místní hodnotu pro vlastnost, která dřív měla `DynamicResource` výraz jako místní hodnotu, `DynamicResource` je zcela odebrána. Podrobnosti najdete v tématu [přednost hodnota vlastnosti závislosti](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).  
  
 Některé scénáře přístupu prostředků jsou zvlášť vhodné pro `DynamicResource` naproti tomu [StaticResource – rozšíření značek](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md). V tématu [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md) diskuzi o relativních výhodách a ovlivnit výkon systému `DynamicResource` a `StaticResource`.  
  
 Zadaný <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> by měla odpovídat existující prostředek dáno [x: Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md) na určité úrovni v stránku, aplikace, k dispozici řízení motivy a externím prostředkům nebo prostředky systému a vyhledávání prostředků proběhne v tomto pořadí. Další informace o vyhledávání prostředků pro statické a dynamické prostředků najdete v tématu [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Klíč prostředku může být libovolný řetězec definovaný v [XamlName – gramatika](../../../../docs/framework/xaml-services/xamlname-grammar.md). Klíč prostředku může také být jiné typy objektů, jako třeba <xref:System.Type>. A <xref:System.Type> klíč je nezbytné, aby jak může být ve ovládací prvky podle motivů. Další informace najdete v tématu [vytváření – Přehled ovládacího prvku](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]pro vyhledávání prostředků hodnot jako například <xref:System.Windows.FrameworkElement.FindResource%2A>, postupujte podle stejné logiky vyhledávání prostředků jako použité ve `DynamicResource`.  
  
 Odkazování na prostředek alternativní deklarativní způsob je jako [StaticResource – rozšíření značek](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Token řetězec zadaný po `DynamicResource` řetězec identifikátoru je přiřazen jako <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> hodnotu základní <xref:System.Windows.DynamicResourceExtension> rozšíření třídy.  
  
 `DynamicResource`lze použít v syntaxi objekt elementu. V takovém případě určující hodnotu <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> vlastnost je povinná.  
  
 `DynamicResource`Můžete také použít využití podrobné atribut, který určuje <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> vlastnost jako vlastnost = dvojice hodnota:  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné. Protože `DynamicResource` má jenom jednu nastavit vlastnost, který je vyžadován, toto podrobné použití není Typická.  
  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementace procesor je definovaný zpracování pro toto rozšíření značek <xref:System.Windows.DynamicResourceExtension> třídy.  
  
 `DynamicResource`je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] použít {a} znaků v jejich syntaxi atributů, což je konvence, podle kterého [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor rozpozná, že rozšíření značek musí zpracovat atribut. Další informace najdete v tématu [rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také  
 [Prostředky XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Prostředky a kód](../../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [x:Key – direktiva](../../../../docs/framework/xaml-services/x-key-directive.md)  
 [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [Rozšíření značek StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)  
 [Rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
