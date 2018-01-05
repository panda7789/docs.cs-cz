---
title: "Kontexty služby dostupné pro převaděče typů a rozšíření značek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: XAML [XAML Services], type converter services how-to
ms.assetid: b4dad00f-03da-4579-a4e9-d8d72d2ccbce
caps.latest.revision: "13"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a75a5e6c6e6f627606ef5883655b6780e7519bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="service-contexts-available-to-type-converters-and-markup-extensions"></a>Kontexty služby dostupné pro převaděče typů a rozšíření značek
Autoři typy, které podporují použití rozšíření typ převaděče a značku, musí mít často kontextové informace o tom, kde je umístěna do kódu nebo v blízkém strukturu grafu objektů na používání. Informace mohou být potřebné tak, že je správně vytvořit instanci zadaného objektu nebo tak, aby objekt odkazy na stávající objekty v grafu objektů můžete provést. Při použití rozhraní .NET Framework XAML Services, je k dispozici kontext, který může být vyžadován jako řadu rozhraní služeb. Typ převaděče nebo značek rozšíření podpory kódu můžete dotazovat pro službu pomocí kontextu poskytovatele služby, který je k dispozici a předaný prostřednictvím z <xref:System.Xaml.XamlObjectWriter> nebo související typy. Kontext schématu XAML je přímo k dispozici prostřednictvím jednoho z těchto služeb. Toto téma popisuje, jak k kontexty služby z na hodnotu převaděč implementace a uvádí obvykle dostupné služby a jejich rolí.  
  
<a name="obtaining_services"></a>   
## <a name="obtaining-services"></a>Získání služby  
 Jako implementátora převaděče hodnoty často potřebují přístup na nějaký typ kontextu, ve kterém je použit převaděč hodnoty. Tento kontext může obsahovat informace, jako je active kontext schématu XAML, přístup k systému mapování typu, který kontext schématu XAML a zapisovače objektu XAML zadejte a tak dále. Dostupnost služeb pro implementaci značek rozšíření nebo typ převaděče se předávají prostřednictvím kontextové parametry, které jsou součástí podpis jednotlivé virtuální metody. V každém případě máte <xref:System.IServiceProvider> implementována v kontextu a můžete volat <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType> k požádání o službu.  
  
<a name="services_for_a_markup_extension"></a>   
## <a name="services-for-a-markup-extension"></a>Služby rozšíření značek  
 <xref:System.Windows.Markup.MarkupExtension>má jenom jeden virtuální metody <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>. Vstup `serviceProvider` parametr je, jak služby se předávají implementace při volání rozšíření značek procesorem XAML. Následující pseudokódu ukazuje, jak může dotazovat na implementace rozšíření značek pro služby v jeho <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>:  
  
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
## <a name="services-for-a-type-converter"></a>Služby pro převaděče typů  
 <xref:System.ComponentModel.TypeConverter>má čtyři virtuální metody, které používají kontext služby, které podporují použití XAML. Každá z těchto metod předá vstup `context` parametr. Tento parametr je typu <xref:System.ComponentModel.ITypeDescriptorContext>, ale tato rozhraní dědí <xref:System.IServiceProvider>a proto není <xref:System.IServiceProvider.GetService%2A> metoda dostupné pro převaděče implementace typů.  
  
 Následující pseudokódu ukazuje, jak na typ převaděče implementace pro použití, XAML může dotazovat na služby v jednom z jeho přepsání, v takovém případě <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>:  
  
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
## <a name="services-for-a-value-serializer"></a>Služby pro serializátor hodnota  
 Pro hodnotu kontext serializátoru, použijete typ poskytovatele služby, které jsou specifické pro <xref:System.Windows.Markup.ValueSerializer> třídy <xref:System.Windows.Markup.IValueSerializerContext>. Tento kontext je předán přepsání těchto čtyř <xref:System.Windows.Markup.ValueSerializer> virtuální metody. Volání <xref:System.IServiceProvider.GetService%2A> z kontextu získat services.  
  
