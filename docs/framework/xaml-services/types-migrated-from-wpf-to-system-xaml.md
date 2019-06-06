---
title: Typy migrované z prostředí WPF do oboru názvů System.Xaml
ms.date: 03/30/2017
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
ms.openlocfilehash: ea8ab81b192e0e8cb40988cb67cce08a7d9dab82
ms.sourcegitcommit: 90f0bee0e8a416e45c78fa3ad4c91ef00e5228d5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2019
ms.locfileid: "66722574"
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>Typy migrované z prostředí WPF do oboru názvů System.Xaml
V rozhraní .NET Framework 3.5 a [!INCLUDE[net_v30_long](../../../includes/net-v30-long-md.md)], obě [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] Windows Workflow Foundation součástí implementace jazyka XAML. V sestavení WindowsBase PresentationCore a PresentationFramework existuje mnoho veřejných typů, které rozšíření k dispozici pro implementaci WPF XAML. Obdobně veřejných typů, které poskytuje rozšíření pro Windows Workflow Foundation XAML existoval v System.Workflow.ComponentModel sestavení. V rozhraní .NET Framework 4 některé typy související s XAML se migrují do oboru názvů System.Xaml sestavení. Běžnou implementaci rozhraní .NET Framework jazykových služeb XAML umožňuje mnoho scénářů rozšíření XAML, které byly původně definované implementací konkrétního rozhraní XAML, ale jsou teď součástí celkového jazykovou podporu rozhraní .NET Framework 4 XAML. Toto téma obsahuje seznam typů, které se migrují a popisuje problémy související s migrací.  
  
<a name="assemblies_and_namespaces"></a>   
## <a name="assemblies-and-namespaces"></a>Sestavení a obory názvů  
 V rozhraní .NET Framework 3.5 a rozhraní .NET Framework 3.0 se obecně v typy, které WPF implementovány pro podporu XAML <xref:System.Windows.Markup> oboru názvů. Většina z těchto typů byly v WindowsBase sestavení.  
  
 V rozhraní .NET Framework 4, je tu nový <xref:System.Xaml> obor názvů a vytvoření nového oboru názvů System.Xaml sestavení. Mnoho typů, které byly původně implementované pro WPF XAML se teď poskytují jako body rozšiřitelnosti nebo služby pro žádnou implementaci XAML. Jako součást zpřístupňuje je pro obecnější scénáře typy jsou předány typu z jeho původní sestavení WPF do oboru názvů System.Xaml sestavení. To umožňuje scénáře rozšiřitelnost XAML bez nutnosti zahrnout sestavení další platformy (jako je například WPF a Windows Workflow Foundation).  
  
 Pro migrované typů většina typů zůstat v <xref:System.Windows.Markup> oboru názvů. To bylo částečně vyhnuli narušení funkčnosti mapování názvového prostoru CLR v existujících implementací na základě podle souborů. V důsledku toho <xref:System.Windows.Markup> obor názvů v rozhraní .NET Framework 4 obsahuje kombinaci obecné typy podporu jazyka XAML (z oboru názvů System.Xaml sestavení) a typy, které jsou specifické pro implementaci WPF XAML (z WindowsBase a jiných sestavení WPF). Libovolný typ, který se migrovat do oboru názvů System.Xaml, ale dříve ve WPF sestavení, má podporu předávání typů v WPF sestavení verze 4.  
  
### <a name="workflow-xaml-support-types"></a>Typy podporu XAML workflowu  
 Windows Workflow Foundation také poskytované typy podporu XAML a v mnoha případech tyto měl stejné krátké názvy do WPF ekvivalentní. Následuje seznam typy podporu Windows Workflow Foundation XAML:  
  
- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>  
  
 Tato podpora typy stále existují v sestaveních Windows Workflow Foundation pro .NET Framework 4 a stále můžete použít pro konkrétní aplikace Windows Workflow Foundation; Nicméně, neměly by být odkazovány aplikace nebo rozhraní, které nepoužívají model Windows Workflow Foundation.  
  
