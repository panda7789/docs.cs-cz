---
title: Kontexty služby dostupné pro převaděče typů a rozšíření značek
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services how-to
ms.assetid: b4dad00f-03da-4579-a4e9-d8d72d2ccbce
ms.openlocfilehash: 850e266aed6fc2d69722ba6dac3baa3e115678a8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59147794"
---
# <a name="service-contexts-available-to-type-converters-and-markup-extensions"></a>Kontexty služby dostupné pro převaděče typů a rozšíření značek
Autoři typy, které podporují použití rozšíření typ převaděče a značky musí mít často kontextové informace o tom, kde je umístěn v kódu nebo v kolem objektu struktura využití. Informace může být nutné tak, že je správně vytvořena instance zadaného objektu, nebo tak, aby odkazy na objekty existujících objektů v grafu objektů lze provést. Při použití rozhraní .NET Framework XAML Services, kontext, který může být vyžadováno vystavena jako řadu rozhraní služeb. Kód podpory rozšíření typ pro převaděč nebo značky můžete dotazovat služby pomocí kontextu poskytovatele služby, který je k dispozici a předaných z <xref:System.Xaml.XamlObjectWriter> nebo souvisejících typů. Kontext schématu XAML je k dispozici přímo prostřednictvím jedné konkrétní služby. Toto téma popisuje, jak získat přístup k kontexty služby z implementace převodníku hodnotu a uvádí obvykle dostupných služeb a jejich rolí.  
  
<a name="obtaining_services"></a>   
## <a name="obtaining-services"></a>Získání služby  
 Jako implementátora převaděče hodnoty často potřebují přístup pro nějaký typ kontext, ve kterém je použito převaděč hodnoty. Tento kontext může obsahovat informace, jako je aktivní kontext schématu XAML, přístup k mapování systém typů, které poskytují kontext schématu XAML a XAML objektu zapisovače a tak dále. Dostupnost služeb pro implementaci kódu rozšíření nebo typ převaděče se předávají prostřednictvím kontextové parametry, které jsou součástí podpis každé virtuální metody. V každém případě je nutné <xref:System.IServiceProvider> implementované v kontextu a může volat <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType> k požádání o službu.  
  
<a name="services_for_a_markup_extension"></a>   
## <a name="services-for-a-markup-extension"></a>Služby rozšíření značek  
 <xref:System.Windows.Markup.MarkupExtension> má pouze jednu virtuální metoda <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>. Vstup `serviceProvider` parametr je, jak služby se předávají do implementace při volání rozšíření značek XAML procesoru. Následujícím pseudokódu ukazuje, jak může dotazovat implementaci rozšíření značek pro služby v jeho <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>:  
  
```  
public override object ProvideValue(IServiceProvider serviceProvider)  
{  
...  
    // Get the IXamlTypeResolver from the service provider  
    if (serviceProvider == null)  
    {  
        throw new ArgumentNullException("serviceProvider");  
    }  
    IXamlTypeResolver xamlTypeResolver = serviceProvider.GetService(typeof(IXamlTypeResolver)) as IXamlTypeResolver;  
    if (xamlTypeResolver == null)  
   {  
        throw new ArgumentException("IXamlTypeResolver"));  
    }  
...  
}  
```  
  
<a name="services_for_a_type_converter"></a>   
## <a name="services-for-a-type-converter"></a>Služby pro konvertor typu  
 <xref:System.ComponentModel.TypeConverter> má čtyři virtuální metody, které používají místní služby, které podporují použití XAML. Každá z těchto metod předá vstupní `context` parametru. Tento parametr je typu <xref:System.ComponentModel.ITypeDescriptorContext>, ale tato rozhraní dědí <xref:System.IServiceProvider>a proto neexistuje <xref:System.IServiceProvider.GetService%2A> metody dostupné pro převaděče implementace typu.  
  
 Následujícím pseudokódu ukazuje, jak na typ převaděče implementace pro použití XAML může dotázat na služby v jednom z jeho přepsání, v tomto případě <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>:  
  
```  
public override object ConvertFrom(ITypeDescriptorContext typeDescriptorContext,  
  CultureInfo cultureInfo,  
  object source)  
{  
    IRootObjectProvider rootProvider = typeDescriptorContext.GetService(typeof(IRootObjectProvider)) as IRootObjectProvider;  
    if (rootProvider != null && source is String)  
    {  
        //return something, else ...  
    }  
    throw GetConvertFromException(source);  
}  
```  
  