<a name="using_the_xaml_service_provider_contexts"></a>   
## <a name="using-the-xaml-service-provider-contexts"></a>Pomocí kontexty poskytovatele služby XAML  
 Poskytovatel služeb pro <xref:System.IServiceProvider.GetService%2A> přístup ke službám XAML dostupné pro převaděče rozšíření nebo typ značky je implementovaný jako interní třída, s ohrožení pouze prostřednictvím rozhraní a jak se předávají do příslušných kontextu. Pokaždé, když zpracování operace XAML v výchozí implementace rozhraní .NET Framework XAML Services načíst cestu nebo cestu uložení vyvolá relevantní značek rozšíření nebo typ převaděče metody, které vyžadují kontext služby, je předán Tento vnitřní objekt. V závislosti na okolnosti, poskytuje kontext služby systému buď `MarkupExtensionContext` nebo `TextSyntaxContext`, ale jsou specifikace obě tyto třídy jsou interní. Interakce se tyto třídy je omezena na vyžádání služby z nich, prostřednictvím <xref:System.IServiceProvider.GetService%2A>.  
  
<a name="available_systemxaml_services"></a>   
## <a name="available-services-from-the-net-framework-xaml-service-context"></a>K dispozici služby z kontextu služby rozhraní .NET Framework XAML  
 Rozhraní .NET framework XAML Services definuje služby rozšíření značek, převaděčů typů, hodnota serializátorů a potenciálně další použití. Následující části popisují každou z těchto služeb a obsahují pokyny o tom, jak služba může být používány implementace.  
  
### <a name="iserviceprovider"></a>IServiceProvider  
 **Referenční dokumentace**:<xref:System.IServiceProvider>  
  
 **Pro relevantní:** základní operace založený na službách infrastruktury v rozhraní .NET Framework, aby můžete volat <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType>.  
  
### <a name="itypedescriptorcontext"></a>ITypeDescriptorContext  
 **Referenční dokumentace**:<xref:System.ComponentModel.ITypeDescriptorContext>  
  
 Odvozená z <xref:System.IServiceProvider>. Tato třída reprezentuje kontextu standardní <xref:System.ComponentModel.TypeConverter> podpisů. <xref:System.ComponentModel.TypeConverter> je třída, která již od rozhraní .NET Framework 1.0. Ho je starší než XAML a XAML <xref:System.ComponentModel.TypeConverter> scénář pro převod typů hodnotu řetězce. V rámci rozhraní .NET Framework XAML Services metody <xref:System.ComponentModel.TypeConverter> jsou explicitně implementované. Explicitní implementace chování označuje volajícím, která <xref:System.ComponentModel.ITypeDescriptorContext> rozhraní API není relevantní pro XAML typ systémy, nebo pro čtení nebo zápis objektů z XAML. <xref:System.ComponentModel.ITypeDescriptorContext.Container%2A>, <xref:System.ComponentModel.ITypeDescriptorContext.Instance%2A>, a <xref:System.ComponentModel.ITypeDescriptorContext.PropertyDescriptor%2A> obecně vrátit `null` z rozhraní .NET Framework XAML Services kontexty.  
  
### <a name="ivalueserializercontext"></a>IValueSerializerContext  
 **Referenční dokumentace**:<xref:System.Windows.Markup.IValueSerializerContext>  
  
 Odvozená z <xref:System.ComponentModel.ITypeDescriptorContext> a také závisí na explicitní implementace potlačit false důsledky o systém typů XAML. Podporuje vyhledávání statické pomocné metody na <xref:System.Windows.Markup.ValueSerializer>.  
  
### <a name="ixamltyperesolver"></a>IXamlTypeResolver  
 **Referenční dokumentace**:<xref:System.Windows.Markup.IXamlTypeResolver>  
  
 **Určené:** <xref:System.Windows.Markup> oboru názvů System.Xaml sestavení  
  
 **Pro relevantní:** zatížení cesta scénáře a interakci s kontext schématu XAML  
  
 **Rozhraní API služby:**  <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>  
  
 Můžete ovlivnit mapování typu XAML CLR, které je potřeba, pokud modul pro zápis XAML vytvoří objekt CLR v grafu objektu. <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>zpracuje potenciálně předponu kvalifikovaný řetězec, který odpovídá názvu typu XAML (<xref:System.Xaml.XamlType.Name%2A?displayProperty=nameWithType>) a vrátí CLR <xref:System.Type>. Řešení typy je obvykle silně závislá na kontext schématu XAML. Pouze kontext schématu XAML si je vědoma aspektů, jako je sestavení, které jsou načteny a která z těchto sestavení můžete nebo by měly být dostupné pro typ řešení.  
  
