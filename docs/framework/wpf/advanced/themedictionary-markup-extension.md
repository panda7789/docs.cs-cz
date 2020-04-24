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
ms.openlocfilehash: f6ba0fe45aa11063c79d673b26794072968f4200
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646190"
---
# <a name="themedictionary-markup-extension"></a>ThemeDictionary – rozšíření značek
Poskytuje způsob, jak pro vlastní autoři ovládacích prvků nebo aplikace, které integrují ovládací prvky třetích stran k načtení slovníky prostředků specifické pro motiv pro použití v styling ovládacího prvku.  
  
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
|`assemblyUri`|Identifikátor jednotného prostředku (URI) sestavení, který obsahuje informace o motivu. Obvykle se jedná o identifikátor URI balení, který odkazuje na sestavení ve větším balíčku. Prostředky sestavení a balíčky identifikátorů URI zjednodušují problémy s nasazením. Další informace naleznete [v tématu Pack URI v WPF](../app-development/pack-uris-in-wpf.md).|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozšíření je určeno k vyplnění pouze <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>jedné konkrétní hodnoty vlastnosti: hodnota pro .  
  
 Pomocí tohoto rozšíření můžete určit jedno sestavení pouze pro prostředky, které obsahuje některé styly, které se použijí pouze v případě, že je motiv Prostředí Windows použit v systému uživatele, jiné styly pouze v případě, že je aktivní motiv Luna a tak dále. Pomocí tohoto rozšíření obsah slovníku prostředků specifické pro ovládací prvek lze automaticky zneplatnit a znovu načíst být specifické pro jiný motiv v případě potřeby.  
  
 Řetězec `assemblyUri` (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> hodnota vlastnosti) tvoří základ konvence pojmenování, která určuje, který slovník platí pro konkrétní motiv. Logika <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> `ThemeDictionary` pro dokončení konvence generováním identifikátoru jednotného prostředku (URI), který odkazuje na konkrétní variantu slovníku motivu, jak je obsaženv rámci sestavení předkompilovaného prostředku. Popis této konvence nebo interakce motivu s obecným řídicím stylem a stylem na úrovni stránky/aplikace jako koncept emituje meze. Základní scénář pro `ThemeDictionary` použití je <xref:System.Windows.ResourceDictionary.Source%2A> určit `ResourceDictionary` vlastnost deklarované na úrovni aplikace. Pokud zadáte identifikátor URI pro `ThemeDictionary` sestavení prostřednictvím rozšíření, nikoli jako přímý identifikátor URI, logika rozšíření poskytne logiku zneplatnění, která se použije při každé změně motivu systému.  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Token řetězce zadaný `ThemeDictionary` po přidělení řetězce <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> identifikátoru jako <xref:System.Windows.ThemeDictionaryExtension> hodnota základní třídy rozšíření.  
  
 `ThemeDictionary`lze také použít v syntaxi prvku objektu. V tomto případě je vyžadováno <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> zadání hodnoty vlastnosti.  
  
 `ThemeDictionary`lze také použít v podrobném použití atributu, který určuje <xref:System.Windows.Markup.StaticExtension.Member%2A> vlastnost jako dvojici vlastností=hodnota:  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné. Protože `ThemeDictionary` má pouze jednu vlastnost settable, která je vyžadována, toto podrobné použití není typické.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] V implementaci procesoru zpracování pro toto rozšíření <xref:System.Windows.ThemeDictionaryExtension> značky je definována třídy.  
  
 `ThemeDictionary`je rozšíření značky. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používají znaky { a } v syntaxi atributu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] což je konvence, podle které procesor rozpozná, že rozšíření značek musí atribut zpracovat. Další informace naleznete [v tématu Markup Extensions a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také

- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Prostředek, obsah a datové soubory aplikace WPF](../app-development/wpf-application-resource-content-and-data-files.md)
