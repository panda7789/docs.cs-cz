---
title: Typy migrované z prostředí WPF do oboru názvů System.Xaml
ms.date: 03/30/2017
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
ms.openlocfilehash: 943cdb2a21cbf2f95ef7fe2feefe6c0e71f57be4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939685"
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>Typy migrované z prostředí WPF do oboru názvů System.Xaml
V .NET Framework 3,5 a .NET Framework 3,0 zahrnuje i [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] programovací model Windows Workflow Foundation implementaci jazyka XAML. Mnohé z veřejných typů, které poskytly rozšíření pro implementaci WPF XAML, existují v sestaveních WindowsBase, PresentationCore a PresentationFramework. Podobně veřejné typy, které v sestavení System. Workflow. ComponentModel poskytly rozšíření pro programovací model Windows Workflow Foundation XAML. V .NET Framework 4 jsou některé typy související s jazykem XAML migrovány do sestavení System. XAML. Společná implementace .NET Framework jazykových služeb jazyka XAML umožňuje mnoho scénářů rozšiřitelnosti XAML, které byly původně definovány implementací XAML konkrétního rozhraní, ale nyní jsou součástí celkové podpory jazyka XAML .NET Framework 4. Toto téma obsahuje seznam typů, které se migrují, a popisuje problémy související s migrací.  
  
<a name="assemblies_and_namespaces"></a>   
## <a name="assemblies-and-namespaces"></a>Sestavení a obory názvů  
 V .NET Framework 3,5 a .NET Framework 3,0 byly v <xref:System.Windows.Markup> oboru názvů obecně implementovány typy, které WPF implementovaly pro podporu XAML. Většina těchto typů byla v WindowsBase sestavení.  
  
 V .NET Framework 4 existuje nový <xref:System.Xaml> obor názvů a nové sestavení System. XAML. Mnohé z typů, které byly původně implementovány pro WPF XAML, jsou nyní poskytovány jako body rozšiřitelnosti nebo služby pro jakoukoli implementaci jazyka XAML. V rámci zpřístupnění pro obecnější scénáře jsou typy typu předávány z původního sestavení WPF do sestavení System. XAML. To umožňuje scénáře rozšiřitelnosti XAML bez nutnosti zahrnutí sestavení jiných rozhraní (například WPF a programovací model Windows Workflow Foundation).  
  
 U migrovaných typů zůstává většina typů v <xref:System.Windows.Markup> oboru názvů. Bylo by částečně zabráněno přerušení mapování oboru názvů CLR ve stávajících implementacích pro jednotlivé soubory. V důsledku toho <xref:System.Windows.Markup> obor názvů v .NET Framework 4 obsahuje kombinaci obecných typů podpory jazyka XAML (ze sestavení System. XAML) a typů, které jsou specifické pro implementaci WPF XAML (z WindowsBase a dalších sestavení WPF). Jakýkoli typ, který byl migrován do System. XAML, ale dříve existoval v sestavení WPF, má podporu předávání typů ve verzi 4 sestavení WPF.  
  
### <a name="workflow-xaml-support-types"></a>Typy podpory jazyka XAML v pracovním postupu  
 Programovací model Windows Workflow Foundation také poskytnuté typy podpory XAML a v mnoha případech mají stejné krátké názvy jako ekvivalent WPF. Následuje seznam programovací model Windows Workflow Foundation typy podpory jazyka XAML:  
  
- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>  
  
 Tyto typy podpory stále existují v programovací model Windows Workflow Foundation sestavení pro .NET Framework 4 a lze je nadále používat pro konkrétní programovací model Windows Workflow Foundation aplikace. neměly by však být odkazovány aplikacemi nebo architekturami, které nepoužívají programovací model Windows Workflow Foundation.  
  
