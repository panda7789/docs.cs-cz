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
ms.openlocfilehash: 08594d9757596eed470ffba8b5b63a01c493c358
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48035055"
---
# <a name="xname-directive"></a>x:Name – direktiva
Jednoznačně identifikuje elementy XAML definované v XAML namescope. Obory názvů XAML a jejich modelů jedinečnost lze použít instance objektů, rozhraní poskytují rozhraní API nebo implementaci chování, které přistupují k graf objektu XAML vytvoří za běhu.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object x:Name="XAMLNameValue".../>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`XAMLNameValue`|Řetězec, který odpovídá omezení [xamlname – gramatika](../../../docs/framework/xaml-services/xamlname-grammar.md).|  
  
## <a name="remarks"></a>Poznámky  
 Po `x:Name` platí pro rozhraní uživatele zálohování programovací model, název je ekvivalentní k proměnné, která obsahuje odkaz na objekt nebo instance vrácená rozhraním konstruktor.  
  
 Hodnota `x:Name` direktivy využití musí být jedinečný v rámci XAML namescope. Ve výchozím nastavení při použití rozhraní .NET Framework XAML Services API primární obor namescope XAML je definován na kořenový prvek XAML jedné výroby XAML a zahrnuje elementy, které jsou součástí výroby XAML. Další samostatné obory názvů XAML, které může dojít v rámci jednoho produkční XAML lze definovat podle platformy, které se vztahují k určité scénářům. Například v WPF nové obory názvů XAML jsou definovány a vytvořil všechny šablony, která je také definováno v XAML výroby. Další informace o obory názvů XAML (ale relevantní pro mnoho konceptů namescope XAML napsané pro WPF), najdete v části [obory názvů WPF XAML](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
 Obecně platí `x:Name` neměla používat v situacích, které používají také `x:Key`. Implementace XAML pomocí konkrétní stávajících architektur zavedli nahrazení koncepty mezi `x:Key` a `x:Name`, ale toto není doporučený postup. Rozhraní .NET framework XAML Services nepodporuje tyto koncepty nahrazení při zpracování informací o název a klíč jako <xref:System.Windows.Markup.INameScope> nebo <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 Pravidla pro permittance z `x:Name` a také vynucení jedinečnost názvu jsou potenciálně definovaném konkrétní implementace rozhraní. Však možné používat s technologií .NET Framework XAML Services, definice rozhraní framework jedinečnosti obor namescope XAML by měl být konzistentní s definicí <xref:System.Windows.Markup.INameScope> informace v této dokumentaci a o tom, kam by měly používat stejná pravidla informace se použijí. Například [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] implementace rozdělí různé prvky kódu na samostatném <xref:System.Windows.NameScope> rozsahy adres, jako jsou slovníky prostředků, logického stromu vytvořené úrovni stránky XAML, šablony a další odložené obsahu a potom vynucuje XAML jedinečnost názvu v rámci každé z těchto obory názvů XAML.  
  
 Pro vlastní typy, které používají rozhraní .NET Framework XAML Services XAML objekt zapisovače, vlastnost, která se mapuje na `x:Name` na typ lze vytvořit nebo změnit. Toto chování můžete definovat pomocí odkazu na název vlastnosti pro mapování s <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> v kódu definice typu.  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> je atribut úrovni typu.  
  
 Using.NET Framework XAML Services základní logiku pro podporu namescope XAML lze definovat v rámci jazykově neutrální způsob implementací <xref:System.Windows.Markup.INameScope> rozhraní.  
  
## <a name="wpf-usage-notes"></a>Poznámky k použití WPF  
 V části standard sestavení [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] aplikaci, která používá XAML, částečné třídy a modelu code-behind, zadaný `x:Name` stane názvem pole, které se vytvoří v základním kódu při [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] zpracovává značky Úloha kompilace sestavení a toto pole obsahuje odkaz na objekt. Ve výchozím nastavení je interní vytvořené pole. Přístup k poli můžete změnit zadáním [x: fieldmodifier – atribut](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md). V WPF a Silverlight sekvence je, že definuje značky kompilace a názvy polí v částečné třídy, ale hodnota je původně prázdné. Potom vytvořena metoda s názvem `InitializeComponent` je volána v rámci konstruktoru třídy. `InitializeComponent` se skládá z `FindName` volá pomocí všech `x:Name` vstupní hodnoty, které existují v součástí definice XAML částečné třídy jako řetězce. Vrácené hodnoty jsou pak přiřadí odkaz s názvem jako pole k vyplnění pole hodnot s objekty, které byly vytvořeny z XAML analýza kódu. Provedení příkazu `InitializeComponent` umožňují odkaz na objekt grafu běhu pomocí `x:Name` / název pole přímo, namísto nutnosti volat `FindName` explicitně kdykoli potřebujete odkaz na objekt definice XAML.  
  
 Pro WPF aplikace, která používá Microsoft Visual Basicu cílí a zahrnuje soubory XAML s `Page` akci sestavení, samostatné referenční vlastnost se vytvoří během kompilaci, která se přidá `WithEvents` – klíčové slovo na všechny elementy, které mají `x:Name`pro zajištění podpory `Handles` syntaxe pro delegáty obsluhy událostí. Tato vlastnost je vždy přístup public. Další informace najdete v tématu [jazyka Visual Basic a WPF zpracování událostí](../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
 `x:Name` procesor WPF XAML se použije k registraci názvu do XAML namescope v okamžiku načtení, dokonce i pro případy, kdy stránky není kód zkompilován s akcí sestavení (například volný XAML slovníku prostředků). Jedním z důvodů pro toto chování je vzhledem k tomu, `x:Name` je můžou být potřebné pro <xref:System.Windows.Data.Binding.ElementName%2A> vazby. Podrobnosti najdete v tématu [přehled datových vazeb](../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Jak už bylo zmíněno dříve, `x:Name` (nebo `Name`) neměla používat v situacích, které používají také `x:Key`. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary> Má zvláštní chování samotné definice jako obor namescope XAML, ale vrací Neimplementováno nebo hodnoty null pro <xref:System.Windows.Markup.INameScope> rozhraní API jako způsob, jak vynucovat toto chování. Pokud analyzátor WPF XAML zaznamená `Name` nebo `x:Name` v XAML definované <xref:System.Windows.ResourceDictionary>, název není přidán do jakékoli obor namescope XAML. Pokusu o nalezení tento název ze libovolný obor namescope XAML a `FindName` metody nebude vrátí platné výsledky.  
  
### <a name="xname-and-name"></a>x: Name a název  
 Mnoho scénářů aplikaci WPF se můžete vyhnout použitím této `x:Name` atribut, protože `Name` vlastnost závislosti jako zadaný ve výchozím oboru názvů XAML pro několik důležitých základních tříd, jako <xref:System.Windows.FrameworkElement> a <xref:System.Windows.FrameworkContentElement> splňuje stejný účel. Dál jsou uvedeny některé obvyklé scénáře XAML a WPF kde kód přístup k prvku bez `Name` vlastnosti na úrovni rozhraní framework je důležité. Například některé animace a scénáře třídy, které podporují nepodporují `Name` vlastnost, ale často potřebují nejde odkazovat v kódu, aby bylo možné řídit animace. Je třeba zadat `x:Name` jako atribut časové osy a transformace, které jsou vytvořeny v XAML, pokud chcete později odkazovat z kódu.  
  
 Pokud <xref:System.Windows.FrameworkElement.Name%2A> je k dispozici jako vlastnost ve třídě, <xref:System.Windows.FrameworkElement.Name%2A> a `x:Name` zaměnitelné jako atributy, ale pokud se zadají obě jsou u stejného elementu se dojít k výjimce analýzy. Pokud XAML je kompilaci kódu, výjimka dojde při kompilaci kódu, jinak proběhne zatížení.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> lze nastavit pomocí syntaxe atributu XAML a v kódu pomocí <xref:System.Windows.DependencyObject.SetValue%2A>; však toto nastavení <xref:System.Windows.FrameworkElement.Name%2A> vlastností v kódu nevytvoří odkaz reprezentativní pole v rámci XAML namescope ve většině případů, ve kterém je již XAML načíst. Namísto pokusu o nastavení <xref:System.Windows.FrameworkElement.Name%2A> v kódu, použijte <xref:System.Windows.NameScope> metody z kódu proti odpovídající obor namescope.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> Můžete také nastavit pomocí syntax prvku vlastnosti vnitřního ovládacího prvku, ale to je běžné. Naproti tomu `x:Name` nelze nastavit v syntax prvku vlastnosti XAML, nebo v kódu pomocí <xref:System.Windows.DependencyObject.SetValue%2A>; ho lze nastavit pouze pomocí syntaxe atributu na objekty, protože se jedná direktivu.  
  
## <a name="silverlight-usage-notes"></a>Poznámky k použití aplikace Silverlight  
 `x:Name` pro prostředí Silverlight je zdokumentován samostatně. Další informace najdete v tématu [Namespace XAML (x:) Funkce jazyka (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>  
 <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>  
 [Stromy v subsystému WPF](../../../docs/framework/wpf/advanced/trees-in-wpf.md)