<a name="markupextension"></a>   
## <a name="markupextension"></a>MarkupExtension  
 V rozhraní .NET Framework 3.5 a rozhraní .NET Framework 3.0 <xref:System.Windows.Markup.MarkupExtension> třídy pro WPF v WindowsBase sestavení. Paralelní třídy pro Windows Workflow Foundation <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>, byl vytvořen v System.Workflow.ComponentModel sestavení. V rozhraní .NET Framework 4 <xref:System.Windows.Markup.MarkupExtension> třídy je migrovat do oboru názvů System.Xaml sestavení. V rozhraní .NET Framework 4 <xref:System.Windows.Markup.MarkupExtension> je určená pro jakýkoli scénář rozšiřitelnost XAML, který používá rozhraní .NET Framework XAML Services, ne jenom pro ty, které sestavení na konkrétní rozhraní. Pokud je to možné, konkrétní rozhraní nebo uživatelský kód v rámci má také sestavit <xref:System.Windows.Markup.MarkupExtension> třídy pro rozšíření XAML.  
  
<a name="markupextension_supporting_service_classes"></a>   
## <a name="markupextension-supporting-service-classes"></a>Třídy MarkupExtension podpora  
 Rozhraní .NET framework 3.5 a rozhraní .NET Framework 3.0 pro WPF poskytuje několik služeb, které byly k dispozici <xref:System.Windows.Markup.MarkupExtension> implementátory a <xref:System.ComponentModel.TypeConverter> implementace pro podporu použití typu nebo vlastnosti v XAML. Tyto služby jsou následující:  
  
- <xref:System.Windows.Markup.IProvideValueTarget>  
  
- <xref:System.Windows.Markup.IUriContext>  
  
- <xref:System.Windows.Markup.IXamlTypeResolver>  
  
> [!NOTE]
>  Jiná služba v rozhraní .NET Framework 3.5, která souvisí s – rozšíření značek <xref:System.Windows.Markup.IReceiveMarkupExtension> rozhraní. <xref:System.Windows.Markup.IReceiveMarkupExtension> nebyl migrován a je označen `[Obsolete]` pro rozhraní .NET Framework 4. Scénáře, které se dřív používal <xref:System.Windows.Markup.IReceiveMarkupExtension> vhodné použít <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> s atributy zpětná volání. <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> je také označena `[Obsolete]`.  
  
<a name="xaml_language_features"></a>   
## <a name="xaml-language-features"></a>Funkce jazyka XAML  
 Několik funkcí jazyka XAML a komponenty pro WPF dříve existoval PresentationFramework sestavení. Tyto byly implementovány jako <xref:System.Windows.Markup.MarkupExtension> podtřídy vystavit použití rozšíření značky ve značkách XAML. V rozhraní .NET Framework 4 existují v oboru názvů System.Xaml sestavení tak, aby projekty, které neobsahují WPF sestavení můžete použít tyto funkce na úrovni jazyka XAML. WPF tyto stejné implementace používá pro aplikace rozhraní .NET Framework 4. Jak s další případy, které jsou uvedeny v tomto tématu, nadále existovat v podpůrných typy <xref:System.Windows.Markup> obor názvů, abyste se vyhnuli narušení funkčnosti předchozí odkazy.  
  
 Následující tabulka obsahuje seznam podporovaných funkcích třídy XAML, které jsou definovány v oboru názvů System.Xaml.  
  
|Funkce jazyka XAML|Použití|  
|---------------------------|-----------|  
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|  
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|  
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|  
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|  
  
 I když oboru názvů System.Xaml nemusí mít třídy, které konkrétní podporují, obecné logiku pro zpracování funkcí jazyka pro jazyk XAML nyní nachází v oboru názvů System.Xaml a jeho implementované XAML čtečky a zapisovače XAML. Například `x:TypeArguments` je atribut, který zpracovává XAML čtečky a zapisovače XAML z oboru názvů System.Xaml implementací; můžete jste si poznamenali v datovém proudu uzlu XAML, má zpracování ve výchozí kontext schématu XAML (založený na modulu CLR), má o typu systému XAML znázornění a tak dále. V důsledku toho referenční dokumentaci pro všechny funkce na úrovni jazyka XAML je Tematická pro [XAML Services](index.md) této sadě dokumentace rozhraní .NET Framework, namísto části dokumentace WPF nastavit jako obecné oblasti a Tematická z [Upřesnit (Windows Presentation Foundation)](../wpf/advanced/index.md) (což je stále písmena v 3.5 sady dokumentace).  
  
