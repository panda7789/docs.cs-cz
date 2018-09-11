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
ms.openlocfilehash: f77f0a952224f79ee95a755cb848a4f8b68c9602
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44368465"
---
# <a name="xkey-directive"></a>x:Key – direktiva
Jednoznačně identifikuje elementy, které jsou vytvořeny a odkazovány ve slovníku definice XAML. Přidání `x:Key` hodnota prvku objektu XAML je nejběžnějším způsobem identifikace prostředku ve slovníku prostředků, například v WPF <xref:System.Windows.ResourceDictionary>.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>Použití atributu XAML (specifické pro WPF)  
  
```  
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
|`stringKeyValue`|Textový řetězec, který se použije jako klíč. Textový řetězec musí odpovídat [xamlname – gramatika](../../../docs/framework/xaml-services/xamlname-grammar.md).|  
|`markupExtensionUsage`|V rámci oddělovačů rozšíření značek {}, použití rozšíření značky, který poskytuje objekt pro použití jako klíč. Viz poznámky.|  
  
## <a name="remarks"></a>Poznámky  
 `x:Key` podporuje koncept slovníku prostředků XAML. XAML jako jazyk nedefinuje implementaci slovníku prostředků, která je ponechána pro určité systémy uživatelského rozhraní. Další informace o způsobu implementace slovníků prostředků XAML ve WPF, naleznete v tématu [prostředky XAML](../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 V XAML 2006 a WPF `x:Key` musí být uveden jako atribut. Můžete stále používat neřetězcové klíče, ale to vyžaduje použití rozšíření značky s cílem poskytnout neřetězcovou hodnotu ve formě atributu. Pokud používáte XAML 2009 `x:Key` se dá nastavit jako prvek, aby explicitně podporoval slovníky klíčované podle typů objektů jiných než řetězců bez nutnosti okamžitého rozšíření kódu. V tomto tématu v části "XAML 2009". Zbytek části poznámky platí konkrétně pro implementaci XAML 2006.  
  
 Hodnota atributu `x:Key` může být libovolný řetězec podle [xamlname – gramatika](../../../docs/framework/xaml-services/xamlname-grammar.md) nebo může být objekt vyhodnocený pomocí rozšíření značek. Viz "Poznámky k použití WPF" s příkladem pro WPF.  
  
 Podřízené elementy nadřazeného elementu, který je <xref:System.Collections.IDictionary> musí obvykle zahrnovat implementace `x:Key` atribut, který určuje jedinečnou hodnotu klíče v rámci daného slovníku. Rámce mohou implementovat klíčové vlastnosti s aliasy pro nahrazení `x:Key` na určité typy; typy, které definují tyto vlastnosti by měly být přiděleny s <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 Ekvivalentní kód pro zadání `x:Key` je klíč, který se používá jako základní <xref:System.Collections.IDictionary>. Například `x:Key` , který se používá ve značkách pro zdroj ve WPF je ekvivalentní hodnotě `key` parametr <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> když přidáte zdroj do WPF <xref:System.Windows.ResourceDictionary> v kódu.  
  
## <a name="wpf-usage-notes"></a>Poznámky k použití WPF  
 Podřízené objekty nadřazeného objektu, který je <xref:System.Collections.IDictionary> implementace, například WPF <xref:System.Windows.ResourceDictionary>, musí obvykle zahrnovat `x:Key` atribut a hodnota klíče musí být jedinečný v rámci daného slovníku. Existují dvě významné výjimky:  
  
-   Některé typy WPF deklarují implicitní klíč pro používání slovníku. Například <xref:System.Windows.Style> s <xref:System.Windows.Style.TargetType%2A>, nebo <xref:System.Windows.DataTemplate> s <xref:System.Windows.DataTemplate.DataType%2A>, může být v <xref:System.Windows.ResourceDictionary> a použít implicitní klíč.  
  
-   WPF podporuje koncept slovníku prostředků. Klíče mohou být sdíleny mezi sloučenými slovníky a ke sdílenému chování klíčů lze přistupovat pomocí <xref:System.Windows.FrameworkContentElement.FindResource%2A>. Další informace najdete v tématu [sloučené slovníky prostředků](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).  
  
 Ve celkové WPF XAML modelu implementace a aplikace není kompilátorem značky XAML povolená jedinečnost klíče. Místo toho chybějící nebo duplicitní `x:Key` hodnoty způsobit chyby analyzátoru XAML během načítání. Nicméně Visual Studio zpracování slovníků pro WPF může často zaznamenat tyto chyby ve fázi návrhu.  
  
 Všimněte si, že v zobrazené syntaxi <xref:System.Windows.ResourceDictionary> objektu je v tom, jak procesor WPF XAML vytváří kolekce k naplnění implicitní <xref:System.Windows.FrameworkElement.Resources%2A> kolekce. A <xref:System.Windows.ResourceDictionary> obvykle není k dispozici explicitně jako element ve značce, i když může být v některých případech, pokud je požadován pro přehlednost (by se jednat o prvek objektu kolekce mezi <xref:System.Windows.FrameworkElement.Resources%2A> naplnit vlastnost elementu a položkami, které slovník). Informace o tom, proč je objekt kolekce téměř vždy implicitním elementem značek, naleznete v tématu [syntaxe XAML v podrobnosti o](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
 V implementaci WPF XAML je zpracování klíčů slovníku prostředků definováno <xref:System.Windows.ResourceKey> abstraktní třídy. Nicméně procesor WPF XAML vytváří různé základní typy rozšíření pro klíče založené na jejich použití. Například klíč pro <xref:System.Windows.DataTemplate> nebo všechny odvozené třídy se využívá samostatně a vytváří samostatný <xref:System.Windows.DataTemplateKey> objektu.  
  
 Klíče a názvy využívají různé směrnice a jazykové prvky (`x:Key` oproti `x:Name`) v základní definici XAML. Klíče a názvy jsou také používány v různých situacích definicí WPF a aplikací těchto konceptů. Podrobnosti najdete v tématu [obory názvů WPF XAML](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
 Jak bylo uvedeno dříve, hodnota klíče může být poskytnuta prostřednictvím rozšíření značek a může být větší než hodnota řetězce. Příkladem scénáře WPF je, že hodnota `x:Key` může být [ComponentResourceKey](../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md). Některé ovládací prvky zveřejňují klíč stylu tohoto typu prostředku vlastního stylu, který ovlivní část vzhledu a chování ovládacího prvku bez úplného nahrazení stylu. Příklad takového klíče je <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.  
  
 Funkce sloučeného slovníku WPF zavádí další aspekty jedinečnosti klíče a chování při vyhledávání klíče. Další informace najdete v tématu [sloučené slovníky prostředků](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 zmírňuje omezení, která `x:Key` poskytne vždy ve formě atributu.  
  
 V WPF můžete použít funkce XAML 2009, ale pouze pro XAML, který není kompilována značka. Kompilována značka XAML pro WPF a BAML formu XAML aktuálně nepodporují klíčová slova XAML 2009 a funkce.  
  
 V části XAML 2009 můžete určit `x:Key` prvky pomocí následujícího využití:  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>Použití elementu XAML (pouze XAML 2009)  
  
```  
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
|`keyObject`|– Element pro objekt, který se používá jako klíč pro objekt daného `object` ve specializovaném slovníku.|  
  
