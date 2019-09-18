---
title: Kontexty služby dostupné pro převaděče typů a rozšíření značek
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services how-to
ms.assetid: b4dad00f-03da-4579-a4e9-d8d72d2ccbce
ms.openlocfilehash: 0d4e274ad7b64820e74347908c08c7726e96bbe8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053847"
---
# <a name="service-contexts-available-to-type-converters-and-markup-extensions"></a>Kontexty služby dostupné pro převaděče typů a rozšíření značek
Autoři typů, které podporují konvertor typu a použití rozšíření značek, musí často obsahovat kontextové informace o tom, kde je použití umístěno v kódu, nebo ve okolní struktuře objektu grafu. Mohou být potřeba informace, aby byl poskytnutý objekt správně vytvořen nebo aby bylo možné vytvořit odkazy na existující objekty v grafu objektů. Při použití .NET Framework služby XAML je kontext, který může být vyžadován, vystaven jako řada rozhraní služeb. Kód podpory konvertoru typu nebo rozšíření značek se může dotazovat na službu pomocí kontextu poskytovatele služby, který je k dispozici a <xref:System.Xaml.XamlObjectWriter> předán prostřednictvím nebo souvisejících typů. Kontext schématu XAML je přímo k dispozici prostřednictvím jedné takové služby. Toto téma popisuje, jak přistupovat k kontextům služby z Implementace konvertoru hodnot a seznam typicky dostupných služeb a jejich rolí.  
  
<a name="obtaining_services"></a>   
## <a name="obtaining-services"></a>Získání služeb  
 Jako implementátor převaděče hodnot často potřebujete přístup k některému typu kontextu, ve kterém je použit převaděč hodnot. Tento kontext může zahrnovat informace, jako je například aktivní kontext schématu XAML, přístup k systému mapování typů, který kontext schématu XAML a zapisovač objektů XAML poskytují atd. Služby, které jsou k dispozici pro rozšíření značek nebo implementaci konvertoru typů, jsou přenášeny prostřednictvím parametrů kontextu, které jsou součástí signatury každé virtuální metody. V každém případě <xref:System.IServiceProvider> jste implementovali v kontextu a mohou volat <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType> pro vyžádání služby.  
  
<a name="services_for_a_markup_extension"></a>   
## <a name="services-for-a-markup-extension"></a>Služby pro rozšíření značek  
 <xref:System.Windows.Markup.MarkupExtension>má pouze jednu virtuální metodu, <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>. Vstupní `serviceProvider` parametr je způsob, jakým jsou služby předávány implementací, pokud je rozšíření značek voláno procesorem XAML. Následující pseudokódu ukazuje, jak se implementace rozšíření značek může dotazovat na služby v <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>jeho:  
  
```csharp  
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
 <xref:System.ComponentModel.TypeConverter>má čtyři virtuální metody, které používají kontext služby a které podporují použití XAML. Každá z těchto metod předává vstupní `context` parametr. Tento parametr je typu <xref:System.ComponentModel.ITypeDescriptorContext>, ale rozhraní dědí <xref:System.IServiceProvider>, a <xref:System.IServiceProvider.GetService%2A> proto je k dispozici metoda pro implementace konvertoru typu.  
  
 Následující pseudokódu ukazuje, jak může Implementace konvertoru typu pro použití XAML dotazovat se na služby v jednom z jeho přepsání, v tomto <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>případě:  
  
```csharp  
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
## <a name="services-for-a-value-serializer"></a>Služby pro serializátor hodnot  
 Pro kontext serializátoru hodnot použijte typ poskytovatele služby, který je specifický pro <xref:System.Windows.Markup.ValueSerializer> třídu,. <xref:System.Windows.Markup.IValueSerializerContext> Tento kontext je předán přepsání těchto čtyř <xref:System.Windows.Markup.ValueSerializer> virtuálních metod. Pro <xref:System.IServiceProvider.GetService%2A> získání služeb zavolejte z kontextu.  
  