<a name="services_for_a_value_serializer"></a>   
## <a name="services-for-a-value-serializer"></a>Služby pro serializátor hodnoty  
 Pro hodnotu kontext serializátoru, použijte typ zprostředkovatele služby, který je přizpůsobený <xref:System.Windows.Markup.ValueSerializer> třídy, <xref:System.Windows.Markup.IValueSerializerContext>. Tento kontext je předán přepsání těchto čtyř <xref:System.Windows.Markup.ValueSerializer> virtuální metody. Volání <xref:System.IServiceProvider.GetService%2A> z kontextu získat services.  
  
<a name="using_the_xaml_service_provider_contexts"></a>   
## <a name="using-the-xaml-service-provider-contexts"></a>Pomocí kontexty poskytovatele služby XAML  
 Poskytovatel služeb pro <xref:System.IServiceProvider.GetService%2A> přístup ke službám XAML do kódu rozšíření nebo typ převaděče k dispozici je implementovaný jako vnitřní třída, s vystavení jenom prostřednictvím rozhraní a jak je předána do relevantní kontext. Pokaždé, když operaci zpracování XAML v výchozí implementace rozhraní .NET Framework XAML Services načíst cesta nebo cesta pro uložení vyvolá relevantní značek rozšíření nebo typ převaděče metody, které vyžadují kontext služby, Tento vnitřní objekt je předán. V závislosti na situaci, poskytuje kontext služby systému buď `MarkupExtensionContext` nebo `TextSyntaxContext`, ale nespecifikuje, obě tyto třídy jsou vnitřní. Interakce s těchto tříd je omezeno na žádost o služby, prostřednictvím <xref:System.IServiceProvider.GetService%2A>.  
  
<a name="available_systemxaml_services"></a>   
## <a name="available-services-from-the-net-framework-xaml-service-context"></a>Dostupné služby z kontextu služby rozhraní .NET Framework XAML  
 Rozhraní .NET framework XAML Services definuje služby rozšíření značek, převaděče typů, hodnota serializátory a potenciálně další použití. Následující části popisují každou z těchto služeb a poskytuje pokyny, jak může služba použít v implementaci.  
  
### <a name="iserviceprovider"></a>IServiceProvider  
 **Referenční dokumentace**: <xref:System.IServiceProvider>  
  
 **Relevantní pro:** Základní operace založené na službách infrastruktury v rozhraní .NET Framework, takže můžete volat <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType>.  
  
### <a name="itypedescriptorcontext"></a>ITypeDescriptorContext  
 **Referenční dokumentace**: <xref:System.ComponentModel.ITypeDescriptorContext>  
  
 Je odvozen od <xref:System.IServiceProvider>. Tato třída reprezentuje kontext ve standardu <xref:System.ComponentModel.TypeConverter> podpisů. <xref:System.ComponentModel.TypeConverter> je třída, která již od rozhraní .NET Framework 1.0. To je starší než XAML a XAML <xref:System.ComponentModel.TypeConverter> scénář pro převod typu řetězec hodnota. V rámci rozhraní .NET Framework XAML Services metody <xref:System.ComponentModel.TypeConverter> jsou explicitně implementované. Určuje chování explicitní implementaci volajícím, který <xref:System.ComponentModel.ITypeDescriptorContext> rozhraní API se nevztahuje typu systému XAML nebo pro čtení nebo zápis objektů z XAML. <xref:System.ComponentModel.ITypeDescriptorContext.Container%2A>, <xref:System.ComponentModel.ITypeDescriptorContext.Instance%2A>, a <xref:System.ComponentModel.ITypeDescriptorContext.PropertyDescriptor%2A> obvykle vracet `null` z rozhraní .NET Framework XAML Services kontexty.  
  
### <a name="ivalueserializercontext"></a>IValueSerializerContext  
 **Referenční dokumentace**: <xref:System.Windows.Markup.IValueSerializerContext>  
  
 Je odvozen od <xref:System.ComponentModel.ITypeDescriptorContext> a také závisí na explicitní implementace rozhraní potlačit false důsledky o typu systému XAML. Podporuje vyhledávání statické pomocné metody na <xref:System.Windows.Markup.ValueSerializer>.  
  
