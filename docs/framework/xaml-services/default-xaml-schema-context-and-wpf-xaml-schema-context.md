---
title: "Výchozí kontext schématu XAML a kontext WPF schématu XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04e06a15-09b3-4210-9bdf-9a64c2eccb83
caps.latest.revision: "7"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9ee7c83868934f1a524bb0068ea5e749e6cbfab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="default-xaml-schema-context-and-wpf-xaml-schema-context"></a>Výchozí kontext schématu XAML a kontext WPF schématu XAML
Kontext schématu XAML je koncepční entita, která kvalifikují jak provozní XAML používající konkrétní termínů XAML komunikuje s objektem zápis chování, včetně způsobu mapování typu řeší, jak se načíst sestavení, jak určitá čtení a zápis nastavení se interpretují. Toto téma popisuje funkce rozhraní .NET Framework XAML Services a přidružená výchozí kontext schématu XAML, který je založený na systému typu CLR. Toto téma také popisuje kontext schématu XAML, který se používá pro grafický subsystém WPF.  
  
## <a name="default-xaml-schema-context"></a>Výchozí kontext schématu XAML  
 Rozhraní .NET framework XAML Services implementuje a používá výchozí kontext schématu XAML. Výchozí chování kontext schématu XAML není vždy zcela viditelné v rozhraní API <xref:System.Xaml.XamlSchemaContext> třídy. V mnoha případech chování, které ovlivňuje výchozí kontext schématu XAML je však lze zobrazit prostřednictvím společné rozhraní API systému XAML typu, například členové <xref:System.Xaml.XamlMember> nebo <xref:System.Xaml.XamlType>, nebo prostřednictvím zveřejněné na XAML čtení a zápis XAML, které používají rozhraní API Výchozí kontext schématu XAML.  
  
 Můžete vytvořit <xref:System.Xaml.XamlSchemaContext> který zapouzdří výchozí chování při volání <xref:System.Xaml.XamlSchemaContext> konstruktor. Tím se explicitně vytvoří výchozí kontext schématu XAML. Stejné výchozí kontext schématu XAML se implicitně, vytvoří, pokud inicializovat XAML čtečky nebo pomocí rozhraní API, které nepřebírají explicitně zapisovače XAML <xref:System.Xaml.XamlSchemaContext> vstupní parametr.  
  
 Výchozí kontext schématu XAML závisí na reflexi CLR pro své chování mapování typu. To zahrnuje zkoumání definující CLR <xref:System.Type>a související <xref:System.Reflection.PropertyInfo> nebo <xref:System.Reflection.MethodInfo>. Chcete-li vyplnit specifika typ jazyka XAML nebo XAML člen informace, která používá zálohování typu modulu CLR se také používá CLR uvedení na typy nebo členy. Výchozí kontext schématu XAML nevyžaduje typ systému rozšíření techniky, jako `Invoker` vzor, protože informace potřebné k dispozici ze systému typu CLR.  
  
 Pro sestavení načítání logiku výchozí kontext schématu XAML závisí hlavně na žádné hodnoty sestavení zadaná v mapování oboru názvů jazyka XAML. Navíc <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A> můžete pomocného parametru sestavení načíst pro scénáře, jako je načítání interní typy.  
  