-   Kontejner/nadřazený prvek pro tento typ použití zde není zobrazen. `object` Očekává se podřízený prvku objektu, který představuje implementaci specializovaného slovníku. `keyObject` Očekává se instance objektu (nebo hodnota typu hodnoty), která je vhodná jako klíč pro tuto implementaci určitého speciálního slovníku.  
  
-   WPF neimplementuje slovníky, které vyžadují toto využití. Klíče objektu je spíše obecnou funkcí jazyka XAML, užitečné případně v určitých vlastních scénářích slovníku kde je vytvoření slovníku v XAML žádoucí. Pro funkce WPF jako jsou implicitní styly, které používají neřetězcové klíče pro prostředky jiné techniky pro stanovení nebo určení klíče existují, takže není nutné použití klíče objektu.  
  
-   *keyObject* mohou být také použití rozšíření značky ve formuláři prvku objektu, nikoli instance přímého objektu.  
  
## <a name="silverlight-usage-notes"></a>Poznámky k použití aplikace Silverlight  
 `x:Key` pro prostředí Silverlight je zdokumentován samostatně. Další informace najdete v tématu [Namespace XAML (x:) Funkce jazyka (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Viz také  
 [Prostředky XAML](../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Prostředky a kód](../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [Rozšíření značek StaticResource](../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)
