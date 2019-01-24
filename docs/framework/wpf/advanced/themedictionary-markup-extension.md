---
title: ThemeDictionary – rozšíření značek
ms.date: 03/30/2017
f1_keywords:
- ThemeDictionaryExtension
- ThemeDictionary
helpviewer_keywords:
- ThemeDictionary markup extension [WPF]
- XAML [WPF], ThemeDictionary markup extension
ms.assetid: aa75e10b-13dd-4989-972d-51bab63a05e2
ms.openlocfilehash: 659af630f697d7f2742bc71006241c4bded842c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718920"
---
# <a name="themedictionary-markup-extension"></a>ThemeDictionary – rozšíření značek
Poskytuje způsob, jak pro vlastní ovládací prvek autorů nebo aplikace, které se integrují ovládací prvky třetích stran pro načtení konkrétní motivu zdrojových slovnících pro použití v používání stylů pro ovládací prvek.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>Použití elementu objektu XAML  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`assemblyUri`|[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] Sestavení, který obsahuje informace o motivech. Obvykle je to identifikátor URI, který odkazuje na sestavení v balíčku větší sadu. Prostředky sestavení a sady identifikátorů URI pro zjednodušení problémů s nasazením. Další informace najdete v části [identifikátory Pack URI v subsystému WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozšíření je určený k vyplnění pouze jednu hodnotu určité vlastnosti: hodnota pro <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.  
  
 Pomocí tohoto rozšíření, můžete určit jedno sestavení pouze pro prostředky, který obsahuje některé styly používat pouze tehdy, když [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] motivu systému uživatele, i jiné styly při Luna motivu je aktivní a tak dále. Pomocí tohoto rozšíření obsah slovník prostředků specifických pro ovládací prvek může být automaticky zneplatněny a specifické pro jiný motiv v případě potřeby znovu načíst.  
  
 `assemblyUri` Řetězce (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> hodnotu vlastnosti) tento balíček je základem zásady vytváření názvů identifikuje slovník, který se vztahuje na konkrétní motivu. <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> Logiku pro `ThemeDictionary` dokončení úmluvy vygenerováním [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] , která odkazuje na hodnotu typu variant slovníku konkrétní motivu obsažené v rámci sestavení předkompilované prostředků. Popisující vytváření názvů nebo motivu interakce s používání stylů pro ovládací prvek obecné a úrovni stylů stránky nebo aplikace jako koncept, není součástí tohoto plně. Základní scénář pro použití `ThemeDictionary` je zadání <xref:System.Windows.ResourceDictionary.Source%2A> vlastnost `ResourceDictionary` deklarované na úrovni aplikace. Když zadáte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro sestavení prostřednictvím `ThemeDictionary` rozšíření, nikoli jako přímou [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], logiku rozšíření poskytne zneplatnění logiku, která se použije při každé změně motiv systému.  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Řetězec s tokenem uvedený za `ThemeDictionary` řetězec identifikátoru je přiřazen jako <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> hodnoty základního <xref:System.Windows.ThemeDictionaryExtension> rozšíření třídy.  
  
 `ThemeDictionary` může také použít v syntaxi elementu objektu. V takovém případě zadáte hodnotu <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> vlastnost je povinná.  
  
 `ThemeDictionary` je také možné využití podrobné atribut, který určuje <xref:System.Windows.Markup.StaticExtension.Member%2A> vlastnost jako vlastnost = hodnota pár:  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné. Protože `ThemeDictionary` má jen jednu nastavitelnou vlastnost, která je požadována, toto použití podrobné syntaxe není typické.  
  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementace procesoru, zpracování tohoto rozšíření značek definováno <xref:System.Windows.ThemeDictionaryExtension> třídy.  
  
 `ThemeDictionary` je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] použít {a} znaků v syntaxi atributu, což je konvence, podle kterého [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru rozpozná, že rozšíření značek musí zpracovat atribut. Další informace najdete v tématu [– rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také:
- [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [Rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [Prostředek, obsah a datové soubory aplikace WPF](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