## <a name="wpf-xaml-schema-context"></a>Kontext schématu WPF XAML  
 Kontext schématu WPF XAML je popsaný v tomto tématu, protože implementace WPF poskytuje ilustraci zajímavých funkcí, které mohou být způsobeny implementace bez výchozí kontext schématu XAML. Také koncepce kontext schématu XAML není velmi mnohem zabývá WPF dokumentace, která řeší WPF XAML; chování, které umožňuje kontext schématu XAML může být pouze plně nerozumí, pokud je spojen s diskuzi o tom, jak funguje výchozí kontext schématu XAML. Kontext schématu WPF XAML implementuje toto chování.  
  
 **Přepsání vyhledávání:** WPF má několik obsahu modely pro jazyk XAML tam, kde nejsou k dispozici XAML obsahu vlastnosti, které funkce aniž by musel být <xref:System.Windows.Markup.ContentPropertyAttribute> s atributy. <xref:System.Xaml.XamlType.LookupContentProperty%2A>přepsání pro grafický subsystém WPF implementovat toto chování.  
  
 **Odložení pro výrazů WPF:** WPF funkce několik tříd výrazu, které odložení hodnotu, dokud nebude k dispozici modul runtime kontextu. Modul runtime chování, které využívá techniky odložení je také rozšíření šablony.  
  
 **Typ systému vyhledávání optimalizace:** WPF má rozsáhlé XAML termínů a objekt modelu, včetně definice člen základní třídy, které dědí na oznámena stovky tříd definovaných grafického subsystému WPF. Navíc WPF samotné je rozdělena mezi několik sestavení. WPF optimalizuje jeho typ vyhledávání pomocí vyhledávací tabulky a další metody. To nabízí vylepšení výkonu v porovnání s výchozí kontext schématu XAML a jeho vyhledávání na základě CLR typu. V případech, kde typy neexistují ve vyhledávací tabulce používá chování techniky kontext schématu XAML, které jsou podobná výchozí kontext schématu XAML.  
  
 **Rozšíření XamlType a XamlMember:** WPF rozšiřuje koncepty vlastnost s vlastností závislostí a událostí konceptech směrované události. Poskytnout tyto koncepty lepší viditelnost pro operace zpracování XAML, WPF rozšiřuje <xref:System.Xaml.XamlType> a <xref:System.Xaml.XamlMember>a přidá vnitřní vlastnosti, které sestavy vlastnost závislosti a směrují vlastnosti události.  
  
### <a name="accessing-the-wpf-xaml-schema-context"></a>Přístup k kontext schématu WPF XAML  
 Pokud používáte XAML techniky, které jsou založeny na formulářích WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> nebo <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>, kontext schématu WPF XAML je již používána na těchto čtečky XAML a implementace zapisovače XAML.  
  
 Pokud používáte jiné XAML čtečka nebo implementace zapisovače XAML, které není inicializovat s kontext schématu WPF XAML, bude pravděpodobně možné získat funkční WPF XAML schématu kontext z <xref:System.Windows.Markup.XamlReader.GetWpfSchemaContext%2A?displayProperty=nameWithType>. Potom můžete tuto hodnotu jako inicializace pro ostatní rozhraní API, které použít <xref:System.Xaml.XamlSchemaContext>. Například může volat <xref:System.Xaml.XamlXmlReader.%23ctor%2A> pro inicializaci a předejte jí kontext schématu WPF XAML. Nebo můžete použít kontext schématu WPF XAML pro operace systému typ XAML. To může zahrnovat inicializace vytváření <xref:System.Xaml.XamlType> nebo <xref:System.Xaml.XamlMember>, nebo volání <xref:System.Xaml.XamlSchemaContext.GetXamlType%2A?displayProperty=nameWithType>.  
  
 Všimněte si, že pokud z čistý perspektivy datový proud uzlu XAML konkrétních aspektů WPF XAML, některé z možností framework WPF nemusí mít reagovali ještě. Například WPF šablony pro ovládací prvky zatím nejsou použité. Proto pokud máte přístup k vlastnosti, která v době běhu může být vyplněny úplné vizuálním stromu, může zobrazit pouze hodnotu vlastnosti, která odkazuje na šablonu. Kontext služby zadaná pro rozšíření značek WPF také nemusí být přesné, pokud zadaná z situaci – modul runtime a může vést k výjimkám při pokusu o zápis grafu objektu.  
  