<a name="using_the_xaml_service_provider_contexts"></a>   
## <a name="using-the-xaml-service-provider-contexts"></a>Použití kontextů zprostředkovatele služby XAML  
 Poskytovatel služeb pro <xref:System.IServiceProvider.GetService%2A> přístup ke službám XAML dostupným pro rozšíření značek nebo konvertory typů je implementován jako interní třída s expozicí pouze prostřednictvím rozhraní a způsobu předání do příslušného kontextu. Pokaždé, když operace zpracování XAML ve výchozích .NET Framework implementaci cesty načtení nebo uložení cesty vyvolá příslušné metody rozšíření označení nebo konvertoru typu, které vyžadují kontext služby, je tento interní objekt předán. V závislosti na okolnostech poskytuje kontext systémové služby buď `MarkupExtensionContext` nebo `TextSyntaxContext`, ale konkrétní obě tyto třídy jsou interní. Vaše interakce s těmito třídami je omezená na požadavky služeb od nich přes <xref:System.IServiceProvider.GetService%2A>.  
  
<a name="available_systemxaml_services"></a>   
## <a name="available-services-from-the-net-framework-xaml-service-context"></a>Dostupné služby z kontextu služby .NET Framework XAML  
 .NET Framework služby XAML definují služby pro rozšíření značek, převaděče typů, serializace hodnot a potenciálně další použití. Následující části popisují každou z těchto služeb a poskytují pokyny k tomu, jak je možné službu použít v implementaci.  
  
### <a name="iserviceprovider"></a>IServiceProvider  
 **Referenční dokumentace**:<xref:System.IServiceProvider>  
  
 **Důležité pro:** Základní operace infrastruktury na základě služby v .NET Framework, takže můžete volat <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType>.  
  
### <a name="itypedescriptorcontext"></a>ITypeDescriptorContext  
 **Referenční dokumentace**:<xref:System.ComponentModel.ITypeDescriptorContext>  
  
 Je odvozen z <xref:System.IServiceProvider>. Tato třída představuje kontext v rámci standardních <xref:System.ComponentModel.TypeConverter> podpisů. <xref:System.ComponentModel.TypeConverter> je třída, která existuje od .NET Framework 1,0. Pro převod typu řetězcových hodnot se data XAML a scénář XAML <xref:System.ComponentModel.TypeConverter> . V kontextu .NET Framework služby XAML <xref:System.ComponentModel.TypeConverter> jsou metody implementovány explicitně. Chování explicitní implementace indikuje volajícím, že <xref:System.ComponentModel.ITypeDescriptorContext> rozhraní API není relevantní pro systémy typů XAML, nebo pro čtení nebo zápis objektů z XAML. <xref:System.ComponentModel.ITypeDescriptorContext.Container%2A>, <xref:System.ComponentModel.ITypeDescriptorContext.Instance%2A>a <xref:System.ComponentModel.ITypeDescriptorContext.PropertyDescriptor%2A> obecně vracejí`null` z .NET Framework kontextů služby XAML.  
  
### <a name="ivalueserializercontext"></a>IValueSerializerContext  
 **Referenční dokumentace**:<xref:System.Windows.Markup.IValueSerializerContext>  
  
 Je odvozen z <xref:System.ComponentModel.ITypeDescriptorContext> a také spoléhá na explicitní implementace pro potlačení falešně negativních dopadů na systém typů XAML. Podporuje metody pomocníka statického vyhledávání <xref:System.Windows.Markup.ValueSerializer>na.  
  
### <a name="ixamltyperesolver"></a>IXamlTypeResolver  
 **Referenční dokumentace**:<xref:System.Windows.Markup.IXamlTypeResolver>  
  
 **Definováno:** <xref:System.Windows.Markup> obor názvů, sestavení System. XAML  
  
 **Důležité pro:** Scénáře načtení cest a interakce s kontextem schématu XAML  
  
 **Rozhraní API služby:**  <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>  
  
 Může ovlivnit mapování typu XAML-to-CLR, který je nezbytný v případě, že zapisovač XAML vytvoří objekt CLR v grafu objektů. <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>zpracuje potenciálně kvalifikovaný řetězec s předponou, který odpovídá názvu typu XAML (<xref:System.Xaml.XamlType.Name%2A?displayProperty=nameWithType>), a vrátí CLR. <xref:System.Type> Řešení typů je obvykle silně závislé na kontextu schématu XAML. Pouze kontext schématu XAML má na paměti informace, jako například která sestavení jsou načtena a která z těchto sestavení mohou nebo by měly být k dispozici pro rozlišení typu.  
  