<a name="markupextension"></a>   
## <a name="markupextension"></a>MarkupExtension  
 V .NET Framework 3,5 a .NET Framework 3,0 <xref:System.Windows.Markup.MarkupExtension> byla třída pro WPF v WindowsBase sestavení. V sestavení System. Workflow. <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>ComponentModel existovala paralelní třída pro programovací model Windows Workflow Foundation. V .NET Framework 4 <xref:System.Windows.Markup.MarkupExtension> je třída migrována do sestavení System. XAML. V .NET Framework 4 <xref:System.Windows.Markup.MarkupExtension> je určena pro jakýkoli scénář rozšiřitelnosti XAML, který používá služby .NET Framework XAML, nikoli jenom pro ty, které se vytvářejí v konkrétních rozhraních. Pokud je to možné, konkrétní architektury nebo uživatelský kód v rozhraní by měly také sestavit <xref:System.Windows.Markup.MarkupExtension> třídu pro rozšíření XAML.  
  
<a name="markupextension_supporting_service_classes"></a>   
## <a name="markupextension-supporting-service-classes"></a>Třídy MarkupExtension podporující třídy služeb  
 .NET Framework 3,5 a .NET Framework 3,0 pro WPF poskytuje několik služeb, které byly k <xref:System.Windows.Markup.MarkupExtension> dispozici pro <xref:System.ComponentModel.TypeConverter> implementátory a implementace pro podporu typu a vlastností v jazyce XAML. Tyto služby jsou následující:  
  
- <xref:System.Windows.Markup.IProvideValueTarget>  
  
- <xref:System.Windows.Markup.IUriContext>  
  
- <xref:System.Windows.Markup.IXamlTypeResolver>  
  
> [!NOTE]
> Další službou z .NET Framework 3,5, která souvisí s rozšířeními značek, <xref:System.Windows.Markup.IReceiveMarkupExtension> je rozhraní. <xref:System.Windows.Markup.IReceiveMarkupExtension>nebyla migrována a je označena `[Obsolete]` pro .NET Framework 4. Ve scénářích, <xref:System.Windows.Markup.IReceiveMarkupExtension> které dřív použili <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> , by místo toho měly používat zpětná volání s atributy. <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute>je také označeno `[Obsolete]`.  
  
<a name="xaml_language_features"></a>   
## <a name="xaml-language-features"></a>Funkce jazyka XAML  
 Několik funkcí jazyka XAML a komponent pro WPF existovalo v PresentationFramework sestavení. Tyto byly implementovány jako <xref:System.Windows.Markup.MarkupExtension> podtřídou pro zveřejnění použití rozšíření značek v kódu XAML. V .NET Framework 4 existují v sestavení System. XAML tak, aby projekty, které neobsahují sestavení WPF, mohly používat tyto funkce na úrovni jazyka XAML. WPF používá stejné implementace pro aplikace .NET Framework 4. Stejně jako ostatní případy, které jsou uvedeny v tomto tématu, pomocné typy nadále existují v <xref:System.Windows.Markup> oboru názvů, aby nedošlo k přerušení předchozích odkazů.  
  
 Následující tabulka obsahuje seznam tříd podpory funkce XAML, které jsou definovány v souboru System. XAML.  
  
|Funkce jazyka XAML|Použití|  
|---------------------------|-----------|  
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|  
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|  
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|  
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|  
  
 I když System. XAML nemůže mít konkrétní třídy podpory, je obecná logika pro zpracování jazykových funkcí pro jazyk XAML nyní uložena v souboru System. XAML a v jeho implementovaných čtecích modulech XAML a zapisovači XAML. Například `x:TypeArguments` je atribut, který je zpracován modulem XAML Readers a moduly pro zápis XAML z implementace System. XAML; lze jej poznamenat v datovém proudu uzlu XAML, který zpracovává ve výchozím kontextu schématu XAML (CLR-based), má typ XAML-System. reprezentace a tak dále. V důsledku toho je referenční dokumentace pro všechny funkce na úrovni jazyka XAML dílčí téma pro [služby XAML](index.md) a obecné místo sady dokumentace pro .NET Framework, místo aby bylo součástí dokumentace k WPF jako dílčí téma [pokročilého ( Windows Presentation Foundation)](../wpf/advanced/index.md) (jak je stále v sadě dokumentace 3,5).  
  
