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
ms.openlocfilehash: 4ffd7a2922c7f3ba35ccb9ac7ce29a6a00cd99af
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837204"
---
# <a name="xkey-directive"></a>x:Key – direktiva
Jednoznačně identifikuje elementy, které jsou vytvořeny a odkazovány ve slovníku definice XAML. Přidání hodnoty `x:Key` do prvku objektu XAML je nejběžnějším způsobem identifikace prostředku ve slovníku prostředku, například v WPF <xref:System.Windows.ResourceDictionary>.  
  
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
|`stringKeyValue`|Textový řetězec, který chcete použít jako klíč. Textový řetězec musí odpovídat [gramatice jazyka XAML](xamlname-grammar.md).|  
|`markupExtensionUsage`|V rámci oddělovačů rozšíření značek {}, použití rozšíření značek, které poskytuje objekt, který se má použít jako klíč. Viz poznámky.|  
  
## <a name="remarks"></a>Poznámky  
 `x:Key` podporuje koncept slovníku prostředků XAML. XAML jako jazyk nedefinuje implementaci slovníku prostředků, která je ponechána pro určité systémy uživatelského rozhraní. Další informace o tom, jak jsou slovníky prostředků XAML implementovány v subsystému WPF, naleznete v tématu [prostředky XAML](../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 V jazyce XAML 2006 a WPF musí být `x:Key` zadáno jako atribut. Můžete stále používat neřetězcové klíče, ale to vyžaduje použití rozšíření značky s cílem poskytnout neřetězcovou hodnotu ve formuláři atributu. Pokud používáte XAML 2009, `x:Key` lze zadat jako prvek, aby explicitně podporovala pouze slovníky pomocí jiných typů objektů než řetězců bez vyžadování zprostředkujícího rozšíření kódu. Viz část "XAML 2009" v tomto tématu. Zbytek oddílu poznámky platí konkrétně pro implementaci XAML 2006.  
  
 Hodnota atributu `x:Key` může být libovolný řetězec definovaný v [gramatice gramatiky](xamlname-grammar.md) nebo může být objekt vyhodnocený prostřednictvím rozšíření značek. Viz "Poznámky k použití WPF" s příkladem pro WPF.  
  
 Podřízené elementy nadřazeného elementu, který je implementace <xref:System.Collections.IDictionary>, musí obvykle zahrnovat atribut `x:Key`, který určuje jedinečnou hodnotu klíče v rámci daného slovníku. Rámce mohou implementovat klíčové vlastnosti s aliasy pro nahrazení `x:Key` na určité typy; typy, které definují tyto vlastnosti, by měly být přiděleny s <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 Ekvivalentní kód pro zadání `x:Key` je klíčem, který slouží jako základní <xref:System.Collections.IDictionary>. Například `x:Key`, který se používá ve značkách pro zdroj ve WPF je ekvivalentní hodnotě parametru `key` <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>, když přidáte zdroj do WPF <xref:System.Windows.ResourceDictionary> v kódu.  
  
## <a name="wpf-usage-notes"></a>Poznámky k použití WPF  
 Podřízené objekty nadřazeného objektu, který je implementace <xref:System.Collections.IDictionary>, například WPF <xref:System.Windows.ResourceDictionary>, musí obvykle zahrnovat atribut `x:Key` a klíčová hodnota musí být jedinečná v rámci daného slovníku. Existují dvě významné výjimky:  
  
- Některé typy WPF deklarují implicitní klíč pro používání slovníku. Například <xref:System.Windows.Style> s <xref:System.Windows.Style.TargetType%2A> nebo <xref:System.Windows.DataTemplate> s <xref:System.Windows.DataTemplate.DataType%2A> může být v <xref:System.Windows.ResourceDictionary> a použít implicitní klíč.  
  
- WPF podporuje koncept sloučeného slovníku prostředků. Klíče mohou být sdíleny mezi sloučenými slovníky a ke sdílenému chování klíčů lze přistupovat pomocí <xref:System.Windows.FrameworkContentElement.FindResource%2A>. Další informace najdete v tématu [sloučené slovníky prostředků](../wpf/advanced/merged-resource-dictionaries.md).  
  
 V celkovém modelu implementace a aplikace WPF XAML není kompilátorem značky XAML kontrolována jedinečnost klíče. Místo toho chybějící nebo duplicitní hodnoty `x:Key` způsobí chyby při načítání analyzátoru XAML. Zpracování slovníkových slovníků v aplikaci Visual Studio pro WPF však často může ve fázi návrhu znamenat chyby.  
  
 Všimněte si, že v zobrazené syntaxi je objekt <xref:System.Windows.ResourceDictionary> implicitní ve smyslu, jakým procesor WPF XAML vytváří kolekce k naplnění kolekce <xref:System.Windows.FrameworkElement.Resources%2A>. <xref:System.Windows.ResourceDictionary> obvykle není k dispozici explicitně jako element ve značce, i když v některých případech může být, pokud je požadován pro přehlednost (jednalo by se o prvek objektu kolekce objektů mezi prvkem vlastnosti <xref:System.Windows.FrameworkElement.Resources%2A> a položkami, které slovník zaplní). Informace o tom, proč je objekt kolekce téměř vždy implicitním prvkem v kódu, naleznete [v tématu Syntaxe jazyka XAML podrobněji](../wpf/advanced/xaml-syntax-in-detail.md).  
  
 Při implementaci WPF XAML je zpracování klíčů slovníku prostředků definováno abstraktní třídou <xref:System.Windows.ResourceKey>. Nicméně procesor WPF XAML vytváří různé základní typy rozšíření pro klíče založené na jejich použití. Například klíč pro <xref:System.Windows.DataTemplate> a všechny odvozené třídy se využívá samostatně a vytváří samostatný objekt <xref:System.Windows.DataTemplateKey>.  
  
 Klíče a názvy využívají různé směrnice a jazykové prvky (`x:Key` oproti `x:Name`) v základní definici XAML. Klíče a názvy jsou také používány v různých situacích definicí WPF a aplikací těchto konceptů. Podrobnosti najdete v tématu [WPF XAML obory názvů WPF](../wpf/advanced/wpf-xaml-namescopes.md).  
  
 Jak bylo uvedeno dříve, hodnota klíče může být poskytnuta prostřednictvím rozšíření kódu a může být větší než hodnota řetězce. Příkladem scénáře WPF je, že hodnota `x:Key` může být [ComponentResourceKey](../wpf/advanced/componentresourcekey-markup-extension.md). Některé ovládací prvky zveřejňují klíč stylu tohoto typu prostředku vlastního stylu, který ovlivní část vzhledu a chování ovládacího prvku bez úplného nahrazení stylu. Příklad takového klíče je <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.  
  
 Funkce sloučeného slovníku WPF zavádí další aspekty jedinečnosti klíče a chování při vyhledávání klíče. Další informace najdete v tématu [sloučené slovníky prostředků](../wpf/advanced/merged-resource-dictionaries.md).  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 omezuje omezení, které `x:Key` vždy k dispozici ve formě atributu.  
  
 V WPF můžete použít funkce XAML 2009, ale pouze pro XAML, které nejsou kompilovány pomocí značek. XAML kompilovaný kód XAML pro WPF a formát BAML jazyka XAML aktuálně nepodporují klíčová slova a funkce XAML 2009.  
  
 V části XAML 2009 můžete určit `x:Key` prvky pomocí následujícího použití:  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>Použití elementu XAML (pouze XAML 2009)  
  
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
|`keyObject`|Prvek objektu pro objekt, který slouží jako klíč pro daný `object` ve specializovaném slovníku.|  
  
- Kontejner/nadřazený prvek pro tento typ použití zde není zobrazen. Očekává se, že `object` bude podřízený prvku objektu, který představuje implementaci specializovaného slovníku. U `keyObject` se předpokládá, že bude instancí objektu (nebo hodnota typu hodnoty), která je vhodná jako klíč pro implementaci určitého speciálního slovníku.  
  
- WPF neimplementuje slovníky, které vyžadují toto využití. Klíče objektu jsou spíše obecnou funkcí jazyka XAML, užitečné případně v určitých vlastních scénářích slovníku, kde je vytvoření slovníku v jazyce XAML žádoucí. Pro funkce WPF jako jsou implicitní styly, které používají neřetězcové klíče pro prostředky, jiné techniky pro stanovení nebo určení klíče existují, takže není nutné použití klíče objektu.  
  
- *objektem* může být také použití rozšíření značek ve formuláři elementu objektu, nikoli přímo instance objektu.  
  
## <a name="silverlight-usage-notes"></a>Poznámky k použití aplikace Silverlight  
 `x:Key` pro prostředí Silverlight je zdokumentován samostatně. Další informace naleznete v tématu [obor názvů XAML (x:). Jazykové funkce (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).  
  
## <a name="see-also"></a>Viz také:

- [Prostředky XAML](../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Prostředky a kód](../wpf/advanced/resources-and-code.md)
- [Rozšíření značek StaticResource](../wpf/advanced/staticresource-markup-extension.md)
