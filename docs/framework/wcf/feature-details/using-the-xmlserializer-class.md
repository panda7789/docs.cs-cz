---
title: Používání třídy XmlSerializer
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XmlSerializer [WCF], using
ms.assetid: c680602d-39d3-44f1-bf22-8e6654ad5069
ms.openlocfilehash: 084a31ec008d1651bb66f7d59731a21d4ef0ece7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732853"
---
# <a name="using-the-xmlserializer-class"></a>Používání třídy XmlSerializer
Windows Communication Foundation (WCF) můžete použít dva různé serializace technologií Chcete-li data ve vaší aplikaci do souboru XML, která se přenášejí mezi klienty a služeb, proces s názvem serializace.  
  
## <a name="datacontractserializer-as-the-default"></a>DataContractSerializer jako výchozí  
 Ve výchozím nastavení používá WCF <xref:System.Runtime.Serialization.DataContractSerializer> třída určená k serializaci datové typy. Tento serializátor podporuje následující typy:  
  
-   Primitivní typy (pro příklad, celá čísla, řetězce a bajtové pole), a také některé speciální typy, jako například <xref:System.Xml.XmlElement> a <xref:System.DateTime>, které jsou považovány za primitiv.  
  
-   Typy kontraktů dat (typy označeny pomocí <xref:System.Runtime.Serialization.DataContractAttribute> atributu).  
  
-   Typy označené <xref:System.SerializableAttribute> atribut, který patří typy, které implementují <xref:System.Runtime.Serialization.ISerializable> rozhraní.  
  
-   Typy, které implementují <xref:System.Xml.Serialization.IXmlSerializable> rozhraní.  
  
