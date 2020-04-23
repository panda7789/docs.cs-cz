---
title: x:Key – direktiva
ms.date: 03/30/2017
f1_keywords:
- xKey
- Key
- x:Key
helpviewer_keywords:
- x:Key attribute [XAML Services]
- Key attribute in XAML [XAML Services]
- XAML [XAML Services], x:Key attribute
ms.assetid: 1985cd45-f197-42d5-b75e-886add64b248
ms.openlocfilehash: c05f98932ceceeb1530b34a09b1923f2af1378b5
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071498"
---
# <a name="xkey-directive"></a>x:Key – direktiva
Jednoznačně identifikuje prvky, které jsou vytvořeny a odkazovány ve slovníku definovaném XAML. Přidání `x:Key` hodnoty k prvku objektu XAML je nejběžnější způsob identifikace prostředku ve slovníku prostředků, například v WPF <xref:System.Windows.ResourceDictionary>.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>Použití atributu XAML (specifické pro WPF)  
  
```xaml  
<object.Resources>  
  <object x:Key="stringKeyValue".../>  
</object.Resources>  
-or-  
<object.Resources>  
  <object x:Key="{markupExtensionUsage}".../>  
</object.Resources>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`stringKeyValue`|Textový řetězec, který se má použít jako klíč. Textový řetězec musí odpovídat [gramatice XamlName](xamlname-grammar.md).|  
|`markupExtensionUsage`|V rámci oddělovačů {}rozšíření značek použití rozšíření značek, které poskytuje objekt použít jako klíč. Viz Poznámky.|  
  
## <a name="remarks"></a>Poznámky  
 `x:Key`podporuje koncept slovníku prostředků XAML. XAML jako jazyk nedefinuje implementaci slovníku prostředků, která je ponechána na konkrétní rozhraní uživatelského rozhraní. Další informace o implementaci slovníků prostředků XAML v wpf naleznete v tématu [XAML Resources](../fundamentals/xaml-resources-define.md).  
  
 V XAML 2006 a `x:Key` WPF musí být poskytnuty jako atribut. Stále můžete použít neřetězcové klíče, ale to vyžaduje použití rozšíření značek, aby byla poskytnuta hodnota nonstring ve formě atributu. Pokud používáte XAML 2009, `x:Key` lze zadat jako prvek, explicitně podporovat slovníky klíčové typy objektů než řetězce bez nutnosti rozšíření značky zprostředkující. Viz část "XAML 2009" v tomto tématu. Zbývající část poznámky se vztahuje konkrétně na implementaci XAML 2006.  
  
 Hodnota atributu `x:Key` může být libovolný řetězec definovaný v [gramatice XamlName](xamlname-grammar.md) nebo může být objekt emitován pomocí rozšíření značek. Viz "WPF Poznámky k použití" pro příklad z WPF.  
  
 Podřízené prvky nadřazeného prvku, který je implementací, <xref:System.Collections.IDictionary> musí obvykle obsahovat `x:Key` atribut, který určuje jedinečnou hodnotu klíče v rámci tohoto slovníku. Architektury mohou implementovat aliased klíčové `x:Key` vlastnosti nahradit na konkrétní typy; typy, které definují tyto <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>vlastnosti by měly být přiřazeny .  
  
 Kód ekvivalent určení `x:Key` je klíč, který se <xref:System.Collections.IDictionary>používá pro podkladové . `x:Key` Například, který je použit ve značkách pro prostředek v WPF `key` je <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> ekvivalentní hodnotu parametru <xref:System.Windows.ResourceDictionary> při přidání prostředku wpf v kódu.  
  
## <a name="wpf-usage-notes"></a>Poznámky k použití WPF  
 Podřízené objekty nadřazeného objektu, který je implementací, <xref:System.Collections.IDictionary> například WPF <xref:System.Windows.ResourceDictionary>, musí obvykle obsahovat `x:Key` atribut a hodnota klíče musí být v rámci tohoto slovníku jedinečná. Existují dvě významné výjimky:  
  
- Některé typy WPF deklarují implicitní klíč pro použití slovníku. Například <xref:System.Windows.Style> s <xref:System.Windows.Style.TargetType%2A>, nebo <xref:System.Windows.DataTemplate> s <xref:System.Windows.DataTemplate.DataType%2A>, může být <xref:System.Windows.ResourceDictionary> v a použít implicitní klíč.  
  
- WPF podporuje koncept slovníku sloučených prostředků. Klíče lze sdílet mezi sloučenými slovníky a chování sdíleného <xref:System.Windows.FrameworkContentElement.FindResource%2A>klíče lze přistupovat pomocí . Další informace naleznete [v tématu Merged Resource Dictionaries](../../framework/wpf/advanced/merged-resource-dictionaries.md).  
  
 V celkové implementaci WPF XAML a aplikačním modelu není jedinečnost klíče kontrolována kompilátorem značek XAML. Místo toho chybějící `x:Key` nebo nejedinečné hodnoty způsobit chyby analyzátoru XAML v době načítání. Visual Studio zpracování slovníků pro WPF však často zaznamenávat takové chyby ve fázi návrhu.  
  
 Všimněte si, že <xref:System.Windows.ResourceDictionary> v syntaxi uvedené objektje implicitní v tom, jak <xref:System.Windows.FrameworkElement.Resources%2A> WPF XAML procesor vytváří kolekci naplnit kolekce. A <xref:System.Windows.ResourceDictionary> není obvykle k dispozici explicitně jako prvek ve značkách, i když může být v některých <xref:System.Windows.FrameworkElement.Resources%2A> případech, pokud chtěl pro přehlednost (by se prvek objektu kolekce mezi element vlastnosti a položky v rámci které naplnit slovník). Informace o tom, proč je objekt kolekce téměř vždy implicitním prvkem ve značkách, naleznete [v podrobnostech syntaxe XAML .](../../framework/wpf/advanced/xaml-syntax-in-detail.md)  
  
 V implementaci WPF XAML je zpracování klíčů slovníku <xref:System.Windows.ResourceKey> prostředků definováno abstraktní třídou. Procesor WPF XAML však vytváří různé základní typy rozšíření pro klíče na základě jejich použití. Například klíč pro <xref:System.Windows.DataTemplate> nebo jakékoli odvozené třídy je zpracována <xref:System.Windows.DataTemplateKey> samostatně a vytváří odlišný objekt.  
  
 Klíče a názvy používají různé`x:Key` direktivy a jazykové prvky ( versus `x:Name`) v základní definici XAML. Klíče a názvy jsou také používány v různých situacích wpf definice a použití těchto pojmů. Podrobnosti naleznete v tématu [WPF XAML Namescopes](../../framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
 Jak již bylo uvedeno dříve, hodnota klíče může být zadána prostřednictvím rozšíření značek a může být jiná než hodnota řetězce. Příkladem wpf scénář je, `x:Key` že hodnota může být [ComponentResourceKey](../../framework/wpf/advanced/componentresourcekey-markup-extension.md). Některé ovládací prvky zveřejňují klíč stylu tohoto typu pro prostředek vlastního stylu, který ovlivňuje část vzhledu a chování tohoto ovládacího prvku, aniž by zcela nahradil styl. Příkladem takového klíče je <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.  
  
 Funkce sloučeného slovníku WPF zavádí další důležité informace o jedinečnosti klíče a chování vyhledávání klíčů. Další informace naleznete [v tématu Merged Resource Dictionaries](../../framework/wpf/advanced/merged-resource-dictionaries.md).  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 uvolňuje omezení, které `x:Key` jsou vždy poskytovány ve formě atributu.  
  
 V WPF můžete použít funkce XAML 2009, ale pouze pro XAML, který není zkompilován značkami. XAML kompilované značkami pro WPF a formu BAML XAML aktuálně nepodporují klíčová slova a funkce XAML 2009.  
  
 V části XAML 2009 `x:Key` můžete určit prvky pomocí následujícího použití:  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>Použití prvku XAML (pouze XAML 2009)  
  
```xaml  
<object>  
  <x:Key>  
