---
title: Výchozí kontext schématu XAML a kontext WPF schématu XAML
ms.date: 03/30/2017
ms.assetid: 04e06a15-09b3-4210-9bdf-9a64c2eccb83
ms.openlocfilehash: 2e92372de61230a98a02282cc28fc3f479cd94eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071862"
---
# <a name="default-xaml-schema-context-and-wpf-xaml-schema-context"></a>Výchozí kontext schématu XAML a kontext WPF schématu XAML
Kontext schématu XAML je koncepční entita, která kvalifikuje, jak produkce XAML, která používá konkrétní slovník XAML, interaguje s chováním zápisu objektu, včetně způsobu, jakým mapování typů řeší, jak jsou načtena sestavení, jak jsou interpretována určitá nastavení čtečky a zapisovače. Toto téma popisuje funkce služby .NET XAML Services a přidružený výchozí kontext schématu XAML, který je založen na systému typu CLR. Toto téma také popisuje kontext schématu XAML, který se používá pro WPF.

## <a name="default-xaml-schema-context"></a>Výchozí kontext schématu XAML

Služba .NET XAML Services implementuje a používá výchozí kontext schématu XAML. Výchozí chování kontextu schématu XAML není vždy plně viditelné <xref:System.Xaml.XamlSchemaContext> v rozhraní API třídy. V mnoha případech je však chování, které ovlivňuje výchozí kontext schématu XAML, pozorovatelné prostřednictvím společného <xref:System.Xaml.XamlMember> <xref:System.Xaml.XamlType>rozhraní API systému typu XAML, například členů nebo rozhraní API vystavených na čtečkách XAML a zapisovačích XAML, kteří používají výchozí kontext schématu XAML.

Můžete <xref:System.Xaml.XamlSchemaContext> vytvořit, který zapouzdřuje výchozí <xref:System.Xaml.XamlSchemaContext> chování voláním konstruktoru. To explicitně vytvoří výchozí kontext schématu XAML. Stejný výchozí kontext schématu XAML je vytvořen implicitně, pokud inicializujete čtečku XAML nebo zapisovač XAML pomocí rozhraní API, která explicitně neberou <xref:System.Xaml.XamlSchemaContext> vstupní parametr.

Výchozí kontext schématu XAML závisí na odrazu CLR pro jeho chování mapování typu. To zahrnuje zkoumání definování CLR <xref:System.Type>a <xref:System.Reflection.PropertyInfo> <xref:System.Reflection.MethodInfo>související nebo . Přiřazení CLR na typy nebo členy se také používá k vyplnění specifik pro typ XAML nebo informace o členu XAML, který používá typ zálohování CLR. Výchozí kontext schématu XAML nevyžaduje techniky rozšíření systému `Invoker` typu, jako je například vzorek, protože potřebné informace jsou k dispozici ze systému typu CLR.

Pro logiku načítání sestavení výchozí kontext schématu XAML závisí hlavně na všech hodnotách sestavení uvedených v mapování oboru názvů XAML. Také <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A> můžete naznačit sestavení načíst, pro scénáře, jako je například načítání vnitřnítypy.

## <a name="wpf-xaml-schema-context"></a>Kontext schématu WPF XAML

Kontext schématu WPF XAML je popsán v tomto tématu, protože implementace WPF poskytuje zajímavou ilustraci druhů funkcí, které lze zavést implementací nevýchozího kontextu schématu XAML. Koncept kontextu schématu XAML také není popsán příliš v dokumentaci WPF, která řeší WPF XAML; chování, které umožňuje kontext schématu XAML může být plně srozumitelné pouze v případě, že je integrován s diskusí o tom, jak funguje výchozí kontext schématu XAML. Kontext schématu WPF XAML implementuje následující chování.

**Přepsání vyhledávání:** WPF má několik modelů obsahu pro XAML, kde jsou vlastnosti obsahu XAML, které fungují bez atributu. <xref:System.Windows.Markup.ContentPropertyAttribute> <xref:System.Xaml.XamlType.LookupContentProperty%2A>přepsání pro WPF implementovat toto chování.

**Časově rozlišené výrazy WPF:** WPF obsahuje několik tříd výrazů, které odkládají hodnotu, dokud není k dispozici kontext za běhu. Rozšíření šablony je také runtime chování, které závisí na technikách časově rozlišených.

**Optimalizace vyhledávání typu systému:** WPF má rozsáhlý slovník XAML a objektový model, včetně definice členů základní třídy, které dědí doslova stovky WPF definované třídy. WPF sám je také rozložena do několika sestavení. WPF optimalizuje vyhledávání typu pomocí vyhledávacích tabulek a dalších technik. To poskytuje vylepšení výkonu oproti výchozímu kontextu schématu XAML a jeho vyhledávání typu clr. V případech, kdy typy neexistují ve vyhledávací tabulce, chování používá kontextové techniky schématu XAML, které jsou podobné výchozímu kontextu schématu XAML.

**Rozšíření XamlType a XamlMember:** WPF rozšiřuje koncepty vlastností s vlastnostmi závislostí a koncepty událostí se směrované události. Chcete-li poskytnout tyto koncepty větší přehled pro operace <xref:System.Xaml.XamlType> zpracování <xref:System.Xaml.XamlMember>XAML WPF rozšiřuje a , a přidá interní vlastnosti, které hlásí závislost vlastnost a směrované události charakteristiky.

### <a name="accessing-the-wpf-xaml-schema-context"></a>Přístup k kontextu schématu WPF XAML

Pokud používáte xaml techniky, které jsou <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>založeny na WPF nebo , wpf XAML kontextu schématu je již používán na ty implementace čtečky XAML a Zapisovač XAML.

