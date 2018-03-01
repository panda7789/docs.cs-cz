---
title: "Používání třídy XmlSerializer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XmlSerializer [WCF], using
ms.assetid: c680602d-39d3-44f1-bf22-8e6654ad5069
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bc1ede649a68747461882dfe607214bfb06b2ec3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-xmlserializer-class"></a>Používání třídy XmlSerializer
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Chcete-li data v aplikaci do souboru XML, která se přenášejí mezi klienty a službách, procesu označovaného jako serializace můžete použít dvě různé serializace technologie.  
  
## <a name="datacontractserializer-as-the-default"></a>DataContractSerializer jako výchozí  
 Ve výchozím nastavení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá <xref:System.Runtime.Serialization.DataContractSerializer> třída určená k serializaci datové typy. Tento serializátor podporuje následující typy:  
  
-   Primitivní typy (pro příklad, celá čísla, řetězce a bajtové pole), a také některé speciální typy, jako například <xref:System.Xml.XmlElement> a <xref:System.DateTime>, které jsou považovány za primitiv.  
  
-   Typy kontraktů dat (označené jako typy <xref:System.Runtime.Serialization.DataContractAttribute> atributu).  
  
-   Typy označené jako <xref:System.SerializableAttribute> atribut, který Zahrnout typy, které implementují <xref:System.Runtime.Serialization.ISerializable> rozhraní.  
  
-   Typy, které implementují <xref:System.Xml.Serialization.IXmlSerializable> rozhraní.  
  
