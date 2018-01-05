---
title: "ThemeDictionary – rozšíření značek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ThemeDictionaryExtension
- ThemeDictionary
helpviewer_keywords:
- ThemeDictionary markup extension [WPF]
- XAML [WPF], ThemeDictionary markup extension
ms.assetid: aa75e10b-13dd-4989-972d-51bab63a05e2
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2372961cdc889528f13e13dd1f1760608030275e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="themedictionary-markup-extension"></a>ThemeDictionary – rozšíření značek
Umožňuje autorům vlastní ovládací prvek nebo aplikací, které se integrují ovládací prvky třetích stran načíst slovnících prostředků motiv specifické pro použití v styly ovládacího prvku.  
  
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
|`assemblyUri`|[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] Sestavení, který obsahuje informace o motivu. Obvykle je to identifikátor URI, který odkazuje na sestavení v větší balíčku aktualizací Service pack. Prostředky sestavení a pack identifikátory URI zjednodušit problémy při nasazení. Další informace najdete v části [Pack identifikátory URI v grafickém subsystému WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozšíření je určený k vyplnění pouze jednu hodnotu určitou vlastnost: hodnotu <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.  
  
 Když použijete toto rozšíření, můžete zadat jednoho pouze prostředky sestavení, který obsahuje některé styly používat pouze tehdy, když [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] motivu uživatele systému, jiné styly po vzhled Luna motiv aktivní a tak dále. Pomocí tohoto rozšíření obsah slovník prostředků specifické pro ovládací prvek může být automaticky zrušena znovu načíst a specifické pro jiný motiv vyžádání.  
  
 `assemblyUri` Řetězec (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> hodnotu vlastnosti) je základem zásady vytváření názvů, který identifikuje, který slovník platí pro konkrétní motiv. <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> Logiku pro `ThemeDictionary` dokončení konvence vygenerováním [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] který odkazuje na hodnotu typu variant slovník konkrétní motiv jako obsažené v sestavení předkompilovaných prostředků. Popisující tento convention nebo motivu interakce s obecné řízení styly a úrovně stylů stránky nebo aplikace jako koncept a nepopisuje plně sem. Základní scénáře použití `ThemeDictionary` slouží k zadání <xref:System.Windows.ResourceDictionary.Source%2A> vlastnost `ResourceDictionary` deklarovat na úrovni aplikace. Když zadáte [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pro sestavení prostřednictvím `ThemeDictionary` rozšíření a nikoli jako přímou [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], logiku rozšíření zajistí zneplatnění logiku, která se použije při každé změně motiv systému.  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Token řetězec zadaný po `ThemeDictionary` řetězec identifikátoru je přiřazen jako <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> hodnotu základní <xref:System.Windows.ThemeDictionaryExtension> rozšíření třídy.  
  
 `ThemeDictionary`také je možné použít objekt elementu syntaxe. V takovém případě určující hodnotu <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> vlastnost je povinná.  
  
 `ThemeDictionary`Můžete také použít využití podrobné atribut, který určuje <xref:System.Windows.Markup.StaticExtension.Member%2A> vlastnost jako vlastnost = dvojice hodnota:  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné. Protože `ThemeDictionary` má jenom jednu nastavit vlastnost, který je vyžadován, toto podrobné použití není Typická.  
  
 V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementace procesor je definovaný zpracování pro toto rozšíření značek <xref:System.Windows.ThemeDictionaryExtension> třídy.  
  
 `ThemeDictionary`je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] použít {a} znaků v jejich syntaxi atributů, což je konvence, podle kterého [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor rozpozná, že rozšíření značek musí zpracovat atribut. Další informace najdete v tématu [rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [Prostředek, obsah a datové soubory aplikace WPF](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