### <a name="iuricontext"></a>IUriContext  
 **Referenční dokumentace**:<xref:System.Windows.Markup.IUriContext>  
  
 **Definováno:** <xref:System.Windows.Markup> obor názvů, sestavení System. XAML  
  
 **Důležité pro:** Načíst cestu a Uložit cestu k hodnotám členů, které jsou identifikátory `x:Uri` URI nebo hodnoty.  
  
 **Rozhraní API služby:**  <xref:System.Windows.Markup.IUriContext.BaseUri%2A>  
  
 Tato služba hlásí globálně dostupný kořenový identifikátor URI, pokud existuje. Kořen identifikátoru URI lze použít k překladu relativních identifikátorů URI na absolutní identifikátory URI nebo naopak. Tento scénář je zvláště relevantní pro aplikační služby, které jsou zpřístupněny konkrétním rozhraním, nebo schopnosti často používané třídy kořenového elementu v rámci rozhraní. Základní identifikátor URI lze vytvořit jako nastavení čtečky XAML, které je pak předáno do zapisovače objektu XAML a hlášeno touto službou.  
  
### <a name="iambientprovider"></a>IAmbientProvider  
 **Referenční dokumentace**:<xref:System.Xaml.IAmbientProvider>  
  
 **Definováno:** <xref:System.Xaml> obor názvů, sestavení System. XAML  
  
 **Důležité pro:** Načítání cest pro zpracování a neodklady nebo optimalizace vyhledávání typů.  
  
 **Rozhraní API služby:** <xref:System.Xaml.IAmbientProvider.GetAllAmbientValues%2A>, 3 ostatní.  
  
 Koncept Ambience v jazyce XAML je technika pro označení konkrétního člena typu jako okolí. Alternativně může být typ ambientní, aby všechny hodnoty vlastností, které obsahují instanci typu, měly být považovány za ambientní vlastnosti. Rozšíření značek nebo konvertory typů, které jsou dále v datovém proudu uzlu XAML a které jsou následníky v objektu Graph, mají přístup k vnější vlastnosti nebo instanci typu v době načítání. nebo můžou v době úspory použít znalosti struktury okolí. To může mít vliv na stupeň kvalifikace, který je potřeba k překladu typů pro jiné služby, například pro <xref:System.Windows.Markup.IXamlTypeResolver> nebo pro `x:Type`. Viz také <xref:System.Xaml.AmbientPropertyValue>.  
  
### <a name="ixamlschemacontextprovider"></a>IXamlSchemaContextProvider  
 **Referenční dokumentace**:<xref:System.Xaml.IXamlSchemaContextProvider>  
  
 **Definováno:** <xref:System.Xaml> obor názvů, sestavení System. XAML  
  
 **Důležité pro:** Cesta načtení a všechny operace, které musí přeložit typ XAML na typ zálohování.  
  
 **Rozhraní API služby:**  <xref:System.Xaml.IXamlSchemaContextProvider.SchemaContext%2A>  
  
 Kontext schématu XAML je nezbytný pro jakékoli operace odloženého načítání, protože stejný kontext schématu musí fungovat na odložené oblasti, aby se mohla integrovat odložený obsah. Další informace o roli kontextu schématu XAML naleznete v tématu [XAML Services](index.md).  
  
