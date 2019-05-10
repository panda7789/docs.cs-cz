---
title: Výchozí kontext schématu XAML a kontext WPF schématu XAML
ms.date: 03/30/2017
ms.assetid: 04e06a15-09b3-4210-9bdf-9a64c2eccb83
ms.openlocfilehash: f29d9eb481903b06ee1f35424baeb055a396b7c1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663283"
---
# <a name="default-xaml-schema-context-and-wpf-xaml-schema-context"></a>Výchozí kontext schématu XAML a kontext WPF schématu XAML
Kontext schématu XAML je koncepční entita, která kvalifikuje interakci produkční XAML, který používá určité slovníkové XAML s objektem zápis chování, včetně způsob mapování typu řeší, jak jsou načtené sestavení, jak některé čtečky a zapisovače nastavení jsou interpretovány. Toto téma popisuje funkce rozhraní .NET Framework XAML Services a přidružené výchozí kontext schématu XAML, která je založena na systému typů CLR. Toto téma také popisuje kontext schématu XAML, který se používá pro WPF.  
  
## <a name="default-xaml-schema-context"></a>Výchozí kontext schématu XAML  
 Rozhraní .NET framework XAML Services implementuje a používá výchozí kontext schématu XAML. Výchozí chování kontext schématu XAML není vždy plně viditelný v rozhraní API <xref:System.Xaml.XamlSchemaContext> třídy. Ale v mnoha případech se chování, které ovlivňuje výchozí kontext schématu XAML pozorovat prostřednictvím společného rozhraní API typu systému XAML, jako je například členové <xref:System.Xaml.XamlMember> nebo <xref:System.Xaml.XamlType>, nebo prostřednictvím rozhraní API, které jsou zveřejněné na XAML čtečky a zapisovače XAML, které používáte Výchozí kontext schématu XAML.  
  
 Můžete vytvořit <xref:System.Xaml.XamlSchemaContext> , který zapouzdřuje výchozí chování při volání <xref:System.Xaml.XamlSchemaContext> konstruktoru. Tím se explicitně vytvoří výchozí kontext schématu XAML. Stejnou výchozí kontext schématu XAML se implicitně vytvoří, pokud inicializovat XAML čtečky nebo zapisovače XAML pomocí rozhraní API, která se nedají zadat explicitně <xref:System.Xaml.XamlSchemaContext> vstupního parametru.  
  
 Výchozí kontext schématu XAML závisí na reflexi CLR pro své chování pro mapování typu. Jedná se o zkoumání definující CLR <xref:System.Type>a související <xref:System.Reflection.PropertyInfo> nebo <xref:System.Reflection.MethodInfo>. Aby bylo možné zadejte podrobnosti pro XAML typ nebo člen informace o XAML, který používá typ podpory modulu CLR se také používá attribution CLR na typech nebo členech. Výchozí kontext schématu XAML nevyžaduje, aby typ systému rozšíření techniky, jako `Invoker` vzorek, protože je k dispozici v systému typů CLR potřebné informace.  
  
 Pro načítání logiku sestavení výchozí kontext schématu XAML se využívají hlavně všechny hodnoty sestavení zadaná v mapování oboru názvů XAML. Navíc <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A> můžete pomocného parametru sestavení, které chcete načíst pro scénáře, jako je například načtení vnitřní typy.  
  