### <a name="ixamltyperesolver"></a>IXamlTypeResolver  
 **Referenční dokumentace**: <xref:System.Windows.Markup.IXamlTypeResolver>  
  
 **Určené:** <xref:System.Windows.Markup> oboru názvů System.Xaml sestavení  
  
 **Relevantní pro:** Načíst cestu scénáře a interakci se kontext schématu XAML  
  
 **Rozhraní API služby:**  <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>  
  
 Mohou mít vliv na mapování typu XAML CLR, který je potřeba, pokud zapisovač XAML vytvoří objekt CLR v grafu objektů. <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A> zpracuje potenciálně kvalifikací předponu řetězec, který odpovídá název typu XAML (<xref:System.Xaml.XamlType.Name%2A?displayProperty=nameWithType>) a vrátí modul CLR <xref:System.Type>. Řešení typů je obvykle silně závisí na kontext schématu XAML. Pouze kontext schématu XAML je důležité informace o seznámen, jako jsou načtené sestavení, a které z těchto sestavení můžete nebo by měl mít přístup pro rozlišení typu.  
  
### <a name="iuricontext"></a>IUriContext  
 **Referenční dokumentace**: <xref:System.Windows.Markup.IUriContext>  
  
 **Určené:** <xref:System.Windows.Markup> oboru názvů System.Xaml sestavení  
  
 **Relevantní pro:** Načíst cestu a uložit cestu zpracování hodnoty členů, které jsou identifikátory URI nebo `x:Uri` hodnoty.  
  
 **Rozhraní API služby:**  <xref:System.Windows.Markup.IUriContext.BaseUri%2A>  
  
 Tato služba sestavy globálně dostupné kořenový identifikátor URI, pokud existuje. Kořenový identifikátor URI lze použít k vyřešení relativní identifikátory URI na absolutní URI nebo naopak. Tento scénář je důležité hlavně pro aplikační služby, které jsou vystaveny konkrétní architekturu nebo funkce třídy často používaných kořenový element v rámci. Základní identifikátor URI je možné navázat XAML pro čtenáře nastavení, která je pak předán pomocí objektu zapisovače XAML a reportovanou touto službou.  
  
### <a name="iambientprovider"></a>IAmbientProvider  
 **Referenční dokumentace**: <xref:System.Xaml.IAmbientProvider>  
  
 **Určené:** <xref:System.Xaml> oboru názvů System.Xaml sestavení  
  
 **Relevantní pro:** Načíst vyhledávání odložení zpracování a zadejte cestu nebo optimalizace.  
  
 **Rozhraní API služeb:**<xref:System.Xaml.IAmbientProvider.GetAllAmbientValues%2A>, 3 ostatní.  
  
 Koncept podmínek v XAML je technika k označení určitého člena typu jako okolí. Typ, případně může být okolí tak, aby všechny hodnoty vlastností, které obsahují instanci typu by měl být vedlejším vlastnostem. Rozšíření značek nebo převaděče typů, které jsou dále na datový proud uzlu XAML a následníky v grafu objektů, které jsou přístupné vedlejší vlastnost nebo typ instance v okamžiku načtení; nebo může použít znalostní báze v okolí struktury ušetřit čas. To může ovlivnit stupeň podmínku, které je potřeba vyřešit typy pro jiné služby, například pro <xref:System.Windows.Markup.IXamlTypeResolver> nebo pro `x:Type`. Viz také <xref:System.Xaml.AmbientPropertyValue>.  
  
### <a name="ixamlschemacontextprovider"></a>IXamlSchemaContextProvider  
 **Referenční dokumentace**: <xref:System.Xaml.IXamlSchemaContextProvider>  
  
 **Určené:** <xref:System.Xaml> oboru názvů System.Xaml sestavení  
  
 **Relevantní pro:** Načíst cestu a jakékoli operaci, která se musí přeložit typ XAML základního typu.  
  
 **Rozhraní API služby:**  <xref:System.Xaml.IXamlSchemaContextProvider.SchemaContext%2A>  
  
 Kontext schématu XAML je nezbytné pro všechny operace zatížení odložit, protože stejný kontext schématu musí fungovat odložené oblasti, aby bylo možné integrovat odloženého obsahu. Další informace o roli kontext schématu XAML najdete v tématu [XAML Services](index.md).  
  