Pokud používáte jiné implementace čtečky XAML nebo zapisovače XAML, které se neinicializují s kontextem schématu WPF XAML, <xref:System.Windows.Markup.XamlReader.GetWpfSchemaContext%2A?displayProperty=nameWithType>bude pravděpodobně možné získat funkční kontext schématu WPF XAML z . Tuto hodnotu pak můžete použít jako inicializaci pro jiné rozhraní API, které používají <xref:System.Xaml.XamlSchemaContext>. Můžete například volat <xref:System.Xaml.XamlXmlReader.%23ctor%2A> k inicializaci a předat kontext schématu WPF XAML. Nebo můžete použít kontext schématu WPF XAML pro operace systému typu XAML. To může zahrnovat inicializaci konstrukce <xref:System.Xaml.XamlType> nebo <xref:System.Xaml.XamlMember>nebo volání <xref:System.Xaml.XamlSchemaContext.GetXamlType%2A?displayProperty=nameWithType>.

Všimněte si, že pokud máte přístup k určité aspekty WPF XAML z čistého xaml uzlu datového proudu perspektivy, některé z wpf framework možnosti nemusí ještě jednal. Například WPF šablony pro ovládací prvky ještě nejsou použity. Pokud tedy přistupujete k vlastnosti, která může být za běhu naplněna úplným vizuálním stromem, může se zobrazit pouze hodnota vlastnosti, která odkazuje na šablonu. Kontext služby podaný pro rozšíření značek WPF také nemusí být přesné, pokud jsou poskytovány z prostředí bez běhu a může mít za následek výjimky při pokusu o zápis grafu objektů.

## <a name="xaml-and-assembly-loading"></a>Zatížení XAML a sestavení

Zatížení sestavení pro služby XAML a .NET XAML services <xref:System.AppDomain>se integruje s konceptem definovaného clr . Kontext schématu XAML interpretuje, jak buď načíst sestavení nebo najít typy v době <xref:System.AppDomain> běhu nebo návrhu, na základě použití a další faktory. Logika se mírně liší v závislosti na tom, zda je XAML volné XAML pro čtečku `XamlBuildTask`XAML, je XAML `PresentationBuildTask`zkompilován do DLL podle , nebo je BAML generován WPF .

Kontext schématu XAML pro WPF integruje s modelem aplikace <xref:System.AppDomain> WPF, který zase používá, stejně jako další faktory, které jsou podrobnosti implementace WPF.

#### <a name="xaml-reader-input-loose-xaml"></a>Vstup čtečky XAML (volný XAML)

01. Kontext schématu XAML itetuje <xref:System.AppDomain> prostřednictvím aplikace a hledá již načtené sestavení, které odpovídá všem aspektům názvu, počínaje naposledy načteným sestavením. Pokud je nalezena shoda, toto sestavení se používá pro rozlišení.

02. V opačném případě se k načtení sestavení používá jedna z následujících technik založených na rozhraní CLR <xref:System.Reflection.Assembly> API:

    - Pokud je název kvalifikovaný v <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> mapování, volání na kvalifikovaný název.

    - Pokud předchozí krok selže, použijte krátký název (a token <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>veřejného klíče, pokud je k dispozici) pro volání .

    - Pokud je název v mapování neúplný, volejte <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.

#### <a name="xamlbuildtask"></a>XamlBuildTask

`XamlBuildTask`používá se pro Windows Communication Foundation (WCF) a Windows Workflow Foundation.

Všimněte si, `XamlBuildTask` že odkazy na sestavení prostřednictvím jsou vždy plně kvalifikované.

1. Zavolejte <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> na kvalifikované jméno.

2. Pokud předchozí krok selže, použijte krátký název (a token <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>veřejného klíče, pokud je k dispozici) pro volání .

#### <a name="baml-presentationbuildtask"></a>BAML (PresentationBuildTask)

Existují dva aspekty zatížení sestavení pro BAML: zatížení počáteční sestavení, která obsahuje BAML jako součást a zatížení sestavení s podporou typu pro všechny typy, na které odkazuje výroba BAML.

##### <a name="assembly-load-for-initial-markup"></a>Montážní zatížení pro počáteční značky:

Odkaz na sestavení načíst značky z je vždy neúplný.

1. WPF XAML kontextu schématu iterates <xref:System.AppDomain> prostřednictvím aplikace WPF, hledá již načtené sestavení, které odpovídá všem aspektům názvu, počínaje naposledy načtené sestavení. Pokud je nalezena shoda, toto sestavení se používá pro rozlišení.

2. Pokud předchozí krok selže, použijte krátký název (a token <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>veřejného klíče, pokud je k dispozici) pro volání .

##### <a name="assembly-references-by-baml-types"></a>Odkazy na sestavy podle typů BAML:

Odkazy na sestavení pro typy používané ve výrobě BAML jsou vždy plně kvalifikované jako výstup úlohy sestavení.

01. WPF XAML kontextu schématu iterates <xref:System.AppDomain> prostřednictvím aplikace WPF, hledá již načtené sestavení, které odpovídá všem aspektům názvu, počínaje naposledy načtené sestavení. Pokud je nalezena shoda, toto sestavení se používá pro rozlišení.

02. V opačném případě se k načtení sestavy používá jedna z následujících technik:

    - Zavolejte <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> na kvalifikované jméno.
  
    - Pokud kombinace tokenu krátkého názvu + veřejného klíče odpovídá sestavení, ze kterého byl baml načten, použijte toto sestavení.

    - K volání <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>použijte token krátkého názvu + veřejného klíče .

## <a name="see-also"></a>Viz také

- [Principy struktur a koncepcí datových proudů uzlů XAML](understanding-xaml-node-stream-structures-and-concepts.md)
