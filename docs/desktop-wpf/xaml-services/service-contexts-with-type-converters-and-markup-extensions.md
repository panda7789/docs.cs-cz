---
title: Kontexty služby dostupné pro převaděče typů a rozšíření značek
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services how-to
ms.assetid: b4dad00f-03da-4579-a4e9-d8d72d2ccbce
ms.openlocfilehash: 59c4385eb4df8c622be6164cdb0a1a911c445ca8
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071659"
---
# <a name="service-contexts-available-to-type-converters-and-markup-extensions"></a>Kontexty služby dostupné pro převaděče typů a rozšíření značek
Autoři typů, které podporují použití převaděče typů a rozšíření značek, musí mít často kontextové informace o tom, kde je použití umístěno ve značkách nebo v okolní struktuře grafu objektů. Informace mohou být potřebné k tomu, aby zadaný objekt byl vytvořena instance správně nebo tak, aby objekt odkazy na existující objekty v grafu objektu lze provést. Při použití služby .NET XAML je kontext, který může být požadován, vystaven jako řada rozhraní služby. Kód podpory převaděče typů nebo rozšíření značek může dotazovat na službu <xref:System.Xaml.XamlObjectWriter> pomocí kontextu poskytovatele služeb, který je k dispozici a předán z nebo související typy. Kontext schématu XAML je přímo k dispozici prostřednictvím jedné takové služby. Toto téma popisuje, jak získat přístup k kontextům služby z implementace převaděče hodnot a uvádí obvykle dostupné služby a jejich role.

## <a name="obtaining-services"></a>Získání služeb

Jako implementátor převaděče hodnot často potřebujete přístup k nějakému typu kontextu, ve kterém je převaděč hodnot použit. Tento kontext může zahrnovat informace, jako je například aktivní kontext schématu XAML, přístup k systému mapování typů, který poskytuje kontext schématu XAML a zapisovač objektů XAML, a tak dále. Služby, které jsou k dispozici pro implementaci rozšíření značek nebo převaděče typu, jsou sdělovány prostřednictvím kontextových parametrů, které jsou součástí podpisu každé virtuální metody. V každém případě <xref:System.IServiceProvider> jste implementovali v kontextu <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType> a můžete volat požádat o službu.

## <a name="services-for-a-markup-extension"></a>Služby pro rozšíření značek

<xref:System.Windows.Markup.MarkupExtension>má pouze jednu <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>virtuální metodu, . Vstupní `serviceProvider` parametr je způsob, jakým jsou služby sdělovány implementacím, když je rozšíření značek voláno procesorem XAML. Následující pseudokód ilustruje, jak může implementace rozšíření značky <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>dotaz na služby v jeho :

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

## <a name="services-for-a-type-converter"></a>Služby pro převaděč typů

<xref:System.ComponentModel.TypeConverter>má čtyři virtuální metody, které používají kontext služby a které podporují použití XAML. Každá z těchto metod `context` předá vstupní parametr. Tento parametr je <xref:System.ComponentModel.ITypeDescriptorContext>typu , ale <xref:System.IServiceProvider>toto rozhraní dědí , a proto je k dispozici <xref:System.IServiceProvider.GetService%2A> metoda pro implementaci převaděče typu.

Následující pseudokód ilustruje, jak může být implementace převaděče typů pro použití XAML dotazována na služby v jednom z jeho přepsání, v tomto případě <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>:

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

## <a name="services-for-a-value-serializer"></a>Služby pro serializátor hodnoty

Pro kontext serializátoru hodnoty použijete typ <xref:System.Windows.Markup.ValueSerializer> zprostředkovatele <xref:System.Windows.Markup.IValueSerializerContext>služeb, který je specifický pro třídu . Tento kontext je předán přepsání čtyř <xref:System.Windows.Markup.ValueSerializer> virtuálních metod. Volání <xref:System.IServiceProvider.GetService%2A> z kontextu k získání služeb.