## <a name="xaml-and-assembly-loading"></a>XAML a načtení sestavení  
 Načítání pro XAML a rozhraní .NET Framework XAML Services sestavení se integruje s koncept definované CLR <xref:System.AppDomain>. Kontext schématu XAML interpretuje jak načíst sestavení nebo najít typy v době běhu nebo návrhu, založené na použití <xref:System.AppDomain> a dalších faktorů. Logika je mírně liší v závislosti na tom, jestli je XAML přijít XAML pro čtečku XAML, XAML zkompilovat do knihovny DLL pomocí `XamlBuildTask`, nebo je generován BAML na WPF `PresentationBuildTask`.  
  
 Kontext WPF schématu XAML integruje s modelem aplikace WPF, které dále používá <xref:System.AppDomain> a dalších faktorů, které jsou podrobnosti implementace WPF.  
  
#### <a name="xaml-reader-input-loose-xaml"></a>Vstup čtečky XAML (přijít XAML)  
  
1.  Kontext schématu XAML iteruje <xref:System.AppDomain> aplikace, hledá již načíst sestavení, která odpovídají všechny aspekty názvu, od nejvíc nedávno načíst sestavení. Pokud je nalezena shoda, se toto sestavení používá pro překlad.  
  
2.  Jeden z následujících postupů, jinak hodnota podle CLR <xref:System.Reflection.Assembly> rozhraní API slouží k načtení sestavení:  
  
    -   Pokud v mapování je kvalifikovaný název, volání <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> na kvalifikovaný název.  
  
    -   Pokud předchozí krok nebyl úspěšný, použít krátký název (a tokenu veřejného klíče pokud existuje) pro volání <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
    -   Pokud je název nekvalifikované v mapování, volání <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.  
  
#### <a name="xamlbuildtask"></a>XamlBuildTask  
 `XamlBuildTask`slouží k [!INCLUDE[vsindigo](../../../includes/vsindigo-md.md)] a [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)].  
  
 Všimněte si, že sestavení odkazuje na prostřednictvím `XamlBuildTask` jsou vždy úplný.  
  
1.  Volání <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> na kvalifikovaný název.  
  
2.  Pokud předchozí krok nebyl úspěšný, použít krátký název (a tokenu veřejného klíče pokud existuje) pro volání <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
#### <a name="baml-presentationbuildtask"></a>BAML (PresentationBuildTask)  
 Existují dva aspekty k načtení sestavení pro BAML: načítání počáteční sestavení, které obsahuje BAML jako součást a načítání sestavení základní typ pro všechny typy odkazuje BAML produkční.  
  
##### <a name="assembly-load-for-initial-markup"></a>Sestavení zatížení pro počáteční značku:  
 Odkaz na sestavení načíst kód z je vždy neúplné.  
  
1.  Kontext schématu WPF XAML iteruje <xref:System.AppDomain> aplikace WPF, hledá již načíst sestavení, která odpovídají všechny aspekty názvu, od nejvíc nedávno načíst sestavení. Pokud je nalezena shoda, se toto sestavení používá pro překlad.  
  
2.  Pokud předchozí krok nebyl úspěšný, použít krátký název (a tokenu veřejného klíče pokud existuje) pro volání <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
##### <a name="assembly-references-by-baml-types"></a>Odkazy na sestavení BAML typy:  
 Odkazy na sestavení pro typy používané v produkčním prostředí BAML jsou vždy plně kvalifikovaný jako výstup sestavovací úlohy.  
  
1.  Kontext schématu WPF XAML iteruje <xref:System.AppDomain> aplikace WPF, hledá již načíst sestavení, která odpovídají všechny aspekty názvu, od nejvíc nedávno načíst sestavení. Pokud je nalezena shoda, se toto sestavení používá pro překlad.  
  
2.  Jeden z následujících postupů, jinak hodnota slouží k načtení sestavení:  
  
    -   Volání <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> na kvalifikovaný název.  
  
    -   Pokud krátký název + veřejného klíče tokenu kombinace odpovídat sestavení, které BAML byl načten z, použijte toto sestavení.  
  
    -   Použít krátký název + tokenu veřejného klíče pro volání <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také  
 [Principy struktur a koncepcí streamu uzlů XAML](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)
