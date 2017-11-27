---
title: "Typy migrované z prostředí WPF do oboru názvů System.Xaml"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
caps.latest.revision: "14"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: db227b5c7915b6ce0b0fe8400a8545256ea6d6b3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>Typy migrované z prostředí WPF do oboru názvů System.Xaml
V [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] a [!INCLUDE[net_v30_long](../../../includes/net-v30-long-md.md)], oba [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] a [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] zahrnuty na implementace jazyka XAML. V sestavení WindowsBase PresentationCore a PresentationFramework řadu veřejné typy, které poskytuje rozšíření pro implementaci WPF XAML existuje. Podobně veřejné typy, poskytuje rozšíření pro [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] XAML existovalo v System.Workflow.ComponentModel sestavení. V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], některé typy související s jazykem XAML se migrují do System.Xaml sestavení. Běžná implementace rozhraní .NET Framework XAML services jazyka umožňuje mnoho scénářů XAML rozšiřitelnosti, které byly původně definované implementací konkrétní framework XAML, ale jsou teď součástí celkovým [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] podporu jazyka XAML. Toto téma uvádí typy, které se migrují a popisuje problémy související s migrací.  
  
<a name="assemblies_and_namespaces"></a>   
## <a name="assemblies-and-namespaces"></a>Sestavení a obory názvů  
 V [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] a [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], typy, které WPF implementována pro podporu XAML byly obecně v <xref:System.Windows.Markup> oboru názvů. Většina těchto typů byly v WindowsBase sestavení.  
  
 V [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], je nová <xref:System.Xaml> obor názvů a nové sestavení System.Xaml. Mnoho typů, které byly poprvé implementované pro jazyk XAML WPF jsou nyní uvedeny jako body rozšiřitelnosti nebo služby pro žádnou implementaci XAML. Jako součást, aby byly k dispozici pro další obecné scénáře typy jsou typ směrovaných z jejich původní WPF sestavení do System.Xaml sestavení. To umožňuje scénáře rozšiřitelnost XAML aniž byste museli zadat sestavení ostatní platformy (například WPF a [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)]).  
  
 Pro migrované typy většinu typů zůstat v <xref:System.Windows.Markup> oboru názvů. To bylo částečně vyhnout nejnovější mapování oboru názvů CLR ve stávající implementací na základě podle souborů. V důsledku toho <xref:System.Windows.Markup> oboru názvů v [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] obsahuje směs obecné typy podporu jazyka XAML (z System.Xaml sestavení) a typy, které jsou specifické pro implementaci WPF XAML (od ostatních sestavení WPF a WindowsBase). Žádný typ, který byl migrovat do oboru názvů System.Xaml, ale existoval dříve v sestavení WPF, má podporu předávání typů v verze 4 sestavení WPF.  
  
### <a name="workflow-xaml-support-types"></a>Typy podporu XAML workflowu  
 [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)]také zadaný XAML podporují typy a v mnoha případech tyto měl identickými krátkých názvů na ekvivalentní WPF. Následuje seznam [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] XAML podporují typy:  
  
-   <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>  
  
-   <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>  
  
-   <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>  
  
 Tato podpora typy nacházet v [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] sestavení pro [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] a pořád můžou použít pro konkrétní [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] aplikace; ale nesmí odkazovat aplikace nebo rozhraní, které nepoužívají [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)].  
  
<a name="markupextension"></a>   
## <a name="markupextension"></a>MarkupExtension  
 V [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] a [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], <xref:System.Windows.Markup.MarkupExtension> třídy pro WPF nebyla v sestavení WindowsBase. Paralelní třídy pro [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)], <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>, byl vytvořen v System.Workflow.ComponentModel sestavení. V [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], <xref:System.Windows.Markup.MarkupExtension> třída migrován do System.Xaml sestavení. V [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], <xref:System.Windows.Markup.MarkupExtension> je určený pro každý scénář rozšiřitelnost XAML, který používá rozhraní .NET Framework XAML Services, ne jenom pro ty, které vychází z konkrétní rozhraní. Pokud je to možné, konkrétní architektury nebo uživatelského kódu v rámci má také sestavit <xref:System.Windows.Markup.MarkupExtension> třída pro rozšíření XAML.  
  
<a name="markupextension_supporting_service_classes"></a>   
## <a name="markupextension-supporting-service-classes"></a>MarkupExtension podpora třídy služeb  
 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)]a [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] pro WPF poskytuje několik služeb, které byly dostupné pro <xref:System.Windows.Markup.MarkupExtension> implementátory informačních technologií a <xref:System.ComponentModel.TypeConverter> implementace pro podporu typu nebo vlastnost využití v jazyce XAML. Tyto služby jsou následující:  
  
-   <xref:System.Windows.Markup.IProvideValueTarget>  
  
-   <xref:System.Windows.Markup.IUriContext>  
  
-   <xref:System.Windows.Markup.IXamlTypeResolver>  
  