## <a name="using-the-xaml-service-provider-contexts"></a>Použití kontextů poskytovatele služeb XAML

Poskytovatel služeb <xref:System.IServiceProvider.GetService%2A> pro přístup ke službám XAML, které jsou k dispozici pro rozšíření značek nebo převaděče typů, je implementován jako interní třída s expozicí pouze prostřednictvím rozhraní a způsobem, jakým je předána do příslušného kontextu. Vždy, když operace zpracování XAML ve výchozí implementaci služby .NET XAML služby cesty zatížení nebo uložit cestu vyvolá příslušné značky rozšíření nebo typ převaděče metody, které vyžadují kontext služby, tento vnitřní objekt je předán. V závislosti na okolnostech kontext `MarkupExtensionContext` systémové `TextSyntaxContext`služby poskytuje buď nebo , ale specifika obou těchto tříd jsou interní. Vaše interakce s těmito třídami je omezena <xref:System.IServiceProvider.GetService%2A>na vyžádání služeb od nich, a to prostřednictvím .

## <a name="available-services-from-the-net-xaml-service-context"></a>Dostupné služby z kontextu služby .NET XAML

Služba .NET XAML Services definuje služby pro rozšíření značek, převaděče typů, serializátory hodnot a potenciálně další použití. Následující části popisují každou z těchto služeb a poskytují pokyny o tom, jak může být služba použita v implementaci.

### <a name="iserviceprovider"></a>Iserviceprovider

**Referenční dokumentace**:<xref:System.IServiceProvider>

**Relevantní pro:** Základní operace infrastruktury založené na službě v rozhraní <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType>.NET, takže můžete volat .

### <a name="itypedescriptorcontext"></a>Itypedescriptorcontext

**Referenční dokumentace**:<xref:System.ComponentModel.ITypeDescriptorContext>

Pochází z <xref:System.IServiceProvider>. Tato třída představuje kontext <xref:System.ComponentModel.TypeConverter> ve standardních podpisech; <xref:System.ComponentModel.TypeConverter> je třída, která existuje od rozhraní .NET Framework 1.0. Předchází XAML a scénář <xref:System.ComponentModel.TypeConverter> XAML pro převod typu řetězcové hodnoty. V kontextu služby .NET XAML jsou metody <xref:System.ComponentModel.TypeConverter> implementovány explicitně. Explicitní provádění chování označuje volajícím, <xref:System.ComponentModel.ITypeDescriptorContext> že rozhraní API není relevantní pro systémy typu XAML nebo pro čtení nebo zápis objektů z XAML. <xref:System.ComponentModel.ITypeDescriptorContext.Container%2A>, <xref:System.ComponentModel.ITypeDescriptorContext.Instance%2A>a <xref:System.ComponentModel.ITypeDescriptorContext.PropertyDescriptor%2A> obecně `null` vrátit z kontextů služby .NET XAML Services.

### <a name="ivalueserializercontext"></a>IValueSerializerContext

**Referenční dokumentace**:<xref:System.Windows.Markup.IValueSerializerContext>

Odvozuje <xref:System.ComponentModel.ITypeDescriptorContext> a také spoléhá na explicitní implementace potlačit falešné důsledky o systému typu XAML. Podporuje metody statického vyhledávání <xref:System.Windows.Markup.ValueSerializer>na .

### <a name="ixamltyperesolver"></a>Překladač iXamlTypeResolver

**Referenční dokumentace**:<xref:System.Windows.Markup.IXamlTypeResolver>

**Definováno:** <xref:System.Windows.Markup> obor názvů, sestava System.Xaml  

**Relevantní pro:** Načtení scénářů cesty a interakce s kontextem schématu XAML

**Rozhraní API služby:**  <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>