-   Mnoho běžné typy kolekcí, které zahrnují mnoho obecné typy kolekcí.  
  
 Mnoho [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy spadají do poslední dvě kategorie a jsou tedy serializable. Pole Serializovatelné typy jsou také serializable. Úplný seznam najdete v tématu [zadání přenos dat v kontraktech služby](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>, Použít společně s datové typy kontraktů, je doporučeným způsobem, jak napsat nové [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
## <a name="when-to-use-the-xmlserializer-class"></a>Kdy použít třídy XmlSerializer  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]podporuje také <xref:System.Xml.Serialization.XmlSerializer> třídy. <xref:System.Xml.Serialization.XmlSerializer> Třída není jedinečný pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Je stejný serializace modul, který [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové služby použijte. <xref:System.Xml.Serialization.XmlSerializer> Třída podporuje mnoho užší sadu typů než <xref:System.Runtime.Serialization.DataContractSerializer> třídy, ale umožňuje lepší kontrolu nad výsledný soubor XML a podporuje mnohem víc schématu XML definice jazyka (XSD) standardní. Také nevyžaduje žádné deklarativní atributy na Serializovatelné typy. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]v tématu serializace XML [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dokumentaci. <xref:System.Xml.Serialization.XmlSerializer> Třída nepodporuje datové typy kontrakt.  
  
 Při použití Svcutil.exe nebo **přidat odkaz na službu** funkci v [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] ke generování kódu klienta pro službu třetí strany, nebo pro přístup k schéma třetích stran, příslušné serializátor se vybere automaticky za vás. Pokud schéma není kompatibilní s <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Xml.Serialization.XmlSerializer> je vybrána.  
  
## <a name="manually-switching-to-the-xmlserializer"></a>Ručně přepnutí do třídy XmlSerializer  
 V některých případech může být nutné ručně přepnout <xref:System.Xml.Serialization.XmlSerializer>. K tomu dojde, například v následujících případech:  
  
-   K migraci aplikace z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webových služeb [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], možná budete chtít znovu použít existující, <xref:System.Xml.Serialization.XmlSerializer>-smlouvy kompatibilní typy místo vytvoření nové datové typy.  
  
-   Pokud přesnou kontrolu nad XML, který se zobrazí v zprávy je důležité, ale dokumentu webové služby popis Language (WSDL) není k dispozici, například při vytváření služby s typy, které je nutné v souladu s určitým standardizovaných, publikované schéma, je není kompatibilní s objektu DataContractSerializer.  
  
-   Při vytváření služby, které následují starší verze standard kódování SOAP.  
  
 V těchto a dalších případů, můžete ručně přepnout <xref:System.Xml.Serialization.XmlSerializer> třída použitím `XmlSerializerFormatAttribute` atribut vaší služby, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[c_XmlSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#1)]
 [!code-vb[c_XmlSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#1)]  
  
## <a name="security-considerations"></a>Důležité informace o zabezpečení  
  
> [!NOTE]
>  Je důležité buďte opatrní při přepínání moduly serializace. Stejný typ může serializovat do formátu XML odlišně v závislosti na serializátoru, který je používán. Pokud používáte omylem nesprávný serializátor, může být odhalení informací z typ, který jste nechtěli zveřejnit.  
  
 Například <xref:System.Runtime.Serialization.DataContractSerializer> třída serializuje pouze členy označené jako <xref:System.Runtime.Serialization.DataMemberAttribute> atributu při serializaci typy kontraktů dat. <xref:System.Xml.Serialization.XmlSerializer> Třída serializuje žádný veřejný člen. V tématu typu v následujícím kódu.  
  
 [!code-csharp[c_XmlSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#2)]
 [!code-vb[c_XmlSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#2)]  
  
 Pokud je typ nechtěně použity v kontraktu služby kde <xref:System.Xml.Serialization.XmlSerializer> je vybraná třída, `creditCardNumber` serializován člen, které je pravděpodobně není určeno.  
  
 I když <xref:System.Runtime.Serialization.DataContractSerializer> třída je výchozí nastavení, můžete explicitně vybrat je pro vaši službu (i když to by měl být nikdy požadované) použitím <xref:System.ServiceModel.DataContractFormatAttribute> atribut typu kontraktu služby.  
  
 Serializátor používaný pro službu je nedílnou součástí kontraktu a nelze změnit tak, že vyberete jinou vazbou nebo změnou dalších nastavení konfigurace.  
  
 Další důležité informace o zabezpečení, na které se týkají <xref:System.Xml.Serialization.XmlSerializer> třídy. První, důrazně doporučujeme že jakékoli [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace, která používá <xref:System.Xml.Serialization.XmlSerializer> třída je podepsaný s klíčem, který je chráněna před vyzrazením. Toto doporučení platí, když ruční přepínač tak, aby <xref:System.Xml.Serialization.XmlSerializer> provádí a po automatické přepínač provádí (Svcutil.exe, přidat odkaz na službu nebo nástroj podobné). Důvodem je, že <xref:System.Xml.Serialization.XmlSerializer> Serializační stroj podporuje načítání *předem vygeneruje sestavení serializace* tak dlouho, dokud jsou podepsané stejným klíčem jako aplikace. Nepodepsané aplikace je zcela nechráněné z možnost škodlivý sestavení odpovídající očekávaný název sestavení předem vygenerovaná serializace je umístěn ve složce aplikace nebo do globální mezipaměti sestavení. Samozřejmě útočník musí nejprve získat přístup pro zápis do jednoho z těchto dvou umístění k pokusu o tuto akci.  
  
 Další hrozby, které existuje při každém použití <xref:System.Xml.Serialization.XmlSerializer> souvisí se oprávnění k zápisu. k dočasné složce systému. <xref:System.Xml.Serialization.XmlSerializer> Serializační stroj vytvoří a použije dočasné *sestavení serializace* v této složce. Je třeba si uvědomit, že jakýkoli proces s oprávnění k zápisu do dočasné složky může přepsat tyto sestavení serializace škodlivý kód.  
  
## <a name="rules-for-xmlserializer-support"></a>Pravidla pro podporu třídy XmlSerializer  
 Nelze použít přímo <xref:System.Xml.Serialization.XmlSerializer>-kompatibilní atributy smlouvy parametry operace nebo návratové hodnoty. Však dají se použít pro typové zprávy (zpráva kontrakt částí textu), jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[c_XmlSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#3)]
 [!code-vb[c_XmlSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#3)]  
  
 Při použití členům zadanou zprávu, tyto atributy přepsat vlastnosti, které je v konfliktu u atributů zadanou zprávu. Například v následujícím kódu `ElementName` přepsání `Name`.  
  
 [!code-csharp[c_XmlSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#4)]
 [!code-vb[c_XmlSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#4)]  
  
 <xref:System.ServiceModel.MessageHeaderArrayAttribute> Atribut není podporován při použití <xref:System.Xml.Serialization.XmlSerializer>.  
  
> [!NOTE]
>  V takovém případě <xref:System.Xml.Serialization.XmlSerializer> následující výjimku, vydané před [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: "nemůže mít element deklarovaný na nejvyšší úrovni schématu `maxOccurs` > 1. Zadejte element obálku pro další pomocí `XmlArray` nebo `XmlArrayItem` místo `XmlElementAttribute`, nebo pomocí styl parametru Wrapped. "  
>   
>  Pokud se zobrazí takové výjimky, zjistěte, zda platí tato situace.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]nepodporuje <xref:System.Xml.Serialization.SoapIncludeAttribute> a <xref:System.Xml.Serialization.XmlIncludeAttribute> měnící atributů v kontrakty zpráv a operací, pomocí <xref:System.Runtime.Serialization.KnownTypeAttribute> atribut místo.  
  
## <a name="types-that-implement-the-ixmlserializable-interface"></a>Typy, které implementují rozhraní IXmlSerializable  
 Typy, které implementují `IXmlSerializable` rozhraní plně podporuje `DataContractSerializer`. <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> Atribut by měl vždy použít pro tyto typy k řízení jejich schématu.  
  
> [!WARNING]
>  Pokud je serializována polymorfní typy musíte použít <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> typu k zajištění správného typu serializován.  
  
 Existují tři typy typy, které implementují `IXmlSerializable`: typy, které představují libovolný typy obsahu, které představují jeden element a starší verze <xref:System.Data.DataSet> typy.  
  
-   Typy obsahu použijte metodu schématu poskytovatele určeného `XmlSchemaProviderAttribute` atribut. Metoda nevrátí `null` a <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> vlastnost v atributu je ponechán v jeho výchozí hodnotu `false`. Toto je nejběžnější použití `IXmlSerializable` typy.  
  
-   Element typy se používají při `IXmlSerializable` typ se musí řídit svůj vlastní název kořenového elementu. Označit jako typ elementu typu, nastavte <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> vlastnost <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atribut `true` , nebo může vracet `null` ze schématu metoda zprostředkovatele. Metody zprostředkovatele schématu je volitelné pro typy elementů – můžete určit `null` místo názvu metody v `XmlSchemaProviderAttribute`. Ale pokud `IsAny` je `true` a metody zprostředkovatele schématu je zadán, musí vracet metodu `null`.  
  
-   Starší verze <xref:System.Data.DataSet> typy jsou `IXmlSerializable` typy, které nejsou označené jako `XmlSchemaProviderAttribute` atribut. Místo toho spoléhají na <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> metoda pro generování schémat. Tento vzor slouží k `DataSet` typu a jeho typové datové sady odvozená třída v dřívějších verzích rozhraní .NET Framework, ale je nyní zastaralé a je podporována pouze pro starší verze důvodů. Nezadávejte závisí na tomto vzoru a vždy použít `XmlSchemaProviderAttribute` k vaší `IXmlSerializable` typy.  
  
### <a name="ixmlserializable-content-types"></a>Typy IXmlSerializable obsahu  
 Při serializaci členem datový typ, který implementuje `IXmlSerializable` a definované dříve, serializátoru, který zapíše element obálku pro datový člen je typ obsahu a předá ovládání do <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metoda. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> Implementace můžete zapsat všechny XML, který zahrnuje přidání atributů do elementu obálku. Po `WriteXml` je Hotovo, serializátor zavře elementu.  
  
 Při deserializaci členem datový typ, který implementuje `IXmlSerializable` a definované dříve je typ obsahu, deserializátor umisťuje čtecí modul XML pro element obálku pro člena dat a předá ovládání do <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> metoda. Metoda musí čtení celý elementu, včetně počáteční a koncové značky. Zajistěte, aby vaše `ReadXml` kód zpracovává případě elementu je prázdný. Kromě toho vaší `ReadXml` implementace neměli spoléhat na element obálky se s názvem určitým způsobem. Název je zvolen podle serializátoru, který se může lišit.  
  
 Je povoleno přiřadit `IXmlSerializable` obsah typy polymorphically, například k datům členy typu <xref:System.Object>. Je také povoleno pro instance typu mít hodnotu null. Nakonec je možné použít `IXmlSerializable` typy s objekt grafu zachovávání povoleno a <xref:System.Runtime.Serialization.NetDataContractSerializer>. Všechny tyto funkce vyžadují [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serializátor připojit určité atributy do elementu obálku ("žádné" a "typ" v oboru názvů Instance schématu XML a "Id", "Ref", "Type" a "Sestavení" v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-konkrétní obor názvů).  
  
#### <a name="attributes-to-ignore-when-implementing-readxml"></a>Atributy, které mají ignorovat při implementaci ReadXml  
 Před předáním řízení pro vaše `ReadXml` kód, deserializátor prozkoumá XML element, zjistí tyto speciální atributy XML a funguje na ně. Například, pokud je "žádné" `true`, je deserializovat hodnotu null a `ReadXml` není volán. Pokud je zjištěn polymorfismus, obsah elementu se deserializovat, jako kdyby byl jiného typu. Typ polymorphically přiřazené implementace `ReadXml` je volána. V každém případě `ReadXml` implementace má tyto speciální atributy ignorovat, protože jsou zpracovávány deserializátor.  
  
### <a name="schema-considerations-for-ixmlserializable-content-types"></a>Důležité informace o schématu pro typy obsahu IXmlSerializable  
 Při exportu schématu a `IXmlSerializable` typ obsahu, je volána metoda zprostředkovatele schématu. <xref:System.Xml.Schema.XmlSchemaSet> Předaný schématu metoda zprostředkovatele. Metodu můžete přidat všechny platné schéma do sady schématu. Sada schématu obsahuje schéma, které je již znám v době, kdy dojde k exportu schématu. Když metoda zprostředkovatele schématu musíte přidat položku do sady schéma, musíte určit jestli <xref:System.Xml.Schema.XmlSchema> s odpovídající obor názvů již existuje v sadě. Pokud ano, metoda zprostředkovatele schématu musíte přidat novou položku do existující `XmlSchema`. V ostatních případech musíte vytvořit nový `XmlSchema` instance. To je důležité, pokud pole `IXmlSerializable` typy jsou používány. Pokud máte například `IXmlSerializable` typ, který získá exportovány jako typ "A" v oboru názvů "B", je možné, že na době metoda zprostředkovatele schématu se nazývá schéma nastavit již obsahuje schéma pro "B" typ "ArrayOfA".  
  
 Kromě přidání typů tak, aby <xref:System.Xml.Schema.XmlSchemaSet>, metoda zprostředkovatele schématu pro typy obsahu, musí vracet hodnotu než null. Můžete vrátit <xref:System.Xml.XmlQualifiedName> určující název typu schématu pro v dané `IXmlSerializable` typu. Tento kvalifikovaný název slouží taky jako data smlouvy názvem a oborem názvů pro typ. Je povoleno návratový typ, který neexistuje ve schématu nastavená, okamžitě, pokud metoda zprostředkovatele schématu vrátí. Ale očekává se, že na době, všechny související typy jsou exportovány ( <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> metoda je volána pro všechny typy relevantní na <xref:System.Runtime.Serialization.XsdDataContractExporter> a <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> získat přístup k vlastnosti), typ existuje v sadě schématu. Přístup k `Schemas` vlastnost před všechny relevantní `Export` byly provedeny volání může mít za následek <xref:System.Xml.Schema.XmlSchemaException>. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Proces exportu, najdete v části [export schémat ze tříd](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
 Metoda zprostředkovatele schéma můžete se taky vrátit <xref:System.Xml.Schema.XmlSchemaType> používat. Typ může nebo nemusí být anonymní. Pokud je anonymní, schéma pro `IXmlSerializable` typu se exportuje jako anonymní typ pokaždé, když `IXmlSerializable` typ se používá jako člena. `IXmlSerializable` Typ stále má název kontraktu dat a oboru názvů. (To je určit, jak je popsáno v [názvy datových kontraktů](../../../../docs/framework/wcf/feature-details/data-contract-names.md) s tím rozdílem, že <xref:System.Runtime.Serialization.DataContractAttribute> nelze atribut použít k přizpůsobení názvu.) Pokud není anonymní, musí být jeden z typů v `XmlSchemaSet`. Tento případ je ekvivalentní vrací `XmlQualifiedName` typu.  
  
 Navíc se pro typ exportují deklaraci globálním elementem. Pokud typ nemá <xref:System.Xml.Serialization.XmlRootAttribute> má atribut použitý k němu element se stejným názvem a oboru názvů jako kontrakt dat a jeho "povolenou" vlastnost `true`. Jedinou výjimkou je obor názvů schématu ("http://www.w3.org/2001/XMLSchema") – Pokud kontrakt dat typ je v tomto oboru názvů, odpovídající globální element je v oboru názvů prázdné, protože je zakázán pro přidání nových elementů do schématu obor názvů. Pokud má typ `XmlRootAttribute` atribut použitý k němu deklaraci globální element exportu pomocí následujících: <xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A>, <xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> a <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A> vlastnosti. Výchozí hodnoty s `XmlRootAttribute` použít jsou název kontraktu dat, prázdné obor názvů a "povolenou" Probíhá `true`.  
  
 Stejná pravidla deklarace globální element platí pro typy starší verze datové sady. Všimněte si, že `XmlRootAttribute` nejde přepsat globální element deklarace přidány prostřednictvím vlastní kód, buď přidat do `XmlSchemaSet` pomocí metody poskytovatele schématu nebo pomocí `GetSchema` pro typy starší verze datové sady.  
  
### <a name="ixmlserializable-element-types"></a>IXmlSerializable Element typy  
 `IXmlSerializable`Element typy mít buď `IsAny` vlastnost nastavena na hodnotu `true` nebo jejich metoda zprostředkovatele schématu vrátit `null`.  
  
 Serializace a deserializace typ elementu je velmi podobné serializaci a deserializaci typ obsahu. Existují však několik důležitých rozdílů:  
  
-   `WriteXml` Implementace budou zapisovat přesně jeden element (který samozřejmě může obsahovat více podřízených elementů). By neměl být zápis atributy mimo tento jeden element více prvků nebo smíšený obsah. Element může být prázdná.  
  
-   `ReadXml` Implementace by neměl čtení prvku obálku. Očekává se číst jeden element který `WriteXml` vytváří.  
  
-   Při serializaci typu elementu pravidelně (například jako člena dat ve smlouvě data), serializátor výstupy element obálky před voláním `WriteXml`, stejně jako u typy obsahu. Ale při serializaci typ elementu na nejvyšší úrovni, serializátoru, který není výstup normálně element obálku kolem elementu vůbec, `WriteXml` zapíše, pokud název kořenové domény a oboru názvů se explicitně zadat při vytváření serializátoru, který je v `DataContractSerializer` nebo `NetDataContractSerializer` konstruktory. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
-   Při serializaci typ elementu na nejvyšší úrovni bez zadání název kořenové domény a oboru názvů v době konstrukce <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> a <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> v podstatě nic nestane a <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> volání `WriteXml`. V tomto režimu nelze serializovaného objektu `null` a nelze jí přiřadit polymorphically. Také, nemůže objekt grafu zachovávání povolena a `NetDataContractSerializer` nelze použít.  
  
-   Při deserializaci typ elementu na nejvyšší úrovni bez zadání název kořenové domény a oboru názvů v době konstrukce <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> vrátí `true` Pokud nemůže najít začátek libovolný element. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A>pomocí `verifyObjectName` parametr nastaven na `true` se chová stejně jako `IsStartObject` před ve skutečnosti čtení objektu. `ReadObject`pak předá řízení `ReadXml` metoda.  
  
 Schéma exportovat za účelem typy elementu je stejná jako u `XmlElement` zadejte, jak je popsáno v předchozí části, s tím rozdílem, že metoda zprostředkovatele schéma můžete přidat žádné další schéma, aby <xref:System.Xml.Schema.XmlSchemaSet> stejně jako u typy obsahu. Pomocí `XmlRootAttribute` atribut s typy element není povolen, a globální element deklarace jsou nikdy vygenerované pro tyto typy.  
  
### <a name="differences-from-the-xmlserializer"></a>Rozdíl oproti třídy XmlSerializer  
 `IXmlSerializable` Rozhraní a `XmlSchemaProviderAttribute` a `XmlRootAttribute` atributy jsou také rozumí <xref:System.Xml.Serialization.XmlSerializer> . Existují však určité rozdíly v tom, jak jsou považovány v datovém modelu kontrakt. Přehled důležitých rozdílů je uveden v následujícím seznamu:  
  
-   Metoda zprostředkovatele schématu musí být veřejné mají být použity v `XmlSerializer`, ale nemusí být veřejné, který se má použít v datovém modelu kontrakt.  
  
-   Metoda zprostředkovatele schématu je volána, když `IsAny` je `true` v datovém modelu kontrakt, ale ne při `XmlSerializer`.  
  
-   Při `XmlRootAttribute` atribut není k dispozici pro obsah nebo typy starší verze datové sady, `XmlSerializer` exportuje deklaraci globální element v oboru názvů prázdné. V datovém modelu kontrakt používá obor názvů je obvykle obor názvů kontraktu dat jak bylo popsáno výše.  
  
 Pamatujte na tyto rozdíly při vytváření typů, které se používají u obou technologií serializace.  
  
### <a name="importing-ixmlserializable-schema"></a>Import schématu IXmlSerializable  
 Při importu schéma vygenerovat z `IXmlSerializable` typy, několik možností:  
  
-   Vygenerovaný schématu může být schématu kontrakt platná data, jak je popsáno v [Přehled schématu kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). V takovém případě schéma můžete importovat jako obvykle a typy kontraktů dat regulární se generují.  
  
-   Vygenerovaný schéma nemusí být schématu kontrakt platná data. Například metoda zprostředkovatele vašeho schématu může generovat schéma, které zahrnuje atributy XML, které nejsou podporované v datovém modelu kontrakt. V takovém případě můžete importovat schéma jako `IXmlSerializable` typy. Tento režim import se nenachází na ve výchozím nastavení ale můžete snadno povolit – například `/importXmlTypes` přepínač příkazového řádku [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). To je podrobně popsaná v [import schématu pro generování tříd](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md). Všimněte si, že musí pracovat přímo se souborem XML pro vaše instance typu. Může také zvažte použití jiné serializace technologie, která podporuje širší rozsah schématu – naleznete v tématu o používání `XmlSerializer`.  
  
-   Možná budete chtít použít stávající `IXmlSerializable` typy proxy serveru, místo aby generovala nové. V takovém případě odkazované typy funkce popsaná v import schématu pro generování typy tématu slouží k označení typu znovu použít. To odpovídá pomocí `/reference` přepínač na svcutil.exe, který určuje sestavení, které obsahuje typy, které mají-li znovu použít.  
  
### <a name="xmlserializer-legacy-behavior"></a>Chování starší třídy XmlSerializer  
 V rozhraní .NET Framework 4.0 a starší vygeneruje třídy XmlSerializer sestavení dočasné serializace psaní kódu jazyka C# do souboru. Soubor byl zkompilován pak do sestavení.  Toto chování měly některé nežádoucího jako zpomalení čas spuštění pro serializátor. V rozhraní .NET Framework 4.5 toto chování změnila ke generování sestavení bez nutnosti použití kompilátoru. Někteří vývojáři chtít najdete v části generovaného kódu C#. Můžete určit, má-li použít tento starší verze chování následující konfigurace:  
  
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
  
 Pokud narazíte na problémy s kompatibilitou, například `XmlSerializer` neúspěšné k serializaci odvozené třídě s neveřejným nové potlačení, můžete přepnout zpět `XMLSerializer` starší verze chování pomocí následující konfigurace:  
  
```xml  
<configuration>  
<appSettings>   
<add key="System:Xml:Serialization:UseLegacySerializerGeneration" value="true" />  
               </appSettings>  
</configuration>  
```  
  
 Jako alternativu k výše konfigurace můžete použít následující konfigurace na počítači se systémem rozhraní .NET Framework 4.5 nebo novější verze:  
  
```xml  
<configuration>  
<system.xml.serialization>  
<xmlSerializer useLegacySerializerGeneration="true"/>  
</system.xml.serialization>  
</configuration>  
```  
  
> [!NOTE]
>  `<xmlSerializer useLegacySerializerGeneration="true"/>` Přepínač funguje pouze na počítači se systémem rozhraní .NET Framework 4.5 nebo novější verze. Výše `appSettings` přístup funguje ve všech verzích rozhraní .NET Framework.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.DataContractFormatAttribute>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 <xref:System.ServiceModel.MessageHeaderArrayAttribute>  
 [Určování přenosu dat v kontraktech služby](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Postupy: Vylepšení doby spouštění klientských aplikací WCF pomocí XmlSerializer](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