### <a name="iuricontext"></a>IUriContext  
 **Referenční dokumentace**:<xref:System.Windows.Markup.IUriContext>  
  
 **Určené:** <xref:System.Windows.Markup> oboru názvů System.Xaml sestavení  
  
 **Pro relevantní:** načíst cestu a uložte cesta zpracování hodnoty členů, které jsou identifikátory URI nebo `x:Uri` hodnoty.  
  
 **Rozhraní API služby:**  <xref:System.Windows.Markup.IUriContext.BaseUri%2A>  
  
 Tato služba hlásí globálně dostupnou URI kořenové, pokud existuje. Identifikátor URI kořenové lze použít k vyřešení relativní identifikátory URI na absolutní identifikátory URI a naopak. Tento scénář je především relevantní pro aplikační služby, které jsou vystavené konkrétní framework nebo možnosti často používaných kořenový element třídy v rozhraní. Základní identifikátor URI by bylo možné navázat XAML pro čtenáře nastavení, která je pak předána do zapisovače objektu XAML a hlášené touto službou.  
  
### <a name="iambientprovider"></a>IAmbientProvider  
 **Referenční dokumentace**:<xref:System.Xaml.IAmbientProvider>  
  
 **Určené:** <xref:System.Xaml> oboru názvů System.Xaml sestavení  
  
 **Pro relevantní:** načíst cestu zpracování a typ vyhledávání rozlišených položek nebo optimalizace.  
  
 **Rozhraní API služby:**<xref:System.Xaml.IAmbientProvider.GetAllAmbientValues%2A>, 3 jiné.  
  
 Koncept podmínek, za v jazyce XAML je technika pro označení členem typu jako vedlejším konkrétní. Typ případně může být vedlejším tak, aby všechny hodnoty vlastností, které hostují instance typu by měly být považovány za vedlejším vlastnostem. Rozšíření značek nebo převaděče typů, které jsou dále na datový proud uzlu XAML a následníky v grafu objektů, které jsou můžete získat přístup k vedlejším vlastnost nebo typ instance v době zatížení; nebo můžou použít znalostní báze vedlejším konstrukce v čas ukládání. To může mít vliv na úroveň kvalifikace, který je nutný k překladu typy pro jiné služby, například pro <xref:System.Windows.Markup.IXamlTypeResolver> nebo `x:Type`. Viz také <xref:System.Xaml.AmbientPropertyValue>.  
  
### <a name="ixamlschemacontextprovider"></a>IXamlSchemaContextProvider  
 **Referenční dokumentace**:<xref:System.Xaml.IXamlSchemaContextProvider>  
  
 **Určené:** <xref:System.Xaml> oboru názvů System.Xaml sestavení  
  
 **Pro relevantní:** zatížení cesta a všechny operace, které se musí přeložit typ jazyka XAML základního typu.  
  
 **Rozhraní API služby:**  <xref:System.Xaml.IXamlSchemaContextProvider.SchemaContext%2A>  
  
 Kontext schématu XAML je nezbytné pro žádné operace zatížení odložit, protože kontext stejné schéma musí fungovat na oblasti odložené integrace odložené obsah. Další informace o roli kontext schématu XAML najdete v tématu [XAML Services](../../../docs/framework/xaml-services/index.md).  
  
### <a name="irootobjectprovider"></a>IRootObjectProvider  
 **Referenční dokumentace**:<xref:System.Xaml.IRootObjectProvider>  
  
 **Určené:** <xref:System.Xaml> oboru názvů System.Xaml sestavení  
  
 **Pro relevantní:** načíst cestu.  
  
 **Rozhraní API služby:**  <xref:System.Xaml.IRootObjectProvider.RootObject%2A>  
  
 Služba je relevantní pro služby aplikací, které jsou přístupné pomocí konkrétní rozhraní nebo pomocí možnosti často používaných kořenový element třídy v rozhraní. Jeden scénář pro získání kořenový objekt se připojuje kódu a spojení události. Například WPF implementace `x:Class` se používá pro kompilaci značek a kabeláž jakéhokoli atributu obslužná rutina události, která se nachází v jiné pozici v kód XAML. Spojovací bod značek a kódu definované částečné třídy pro kompilaci kódu je kořenový element.  
  