### <a name="irootobjectprovider"></a>IRootObjectProvider  
 **Referenční dokumentace**:<xref:System.Xaml.IRootObjectProvider>  
  
 **Definováno:** <xref:System.Xaml> obor názvů, sestavení System. XAML  
  
 **Důležité pro:** Načíst cestu  
  
 **Rozhraní API služby:**  <xref:System.Xaml.IRootObjectProvider.RootObject%2A>  
  
 Služba je relevantní pro aplikační služby, které jsou zpřístupněny konkrétním rozhraním, nebo funkcemi často používané třídy kořenového prvku v rozhraní. Jedním z scénářů, jak získat kořenový objekt, je propojení s kódem na pozadí a s událostmi. Například implementace `x:Class` WPF pro se používá pro kompilaci kódu a kabely libovolného atributu obslužné rutiny události, který se nachází na libovolné jiné pozici v kódu XAML. Bod připojení značek a definovaných částečných tříd kódu na pozadí pro kompilaci kódu je umístěn v kořenovém elementu.  
  
### <a name="ixamlnamespaceresolver"></a>IXamlNamespaceResolver  
 **Referenční dokumentace**:<xref:System.Xaml.IXamlNamespaceResolver>  
  
 **Definováno:** <xref:System.Xaml> obor názvů, sestavení System. XAML  
  
 **Důležité pro:** Cesta načtení, Uložit cestu.  
  
 **Rozhraní API služby:** procestunačteníprocestuprouložení.<xref:System.Xaml.IXamlNamespaceResolver.GetNamespace%2A> <xref:System.Xaml.IXamlNamespaceResolver.GetNamespacePrefixes%2A>  
  
 <xref:System.Xaml.IXamlNamespaceResolver>je služba, která může vracet identifikátor oboru názvů XAML nebo identifikátor URI na základě jeho předpony, jak je mapováno v označení původ XAML.  
  
### <a name="iprovidevaluetarget"></a>IProvideValueTarget  
 **Referenční dokumentace**:<xref:System.Windows.Markup.IProvideValueTarget>  
  
 **Definováno:** <xref:System.Windows.Markup> obor názvů, sestavení System. XAML  
  
 **Důležité pro:** Načte cestu a cestu pro uložení.  
  
 **Rozhraní API služby:** <xref:System.Windows.Markup.IProvideValueTarget.TargetObject%2A>, <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A>.  
  
 <xref:System.Windows.Markup.IProvideValueTarget>umožňuje konvertoru typu nebo rozšíření značek získat kontext, kde funguje v době načítání. Implementace mohou používat tento kontext k zrušení platnosti použití. Například WPF má logiku uvnitř některých rozšíření značek, jako je <xref:System.Windows.DynamicResourceExtension>například. Logika zkontroluje <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A> , zda se rozšíření používá pouze k nastavení vlastností závislosti (nebo krátkého seznamu jiných vlastností bez závislosti).  
  
### <a name="ixamlnameresolver"></a>IXamlNameResolver  
 **Referenční dokumentace**:<xref:System.Xaml.IXamlNameResolver>  
  
 **Definováno:** <xref:System.Xaml> obor názvů, sestavení System. XAML  
  
 **Důležité pro:** Načtení definice grafu objektu cesty, řešení objektů identifikovaných `x:Name`technikami, `x:Reference`nebo pro konkrétní rozhraní.  
  
 **Rozhraní API služby:** <xref:System.Xaml.IXamlNameResolver.Resolve%2A>; další rozhraní API pro pokročilejší scénáře, jako je například řešení problémů s dopředné odkazy.  
  
 Tato služba využívá implementaci `x:Reference` zpracování .NET Framework XAML Services. Konkrétní architektury nebo nástroje, které podporují rozhraní, používají tuto službu ke `x:Name` zpracování nebo ekvivalentnímu<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> zpracování vlastností (s atributy).  
  
### <a name="idestinationtypeprovider"></a>IDestinationTypeProvider  
 **Referenční dokumentace**:<xref:System.Xaml.IDestinationTypeProvider>  
  
 **Definováno:** <xref:System.Xaml> obor názvů, sestavení System. XAML  
  
 **Důležité pro:** Načíst rozlišení cesty k nepřímým informacím o typu CLR.  
  
 **Rozhraní API služby:** <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>  
  
 Další informace naleznete v tématu <xref:System.Xaml.IDestinationTypeProvider>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [Přehled rozšíření značek pro jazyk XAML](markup-extensions-for-xaml-overview.md)
- [Přehled převaděčů typů pro jazyk XAML](type-converters-for-xaml-overview.md)