> [!NOTE]
>  Jiné služby z [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] které se vztahují k rozšíření značek je <xref:System.Windows.Markup.IReceiveMarkupExtension> rozhraní. <xref:System.Windows.Markup.IReceiveMarkupExtension>nebyl migrován a je označen jako `[Obsolete]` pro [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. Scénáře, které použil <xref:System.Windows.Markup.IReceiveMarkupExtension> měli místo toho použít <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> s atributy zpětných volání. <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute>je také označen `[Obsolete]`.  
  
<a name="xaml_language_features"></a>   
## <a name="xaml-language-features"></a>Funkce jazyka XAML  
 Několik funkce jazyka XAML a součásti pro grafický subsystém WPF dříve existoval v PresentationFramework sestavení. Tyto byly implementovány jako <xref:System.Windows.Markup.MarkupExtension> podtřídami vystavit použití rozšíření značek v kódu XAML. V [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], tyto existovat v System.Xaml sestavení tak, aby projekty, které neobsahují WPF sestavení můžete použít tyto funkce úroveň jazyka XAML. WPF používá tyto stejné implementace pro [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] aplikace. Jak se ostatních případech, které jsou uvedeny v tomto tématu, zůstanou podpůrné typy v <xref:System.Windows.Markup> obor názvů, abyste předešli porušení předchozí odkazy.  
  
 Následující tabulka obsahuje seznam tříd XAML podporovaných funkcích, které jsou definovány v System.Xaml.  
  
|Funkce jazyka XAML|Použití|  
|---------------------------|-----------|  
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|  
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|  
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|  
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|  
  
 I když System.Xaml nemusí mít třídy, které podporují konkrétní, obecné logiku pro zpracování funkce jazyka pro jazyk XAML teď se nachází v System.Xaml a jeho implementovaná XAML čtení a zápis XAML. Například `x:TypeArguments` je atribut, který zpracovává XAML čtení a zápis XAML z implementace System.Xaml; může být uvedeno v datový proud uzlu XAML, má zpracování ve výchozí kontext schématu XAML (CLR na základě), typ XAML – systém reprezentace a tak dále. V důsledku toho je referenční dokumentaci k nástroji pro všechny součásti úroveň jazyka XAML pro dílčí téma [XAML Services](../../../docs/framework/xaml-services/index.md) a této obecné oblasti sady dokumentace rozhraní .NET Framework, namísto součást nastavit jako dokumentace WPF dílčí téma z [Upřesnit (Windows Presentation Foundation)](../../../docs/framework/wpf/advanced/index.md) (protože je stále velká písmena v 3.5 sady dokumentace).  
  
<a name="valueserializer_and_supporting_classes"></a>   
## <a name="valueserializer-and-supporting-classes"></a>ValueSerializer a podpůrné třídy  
 <xref:System.Windows.Markup.ValueSerializer> Třída podporuje převod typů na řetězec, zejména pro případy serializace XAML, kde serializace může vyžadovat více režimy nebo uzlů ve výstupu. V [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] a [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], <xref:System.Windows.Markup.ValueSerializer> pro WPF nebyla v sestavení WindowsBase. V [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], <xref:System.Windows.Markup.ValueSerializer> třída je v System.Xaml a je určený pro každý scénář rozšiřitelnost XAML, ne jenom pro ty, které vychází z grafického subsystému WPF. <xref:System.Windows.Markup.IValueSerializerContext>(podpůrná služba) a <xref:System.Windows.Markup.DateTimeValueSerializer> (konkrétní podtřídy) jsou taky migrovat do oboru názvů System.Xaml.  
  
<a name="xamlrelated_attributes"></a>   
## <a name="xaml-related-attributes"></a>Atributy související s jazykem XAML  
 WPF XAML zahrnuty několik atributů, které lze použít pro typy CLR udávajících něco o jejich chování XAML. Následuje seznam atributů, které existovaly v sestavení WPF v sadě [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] a [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]. Tyto atributy se migrují do oboru názvů System.Xaml v [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
-   <xref:System.Windows.Markup.AmbientAttribute>  
  
-   <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
-   <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
-   <xref:System.Windows.Markup.DependsOnAttribute>  
  
-   <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
-   <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
-   <xref:System.Windows.Markup.RootNamespaceAttribute>  
  
-   <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
-   <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
-   <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
-   <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
-   <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
-   <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
-   <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
-   <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
<a name="miscellaneous_classes"></a>   
## <a name="miscellaneous-classes"></a>Různé třídy  
 <xref:System.Windows.Markup.IComponentConnector> Rozhraní existovalo v WindowsBase v [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] a [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], ale neexistují v System.Xaml v [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. <xref:System.Windows.Markup.IComponentConnector>je primárně určený pro tooling podporu a kompilátory kód XAML.  
  
 <xref:System.Windows.Markup.INameScope> Rozhraní existovalo v WindowsBase v [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] a [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], ale neexistují v System.Xaml v [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. <xref:System.Windows.Markup.INameScope>definuje základní operace pro XAML namescope.  
  
<a name="xamlrelated_classes_with_shared_names_that_exist_in_wpf_and_systemxaml"></a>   
## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>Třídy související s jazykem XAML s sdílené názvy, které se nacházejí ve WPF a System.Xaml  
 Následující třídy existovat v sestavení WPF a System.Xaml sestavení v [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]:  
  
 `XamlReader`  
  
 `XamlWriter`  
  
 `XamlParseException`  
  
 Implementace WPF se nachází v <xref:System.Windows.Markup> obor názvů a PresentationFramework sestavení. Implementace System.Xaml se nachází v <xref:System.Xaml> oboru názvů. Pokud používáte WPF typy nebo jsou odvozování z grafického subsystému WPF typy, měli byste obvykle použít implementace WPF <xref:System.Windows.Markup.XamlReader> a <xref:System.Windows.Markup.XamlWriter> místo System.Xaml implementace. Další informace najdete v části poznámky v <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> a <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>.  
  
 Pokud jsou včetně odkazy na sestavení WPF a System.Xaml a také používáte `include` příkazy pro oba <xref:System.Windows.Markup> a <xref:System.Xaml> obory názvů, musíte k plnému určení volání tato rozhraní API za účelem vyřešení typy bez nejednoznačnosti.  
  
## <a name="see-also"></a>Viz také  
 [XAML Services](../../../docs/framework/xaml-services/index.md)
