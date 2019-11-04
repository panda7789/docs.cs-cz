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
ms.openlocfilehash: 8a790ea964ffe399136a82ea298e1c7600f48366
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459965"
---
# <a name="xname-directive"></a>x:Name – direktiva
Jednoznačně identifikuje prvky definované XAML v namescope XAML. Obory názvů WPF XAML a jejich modely jedinečnosti lze použít na instance objektů, když rozhraní poskytují rozhraní API nebo implementují chování, které přistupují k grafu objektů vytvořeným XAML v době běhu.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object x:Name="XAMLNameValue".../>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`XAMLNameValue`|Řetězec, který odpovídá omezením [gramatiky XAML](xamlname-grammar.md).|  
  
## <a name="remarks"></a>Poznámky  
 Po `x:Name` se použije na programovací model pro zálohování rozhraní, je název ekvivalentní proměnné, která obsahuje odkaz na objekt nebo instanci vrácenou konstruktorem.  
  
 Hodnota použití direktivy `x:Name` musí být jedinečná v rámci namescope XAML. Ve výchozím nastavení, pokud je používána rozhraním API služby .NET Framework XAML Services, je primární XAML namescope definováno v kořenovém elementu XAML s jednou výrobou XAML a zahrnuje prvky, které jsou obsaženy v dané produkci XAML. Další diskrétní XAML obory názvů WPF, ke kterým může dojít v rámci jedné výroby XAML, lze definovat pomocí platforem pro řešení konkrétních scénářů. Například v jazyce WPF jsou nové obory názvů wpfy XAML definovány a vytvořeny libovolnou šablonou, která je také definována v této produkci XAML. Další informace o obory názvů WPF XAML (napsané pro WPF, ale relevantní pro mnoho konceptů XAML namescope) naleznete v tématu [WPF XAML obory názvů WPF](../wpf/advanced/wpf-xaml-namescopes.md).  
  
 Obecně platí, `x:Name` by se neměly používat v situacích, kdy se používá také `x:Key`. Implementace XAML specificky existujícími architekturami představily substituční koncepty mezi `x:Key` a `x:Name`, ale to není doporučený postup. .NET Framework služby XAML nepodporují tyto koncepty nahrazení při zpracování informací o jménu nebo klíči, jako je <xref:System.Windows.Markup.INameScope> nebo <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 Pravidla pro povolení `x:Name` a vynucování jedinečnosti názvu jsou potenciálně definovány konkrétní implementací rozhraní. Aby bylo možné použít .NET Framework služby XAML, definice rozhraní XAML namescope by měla být konzistentní s definicí <xref:System.Windows.Markup.INameScope> informace v této dokumentaci a měla by používat stejná pravidla, která se týkají, kde tyto informace je použito. Například implementace [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] rozdělí různé prvky značek na samostatné <xref:System.Windows.NameScope> oblasti, jako jsou například slovníky prostředků, logický strom vytvořený pomocí XAML na úrovni stránky, šablony a další odložený obsah a pak vynutil název XAML. jedinečnost v rámci každého z těchto obory názvů WPF XAML.  
  
 Pro vlastní typy, které používají .NET Framework moduly XAML pro vytváření objektů XAML, lze vytvořit nebo změnit vlastnost, která je mapována na `x:Name` typu. Toto chování definujete tak, že odkazujete na název vlastnosti, která má být mapována s <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> v kódu definice typu.  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> je atribut na úrovni typu.  
  
 Using.NET Framework XAML Services: logiku pro podporu namescope v jazyce XAML lze definovat v neutrálním způsobu implementací rozhraní <xref:System.Windows.Markup.INameScope>.  
  
