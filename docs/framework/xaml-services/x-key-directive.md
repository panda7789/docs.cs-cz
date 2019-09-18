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
ms.openlocfilehash: eb9f9cc1dfdb802e340123d0d39e9c9ebaa457f0
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053748"
---
# <a name="xkey-directive"></a>x:Key – direktiva
Jednoznačně identifikuje elementy, které jsou vytvořeny a odkazovány ve slovníku definovaném v jazyce XAML. Přidání hodnoty do prvku objektu XAML je nejběžnější způsob, jak identifikovat prostředek ve slovníku prostředků, například v WPF <xref:System.Windows.ResourceDictionary>. `x:Key`  
  
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
|`stringKeyValue`|Textový řetězec, který se má použít jako klíč Textový řetězec musí odpovídat [gramatice jazyka XAML](xamlname-grammar.md).|  
|`markupExtensionUsage`|V rámci oddělovačů {}rozšíření značek je použití rozšíření značek, které poskytuje objekt, který se má použít jako klíč. Viz poznámky.|  
  
## <a name="remarks"></a>Poznámky  
 `x:Key`podporuje koncept slovníku prostředků XAML. XAML jako jazyk nedefinuje implementaci slovníku prostředků, která je ponechána na konkrétní architektury uživatelského rozhraní. Další informace o tom, jak jsou slovníky prostředků XAML implementovány v subsystému WPF, naleznete v tématu [prostředky XAML](../wpf/advanced/xaml-resources.md).  
  
 V jazyce XAML 2006 a WPF `x:Key` je třeba zadat atribut. Pořád můžete používat neřetězcové klíče, ale to vyžaduje použití rozšíření značek, aby bylo možné poskytnout neřetězcovou hodnotu ve formě atributu. Pokud používáte XAML 2009, `x:Key` lze zadat jako element, aby explicitně podporovala slovní kódování pomocí jiných typů objektů než řetězců bez vyžadování zprostředkujícího rozšíření kódu. Viz část "XAML 2009" v tomto tématu. Zbytek oddílu poznámky platí konkrétně pro implementaci XAML 2006.  
  
 Hodnota `x:Key` atributu může být libovolný řetězec definovaný v [gramatice gramatiky](xamlname-grammar.md) nebo může být objekt vyhodnocený prostřednictvím rozšíření značek. Příklad z WPF naleznete v tématu "poznámky k použití WPF".  
  
 Podřízené prvky nadřazeného elementu, který je <xref:System.Collections.IDictionary> implementací, musí obvykle `x:Key` zahrnovat atribut, který určuje jedinečnou hodnotu klíče v rámci tohoto slovníku. Rozhraní mohou implementovat vlastnosti klíče s aliasy k nahrazení `x:Key` na konkrétní typy; typy, které tyto vlastnosti definují, by měly být s <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>atributem.  
  
 Ekvivalent kódu pro zadání `x:Key` je klíč, který se používá pro základní. <xref:System.Collections.IDictionary> Například `x:Key` , který je použit v označení pro prostředek v WPF, je ekvivalentní hodnotě `key` parametru <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> , když přidáte prostředek do WPF <xref:System.Windows.ResourceDictionary> v kódu.  
  
## <a name="wpf-usage-notes"></a>Poznámky k použití WPF  
 Podřízené objekty nadřazeného objektu, který je <xref:System.Collections.IDictionary> implementací, jako je například WPF <xref:System.Windows.ResourceDictionary> `x:Key` , musí obvykle zahrnovat atribut a hodnota klíče musí být v rámci tohoto slovníku jedinečná. Existují dvě významné výjimky:  
  
- Některé typy WPF deklaruje implicitní klíč pro použití slovníku. <xref:System.Windows.Style> Například a <xref:System.Windows.ResourceDictionary> s <xref:System.Windows.Style.TargetType%2A> ,nebo<xref:System.Windows.DataTemplate> s ,můžebýtva<xref:System.Windows.DataTemplate.DataType%2A>použít implicitní klíč.  
  
