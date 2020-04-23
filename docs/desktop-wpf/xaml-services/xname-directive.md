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
ms.openlocfilehash: 9f812a49a3217a563be1bd7f1d999b641c28463d
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071449"
---
# <a name="xname-directive"></a>x:Name – direktiva

Jednoznačně identifikuje prvky definované XAML v oboru názvů XAML. XAML namescopes a jejich modely jedinečnosti lze použít na instanci objekty, když rozhraní poskytují rozhraní API nebo implementovat chování, které přístup k grafu objektů vytvořených XAML za běhu.

## <a name="xaml-attribute-usage"></a>Použití atributu XAML

```xaml
<object x:Name="XAMLNameValue".../>
```

## <a name="xaml-values"></a>Hodnoty XAML

|||
|-|-|
|`XAMLNameValue`|Řetězec, který odpovídá [omezením gramatiky XamlName](xamlname-grammar.md).|

## <a name="remarks"></a>Poznámky

Po `x:Name` použití na rámec je záložní programovací model, název je ekvivalentní proměnné, která obsahuje odkaz na objekt nebo instance, jak je vrácena konstruktoru.

Hodnota `x:Name` použití směrnice musí být jedinečný v rámci oboru názvů XAML. Ve výchozím nastavení při použití rozhraní .NET XAML Services API je primární název pole XAML definován v kořenovém prvku XAML jedné produkční hodu XAML a zahrnuje prvky, které jsou obsaženy v této výrobě XAML. Další diskrétní názvy XAML, ke kterým může dojít v rámci jedné výroby XAML, mohou být definovány rámci pro řešení konkrétních scénářů. Například v WPF nové názvové obory XAML jsou definovány a vytvořeny libovolnou šablonou, která je také definována v této výrobě XAML. Další informace o názvových oborech XAML (napsaných pro WPF, ale relevantních pro mnoho konceptů oboru názvů XAML) naleznete v tématu [WPF XAML Namescopes](../../framework/wpf/advanced/wpf-xaml-namescopes.md).

Obecně by `x:Name` se neměly používat v `x:Key`situacích, které se používají také . Implementace XAML podle konkrétních existujících rámců `x:Key` zavedly koncepty substituce mezi písmeny a) a `x:Name`b), ale to není doporučený postup. Služba .NET XAML Services nepodporuje tyto koncepty nahrazení <xref:System.Windows.Markup.INameScope> při <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>zpracování informací o názvu/klíči, jako je například nebo .

Pravidla pro `x:Name` povolení, jakož i prosazování jedinečnosti názvu jsou potenciálně definována konkrétními prováděcími rámci. Aby však byly použitelné se službami .NET XAML Services, definice architektury jedinečnosti oboru názvů <xref:System.Windows.Markup.INameScope> XAML by měly být v souladu s definicí informací v této dokumentaci a měly by používat stejná pravidla týkající se použití informací. [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] Implementace například rozděluje různé prvky značek <xref:System.Windows.NameScope> do samostatných oblastí, jako jsou slovníky prostředků, logický strom vytvořený xaml na úrovni stránky, šablony a další odložený obsah, a pak vynucuje jedinečnost názvu XAML v rámci každého z těchto oborů názvů XAML.

Pro vlastní typy, které používají zapisovače objektů XAML `x:Name` služby .NET XAML, lze vytvořit nebo změnit vlastnost, která se mapuje na typ. Toto chování definujete odkazem na název vlastnosti mapovat s <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> v kódu definice typu.  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>je atribut na úrovni typu.

Using.NET služby XAML lze logiku zálohování pro podporu název oboru XAML definovat <xref:System.Windows.Markup.INameScope> způsobem neutrálním v rámci implementací rozhraní.

## <a name="wpf-usage-notes"></a>Poznámky k použití WPF

Pod standardní konfigurace sestavení [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] pro aplikaci, která používá XAML, částečné `x:Name` třídy a kód na pozadí, zadaný stane název pole, které je vytvořeno v podkladovém kódu, když [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] je zpracována úkol sestavení kompilace značek a toto pole obsahuje odkaz na objekt. Ve výchozím nastavení je vytvořené pole interní. Přístup k polím můžete změnit zadáním [atributu x:FieldModifier](xfieldmodifier-directive.md). V WPF a Silverlight pořadí je, že kompilace značek definuje a názvy pole v částečné třídě, ale hodnota je zpočátku prázdný. Potom generované metody s `InitializeComponent` názvem je volána z v rámci konstruktoru třídy. `InitializeComponent`se skládá `FindName` z volání `x:Name` pomocí každé z hodnot, které existují v XAML definované části částečné třídy jako vstupní řetězce. Vrácené hodnoty jsou pak přiřazeny k odkazu na pole s označením like, aby vyplnily hodnoty polí objekty, které byly vytvořeny z analýzy XAML. Spuštění umožňují `InitializeComponent` odkazovat na graf objektu za `x:Name` běhu pomocí názvu pole / `FindName` přímo, spíše než muset explicitně volat kdykoli budete potřebovat odkaz na objekt definovaný xaml.