## <a name="wpf-usage-notes"></a>Poznámky k použití WPF  
 V rámci standardní konfigurace sestavení pro aplikaci [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], která používá XAML, částečné třídy a kódu na pozadí, se zadaný `x:Name` stávají názvem pole vytvořeným v podkladovém kódu, když je [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] zpracován sestavením kompilace kódu. úkol a toto pole obsahuje odkaz na objekt. Ve výchozím nastavení je pole Vytvořeno interní. Přístup k poli můžete změnit zadáním [atributu x:FieldModifier –](x-fieldmodifier-directive.md). V jazyce WPF a Silverlight je sekvence, že kompilace značek definuje a pojmenovává pole v částečné třídě, ale hodnota je zpočátku prázdná. Následně vygenerovaná metoda s názvem `InitializeComponent` je volána v rámci konstruktoru třídy. `InitializeComponent` se skládá z `FindName` volání pomocí každé z `x:Name` hodnot, které jsou obsaženy v části částečné třídy definované v jazyce XAML jako vstupní řetězce. Návratové hodnoty jsou poté přiřazeny k odkazu na pole s názvem like. k vyplnění hodnot polí objekty, které byly vytvořeny při analýze XAML. Provedení `InitializeComponent` umožňuje odkazování na graf objektu run time pomocí názvu `x:Name`/pole přímo, místo nutnosti volat `FindName` explicitně kdykoli potřebujete odkaz na objekt definovaný v jazyce XAML.  
  
 Pro aplikaci WPF, která používá cíle od společnosti Microsoft Visual Basic a obsahuje soubory XAML s akcí sestavení `Page`, je během kompilace vytvořena samostatná referenční vlastnost, která přidá klíčové slovo `WithEvents` do všech prvků, které mají `x:Name`, pro podporu @no syntaxe __t_3_ pro delegáty obslužné rutiny události Tato vlastnost je vždy veřejná. Další informace naleznete v tématu [Visual Basic a zpracování událostí WPF](../wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
 `x:Name` používá procesor XAML v jazyce WPF k registraci názvu do namescope jazyka XAML v době načítání, a to i v případě, že stránka není značkami zkompilovány pomocí akcí sestavení (například volný kód XAML slovníku prostředků). Jedním z důvodů tohoto chování je, že `x:Name` je potenciálně nutné pro <xref:System.Windows.Data.Binding.ElementName%2A> vazby. Podrobnosti najdete v tématu [Přehled datových vazeb](../../desktop-wpf/data/data-binding-overview.md).  
  
 Jak jsme už uvedli, `x:Name` (nebo `Name`) by se neměla používat v situacích, kdy se taky používá `x:Key`. <xref:System.Windows.ResourceDictionary> [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] má zvláštní chování při definování sebe sama jako XAML namescope, ale vrácení neimplementovaných nebo hodnot null pro <xref:System.Windows.Markup.INameScope> rozhraní API jako způsob, jak toto chování vykonat. Pokud analyzátor XAML jazyka WPF nalezne `Name` nebo `x:Name` v <xref:System.Windows.ResourceDictionary>definovaném v jazyce XAML, název není přidán do žádného namescope XAML. Při pokusu o nalezení názvu z libovolného namescopey XAML a metody `FindName` nebudou vracet platné výsledky.  
  
### <a name="xname-and-name"></a>x:Name a název  
 Mnoho scénářů aplikace WPF se může vyhnout jakémukoli použití atributu `x:Name`, protože vlastnost `Name` Dependency, která je zadána ve výchozím oboru názvů jazyka XAML pro několik důležitých základních tříd, jako je například <xref:System.Windows.FrameworkElement> a <xref:System.Windows.FrameworkContentElement> splňuje tento stejný účel. Stále existují některé běžné scénáře XAML a WPF, kde je důležité mít přístup ke kódu k elementu bez `Name` vlastností na úrovni rozhraní. Například určité animace a třídy podpory scénářů nepodporují vlastnost `Name`, ale často je potřeba na ně odkazovat v kódu, aby bylo možné tuto animaci řídit. Měli byste zadat `x:Name` jako atribut na časové ose a transformace, které jsou vytvořeny v jazyce XAML, pokud je chcete později odkazovat z kódu.  
  
 Pokud je <xref:System.Windows.FrameworkElement.Name%2A> k dispozici jako vlastnost třídy, <xref:System.Windows.FrameworkElement.Name%2A> a `x:Name` lze použít jako atributy, ale výjimka analýzy bude mít za následek, pokud jsou obě zadány u stejného prvku. Pokud je XAML zkompilován kód, výjimka bude provedena na kompilaci kódu, jinak dojde při zatížení.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> lze nastavit pomocí syntaxe atributu XAML a v kódu pomocí <xref:System.Windows.DependencyObject.SetValue%2A>; Upozorňujeme však, že nastavení vlastnosti <xref:System.Windows.FrameworkElement.Name%2A> v kódu nevytvoří odkaz na pole zástupce v rámci namescope XAML ve většině případů, kdy je XAML již načten. Namísto pokusu o nastavení <xref:System.Windows.FrameworkElement.Name%2A> v kódu použijte metody <xref:System.Windows.NameScope> z kódu proti příslušnému namescope.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> lze také nastavit pomocí syntaxe elementu Property s vnitřním textem, ale to je neobvyklé. Naproti tomu `x:Name` nelze nastavit v syntaxi elementu vlastnosti XAML nebo v kódu pomocí <xref:System.Windows.DependencyObject.SetValue%2A>; dá se nastavit jenom pomocí syntaxe atributu u objektů, protože to je direktiva.  
  
## <a name="silverlight-usage-notes"></a>Poznámky k používání Silverlight  
 `x:Name` pro Silverlight se zdokumentují samostatně. Další informace naleznete v tématu [obor názvů XAML (x:). Jazykové funkce (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>
- [Stromy v subsystému WPF](../wpf/advanced/trees-in-wpf.md)