<a name="valueserializer_and_supporting_classes"></a>   
## <a name="valueserializer-and-supporting-classes"></a>ValueSerializer a podporu tříd  
 <xref:System.Windows.Markup.ValueSerializer> Třída podporuje typ převodu na řetězec, zejména pro XAML serializace případy, kdy serializace může vyžadovat více režimů nebo uzly ve výstupu. V rozhraní .NET Framework 3.5 a rozhraní .NET Framework 3.0 <xref:System.Windows.Markup.ValueSerializer> pro WPF v WindowsBase sestavení. V rozhraní .NET Framework 4 <xref:System.Windows.Markup.ValueSerializer> třída je v oboru názvů System.Xaml a je určená pro jakýkoli scénář rozšiřitelnost XAML, ne jenom pro ty, jejichž základem WPF. <xref:System.Windows.Markup.IValueSerializerContext> (podpůrná služba) a <xref:System.Windows.Markup.DateTimeValueSerializer> (konkrétní podtřídy) migrují do oboru názvů System.Xaml.  
  
<a name="xamlrelated_attributes"></a>   
## <a name="xaml-related-attributes"></a>Atributy vztahující se k XAML  
 WPF XAML zahrnuté několik atributů, které lze použít u typů CLR k označení něco o své chování pro XAML. Následuje seznam atributů, které existují v sestaveních WPF v rozhraní .NET Framework 3.5 a rozhraní .NET Framework 3.0. Tyto atributy se migrují do oboru názvů System.Xaml v rozhraní .NET Framework 4.  
  
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
 <xref:System.Windows.Markup.IComponentConnector> Rozhraní existovala v WindowsBase v rozhraní .NET Framework 3.5 a rozhraní .NET Framework 3.0, ale neexistuje v oboru názvů System.Xaml v rozhraní .NET Framework 4. <xref:System.Windows.Markup.IComponentConnector> je primárně určena pro nástroje podpory a kompilátory značek XAML.  
  
 <xref:System.Windows.Markup.INameScope> Rozhraní existovala v WindowsBase v rozhraní .NET Framework 3.5 a rozhraní .NET Framework 3.0, ale neexistuje v oboru názvů System.Xaml v rozhraní .NET Framework 4. <xref:System.Windows.Markup.INameScope> definuje základní operace pro obor namescope XAML.  
  
<a name="xamlrelated_classes_with_shared_names_that_exist_in_wpf_and_systemxaml"></a>   
## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>Třídy související s XAML s sdílené názvy, které existují v projektech WPF a oboru názvů System.Xaml  
 V WPF sestavení a oboru názvů System.Xaml sestavení v rozhraní .NET Framework 4 existují následující třídy:  
  
 `XamlReader`  
  
 `XamlWriter`  
  
 `XamlParseException`  
  
 Implementaci WPF se nachází v <xref:System.Windows.Markup> obor názvů a PresentationFramework sestavení. Je součástí implementace oboru názvů System.Xaml <xref:System.Xaml> oboru názvů. Pokud používáte typy WPF nebo jsou odvozené od typy WPF, používejte obvykle implementace WPF <xref:System.Windows.Markup.XamlReader> a <xref:System.Windows.Markup.XamlWriter> místo oboru názvů System.Xaml implementace. Další informace najdete v části poznámky v <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> a <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>.  
  
 Pokud jsou včetně odkazů na sestavení WPF a oboru názvů System.Xaml a také používáte `include` příkazy pro obě <xref:System.Windows.Markup> a <xref:System.Xaml> obory názvů, musíte k plnému určení volání těchto rozhraní API pro překlad typů bez nejednoznačnost.  
  
## <a name="see-also"></a>Viz také:

- [XAML Services](index.md)