## <a name="wpf-xaml-schema-context"></a>WPF XAML Schema Context  
 Kontext schématu XAML WPF je popsané v tomto tématu, protože poskytuje implementaci WPF zajímavé ilustraci typy funkcí, které je možné vytvářet implementací jiné než výchozí kontext schématu XAML. Navíc koncept kontext schématu XAML není velmi mnohem podrobněji dokumentace WPF, která řeší WPF XAML; chování, které umožňuje kontext schématu XAML může být pouze plně srozumitelný, pokud je integrovaný s diskusi o tom, jak funguje výchozí kontext schématu XAML. Kontext schématu XAML WPF implementuje toto chování.  
  
 **Vyhledání přepsání:** WPF obsahuje několik modelů obsahu pro XAML tam, kde jsou vlastnosti obsahu XAML, které fungují bez <xref:System.Windows.Markup.ContentPropertyAttribute> s atributy. <xref:System.Xaml.XamlType.LookupContentProperty%2A> přepsání pro WPF implementaci tohoto chování.  
  
 **Odložení pro WPF výrazy:** WPF obsahuje několik výrazů tříd, které hodnotu odložit, dokud nebude k dispozici kontext modulu runtime. Rozšíření šablon je také chování modulu runtime, který využívá techniky odložení.  
  
 **Typ optimalizace vyhledávání systému:** WPF má rozsáhlé XAML slovník a objekt modelu, včetně definice členů základní třídy, které dědí doslova stovky tříd definovaných WPF. Také WPF, samotného je rozdělena mezi několik sestavení. WPF optimalizuje jeho typ vyhledávání pomocí vyhledávacích tabulek a dalších metod. To nabízí vylepšení výkonu v porovnání s výchozí kontext schématu XAML a jeho vyhledání typu založeného na modulu CLR. V případech, kde typy neexistují ve vyhledávací tabulce používá chování XAML schématu kontextu techniky, které jsou podobné výchozí kontext schématu XAML.  
  
 **Typ XamlType a XamlMember rozšíření:** WPF rozšiřuje vlastnost prostřednictvím vlastností závislosti a události pojmy za použití směrovaných událostí. Tyto koncepty poskytnout větší viditelnost pro operace zpracování XAML, WPF rozšiřuje <xref:System.Xaml.XamlType> a <xref:System.Xaml.XamlMember>a přidá vnitřní vlastnosti, které sestavy vlastnost závislosti a směrovat vlastnosti události.  
  
### <a name="accessing-the-wpf-xaml-schema-context"></a>Přístup k kontext schématu XAML WPF  
 Pokud používáte XAML techniky, které jsou založeny na WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> nebo <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>, kontext schématu XAML WPF se už používá na XAML čtečky a zapisovače implementace XAML.  
  
 Pokud používáte jiné XAML čtečky nebo zapisovače implementace XAML, které nebyl inicializován s kontext schématu XAML WPF, bude pravděpodobně možné začít pracovat WPF XAML kontext schématu z <xref:System.Windows.Markup.XamlReader.GetWpfSchemaContext%2A?displayProperty=nameWithType>. Pak můžete tuto hodnotu jako inicializace pro ostatní rozhraní API, které použijte <xref:System.Xaml.XamlSchemaContext>. Například lze zavolat <xref:System.Xaml.XamlXmlReader.%23ctor%2A> pro inicializaci a předejte jí kontext schématu XAML WPF. Nebo můžete použít kontext schématu XAML WPF pro operace typu systému XAML. To může zahrnovat inicializace konstrukce <xref:System.Xaml.XamlType> nebo <xref:System.Xaml.XamlMember>, nebo zavolání <xref:System.Xaml.XamlSchemaContext.GetXamlType%2A?displayProperty=nameWithType>.  
  
 Všimněte si, že pokud přistupujete některé aspekty WPF XAML z čistě perspektiv datový proud uzlu XAML, některé funkce rozhraní WPF nemusí se zachovali ještě. Například WPF šablony pro ovládací prvky ještě se nepoužívají. Proto pokud přístup k vlastnosti, která v době běhu může být vyplní celý vizuální strom, může zobrazovat jenom hodnotu vlastnosti, která odkazuje na šablonu. Kontext služby pro WPF – rozšíření značek k dispozici také nemusí být přesné, pokud od situace – modul runtime a může vést k výjimkám při pokusu o zápis grafu objektů.  
  