-   Mnoho běžných kolekce typů, které zahrnují mnoho typů obecných kolekcí.  
  
 Mnoho [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy spadají do druhé dvě kategorie a proto jsou serializovatelné. Pole Serializovatelné typy jsou také serializovat. Úplný seznam najdete v tématu [zadání přenosu dat v kontraktech služeb](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>, Spolu s daty používá typy kontraktů, je doporučený postup pro zápis nových služeb WCF. Další informace najdete v tématu [kontraktů dat pomocí](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
## <a name="when-to-use-the-xmlserializer-class"></a>Kdy použít třídy XmlSerializer  
 Také podporuje WCF <xref:System.Xml.Serialization.XmlSerializer> třídy. <xref:System.Xml.Serialization.XmlSerializer> Třída není jedinečný pro WCF. Je stejný serializace modul, který [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] použití na webové služby. <xref:System.Xml.Serialization.XmlSerializer> Třída podporuje mnoho užší sadu typů než <xref:System.Runtime.Serialization.DataContractSerializer> třídy, ale umožňuje lepší kontrolu nad tím výsledného kódu XML a podporuje mnohem více schématu XML definice jazyk (XSD) standard. Také nevyžaduje žádné deklarativních atributů na Serializovatelné typy. Další informace najdete v tématu serializace XML v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dokumentaci. <xref:System.Xml.Serialization.XmlSerializer> Třídy typy kontraktů dat nepodporuje.  
  
 Při použití Svcutil.exe nebo **přidat odkaz na službu** je automaticky vybraná funkce v sadě Visual Studio pro generování kódu klienta pro služby třetích stran nebo pro přístup k schématu třetích stran, příslušný serializátor. Pokud schéma není kompatibilní s <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Xml.Serialization.XmlSerializer> zaškrtnuto.  
  
## <a name="manually-switching-to-the-xmlserializer"></a>Ruční přepínání objektu XmlSerializer  
 V některých případech bude pravděpodobně nutné ručně nepřepnete na <xref:System.Xml.Serialization.XmlSerializer>. K tomu dojde, například v těchto případech:  
  
-   Při migraci aplikace z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové služby WCF, můžete znovu použít existující, <xref:System.Xml.Serialization.XmlSerializer>– typy kontraktů kompatibilní typy místo vytváří nová data.  
  
-   Když je důležité mít naprostou kontrolu nad XML, který se zobrazuje zprávy, ale dokumentu webové služby WSDL (Description Language) není k dispozici, například při vytváření služby s typy, které mají zajistit do určité standardizovaných publikované schématu, který je není kompatibilní s objektu DataContractSerializer.  
  
-   Při vytváření služeb dodržujících starší verze standard kódování SOAP.  
  
 V těchto a dalších případů, můžete ručně nepřepnete na <xref:System.Xml.Serialization.XmlSerializer> třídy použitím `XmlSerializerFormatAttribute` atribut k vaší službě, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[c_XmlSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#1)]
 [!code-vb[c_XmlSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#1)]  
  
## <a name="security-considerations"></a>Důležité informace o zabezpečení  
  
> [!NOTE]
>  Je důležité mít na paměti, při přechodu serializace moduly. Stejného typu může serializovat do formátu XML odlišně v závislosti na serializátoru, který je používán. Pokud používáte omylem nesprávné serializátor, může být zveřejnění informací o z typu, který jste neměli v úmyslu zpřístupnit.  
  
 Například <xref:System.Runtime.Serialization.DataContractSerializer> třídy serializuje pouze členy označené <xref:System.Runtime.Serialization.DataMemberAttribute> atribut při serializaci dat smlouvy typů. <xref:System.Xml.Serialization.XmlSerializer> Třídy serializuje žádný veřejný člen. Podívejte se typ v následujícím kódu.  
  
 [!code-csharp[c_XmlSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#2)]
 [!code-vb[c_XmlSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#2)]  
  
 Pokud je typ nechtěně použít v kontraktu služby kde <xref:System.Xml.Serialization.XmlSerializer> je vybraná třída, `creditCardNumber` člen serializován, pravděpodobně není určený.  
  
 I když <xref:System.Runtime.Serialization.DataContractSerializer> třída je výchozím nastavením, můžete explicitně vybrat ho pro vaši službu (i když to by nikdy neměly být povinné) s použitím <xref:System.ServiceModel.DataContractFormatAttribute> atribut Typ kontraktu služby.  
  
 Serializátor používaný pro službu je nedílnou součástí toho, kontrakt a nedá se změnit tak, že vyberete jiný vazby nebo změnou dalších nastavení konfigurace.  
  
 Další důležité informace o zabezpečení platí pro <xref:System.Xml.Serialization.XmlSerializer> třídy. Nejprve, důrazně doporučujeme, aby všechny aplikace WCF, který používá <xref:System.Xml.Serialization.XmlSerializer> třídy je podepsán klíčem, který je chráněna před vyzrazením. Toto doporučení se vztahuje i při ručním přepnout na <xref:System.Xml.Serialization.XmlSerializer> provádí a kdy k automatické přepnutí provádí (Svcutil.exe, přidat odkaz na službu nebo něco podobného). Je to proto, <xref:System.Xml.Serialization.XmlSerializer> Serializační stroj podporuje načítání *předem generovaného sestavení serializace* za předpokladu, že jsou podepsané stejným klíčem jako aplikace. Nepodepsaná aplikace není zcela chráněný z možnost škodlivé sestavení odpovídající očekávaný název sestavení serializace předem generovaného umístěných ve složce aplikace nebo globální mezipaměti sestavení. Samozřejmě útočník musíte nejprve získat přístup pro zápis do jednoho z těchto dvou umístění se pokusit tuto akci.  
  
 Další hrozby, které existuje při každém použití <xref:System.Xml.Serialization.XmlSerializer> se vztahuje na oprávnění k zápisu do dočasné složky systému. <xref:System.Xml.Serialization.XmlSerializer> Serializační stroj vytváří a používá dočasné *sestavení serializace* v této složce. Byste měli vědět, že jakýkoli proces s oprávněním k zápisu do dočasné složky může přepsat tyto sestavení serializace se škodlivý kód.  
  
## <a name="rules-for-xmlserializer-support"></a>Pravidla pro podporu XmlSerializer  
 Není možné přímo použít <xref:System.Xml.Serialization.XmlSerializer>-kompatibilní atributů, které mají parametry operace smlouvy nebo návratové hodnoty. Nicméně se můžou uplatnit na zadané zprávy (zprávy kontraktu částí textu), jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[c_XmlSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#3)]
 [!code-vb[c_XmlSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#3)]  
  
 Při použití zadanou zprávu členům přepsat tyto atributy vlastnosti, které jsou v konfliktu u atributů zadanou zprávu. Například v následujícím kódu `ElementName` přepíše `Name`.  
  
 [!code-csharp[c_XmlSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#4)]
 [!code-vb[c_XmlSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#4)]  
  
 <xref:System.ServiceModel.MessageHeaderArrayAttribute> Atribut není podporováno při použití <xref:System.Xml.Serialization.XmlSerializer>.  
  
> [!NOTE]
>  V takovém případě <xref:System.Xml.Serialization.XmlSerializer> následující výjimku, který je vydaný před WCF: "Nemůže mít element deklarovaný v nejvyšší úrovni schématu `maxOccurs` > 1. Uveďte element obálky pro další s využitím `XmlArray` nebo `XmlArrayItem` místo `XmlElementAttribute`, nebo s použitím stylu parametru Wrapped. "  
>   
>  Pokud se zobrazí takové výjimky, zjistěte, jestli tato situace se týká.  
  
 WCF nepodporuje <xref:System.Xml.Serialization.SoapIncludeAttribute> a <xref:System.Xml.Serialization.XmlIncludeAttribute> atributy v kontraktů zpráv a operací smluv; použijte <xref:System.Runtime.Serialization.KnownTypeAttribute> místo atributu.  
  
## <a name="types-that-implement-the-ixmlserializable-interface"></a>Typy, které implementují rozhraní IXmlSerializable  
 Typy, které implementují `IXmlSerializable` rozhraní jsou plně podporovány `DataContractSerializer`. <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> Atribut by měl vždy použít pro tyto typy řídit jejich schématu.  
  
> [!WARNING]
>  Pokud serializujete polymorfní typy musíte použít <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> typu k zajištění správného typu je serializována.  
  
 Existují tři typy prvků typy, které implementují `IXmlSerializable`: typy, které představují libovolného obsahu, typy, které představují jeden prvek a starší verze <xref:System.Data.DataSet> typy.  
  
-   Typy obsahu použít metodu schématu poskytovatele určeného `XmlSchemaProviderAttribute` atribut. Metoda nevrací `null` a <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> vlastnost pro atribut je ponecháno na jeho výchozí hodnotu `false`. Toto je nejběžnější použití `IXmlSerializable` typy.  
  
-   Typy elementů se používají při `IXmlSerializable` typ musí řídit svůj vlastní název kořenového elementu. K označení typu jako typ elementu, nastavte <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> vlastnost <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atribut `true` nebo vrátit `null` z metody zprostředkovatele schématu. Metoda poskytovatele schématu je volitelné pro typy prvků – můžete zadat `null` místo názvu metody v `XmlSchemaProviderAttribute`. Nicméně pokud `IsAny` je `true` a metody zprostředkovatele schématu není zadána, metoda musí vracet `null`.  
  
-   Starší verze <xref:System.Data.DataSet> typy jsou `IXmlSerializable` typy, které nejsou označené `XmlSchemaProviderAttribute` atribut. Místo toho spoléhají na <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> metody pro generování schématu. Tento model se používá pro `DataSet` typu a jeho typové datové sady odvozená třída v dřívějších verzích rozhraní .NET Framework, ale je zastaralá a je podporován pouze kvůli starším verzím. Nezadávejte Spolehněte se na tento model a vždycky používat `XmlSchemaProviderAttribute` do vaší `IXmlSerializable` typy.  
  
### <a name="ixmlserializable-content-types"></a>Typy rozhraní IXmlSerializable obsahu  
 Při serializaci datový člen typu, který implementuje `IXmlSerializable` a definované dříve, serializátoru, který zapíše element obálky pro datový člen je typu obsahu a předá řízení k <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metody. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> Implementace může zapisovat všechny XML, který zahrnuje přidání atributy pro element obálky. Po `WriteXml` je Hotovo, serializátor zavře elementu.  
  
 Při deserializaci datový člen typu, který implementuje `IXmlSerializable` a je typem obsahu, protože dříve definovali, deserializátor umístí čtecí funkce XML na element obálky pro datový člen a mít pod kontrolou předá <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> metody. Metoda musí číst celý prvek, včetně počáteční a koncovou značku. Ujistěte se, že vaše `ReadXml` kód zpracovává případ, ve kterém je prázdný element. Kromě toho vaše `ReadXml` implementace neměli byste tedy spoléhat na element obálky jmenován určitým způsobem. Je název zvoleném serializátoru, který se může lišit.  
  
 Je povoleno přiřadit `IXmlSerializable` typy obsahu polymorphically, třeba k datům členy typu <xref:System.Object>. Může se také atribut instance typu mít hodnotu null. A konečně, je možné použít `IXmlSerializable` typy s objektu grafu a zachovávání s rozlišením povolen a <xref:System.Runtime.Serialization.NetDataContractSerializer>. Všechny tyto funkce vyžadují serializátor WCF připojit určité atributy do prvku obálky ("nulový" a "type" v oboru názvů Instance schématu XML a "Id", "Ref", "Type" a "Sestavení" v oboru názvů specifických WCF).  
  
#### <a name="attributes-to-ignore-when-implementing-readxml"></a>Atributy se mají ignorovat při implementaci ReadXml  
 Před předáním řízení pro vaše `ReadXml` kód, deserializátor zkontroluje prvek XML, zjistí tyto speciální atributy XML a funguje na ně. Například, pokud je "nulový" `true`, deserializovat hodnotu null a `ReadXml` není volána. Pokud se zjistí polymorfismus obsah elementu se deserializovat jako by to byla jiného typu. Implementace typu polymorphically přiřazené `ReadXml` je volána. V každém případě `ReadXml` implementace by měl ignorovat tyto speciální atributy, protože deserializátor zpracovává.  
  
### <a name="schema-considerations-for-ixmlserializable-content-types"></a>Důležité informace o schématu pro typy obsahu IXmlSerializable  
 Při exportu schématu a vlastní `IXmlSerializable` typ obsahu, je volána metoda poskytovatele schématu. <xref:System.Xml.Schema.XmlSchemaSet> Se předá metodě poskytovatele schématu. Metodu můžete přidat libovolné platné schéma k sadě schémat. Sada schéma obsahuje schéma, které je již znám v době, kdy dojde k exportu schématu. Když metoda poskytovatele schématu musí přidat položku do sady schémat, musíte určit, jestli <xref:System.Xml.Schema.XmlSchema> s odpovídající obor názvů již existuje v sadě. Pokud ano, metoda poskytovatele schématu musí přidat novou položku do stávající `XmlSchema`. V opačném případě se musí vytvořit nový `XmlSchema` instance. To je důležité, pokud pole `IXmlSerializable` typy se používají. Pokud máte například `IXmlSerializable` typ, který získá exportovat jako typ "A" v oboru názvů "B", je možné, že podle času je volána metoda poskytovatele schématu schématu nastavení už obsahuje schéma pro "B" typ "ArrayOfA".  
  
 Kromě přidání typů, který chcete <xref:System.Xml.Schema.XmlSchemaSet>, metoda poskytovatele schématu pro typy obsahu musí vrátit nenulovou hodnotu. Může vrátit <xref:System.Xml.XmlQualifiedName> , který určuje název typu schématu pro daný `IXmlSerializable` typu. Tento kvalifikovaný název slouží taky jako data názvem a oborem názvů pro typ kontraktu. Je povoleno návratový typ, který neexistuje v sadě hned po návratu metody zprostředkovatele schématu schémat. Ale očekává se, že v době všechny související typy jsou exportovány ( <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> metoda je volána pro všechny typy relevantní na <xref:System.Runtime.Serialization.XsdDataContractExporter> a <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> získat přístup k vlastnosti), typ existuje v sadě schémat. Přístup k `Schemas` vlastnost před všechny relevantní `Export` byly provedeny volání může vést <xref:System.Xml.Schema.XmlSchemaException>. Další informace o procesu exportu, naleznete v tématu [export schémat ze tříd](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
 Metoda poskytovatele schéma může taky vrátit <xref:System.Xml.Schema.XmlSchemaType> používat. Typ může nebo nemusí být anonymní. Pokud je anonymní, schéma pro `IXmlSerializable` typu se exportuje jako anonymního typu pokaždé, když `IXmlSerializable` typ používá jako datový člen. `IXmlSerializable` Typ stále má název kontraktu dat a obor názvů. (Tím se určuje, jak je popsáno v [názvy datových kontraktů](../../../../docs/framework/wcf/feature-details/data-contract-names.md) s tím rozdílem, že <xref:System.Runtime.Serialization.DataContractAttribute> atributu nelze použít k přizpůsobení názvu.) Pokud není anonymní, musí být jeden z typů v `XmlSchemaSet`. Tento případ je ekvivalentní k vrácení `XmlQualifiedName` typu.  
  
 Kromě toho se pro typ exportuje globální prvek prohlášení. Pokud typ nemá <xref:System.Xml.Serialization.XmlRootAttribute> atribut WebMethod, element má stejný název a obor názvů jako kontraktu dat, a je vlastnost "nillable" `true`. Jedinou výjimkou je obor názvů schématu (`http://www.w3.org/2001/XMLSchema`) – Pokud typ kontraktu dat je v tomto oboru názvů, odpovídající globální element je v oboru názvů prázdné, protože je zakázaná pro přidání nových elementů do oboru názvů schématu. Pokud má typ `XmlRootAttribute` atribut WebMethod, globální prvek prohlášení je exportovat pomocí následující: <xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A>, <xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> a <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A> vlastnosti. Výchozí hodnoty s `XmlRootAttribute` použít jsou názvem kontraktu dat, prázdný obor názvů a "nillable" použití `true`.  
  
 Stejná pravidla deklarace globální element se vztahují na typy starší datová sada. Všimněte si, že `XmlRootAttribute` nemůže přepsat globální prvek prohlášení přidané prostřednictvím vlastního kódu buď přidat do `XmlSchemaSet` pomocí metody poskytovatele schématu nebo prostřednictvím `GetSchema` pro datovou sadu starší verze typů.  
  
### <a name="ixmlserializable-element-types"></a>Typy elementů IXmlSerializable  
 `IXmlSerializable` typy elementů mít buď `IsAny` vlastnost nastavena na hodnotu `true` nebo jejich schématu poskytovatele metoda vrátit `null`.  
  
 Serializace a deserializace typ elementu je velmi podobná serializace a deserializace typu obsahu. Existují však několik důležitých rozdílů:  
  
-   `WriteXml` Implementace má napsat přesně jeden element (který samozřejmě může obsahovat více podřízených prvků). To by neměl být zápis atributů mimo tento jeden element více na stejné úrovni elementy nebo smíšený obsah. Element může být prázdný.  
  
-   `ReadXml` Implementace by neměla číst element obálky. Očekává se číst jeden element, který `WriteXml` vytvoří.  
  
-   Při serializaci typ elementu pravidelně (například jako datový člen v kontraktu dat), serializátoru, který vypíše element obálky, a před voláním `WriteXml`, stejně jako u typů obsahu. Ale při serializaci typ elementu na nejvyšší úrovni, serializátoru, který je výstupem však nejsou obvykle element obálky, a po elementu, který `WriteXml` zapíše název kořenového adresáře a obor názvů jsou explicitně určena při vytváření serializátoru, který je v `DataContractSerializer` nebo `NetDataContractSerializer` konstruktory. Další informace najdete v tématu [serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
-   Při serializaci typ elementu na nejvyšší úrovni bez zadání kořenový název a obor názvů v době konstrukce <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> a <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> v podstatě Neprovádět žádnou akci a <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> volání `WriteXml`. V tomto režimu nelze serializovaného objektu `null` a nelze jí přiřadit polymorphically. Navíc nelze povolit zachování graf objektu a `NetDataContractSerializer` nelze použít.  
  
-   Při deserializaci typ elementu na nejvyšší úrovni bez zadání kořenový název a obor názvů v době konstrukce <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> vrátí `true` Pokud nemůže najít začátek libovolný element. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> s `verifyObjectName` parametr nastaven na `true` se chová stejně jako `IsStartObject` před skutečně čtení objektu. `ReadObject` ovládací prvek pak předá `ReadXml` metody.  
  
 Schéma exportovat pro typy prvků je stejné jako v případě `XmlElement` zadejte, jak je popsáno v předchozí části, s tím rozdílem, že metoda poskytovatele schématu můžete přidat žádné další schéma, aby <xref:System.Xml.Schema.XmlSchemaSet> stejně jako u typů obsahu. Použití `XmlRootAttribute` atribut s typy prvků není povoleno a globální prvek prohlášení jsou emitovány nikdy pro tyto typy.  
  
### <a name="differences-from-the-xmlserializer"></a>Rozdíl oproti třídy XmlSerializer  
 `IXmlSerializable` Rozhraní a `XmlSchemaProviderAttribute` a `XmlRootAttribute` atributy také rozumí <xref:System.Xml.Serialization.XmlSerializer> . Existují však určité rozdíly v tom, jak jsou považovány v datovém modelu smlouvy. Důležité rozdíly jsou shrnuty v následujícím seznamu:  
  
-   Metoda poskytovatele schématu musí být veřejné se používá v `XmlSerializer`, ale nemusí být veřejné použitého v datovém modelu kontraktu.  
  
-   Při volání metody zprostředkovatele schématu `IsAny` je `true` v datovém modelu smlouvy, ale ne s `XmlSerializer`.  
  
-   Když `XmlRootAttribute` atribut není k dispozici pro obsah nebo starší datová sada typů, `XmlSerializer` exportuje globální prvek prohlášení v oboru názvů prázdné. V datovém modelu smlouvy oboru názvů použitého je obvykle obor názvů kontraktu dat jak je popsáno výše.  
  
 Mějte na paměti tyto rozdíly při vytváření typů, které se používají u obou technologií serializace.  
  
### <a name="importing-ixmlserializable-schema"></a>Import schématu rozhraní IXmlSerializable  
 Při importu schématu generovaném z `IXmlSerializable` typy, existuje několik možností:  
  
-   Generované schéma může být schématu platný datový kontrakt, jak je popsáno v [schéma kontraktů dat – referenční informace](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). V tomto případě obvyklým způsobem můžete importovat schéma a typy kontraktů běžných dat jsou generovány.  
  
-   Generované schéma nemusí být platný datový kontrakt schéma. Například metodu schématu poskytovatele může vygenerovat schéma, které zahrnuje atributy ve formátu XML, které nejsou podporované v datovém modelu kontraktu. V takovém případě můžete importovat schéma jako `IXmlSerializable` typy. Tento režim importu se nenachází na ve výchozím nastavení lze snadno ji však povolit – například s `/importXmlTypes` přepínač příkazového řádku [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). To je podrobně popsáno [import schématu pro generování třídy](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md). Všimněte si, že musíte pracovat přímo s XML pro typ instance. Mohou také zvážit použití jiné technologie serializace, který podporuje používání nástroje většímu počtu schématu – naleznete v tématu o používání `XmlSerializer`.  
  
-   Můžete chtít znovu použít stávající `IXmlSerializable` typy v proxy namísto generování nové. V takovém případě funkce odkazované typy popsaná v import schématu pro téma generovat typy lze označující typ, který chcete znovu použít. To odpovídá pomocí `/reference` zapnout svcutil.exe, který určuje sestavení, který obsahuje typy pro opětovné použití.  
  
### <a name="xmlserializer-legacy-behavior"></a>Starší verze XmlSerializer chování  
 V rozhraní .NET Framework 4.0 a dřívějších verzí XmlSerializer generované sestavení serializace dočasné napsáním kódu jazyka C# do souboru. Soubor se potom kompilovány do sestavení.  Toto chování měli některé nežádoucí důsledky jako zpomalení doby spuštění pro serializátor. V rozhraní .NET Framework 4.5 toto chování změnila ke generování sestavení bez nutnosti použití kompilátoru. Někteří vývojáři mohou chtít zobrazit generovaný kód C#. Můžete zadat tuto starší chování pomocí následující konfigurace:  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer tempFilesLocation='e:\temp\XmlSerializerBug' useLegacySerializerGeneration="true" />  
  </system.xml.serialization>  
  <system.diagnostics>  
    <switches>  
      <add name="XmlSerialization.Compilation" value="1" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
 Pokud narazíte na problémy s kompatibilitou, například `XmlSerializer` neúspěšné serializace odvozené třídy s neveřejným nové přepsání, můžete přepnout zpět `XMLSerializer` starší chování pomocí následující konfigurace:  
  
```xml  
<configuration>  
<appSettings>   
<add key="System:Xml:Serialization:UseLegacySerializerGeneration" value="true" />  
               </appSettings>  
</configuration>  
```  
  
 Jako alternativu k konfiguraci uvedené výš můžete použít následující konfiguraci na počítači se systémem rozhraní .NET Framework 4.5 nebo novější verzi:  
  
```xml  
<configuration>  
<system.xml.serialization>  
<xmlSerializer useLegacySerializerGeneration="true"/>  
</system.xml.serialization>  
</configuration>  
```  
  
> [!NOTE]
>  `<xmlSerializer useLegacySerializerGeneration="true"/>` Přepínač funguje jenom na počítači se systémem rozhraní .NET Framework 4.5 nebo vyšší verze. Výše uvedené `appSettings` přístup funguje ve všech verzích rozhraní .NET Framework.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.DataContractFormatAttribute>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.XmlSerializer>
- <xref:System.ServiceModel.MessageHeaderArrayAttribute>
- [Určování přenosu dat v kontraktech služby](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
- [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Postupy: Vylepšení spuštění čas z klientských aplikací WCF pomocí třídy XmlSerializer](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