Pro aplikaci WPF, která používá cíle jazyka Microsoft `Page` Visual Basic a obsahuje soubory XAML `WithEvents` s akcí sestavení, `x:Name`je během `Handles` kompilace vytvořena samostatná vlastnost odkazu, která přidá klíčové slovo ke všem prvkům, které mají , pro podporu syntaxe pro delegáty obslužné rutiny události. Tato vlastnost je vždy veřejná. Další informace naleznete [v tématu Visual Basic a WPF Event Handling](../../framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).

`x:Name`používá wpf XAML procesor zaregistrovat název do oboru názvů XAML v době načítání, a to i v případech, kdy stránka není zkompilována značky pomocí akce sestavení (například volné XAML slovníku prostředků). Jedním z důvodů pro `x:Name` toto chování <xref:System.Windows.Data.Binding.ElementName%2A> je, protože je potenciálně potřebné pro vazbu. Podrobnosti naleznete v [tématu Přehled datových vazeb](../data/data-binding-overview.md).

Jak již bylo `x:Name` zmíněno dříve, (nebo `Name`) `x:Key`by neměly být používány v situacích, které také používají . Má [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary> zvláštní chování definování sebe jako název oboru XAML, ale vrací <xref:System.Windows.Markup.INameScope> není implementována nebo null hodnoty pro api jako způsob, jak vynutit toto chování. Pokud se analyzátor WPF XAML setká `Name` nebo `x:Name` je <xref:System.Windows.ResourceDictionary>definován xaml , název není přidán do žádného oboru názvů XAML. Pokus o nalezení tohoto názvu z libovolného `FindName` oboru názvů XAML a metody nevrátí platné výsledky.

### <a name="xname-and-name"></a>x:Jméno a název

Mnoho scénářů aplikace WPF můžete `x:Name` vyhnout jakékoli `Name` použití atributu, protože vlastnost závislosti, jak je uvedeno ve <xref:System.Windows.FrameworkElement> výchozím <xref:System.Windows.FrameworkContentElement> oboru názvů XAML pro několik důležitých základních tříd, jako je například a splňuje stejný účel. Stále existují některé běžné scénáře XAML a WPF, `Name` kde je důležitý přístup kódu k elementu bez vlastnosti na úrovni rozhraní. Například některé třídy podpory animace a `Name` scénáře nepodporují vlastnost, ale často je třeba odkazovat v kódu, aby bylo možné řídit animaci. Měli byste `x:Name` zadat jako atribut na časové osy a transformace, které jsou vytvořeny v XAML, pokud máte v úmyslu odkazovat je z kódu později.

Pokud <xref:System.Windows.FrameworkElement.Name%2A> je k dispozici jako <xref:System.Windows.FrameworkElement.Name%2A> vlastnost `x:Name` na třídu a lze použít zaměnitelně jako atributy, ale výjimka analýzy bude mít za následek, pokud jsou zadány na stejný prvek. Pokud xaml je zkompilován značky, dojde k výjimce na značky kompilace, jinak k němu dojde při zatížení.

<xref:System.Windows.FrameworkElement.Name%2A>lze nastavit pomocí syntaxe atributu XAML a v kódu pomocí <xref:System.Windows.DependencyObject.SetValue%2A>; Všimněte si <xref:System.Windows.FrameworkElement.Name%2A> však, že nastavení vlastnosti v kódu nevytvoří reprezentativní odkaz na pole v rámci oboru názvů XAML ve většině okolností, kdy je xaml již načten. Namísto pokusu <xref:System.Windows.FrameworkElement.Name%2A> o nastavení <xref:System.Windows.NameScope> v kódu, použijte metody z kódu, proti příslušné namescope.

<xref:System.Windows.FrameworkElement.Name%2A>lze také nastavit pomocí syntaxe prvku vlastnosti s vnitřním textem, ale to je neobvyklé. Naproti tomu `x:Name` nelze nastavit v syntaxi elementu vlastnosti <xref:System.Windows.DependencyObject.SetValue%2A>XAML nebo v kódu pomocí ; lze nastavit pouze pomocí syntaxe atributu na objektech, protože se jedná o direktivu.

## <a name="silverlight-usage-notes"></a>Poznámky k použití aplikace Silverlight

`x:Name`pro Program Silverlight je dokumentován samostatně. Další informace naleznete v [tématu XAML Namespace (x:) Jazykové funkce (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).

## <a name="see-also"></a>Viz také

- <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>
- [Stromy v subsystému WPF](../../framework/wpf/advanced/trees-in-wpf.md)
