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
ms.openlocfilehash: 511721c3ffffb3b80b339c4671ad99e16bafda93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565896"
---
# <a name="xkey-directive"></a>x:Key – direktiva
Jednoznačně identifikuje prvky, které jsou vytvořeny a odkazovat ve slovníku definované XAML. Přidání `x:Key` hodnotu do elementu objektu XAML je nejběžnější způsob, jak identifikovat prostředku v slovník prostředků, například v WPF <xref:System.Windows.ResourceDictionary>.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>Použití atributu XAML (WPF konkrétní)  
  
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
|`stringKeyValue`|Textový řetězec sloužící jako klíč. Textový řetězec musí odpovídat [XamlName – gramatika](../../../docs/framework/xaml-services/xamlname-grammar.md).|  
|`markupExtensionUsage`|V rámci oddělovače rozšíření značek {}, využití rozšíření značek, které obsahuje objekt, který použijete jako klíč. V části poznámky.|  
  
## <a name="remarks"></a>Poznámky  
 `x:Key` podporuje koncept slovník prostředků XAML. XAML jako jazyk nedefinuje implementace slovník prostředků, který se nechá pro konkrétní rozhraní uživatelského rozhraní. Další informace o tom, jak jsou implementované slovnících prostředků XAML v grafickém subsystému WPF najdete v tématu [XAML prostředky](../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 V jazyce XAML 2006 a WPF `x:Key` musí být zadán jako atribut. Můžete dál používat neřetězcový klíče, ale to vyžaduje použití rozšíření značek zadejte neřetězcový hodnotu v podobě atributu. Pokud používáte XAML 2009 `x:Key` lze zadat jako element, explicitně podporují slovník s klíči objektu typy jiné než řetězce bez nutnosti – zprostředkující rozšíření značek. Najdete v části "XAML 2009" v tomto tématu. Zbývající část oddílu poznámky platí konkrétně pro implementaci XAML 2006.  
  
 Hodnota atributu `x:Key` lze v definovat libovolný řetězec [XamlName – gramatika](../../../docs/framework/xaml-services/xamlname-grammar.md) nebo může být objekt vyhodnotit prostřednictvím rozšíření značek. Příklad z grafického subsystému WPF najdete v části "Použití WPF poznámky k".  
  
 Podřízené elementy nadřazeného elementu, který je <xref:System.Collections.IDictionary> implementace obvykle musí zahrnovat `x:Key` atribut, který určuje jedinečnou hodnotu klíče v rámci tohoto slovníku. Rozhraní může implementovat alias klíčové vlastnosti nahradit pro `x:Key` na konkrétní typy; by měl být opatřená typy, které definují vlastností <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 Ekvivalentní kód zadávání `x:Key` klíč, který se používá pro základní <xref:System.Collections.IDictionary>. Například `x:Key` který se použije v značek pro prostředek v grafickém subsystému WPF je ekvivalentní hodnotě `key` parametr <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> při přidávání prostředku do WPF <xref:System.Windows.ResourceDictionary> v kódu.  
  
## <a name="wpf-usage-notes"></a>Poznámky pro použití WPF  
 Podřízené objekty nadřazený objektu, který je <xref:System.Collections.IDictionary> implementace, jako je například WPF <xref:System.Windows.ResourceDictionary>, obvykle musí zahrnovat `x:Key` atribut a hodnota klíče musí být jedinečné v rámci tohoto slovníku. Existují dvě důležitými výjimkami:  
  
-   Některé typy WPF deklarovat klíčem implicitní pro použití slovníku. Například <xref:System.Windows.Style> s <xref:System.Windows.Style.TargetType%2A>, nebo <xref:System.Windows.DataTemplate> s <xref:System.Windows.DataTemplate.DataType%2A>, může být v <xref:System.Windows.ResourceDictionary> a pomocí implicitní klíče.  
  
-   WPF podporuje koncept slovník sloučené prostředků. Klíče lze sdílet mezi sloučené slovník a sdíleného klíče chování lze přistupovat pomocí <xref:System.Windows.FrameworkContentElement.FindResource%2A>. Další informace najdete v tématu [sloučit slovnících prostředků](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).  
  
 V celkové WPF XAML provádění a použití modelu klíče jedinečnosti kontrolována kompilátorem kód XAML. Místo toho chybí nebo nejedinečný `x:Key` hodnoty způsobit chyby analyzátoru XAML při načtení. Zpracování sady Visual Studio slovníků pro grafický subsystém WPF můžete často však takové chyby ve fázi návrhu.  
  
 Všimněte si, že v syntaxi uvedenou, <xref:System.Windows.ResourceDictionary> objektu je implicitní v jak procesoru WPF XAML vytvoří kolekci k naplnění <xref:System.Windows.FrameworkElement.Resources%2A> kolekce. A <xref:System.Windows.ResourceDictionary> není k dispozici obvykle explicitně jako elementu v kódu, i když může být v některých případech, pokud je potřeba pro přehlednost (je prvek kolekce objektů mezi <xref:System.Windows.FrameworkElement.Resources%2A> element vlastnosti a položky v rámci které naplnit slovník). Informace o tom, proč je objekt kolekce téměř vždy implicitní elementu v kódu najdete v tématu [XAML syntaxe v podrobností](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
 K implementaci WPF XAML zpracování pro klíče slovníku prostředků definované <xref:System.Windows.ResourceKey> abstraktní třídy. Procesor WPF XAML ale vytváří různé základní typy rozšíření pro klíče založené na jejich použití. Například klíč pro <xref:System.Windows.DataTemplate> nebo všechny odvozené třídy zpracovává samostatně a vytvoří samostatnou <xref:System.Windows.DataTemplateKey> objektu.  
  
 Klíče a názvy používat různé direktivy a jazykové elementy (`x:Key` versus `x:Name`) v základní definici XAML. Názvy klíčů a také používají v různých situacích definici WPF a aplikace tyto koncepty. Podrobnosti najdete v tématu [WPF XAML Namescopes](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
 Jak jsme uvedli dříve, můžete zadat prostřednictvím rozšíření značek hodnoty klíče a může být než hodnotu řetězce. Příklad scénáře WPF je, že hodnota `x:Key` může být[ComponentResourceKey](../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md). Některé ovládací prvky vystavit klíč styl tohoto typu pro vlastní styl prostředek, který ovlivňuje součástí vzhled a chování tohoto ovládacího prvku bez zcela nahrazení styl. Příkladem takových klíč je <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.  
  
 Funkci sloučené slovník WPF zavádí další důležité informace pro klíče jedinečnost a chování vyhledávání klíčů. Další informace najdete v tématu [sloučit slovnících prostředků](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 zmírní omezení, `x:Key` vždy je třeba zadat v podobě atributu.  
  
 V grafickém subsystému WPF můžete použít funkce jazyka XAML 2009, ale jenom pro jazyk XAML, který zkompiluje značek není. Zkompilovaný kód XAML pro WPF a BAML formu XAML aktuálně nepodporují klíčová slova jazyka XAML 2009 a funkce.  
  
 V části XAML 2009, můžete zadat `x:Key` elementy prostřednictvím použití následující:  
  
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
|`keyObject`|Objekt elementu pro objekt, který slouží jako klíč pro danou `object` v specializované slovníku.|  
  
-   Kontejner nebo nadřízené pro tento typ použití není zobrazeny zde. `object` musí být podřízeným elementu objekt, který představuje implementaci specializované slovníku. `keyObject` musí být instanci objektu (nebo hodnota typu hodnoty), je vhodné jako klíč pro tuto implementaci konkrétní specializované slovníku.  
  
-   WPF neimplementuje slovníky, které vyžadují toto použití. Objekt klíče je více obecné funkce jazyka XAML, může být užitečná pro určité vlastní slovník scénářích, kdy vytváření slovníku v jazyce XAML žádoucí. WPF funkcí, jako jsou implicitní stylů, které používají jiné než řetězec klíče pro prostředky další metody pro vytvoření nebo zadání klíče existují, takže není nutné používat klíč objektu.  
  
-   *keyObject* mohou být také na používání rozšíření značek v objektu element formuláře, nikoli instanci objektu přímo.  
  
## <a name="silverlight-usage-notes"></a>Poznámky pro použití programu Silverlight  
 `x:Key` pro Silverlight je popsána samostatně. Další informace najdete v tématu [Namespace XAML (x:) Funkce jazyka (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Viz také  
 [Prostředky XAML](../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Prostředky a kód](../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [Rozšíření značek StaticResource](../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)