- WPF podporuje koncept sloučeného slovníku prostředků. Klíče lze sdílet mezi sloučenými slovníky a chování sdíleného klíče lze použít pomocí nástroje <xref:System.Windows.FrameworkContentElement.FindResource%2A>. Další informace najdete v tématu [sloučené slovníky prostředků](../wpf/advanced/merged-resource-dictionaries.md).  
  
 V celkové implementaci a modelu aplikace WPF XAML není kontrolována klíčová jedinečnost kompilátorem kódu XAML. Místo toho chybějící nebo nejedinečné `x:Key` hodnoty způsobují chyby analyzátoru XAML při načítání. Zpracování slovníkových slovníků v aplikaci Visual Studio pro WPF však často může ve fázi návrhu znamenat chyby.  
  
 Všimněte si, že v zobrazené syntaxi je <xref:System.Windows.ResourceDictionary> objekt implicitní ve způsobu, jakým procesor WPF XAML generuje kolekci k <xref:System.Windows.FrameworkElement.Resources%2A> naplnění kolekce. Není obvykle poskytován explicitně jako element v kódu, i když může být v některých případech, pokud je potřeba pro přehlednost (by to byl prvek objektu kolekce <xref:System.Windows.FrameworkElement.Resources%2A> mezi prvkem vlastnosti a položky v rámci, které naplní <xref:System.Windows.ResourceDictionary> slovník). Informace o tom, proč je objekt kolekce téměř vždy implicitním prvkem v kódu, naleznete [v tématu Syntaxe jazyka XAML podrobněji](../wpf/advanced/xaml-syntax-in-detail.md).  
  
 V implementaci WPF XAML je zpracování klíčů pro slovníky prostředků definováno <xref:System.Windows.ResourceKey> abstraktní třídou. Procesor WPF XAML však vytváří různé základní typy rozšíření pro klíče na základě jejich použití. Například klíč pro <xref:System.Windows.DataTemplate> nebo jakoukoliv odvozenou třídu je zpracováván samostatně a vytvoří odlišný <xref:System.Windows.DataTemplateKey> objekt.  
  
 Klíče a názvy používají různé direktivy a jazykové prvky`x:Key` ( `x:Name`versus) v definici Basic XAML. Klíče a názvy jsou také používány v různých situacích definice WPF a aplikací těchto konceptů. Podrobnosti najdete v tématu [WPF XAML obory názvů WPF](../wpf/advanced/wpf-xaml-namescopes.md).  
  
 Jak bylo uvedeno dříve, hodnota klíče může být poskytnuta prostřednictvím rozšíření značek a může být jiná než hodnota řetězce. Příkladem scénáře WPF je, že hodnota `x:Key` může být [ComponentResourceKey](../wpf/advanced/componentresourcekey-markup-extension.md). Některé ovládací prvky zpřístupňují klíč stylu daného typu pro prostředek vlastního stylu, který ovlivňuje část vzhledu a chování daného ovládacího prvku, aniž by zcela nahradil styl. Příkladem takového klíče je <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.  
  
 Funkce sloučeného slovníku WPF zavádí další důležité informace týkající se jedinečnosti klíčů a chování vyhledávání klíčů. Další informace najdete v tématu [sloučené slovníky prostředků](../wpf/advanced/merged-resource-dictionaries.md).  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 omezuje omezení, které `x:Key` je vždy k dispozici ve formě atributu.  
  
 V WPF můžete použít funkce XAML 2009, ale pouze pro XAML, které nejsou kompilovány pomocí značek. XAML kompilovaný kód XAML pro WPF a formát BAML jazyka XAML aktuálně nepodporují klíčová slova a funkce XAML 2009.  
  
 V části XAML 2009 můžete určit `x:Key` prvky pomocí následujícího použití:  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>Použití prvku XAML (pouze XAML 2009)  
  
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
|`keyObject`|Prvek objektu pro objekt, který je použit jako klíč pro daný `object` ve specializovaném slovníku.|  
  
- Kontejner/nadřazený objekt pro tento druh použití není zde zobrazen. `object`očekává se, že bude podřízený objekt elementu, který představuje implementaci specializovaného slovníku. `keyObject`očekává se, že bude instancí objektu (nebo hodnotou typu hodnoty), která je vhodná jako klíč pro konkrétní specializovanou implementaci slovníku.  
  
- WPF neimplementuje slovníky, které vyžadují toto použití. Klíče objektu jsou obecnější funkce jazyka XAML, které mohou být užitečné pro některé vlastní slovníky scénářů, kde je vhodné vytvořit slovník v jazyce XAML. Pro funkce WPF, jako jsou například implicitní styly, které používají neřetězcové klíče pro prostředky, existují jiné techniky pro vytváření a určování klíčů, takže použití klíče objektu není nutné.  
  
- *objektem* může být také použití rozšíření značek ve formuláři elementu objektu, nikoli přímo instance objektu.  
  
## <a name="silverlight-usage-notes"></a>Poznámky k používání Silverlight  
 `x:Key`Silverlight je dokumentován samostatně. Další informace naleznete v tématu [obor názvů XAML (x:). Jazykové funkce (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Viz také:

- [Prostředky XAML](../wpf/advanced/xaml-resources.md)
- [Prostředky a kód](../wpf/advanced/resources-and-code.md)
- [Rozšíření značek StaticResource](../wpf/advanced/staticresource-markup-extension.md)
