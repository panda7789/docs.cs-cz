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
ms.openlocfilehash: ab38c2c885e230183852fff895e0a8a8f1d7a666
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459485"
---
# <a name="themedictionary-markup-extension"></a>ThemeDictionary – rozšíření značek
Poskytuje způsob, jak vlastní autoři ovládacích prvků nebo aplikace, které integrují ovládací prvky třetích stran pro načtení slovníků prostředků specifických pro motiv pro použití při stylování ovládacího prvku.  
  
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
|`assemblyUri`|Identifikátor URI (Uniform Resource Identifier) sestavení, které obsahuje informace o motivu. Obvykle se jedná o identifikátor URI balíčku, který odkazuje na sestavení ve větším balíčku. Prostředky sestavení a identifikátory URI balíčku zjednodušují problémy s nasazením. Další informace najdete v tématu [identifikátory URI Pack v](../app-development/pack-uris-in-wpf.md)subsystému WPF.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozšíření má vyplnit jenom jednu konkrétní hodnotu vlastnosti: hodnotu pro <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.  
  
 Pomocí tohoto rozšíření můžete zadat jediné sestavení pouze pro prostředky, které obsahuje některé styly, které se použijí, když se v systému uživatele použije motiv Windows Aero, ostatní styly, jenom když je motiv Luna aktivní a tak dále. Když použijete toto rozšíření, obsah slovníku prostředků specifický pro ovládací prvek se dá v případě potřeby automaticky zrušit a znovu načíst, aby byl pro jiný motiv specifický.  
  
 `assemblyUri` řetězec (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> hodnota vlastnosti) tvoří základ konvence pojmenování, která určuje, který slovník se použije pro konkrétní motiv. Logika <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> pro `ThemeDictionary` dokončí konvenci vygenerováním identifikátoru URI (Uniform Resource Identifier), který odkazuje na konkrétní variantu slovníku motivů, jak je obsaženo v předkompilovaném sestavení prostředků. Popis této konvence nebo interakce motivů s obecným stylem řízení a stylem stránky nebo aplikace jako konceptu se zde nepokrývá. Základní scénář použití `ThemeDictionary` je zadání vlastnosti <xref:System.Windows.ResourceDictionary.Source%2A> `ResourceDictionary` deklarované na úrovni aplikace. Pokud zadáte identifikátor URI pro sestavení prostřednictvím rozšíření `ThemeDictionary`, nikoli jako přímý identifikátor URI, logika rozšíření poskytne neplatnou logiku, která se použije vždy, když se změní motiv systému.  
  
 Nejčastějším typem syntaxe, která se používá u tohoto rozšíření značek, je syntaxe atributu. Token řetězce poskytnutý po řetězci `ThemeDictionary` identifikátoru je přiřazen jako hodnota <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> základní třídy rozšíření <xref:System.Windows.ThemeDictionaryExtension>.  
  
 `ThemeDictionary` lze také použít v syntaxi elementu Object. V takovém případě je nutné zadat hodnotu vlastnosti <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A>.  
  
 `ThemeDictionary` lze také použít v podrobném použití atributu, které určuje vlastnost <xref:System.Windows.Markup.StaticExtension.Member%2A> jako dvojici vlastnost = hodnota:  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 Použití podrobné syntaxe je často užitečné pro rozšíření, která mají více než jednu nastavitelnou vlastnost, nebo v případě, že jsou některé vlastnosti volitelné. Protože `ThemeDictionary` má pouze jednu nastavitelnou vlastnost, která je povinná, toto podrobné použití není typické.  
  
 V implementaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru je zpracování tohoto rozšíření značek definováno třídou <xref:System.Windows.ThemeDictionaryExtension>.  
  
 `ThemeDictionary` je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku, aby díky použití řídicí sekvence mohly být hodnoty atributů něčím jiným než literálními hodnotami nebo názvy obslužných rutin, a tento požadavek má tak rozsáhlou platnost, že nestačí jednoduše použít převaděče typů pro určité typy nebo vlastnosti. Všechna rozšíření značek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] používají znaky {a} v jejich syntaxi atributu, což je konvence, podle které procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] rozpoznává, že rozšíření značek musí zpracovat atribut. Další informace naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Viz také:

- [Styly a šablony](../controls/styling-and-templating.md)
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Prostředek, obsah a datové soubory aplikace WPF](../app-development/wpf-application-resource-content-and-data-files.md)