### <a name="irootobjectprovider"></a>IRootObjectProvider  
 **Referenční dokumentace**: <xref:System.Xaml.IRootObjectProvider>  
  
 **Určené:** <xref:System.Xaml> oboru názvů System.Xaml sestavení  
  
 **Relevantní pro:** Načíst cestu.  
  
 **Rozhraní API služby:**  <xref:System.Xaml.IRootObjectProvider.RootObject%2A>  
  
 Tato služba je relevantní pro aplikační služby, které jsou vystaveny konkrétní rozhraním nebo funkce třídy často používaných kořenový element v rámci. Použití modelu code-behind a její události připojení jeden scénář pro získání kořenového objektu. Například WPF provádění `x:Class` se používá pro značky kompilace a její jakéhokoliv atributu obslužná rutina události, která se nachází na další pozici ve značkách XAML. Spojovací bod značky a modelu code-behind definované částečné třídy pro kompilaci kódu je kořenový element.  
  
### <a name="ixamlnamespaceresolver"></a>IXamlNamespaceResolver  
 **Referenční dokumentace**: <xref:System.Xaml.IXamlNamespaceResolver>  
  
 **Určené:** <xref:System.Xaml> oboru názvů System.Xaml sestavení  
  
 **Relevantní pro:** Načíst cestu, cesta pro uložení.  
  
 **Rozhraní API služby:** <xref:System.Xaml.IXamlNamespaceResolver.GetNamespace%2A> pro cestu zatížení <xref:System.Xaml.IXamlNamespaceResolver.GetNamespacePrefixes%2A> pro cesta pro uložení.  
  
 <xref:System.Xaml.IXamlNamespaceResolver> je služba, která vrací identifikátor oboru názvů XAML / identifikátor URI na základě jeho předpony jako mapované v původní kód XAML.  
  
### <a name="iprovidevaluetarget"></a>IProvideValueTarget  
 **Referenční dokumentace**: <xref:System.Windows.Markup.IProvideValueTarget>  
  
 **Určené:** <xref:System.Windows.Markup> oboru názvů System.Xaml sestavení  
  
 **Relevantní pro:** Načíst cestu a uložit cestu.  
  
 **Rozhraní API služeb:**<xref:System.Windows.Markup.IProvideValueTarget.TargetObject%2A>, <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A>.  
  
 <xref:System.Windows.Markup.IProvideValueTarget> umožňuje získat kontext, o kterém funguje v okamžiku načtení typ převaděče nebo značky rozšíření. Implementace může používat kontext tohoto zrušit platnost využití. Například WPF, jako je logika uvnitř některé z jeho rozšíření značek <xref:System.Windows.DynamicResourceExtension>. Logické kontroly <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A> abyste měli jistotu, že rozšíření slouží pouze k nastavení vlastnosti závislosti (nebo krátký seznam dalších vlastností bez závislostí).  
  
### <a name="ixamlnameresolver"></a>IXamlNameResolver  
 **Referenční dokumentace**: <xref:System.Xaml.IXamlNameResolver>  
  
 **Určené:** <xref:System.Xaml> oboru názvů System.Xaml sestavení  
  
 **Relevantní pro:** Načíst definice grafu objekt cesty, řešení objekty identifikovaný `x:Name`, `x:Reference`, nebo techniky pro konkrétní rozhraní.  
  
 **Rozhraní API služeb:**<xref:System.Xaml.IXamlNameResolver.Resolve%2A>; jiná rozhraní API pro pokročilejší scénáře, jako je řešení dopředné odkazy.  
  
 Implementace rozhraní .NET Framework XAML Services `x:Reference` zpracování závisí na tuto službu. Konkrétní rozhraní nebo nástroje, které podporují rozhraní framework pomocí této služby pro `x:Name` zpracování nebo ekvivalentní (<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> s atributy) vlastnosti zpracování.  
  
### <a name="idestinationtypeprovider"></a>IDestinationTypeProvider  
 **Referenční dokumentace**: <xref:System.Xaml.IDestinationTypeProvider>  
  
 **Určené:** <xref:System.Xaml> oboru názvů System.Xaml sestavení  
  
 **Relevantní pro:** Načíst cestu řešení nepřímé informace o typu modulu CLR.  
  
 **Rozhraní API služby:** <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>  
  
 Další informace naleznete v tématu <xref:System.Xaml.IDestinationTypeProvider>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [Přehled rozšíření značek pro jazyk XAML](markup-extensions-for-xaml-overview.md)
- [Přehled převaděčů typů pro jazyk XAML](type-converters-for-xaml-overview.md)