keyObject  
  </x:Key>  
...  
</object>  
```  
  
### <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`keyObject`|Objektový prvek pro objekt, který se `object` používá jako klíč pro daný ve specializovaném slovníku.|  
  
- Kontejner/nadřazený pro tento druh použití není zde zobrazen. `object`očekává se, že bude podřízený prvek objektu, který představuje implementaci specializovaného slovníku. `keyObject`očekává se, že instance objektu (nebo hodnota typu hodnoty), která je vhodná jako klíč pro konkrétní implementaci specializovaného slovníku.  
  
- WPF neimplementuje slovníky, které vyžadují toto použití. Klíče objektů je obecnější funkce jazyka XAML, případně užitečné pro některé scénáře vlastního slovníku, kde je žádoucí vytvořit slovník v XAML. Pro wpf funkce, jako jsou implicitní styly, které používají klíče bez řetězce pro prostředky, existují jiné techniky pro vytvoření nebo určení klíčů, takže použití klíče objektu není nutné.  
  
- `keyObject`může být také použití rozšíření značky ve formě prvku objektu, nikoli instance přímého objektu.  
  
## <a name="silverlight-usage-notes"></a>Poznámky k použití aplikace Silverlight  
 `x:Key`pro Program Silverlight je dokumentován samostatně. Další informace naleznete v [tématu XAML Namespace (x:) Jazykové funkce (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).  
  
## <a name="see-also"></a>Viz také

- [Zdroje XAML](../fundamentals/xaml-resources-define.md)
- [Zdroje a kód](../../framework/wpf/advanced/resources-and-code.md)
- [StaticResource – rozšíření značek](../../framework/wpf/advanced/staticresource-markup-extension.md)