Může ovlivnit mapování typu XAML-CLR, které je nezbytné, když zapisovač XAML vytvoří objekt CLR v grafu objektu. <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>zpracuje řetězec s potenciálně předponou, který odpovídá názvu<xref:System.Xaml.XamlType.Name%2A?displayProperty=nameWithType>typu XAML <xref:System.Type>( ) a vrátí příkaz CLR . Řešení typů je obvykle silně závislá na kontextu schématu XAML. Pouze kontext schématu XAML si je vědoma aspekty, jako jsou sestavení, které jsou načteny a které z těchto sestavení může nebo by měly být přístupné pro rozlišení typu.

### <a name="iuricontext"></a>IUriContext

**Referenční dokumentace**:<xref:System.Windows.Markup.IUriContext>

**Definováno:** <xref:System.Windows.Markup> obor názvů, sestava System.Xaml  

**Relevantní pro:** Načtěte cestu a uložte zpracování cesty `x:Uri` s hodnotami členů, které jsou identifikátory URI nebo hodnotami.

**Rozhraní API služby:**  <xref:System.Windows.Markup.IUriContext.BaseUri%2A>

Tato služba hlásí globálně dostupný kořen URI, pokud existuje. Kořen identifikátoru URI lze použít k vyřešení relativních identifikátorů URI na absolutní identifikátory URI nebo naopak. Tento scénář je relevantní především pro aplikační služby, které jsou vystaveny určité rozhraní nebo možnosti často používané třídy kořenových prvků v rámci. Základní identifikátor URI lze vytvořit jako nastavení čtečky XAML, které je pak předáno zapisovateli objektu XAML a hlášeno touto službou.

### <a name="iambientprovider"></a>IAmbientProvider

**Referenční dokumentace**:<xref:System.Xaml.IAmbientProvider>

**Definováno:** <xref:System.Xaml> obor názvů, sestava System.Xaml  

**Relevantní pro:** Zpracování cesty zatížení a typ vyhledávání časově rozlišené nebo optimalizace.

**Service API:**  <xref:System.Xaml.IAmbientProvider.GetAllAmbientValues%2A>, tři další.

Koncepce prostředí v XAML je technika pro označení určitého člena typu jako okolí. Alternativně typ může být okolí tak, aby všechny hodnoty vlastností, které mají instanci typu by měly být považovány za vlastnosti okolí. Rozšíření značek nebo převaděče typu, které jsou dále podél datového proudu uzlu XAML a které jsou následníky v objektovém grafu, mohou přistupovat k vlastnosti okolí nebo instanci typu v době načítání; nebo mohou využít znalosti okolní struktury v době úspoře času. To může ovlivnit stupeň kvalifikace, který je nutný k <xref:System.Windows.Markup.IXamlTypeResolver> vyřešení `x:Type`typů pro jiné služby, například pro nebo pro . Viz <xref:System.Xaml.AmbientPropertyValue>také .

### <a name="ixamlschemacontextprovider"></a>Ixamlschemacontextprovider

**Referenční dokumentace**:<xref:System.Xaml.IXamlSchemaContextProvider>

**Definováno:** <xref:System.Xaml> obor názvů, sestava System.Xaml  

**Relevantní pro:** Načíst cestu a všechny operace, které musí přeložit typ XAML na typ zálohování.

**Rozhraní API služby:**  <xref:System.Xaml.IXamlSchemaContextProvider.SchemaContext%2A>

Kontext schématu XAML je nezbytné pro všechny operace odložit zatížení, protože stejný kontext schématu musí působit na odložené oblasti za účelem integrace odložené obsahu. Další informace o roli kontextu schématu XAML naleznete v tématu [XAML Services](../../../api/index.md).

### <a name="irootobjectprovider"></a>Zprostředkovatel iRootObjectProvider

**Referenční dokumentace**:<xref:System.Xaml.IRootObjectProvider>

**Definováno:** <xref:System.Xaml> obor názvů, sestava System.Xaml  

**Relevantní pro:** Načíst cestu.

**Rozhraní API služby:**  <xref:System.Xaml.IRootObjectProvider.RootObject%2A>