## <a name="xaml-and-assembly-loading"></a>XAML a načítání sestavení  
 Načítání XAML a rozhraní .NET Framework XAML Services sestavení se integruje s konceptem CLR definované <xref:System.AppDomain>. Kontext schématu XAML interpretuje načtení sestavení nebo najít typy v době běhu nebo návrhu, založené na použití <xref:System.AppDomain> a dalších faktorů. Logika se mírně liší v závislosti na tom, zda XAML je volný XAML pro čtečku XAML, je zkompilován s knihovnou DLL pomocí XAML `XamlBuildTask`, nebo je generován BAML pro WPF `PresentationBuildTask`.  
  
 Kontext WPF schématu XAML se integruje s modelem aplikace WPF, která dále používá <xref:System.AppDomain> a dalších faktorů, které jsou podrobnosti o implementaci WPF.  
  
#### <a name="xaml-reader-input-loose-xaml"></a>Čtečka vstup XAML (volný XAML)  
  
1. Kontext schématu XAML prochází <xref:System.AppDomain> aplikace hledání už načíst sestavení, která odpovídá názvu, všechny aspekty od nejvíce nedávno načíst sestavení. Pokud se najde shoda, toto sestavení se používá pro rozlišení.  
  
2. V opačném případě jednu z následujících postupů na základě CLR <xref:System.Reflection.Assembly> rozhraní API slouží k načtení sestavení:  
  
    - Pokud se název kvalifikovaný v mapování, zavolejte <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> na kvalifikovaný název.  
  
    - Pokud předchozí krok nebyl úspěšný, použijte krátký název (a token veřejného klíče Pokud jsou k dispozici) pro volání <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
    - Pokud je název nekvalifikované v mapování, zavolejte <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.  
  
#### <a name="xamlbuildtask"></a>XamlBuildTask  
 `XamlBuildTask` se používá pro Windows Communication Foundation (WCF) a Windows Workflow Foundation.  
  
 Všimněte si, že sestavení se odkazuje prostřednictvím `XamlBuildTask` jsou vždy plně kvalifikovaný.  
  
1. Volání <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> na kvalifikovaný název.  
  
2. Pokud předchozí krok nebyl úspěšný, použijte krátký název (a token veřejného klíče Pokud jsou k dispozici) pro volání <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
#### <a name="baml-presentationbuildtask"></a>BAML (PresentationBuildTask)  
 Existují dva aspekty k načtení sestavení BAML: načítání počáteční sestavení, který obsahuje BAML jako součást a načítání sestavení základní typ pro typy, které odkazuje produkční BAML.  
  
##### <a name="assembly-load-for-initial-markup"></a>Načtení sestavení pro počáteční značky:  
 Odkaz na sestavení pro načtení značky z je vždy neúplné.  
  
1. Kontext schématu XAML WPF prochází <xref:System.AppDomain> aplikace WPF, hledá již načtena sestavení, která odpovídá názvu, všechny aspekty od nejvíce nedávno načíst sestavení. Pokud se najde shoda, toto sestavení se používá pro rozlišení.  
  
2. Pokud předchozí krok nebyl úspěšný, použijte krátký název (a token veřejného klíče Pokud jsou k dispozici) pro volání <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
##### <a name="assembly-references-by-baml-types"></a>Odkazy na sestavení podle typů BAML:  
 Odkazy na sestavení pro typy používané v produkčním prostředí BAML jsou vždy plně kvalifikovaný, jako výstup úkolu sestavení.  
  
1. Kontext schématu XAML WPF prochází <xref:System.AppDomain> aplikace WPF, hledá již načtena sestavení, která odpovídá názvu, všechny aspekty od nejvíce nedávno načíst sestavení. Pokud se najde shoda, toto sestavení se používá pro rozlišení.  
  
2. Jednu z následujících postupů v opačném případě se používá k načtení sestavení:  
  
    - Volání <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> na kvalifikovaný název.  
  
    - Pokud krátký název + veřejné token kombinace kláves odpovídaly sestavení, která byla načtena BAML z, použijte toto sestavení.  
  
    - Použít krátký název a token veřejného klíče pro volání <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také:

- [Principy struktur a koncepcí streamu uzlů XAML](understanding-xaml-node-stream-structures-and-concepts.md)