<a name="valueserializer_and_supporting_classes"></a>   
## <a name="valueserializer-and-supporting-classes"></a>Objekt ValueSerializer nemůže a podpůrné třídy  
 <xref:System.Windows.Markup.ValueSerializer> Třída podporuje převod typu na řetězec, zejména pro případy serializace XAML, kde serializace může vyžadovat více režimů nebo uzlů ve výstupu. V .NET Framework 3,5 a .NET Framework 3,0 <xref:System.Windows.Markup.ValueSerializer> byl pro WPF v WindowsBase sestavení. V .NET Framework 4 <xref:System.Windows.Markup.ValueSerializer> je třída v System. XAML a je určena pro jakýkoli scénář rozšiřitelnosti XAML, nikoli pouze pro ty, které se vytvářejí v WPF. <xref:System.Windows.Markup.IValueSerializerContext>(podpůrná služba) a <xref:System.Windows.Markup.DateTimeValueSerializer> (konkrétní podtřída) se migrují také na System. XAML.  
  
<a name="xamlrelated_attributes"></a>   
## <a name="xaml-related-attributes"></a>Atributy související s jazykem XAML  
 WPF XAML obsahuje několik atributů, které lze použít na typy CLR pro indikaci toho, jak se chování XAML. Následuje seznam atributů, které existovaly v sestaveních WPF v .NET Framework 3,5 a .NET Framework 3,0. Tyto atributy jsou migrovány do souboru System. XAML v .NET Framework 4.  
  
- <xref:System.Windows.Markup.AmbientAttribute>  
  
- <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
- <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
- <xref:System.Windows.Markup.DependsOnAttribute>  
  
- <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
- <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
- <xref:System.Windows.Markup.RootNamespaceAttribute>  
  
- <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
- <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
- <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
- <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
- <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
- <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
- <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
- <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
<a name="miscellaneous_classes"></a>   
## <a name="miscellaneous-classes"></a>Různé třídy  
 <xref:System.Windows.Markup.IComponentConnector> Rozhraní existovalo v WindowsBase v .NET Framework 3,5 a .NET Framework 3,0, ale existuje v souboru System. XAML v .NET Framework 4. <xref:System.Windows.Markup.IComponentConnector>je primárně určena pro podporu nástrojů a kompilátory kódu XAML.  
  
 <xref:System.Windows.Markup.INameScope> Rozhraní existovalo v WindowsBase v .NET Framework 3,5 a .NET Framework 3,0, ale existuje v souboru System. XAML v .NET Framework 4. <xref:System.Windows.Markup.INameScope>definuje základní operace pro namescope XAML.  
  
<a name="xamlrelated_classes_with_shared_names_that_exist_in_wpf_and_systemxaml"></a>   
## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>Třídy související s jazykem XAML se sdílenými názvy, které existují v jazyce WPF a System. XAML  
 Následující třídy existují v sestaveních WPF i v sestavení System. XAML v .NET Framework 4:  
  
 `XamlReader`  
  
 `XamlWriter`  
  
 `XamlParseException`  
  
 Implementace WPF se nachází v <xref:System.Windows.Markup> oboru názvů a v PresentationFramework sestavení. V <xref:System.Xaml> oboru názvů se nachází implementace System. XAML. Pokud používáte typy WPF nebo jsou odvozeny z typů WPF, měli byste obvykle použít implementace WPF pro <xref:System.Windows.Markup.XamlReader> a <xref:System.Windows.Markup.XamlWriter> namísto implementace System. XAML. Další informace najdete v tématu poznámky v <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> a <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>.  
  
 Pokud zahrnujete odkazy na sestavení WPF a System. XAML a používáte také `include` příkazy pro <xref:System.Windows.Markup> obory názvů a <xref:System.Xaml> , možná budete muset plně kvalifikovat volání těchto rozhraní API, aby bylo možné tyto typy přeložit. bez nejednoznačnosti.  
  
## <a name="see-also"></a>Viz také:

- [XAML Services](index.md)