Služba je relevantní pro aplikační služby, které jsou vystaveny určité rozhraní nebo možnosti často používané třídy kořenových prvků v rámci. Jedním z scénářů pro získání kořenového objektu je připojení zapojení kódu a události. Například WPF implementace `x:Class` se používá pro kompilaci značek a zapojení jakékoli atributobslužné rutiny události, která se nachází na jakékoli jiné pozici v xaml značky. Spojovací bod značky a kód na pozadí definované částečné třídy pro kompilaci značek je na kořenový prvek.

### <a name="ixamlnamespaceresolver"></a>Překladač iXamlNamespaceResolver

**Referenční dokumentace**:<xref:System.Xaml.IXamlNamespaceResolver>

**Definováno:** <xref:System.Xaml> obor názvů, sestava System.Xaml  

**Relevantní pro:** Načíst cestu, uložit cestu.

**Rozhraní API služby:** <xref:System.Xaml.IXamlNamespaceResolver.GetNamespace%2A> pro načíst cestu, <xref:System.Xaml.IXamlNamespaceResolver.GetNamespacePrefixes%2A> pro uložení cesty.

<xref:System.Xaml.IXamlNamespaceResolver>je služba, která může vrátit identifikátor oboru názvů XAML / identifikátor URI na základě jeho předpony mapované v původní značce XAML.

### <a name="iprovidevaluetarget"></a>Iprovidevaluetarget

**Referenční dokumentace**:<xref:System.Windows.Markup.IProvideValueTarget>

**Definováno:** <xref:System.Windows.Markup> obor názvů, sestava System.Xaml  

**Relevantní pro:** Načtěte cestu a uložte cestu.

**Servisní api:**<xref:System.Windows.Markup.IProvideValueTarget.TargetObject%2A> <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A>, .  

<xref:System.Windows.Markup.IProvideValueTarget>umožňuje převaděč typu nebo rozšíření značek získat kontext o tom, kde pracuje v době načítání. Implementace může použít tento kontext zneplatnit použití. Například WPF má logiku uvnitř některé z <xref:System.Windows.DynamicResourceExtension>jeho rozšíření značky, jako je například . Logika zkontroluje <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A> a ujistěte se, že rozšíření se používá pouze k nastavení vlastností závislostí (nebo krátký seznam jiných vlastností bez závislosti).

### <a name="ixamlnameresolver"></a>Překladač iXamlNameResolver

**Referenční dokumentace**:<xref:System.Xaml.IXamlNameResolver>

**Definováno:** <xref:System.Xaml> obor názvů, sestava System.Xaml  

**Relevantní pro:** Načíst definici grafu objektu `x:Name`cesty, řešení objektů identifikovaných pomocí aplikace `x:Reference`, nebo techniky specifické pro architekturu.

**Servisní api:**  <xref:System.Xaml.IXamlNameResolver.Resolve%2A>; další api pro pokročilejší scénáře, jako je například řešení dopředných odkazů.

Implementace `x:Reference` zpracování služby .NET XAML Services závisí na této službě. Specifické rámce nebo nástroje, které podporují `x:Name` rozhraní framework<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> používat tuto službu pro zpracování nebo ekvivalentní (přiřazené) zpracování vlastností.

### <a name="idestinationtypeprovider"></a>IDestinationTypeProvider

**Referenční dokumentace**:<xref:System.Xaml.IDestinationTypeProvider>

**Definováno:** <xref:System.Xaml> obor názvů, sestava System.Xaml  

**Relevantní pro:** Načíst rozlišení cesty informací o typu nepřímé CLR.

**Rozhraní API služby:**<xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>

Další informace naleznete v tématu <xref:System.Xaml.IDestinationTypeProvider>.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [Přehled rozšíření značek pro jazyk XAML](markup-extensions-overview.md)
- [Přehled převaděčů typů pro jazyk XAML](type-converters-overview.md)
