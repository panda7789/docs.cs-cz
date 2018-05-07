---
title: x:Name – direktiva
ms.date: 03/30/2017
f1_keywords:
- x:Name
- xName
- Name
helpviewer_keywords:
- x:Name attribute [XAML Services]
- XAML [XAML Services], x:Name attribute
- Name attribute in XAML [XAML Services]
ms.assetid: b7e61222-e8cf-48d2-acd0-6df3b7685d48
ms.openlocfilehash: 7fcb7fe767e892109e48c5e56db26b5943b6ef13
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="xname-directive"></a>x:Name – direktiva
Jednoznačně identifikuje elementů XAML definované v XAML namescope. XAML namescopes a jejich jedinečnost modely je použít pro vytvořených objektů architektury poskytují rozhraní API nebo implementaci chování, které přístup k objektu vytvořeny XAML grafu v době běhu.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object x:Name="XAMLNameValue".../>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`XAMLNameValue`|Řetězec, který je v souladu s omezeními z [XamlName – gramatika](../../../docs/framework/xaml-services/xamlname-grammar.md).|  
  
## <a name="remarks"></a>Poznámky  
 Po `x:Name` se použije pro rozhraní je zálohování programovací model, název odpovídá proměnné, která obsahuje odkaz na objekt nebo instanci, jak ho vrátila konstruktor.  
  
 Hodnota `x:Name` direktivy využití musí být jedinečný v rámci XAML namescope. Ve výchozím nastavení při použití s rozhraní .NET Framework XAML Services API primární namescope XAML je definován kořenový element XAML jedné XAML výroby a zahrnuje prvky, které jsou obsaženy v produkčním prostředí tuto XAML. Další diskrétní namescopes XAML, které může dojít v rámci jediné provozní XAML lze definovat pomocí architektury vyřešit konkrétní scénáře. Například v grafickém subsystému WPF, nové XAML namescopes jsou definovány a vytvořit všechny šablony, který je také definován v této XAML výroby. Další informace o namescopes XAML (napsané pro WPF ale relevantní pro mnohé koncepty namescope XAML) najdete v tématu [WPF XAML Namescopes](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
 Obecně platí `x:Name` nesmí použít v situacích, kteří také používají `x:Key`. Implementace XAML podle konkrétní existující architektury zavedly nahrazení koncepty mezi `x:Key` a `x:Name`, ta však není doporučený postup. Rozhraní .NET framework XAML Services nepodporuje tyto koncepty nahrazení při zpracování název nebo klíčové informace, jako <xref:System.Windows.Markup.INameScope> nebo <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 Pravidla pro permittance z `x:Name` a také vynucení jedinečnosti název jsou potenciálně definované konkrétní implementující rozhraní. Však možné používat s rozhraní .NET Framework XAML Services, definice framework XAML namescope jedinečnosti by měla být v souladu s definice <xref:System.Windows.Markup.INameScope> informace v této dokumentaci a musí používat stejná pravidla o tom, kam informace se použije. Například [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] implementace rozdělí různé prvky značek na samostatné <xref:System.Windows.NameScope> rozsahy logického stromu vytvořené úrovně stránky XAML, šablony a dalších odložení obsah, jako je například slovnících prostředků a pak vynucuje XAML Název jedinečnosti v každém z těchto namescopes XAML.  
  
 Pro vlastní typy, které používají rozhraní .NET Framework XAML Services XAML objekt zapisovače, vlastnost která se mapuje `x:Name` na typ lze vytvořit nebo změnit. Pod položkou Název vlastnosti pro mapování s definujete toto chování <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> v kódu definice typu.  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> je úrovni typu atributu.  
  
 Using.NET Framework XAML Services základní logika pro podporu namescope XAML lze definovat způsobem framework jazykově neutrální implementací <xref:System.Windows.Markup.INameScope> rozhraní.  
  
## <a name="wpf-usage-notes"></a>Poznámky pro použití WPF  
 V části Konfigurace standardní sestavení [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] aplikace, která používá XAML, částečné třídy a kódu, zadaný `x:Name` stane název pole, který je vytvořen v základní kódu, kdy [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] zpracovává značky Úloha kompilace sestavení a toto pole obsahuje odkaz na objekt. Ve výchozím nastavení je interní vytvořené pole. Přístup k poli můžete změnit zadáním [x: fieldmodifier – atribut](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md). WPF a Silverlight sekvenci je, že definuje kompilace kódu a názvy polí v konkrétní třídu, ale hodnota je původně prázdné. Potom generovaného metodu s názvem `InitializeComponent` je volána v rámci konstruktoru třídy. `InitializeComponent` se skládá z `FindName` volá pomocí všech `x:Name` hodnoty, které existují v části definované XAML třídu jako vstup řetězce. Návratové hodnoty jsou posléze přiřazeny k odkaz s názvem jako pole k vyplnění pole hodnot s objekty, které byly vytvořeny z XAML analýze. Provádění `InitializeComponent` umožňují odkaz na objekt grafu běhu pomocí `x:Name` / název pole přímo, namísto nutnosti volání `FindName` explicitně kdykoli potřebujete odkaz na objekt definovaný XAML.  
  
 Pro WPF aplikace, která používá Microsoft Visual Basicu cílem a obsahuje soubory XAML s `Page` akce sestavení, vlastnost samostatné referenčního se vytvoří během kompilace, která přidává `WithEvents` – klíčové slovo na všechny elementy, které mají `x:Name`, pro podporu `Handles` syntaxe delegátů obslužných rutin událostí. Tato vlastnost je vždy veřejné. Další informace najdete v tématu [Visual Basic a zpracování události WPF](../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
 `x:Name` se používá procesorem WPF XAML registraci názvu v XAML namescope během zatížení, i pro případy, kdy stránky není značek zkompilovat akcemi sestavení (například přijít XAML slovník prostředků). Jedním z důvodů toto chování je, protože `x:Name` je můžou být potřebné pro <xref:System.Windows.Data.Binding.ElementName%2A> vazby. Podrobnosti najdete v tématu [přehled vazby dat](../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Jak je uvedeno nahoře, `x:Name` (nebo `Name`) by neměl být použít v situacích, kteří také používají `x:Key`. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary> Je zvláštní chování definování sám sebe jako XAML namescope, ale vrací není implementován nebo jeho hodnoty null pro <xref:System.Windows.Markup.INameScope> rozhraní API jako způsob, jak vynutit toto chování. Pokud analyzátor WPF XAML nalezne `Name` nebo `x:Name` v jazyce XAML definované <xref:System.Windows.ResourceDictionary>, zadaný název není přidaný do jakékoli namescope XAML. Pokusu o nalezení tento název z jakékoli namescope XAML a `FindName` metody nevrátí platnou výsledky.  
  
### <a name="xname-and-name"></a>x: Name a název  
 Mnoho scénářů aplikace WPF se můžete vyhnout jakékoli použití `x:Name` atributů, protože `Name` vlastnost závislosti jako zadaný v výchozí nastavení oboru názvů jazyka XAML pro několik důležitých základní třídy, jako <xref:System.Windows.FrameworkElement> a <xref:System.Windows.FrameworkContentElement> splňuje tento stejný účel. Stále existují některé běžné scénáře XAML a WPF kde code přístup k elementu bez `Name` vlastnost na úrovni framework je důležité. Například určité třídy pro podporu animace a scénáře nepodporují `Name` vlastnost, ale často potřebují bude odkazovat v kódu, aby bylo možné řídit animace. Musíte zadat `x:Name` jako atribut časové osy a transformace, které jsou vytvořené v jazyce XAML, pokud máte v úmyslu později odkazovat z kódu.  
  
 Pokud <xref:System.Windows.FrameworkElement.Name%2A> je k dispozici jako vlastnost ve třídě, <xref:System.Windows.FrameworkElement.Name%2A> a `x:Name` zaměnitelné jako atributy, ale výjimka analýzy dojde, pokud obou zadaná u stejného elementu. Pokud XAML kompilaci kódu, se výjimka vyskytne v kompilaci značek, jinak proběhne zatížení.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> se dá nastavit pomocí syntaxe jazyka XAML atribut a v kódu pomocí <xref:System.Windows.DependencyObject.SetValue%2A>; Všimněte si, ale toto nastavení <xref:System.Windows.FrameworkElement.Name%2A> vlastností v kódu nevytváří odkaz na reprezentativní pole v jazyce XAML namescope ve většině situací, kde je již XAML načíst. Namísto pokusu o nastavení <xref:System.Windows.FrameworkElement.Name%2A> v kódu pomocí <xref:System.Windows.NameScope> metody z kódu pro příslušné namescope.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> Můžete také nastavit vnitřní text pomocí syntaxe vlastnost elementu, ale který neobvyklé. Naproti tomu `x:Name` nelze nastavit v XAML vlastnost element syntaxe nebo v kódu pomocí <xref:System.Windows.DependencyObject.SetValue%2A>; ho lze nastavit pouze pomocí syntaxe atribut u objektů, protože se jedná o direktivu.  
  
## <a name="silverlight-usage-notes"></a>Poznámky pro použití programu Silverlight  
 `x:Name` pro Silverlight je popsána samostatně. Další informace najdete v tématu [Namespace XAML (x:) Funkce jazyka (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>  
 <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>  
 [Stromy v subsystému WPF](../../../docs/framework/wpf/advanced/trees-in-wpf.md)