### <a name="ixamlnamespaceresolver"></a>IXamlNamespaceResolver  
 **Referenční dokumentace**:<xref:System.Xaml.IXamlNamespaceResolver>  
  
 **Určené:** <xref:System.Xaml> oboru názvů System.Xaml sestavení  
  
 **Pro relevantní:** zatížení cesta cestu uložení.  
  
 **Rozhraní API služby:** <xref:System.Xaml.IXamlNamespaceResolver.GetNamespace%2A> pro cestu zatížení <xref:System.Xaml.IXamlNamespaceResolver.GetNamespacePrefixes%2A> pro cestu uložení.  
  
 <xref:System.Xaml.IXamlNamespaceResolver>je služba, která může vrátit identifikátor oboru názvů jazyka XAML / URI na základě jeho předpony jako v původním kód XAML namapované.  
  
### <a name="iprovidevaluetarget"></a>IProvideValueTarget  
 **Referenční dokumentace**:<xref:System.Windows.Markup.IProvideValueTarget>  
  
 **Určené:** <xref:System.Windows.Markup> oboru názvů System.Xaml sestavení  
  
 **Pro relevantní:** načíst cestu a uložit cestu.  
  
 **Rozhraní API služby:**<xref:System.Windows.Markup.IProvideValueTarget.TargetObject%2A>, <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A>.  
  
 <xref:System.Windows.Markup.IProvideValueTarget>umožňuje získat kontext, o kterém funguje v okamžiku načtení typu převaděč nebo značek rozšíření. Implementace může používat tento kontext zneplatní použití. Například WPF, jako má logiku v některé z jeho rozšíření značek <xref:System.Windows.DynamicResourceExtension>. Logické kontroly <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A> a ujistěte se, že se rozšíření slouží pouze k nastavení vlastností závislostí (nebo krátkou seznam dalších vlastností bez závislostí).  
  
### <a name="ixamlnameresolver"></a>IXamlNameResolver  
 **Referenční dokumentace**:<xref:System.Xaml.IXamlNameResolver>  
  
 **Určené:** <xref:System.Xaml> oboru názvů System.Xaml sestavení  
  
 **Pro relevantní:** zatížení cesta grafu definice objektu, řešení objekty identifikovaný `x:Name`, `x:Reference`, nebo techniky pro konkrétní rozhraní.  
  
 **Rozhraní API služby:**<xref:System.Xaml.IXamlNameResolver.Resolve%2A>; jiná rozhraní API pro pokročilejší scénáře, jako je práci s dopředného odkazy.  
  
 Implementace rozhraní .NET Framework XAML Services `x:Reference` zpracování spoléhá na tuto službu. Konkrétní architektury nebo nástroje, které podporují rozhraní použít službu pro `x:Name` zpracování nebo ekvivalentní (<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> s atributy) vlastnosti zpracování.  
  
### <a name="idestinationtypeprovider"></a>IDestinationTypeProvider  
 **Referenční dokumentace**:<xref:System.Xaml.IDestinationTypeProvider>  
  
 **Určené:** <xref:System.Xaml> oboru názvů System.Xaml sestavení  
  
 **Pro relevantní:** načíst cestu řešení nepřímých informace o typu CLR.  
  
 **Rozhraní API služby:**<xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>  
  
 Další informace naleznete v tématu <xref:System.Xaml.IDestinationTypeProvider>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Markup.MarkupExtension>  
 <xref:System.Xaml.XamlObjectWriter>  
 [Přehled rozšíření značek pro jazyk XAML](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)  
 [Přehled převaděčů typů pro jazyk XAML](../../../docs/framework/xaml-services/type-converters-for-xaml-overview.md)
