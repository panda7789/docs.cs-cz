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
ms.openlocfilehash: 8321a09db31c9f6d2103a252a195fcdbf8da3e66
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283860"
---
# <a name="xkey-directive"></a>x:Key – direktiva
Jednoznačně identifikuje elementy, které jsou vytvořeny a odkazovány ve slovníku definovaném v jazyce XAML. Přidání `x:Key` hodnoty do prvku objektu XAML je nejběžnější způsob, jak identifikovat prostředek ve slovníku prostředků, například v <xref:System.Windows.ResourceDictionary>WPF.  
  
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
|`markupExtensionUsage`|V rámci oddělovačů rozšíření značek {}, použití rozšíření značek, které poskytuje objekt, který se má použít jako klíč. Viz poznámky.|  
  
## <a name="remarks"></a>Poznámky  
 `x:Key` podporuje koncept slovníku prostředků XAML. XAML jako jazyk nedefinuje implementaci slovníku prostředků, která je ponechána na konkrétní architektury uživatelského rozhraní. Další informace o tom, jak jsou slovníky prostředků XAML implementovány v subsystému WPF, naleznete v tématu [prostředky XAML](../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 V jazyce XAML 2006 a WPF musí být `x:Key` zadáno jako atribut. Pořád můžete používat neřetězcové klíče, ale to vyžaduje použití rozšíření značek, aby bylo možné poskytnout neřetězcovou hodnotu ve formě atributu. Pokud používáte XAML 2009, `x:Key` lze zadat jako prvek, aby explicitně podporovala pouze slovníky pomocí jiných typů objektů než řetězců bez vyžadování zprostředkujícího rozšíření kódu. Viz část "XAML 2009" v tomto tématu. Zbytek oddílu poznámky platí konkrétně pro implementaci XAML 2006.  
  
 Hodnota atributu `x:Key` může být libovolný řetězec definovaný v [gramatice gramatiky](xamlname-grammar.md) nebo může být objekt vyhodnocený prostřednictvím rozšíření značek. Příklad z WPF naleznete v tématu "poznámky k použití WPF".  
  
 Podřízené prvky nadřazeného elementu, který je <xref:System.Collections.IDictionary> implementace, musí obvykle zahrnovat atribut `x:Key`, který určuje jedinečnou hodnotu klíče v rámci tohoto slovníku. Rozhraní můžou implementovat klíčové vlastnosti s aliasy, které nahradí `x:Key` určitých typů; typy, které definují takové vlastnosti, by měly mít atribut <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 Kód ekvivalentu určení `x:Key` je klíč, který se používá pro podkladovou <xref:System.Collections.IDictionary>. Například `x:Key`, který je použit v označení pro prostředek v WPF, je ekvivalentní hodnotě parametru `key` <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> při přidání prostředku do <xref:System.Windows.ResourceDictionary> WPF v kódu.  
  
## <a name="wpf-usage-notes"></a>Poznámky k použití WPF  
 Podřízené objekty nadřazeného objektu, který je <xref:System.Collections.IDictionary> implementace, jako je například <xref:System.Windows.ResourceDictionary>WPF, musí obvykle zahrnovat atribut `x:Key` a hodnota klíče musí být v rámci tohoto slovníku jedinečná. Existují dvě významné výjimky:  
  
- Některé typy WPF deklaruje implicitní klíč pro použití slovníku. Například <xref:System.Windows.Style> s <xref:System.Windows.Style.TargetType%2A>nebo <xref:System.Windows.DataTemplate> s <xref:System.Windows.DataTemplate.DataType%2A>může být v <xref:System.Windows.ResourceDictionary> a používat implicitní klíč.  
  
- WPF podporuje koncept sloučeného slovníku prostředků. Klíče lze sdílet mezi sloučenými slovníky a chování sdíleného klíče lze použít <xref:System.Windows.FrameworkContentElement.FindResource%2A>. Další informace najdete v tématu [sloučené slovníky prostředků](../wpf/advanced/merged-resource-dictionaries.md).  
  
 V celkové implementaci a modelu aplikace WPF XAML není kontrolována klíčová jedinečnost kompilátorem kódu XAML. Místo toho chybějící nebo nejedinečné `x:Key` hodnoty způsobují chyby analyzátoru XAML při načítání. Zpracování slovníkových slovníků v aplikaci Visual Studio pro WPF však často může ve fázi návrhu znamenat chyby.  
  
 Všimněte si, že v zobrazené syntaxi je objekt <xref:System.Windows.ResourceDictionary> implicitní ve způsobu, jakým procesor WPF XAML vytváří kolekci k naplnění kolekce <xref:System.Windows.FrameworkElement.Resources%2A>. <xref:System.Windows.ResourceDictionary> není obvykle k dispozici explicitně jako element v kódu, i když může být v některých případech, pokud je žádoucí pro přehlednost (by to byl prvek objektu kolekce mezi elementem vlastnosti <xref:System.Windows.FrameworkElement.Resources%2A> a položky v rámci tohoto slovníku). Informace o tom, proč je objekt kolekce téměř vždy implicitním prvkem v kódu, naleznete [v tématu Syntaxe jazyka XAML podrobněji](../wpf/advanced/xaml-syntax-in-detail.md).  
  
 V implementaci WPF XAML je zpracování klíčů pro slovníky prostředků definováno pomocí abstraktní třídy <xref:System.Windows.ResourceKey>. Procesor WPF XAML však vytváří různé základní typy rozšíření pro klíče na základě jejich použití. Například klíč pro <xref:System.Windows.DataTemplate> nebo jakákoli odvozená třída se zpracovává samostatně a vytvoří odlišný objekt <xref:System.Windows.DataTemplateKey>.  
  
 Klíče a názvy používají jiné direktivy a jazykové prvky (`x:Key` oproti `x:Name`) v definici Basic XAML. Klíče a názvy jsou také používány v různých situacích definice WPF a aplikací těchto konceptů. Podrobnosti najdete v tématu [WPF XAML obory názvů WPF](../wpf/advanced/wpf-xaml-namescopes.md).  
  
 Jak bylo uvedeno dříve, hodnota klíče může být poskytnuta prostřednictvím rozšíření značek a může být jiná než hodnota řetězce. Příkladem scénáře WPF je, že hodnota `x:Key` může být [ComponentResourceKey](../wpf/advanced/componentresourcekey-markup-extension.md). Některé ovládací prvky zpřístupňují klíč stylu daného typu pro prostředek vlastního stylu, který ovlivňuje část vzhledu a chování daného ovládacího prvku, aniž by zcela nahradil styl. Příkladem takového klíče je <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.  
  
 Funkce sloučeného slovníku WPF zavádí další důležité informace týkající se jedinečnosti klíčů a chování vyhledávání klíčů. Další informace najdete v tématu [sloučené slovníky prostředků](../wpf/advanced/merged-resource-dictionaries.md).  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 omezuje omezení, které `x:Key` vždy k dispozici ve formě atributu.  
  
 V WPF můžete použít funkce XAML 2009, ale pouze pro XAML, které nejsou kompilovány pomocí značek. XAML kompilovaný kód XAML pro WPF a formát BAML jazyka XAML aktuálně nepodporují klíčová slova a funkce XAML 2009.  
  
 V části XAML 2009 můžete určit `x:Key` prvky pomocí následujícího použití:  
  
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
|`keyObject`|Prvek objektu pro objekt, který je použit jako klíč pro daný `object` ve specializovaném slovníku.|  
  
- Kontejner/nadřazený objekt pro tento druh použití není zde zobrazen. `object` by měl být podřízeným objektem elementu, který představuje implementaci specializovaného slovníku. `keyObject` se očekává jako instance objektu (nebo hodnota typu hodnoty), která je vhodná jako klíč pro konkrétní specializovanou implementaci slovníku.  
  
- WPF neimplementuje slovníky, které vyžadují toto použití. Klíče objektu jsou obecnější funkce jazyka XAML, které mohou být užitečné pro některé vlastní slovníky scénářů, kde je vhodné vytvořit slovník v jazyce XAML. Pro funkce WPF, jako jsou například implicitní styly, které používají neřetězcové klíče pro prostředky, existují jiné techniky pro vytváření a určování klíčů, takže použití klíče objektu není nutné.  
  
- *objektem* může být také použití rozšíření značek ve formuláři elementu objektu, nikoli přímo instance objektu.  
  
## <a name="silverlight-usage-notes"></a>Poznámky k používání Silverlight  
 `x:Key` pro Silverlight se zdokumentují samostatně. Další informace naleznete v tématu [obor názvů XAML (x:). Jazykové funkce (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Viz také:

- [Prostředky XAML](../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Prostředky a kód](../wpf/advanced/resources-and-code.md)
- [Rozšíření značek StaticResource](../wpf/advanced/staticresource-markup-extension.md)
