---
title: Používání třídy XmlSerializer
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XmlSerializer [WCF], using
ms.assetid: c680602d-39d3-44f1-bf22-8e6654ad5069
ms.openlocfilehash: 665ede5b5a46c4093382bed5ed28a0d2bba979be
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988597"
---
# <a name="using-the-xmlserializer-class"></a>Používání třídy XmlSerializer
Windows Communication Foundation (WCF) může použít dvě různé technologie serializace k zapínání dat v aplikaci do formátu XML, který se přenáší mezi klienty a službami, což je proces, který se nazývá serializace.  
  
## <a name="datacontractserializer-as-the-default"></a>DataContractSerializer jako výchozí  
 Ve výchozím nastavení používá <xref:System.Runtime.Serialization.DataContractSerializer> WCF k serializaci datových typů třídu. Tento serializátor podporuje následující typy:  
  
- Primitivní typy (například celá čísla, řetězce a pole bajtů) a také některé speciální typy, <xref:System.Xml.XmlElement> jako například a <xref:System.DateTime>, které jsou považovány za primitivní.  
  
- Typy kontraktů dat (typy označené <xref:System.Runtime.Serialization.DataContractAttribute> atributem).  
  
- Typy označené <xref:System.SerializableAttribute> atributem, které obsahují typy, které <xref:System.Runtime.Serialization.ISerializable> implementují rozhraní.  
  
- Typy, které implementují <xref:System.Xml.Serialization.IXmlSerializable> rozhraní.  
  
- Mnoho běžných typů kolekcí, mezi které patří mnoho typů obecných kolekcí.  
  
 Mnoho typů .NET Framework spadají do těchto dvou kategorií a je tak serializovatelný. Pole serializovatelných typů jsou také serializovatelný. Úplný seznam najdete [v tématu určení přenos dat v kontraktech služeb](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
 Rozhraní <xref:System.Runtime.Serialization.DataContractSerializer>, které se používá společně s typy kontraktů dat, je doporučeným způsobem psaní nových služeb WCF. Další informace najdete v tématu [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
## <a name="when-to-use-the-xmlserializer-class"></a>Kdy použít třídu XmlSerializer  
 WCF podporuje <xref:System.Xml.Serialization.XmlSerializer> také třídu. <xref:System.Xml.Serialization.XmlSerializer> Třída není jedinečná pro WCF. Je to stejný Serializační modul, který používají webové služby ASP.NET. Třída podporuje mnohem užší sadu typů <xref:System.Runtime.Serialization.DataContractSerializer> než třídy, ale umožňuje mnohem větší kontrolu nad výsledným XML a podporuje mnohem více ve standardu XSD (XML Schema Definition Language). <xref:System.Xml.Serialization.XmlSerializer> Nevyžaduje také žádné deklarativní atributy pro Serializovatelné typy. Další informace naleznete v tématu serializace XML v dokumentaci .NET Framework. <xref:System.Xml.Serialization.XmlSerializer> Třída nepodporuje typy kontraktů dat.  
  
 Při použití Svcutil. exe nebo funkce **Přidat odkaz na službu** v aplikaci Visual Studio k vygenerování kódu klienta pro službu třetí strany nebo pro přístup k schématu třetí strany se pro vás automaticky vybere vhodný serializátor. Pokud schéma není kompatibilní s nástrojem <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Xml.Serialization.XmlSerializer> , je vybrána možnost.  
  
## <a name="manually-switching-to-the-xmlserializer"></a>Ruční přepnutí na XmlSerializer  
 V některých případech může být nutné ručně přepnout na <xref:System.Xml.Serialization.XmlSerializer>. K tomu dochází například v následujících případech:  
  
- Při migraci aplikace z webových služeb ASP.NET do WCF můžete místo vytváření nových typů kontraktů dat znovu <xref:System.Xml.Serialization.XmlSerializer>použít existující typy, které jsou kompatibilní.  
  
- Pokud je v souboru XML zobrazená přesná kontrola, která se zobrazuje ve zprávách, je důležité, ale dokument WSDL (Web Services Description Language) není k dispozici, například při vytváření služby s typy, které musí dodržovat určité standardizované, publikované schéma, které je není kompatibilní s DataContractSerializer.  
  
- Při vytváření služeb, které následují starší kódování SOAP Encoding Standard.  
  
 V těchto a dalších případech můžete ručně přepnout na <xref:System.Xml.Serialization.XmlSerializer> třídu tím, že `XmlSerializerFormatAttribute` použijete atribut pro vaši službu, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[c_XmlSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#1)]
 [!code-vb[c_XmlSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#1)]  
  
## <a name="security-considerations"></a>Důležité informace o zabezpečení  
  
> [!NOTE]
> Při přepínání modulů serializace je důležité být opatrní. Stejný typ může serializovat do XML odlišně v závislosti na použitém serializátoru. Pokud omylem nepoužijete nesprávný serializátor, může dojít k vynechání informací z typu, který jste nechtěli zveřejnit.  
  
 Například <xref:System.Runtime.Serialization.DataContractSerializer> třída serializace členy označené <xref:System.Runtime.Serialization.DataMemberAttribute> atributem při serializaci typů kontraktů dat. <xref:System.Xml.Serialization.XmlSerializer> Třída zaserializace všechny veřejné členy. Podívejte se na typ v následujícím kódu.  
  
 [!code-csharp[c_XmlSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#2)]
 [!code-vb[c_XmlSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#2)]  
  
 Pokud je typ neúmyslně používán v kontraktu služby <xref:System.Xml.Serialization.XmlSerializer> `creditCardNumber` , kde je vybrána třída, člen je serializován, což pravděpodobně není určeno.  
  
 I když <xref:System.Runtime.Serialization.DataContractSerializer> je třída výchozí, můžete ji explicitně vybrat pro vaši službu (i když by to mělo být nikdy nutné), a to <xref:System.ServiceModel.DataContractFormatAttribute> použitím atributu na typ kontraktu služby.  
  
 Serializátor použitý pro službu je nedílnou součástí kontraktu a nedá se změnit výběrem jiné vazby nebo změnou dalších nastavení konfigurace.  
  
 Další důležité požadavky na zabezpečení se vztahují <xref:System.Xml.Serialization.XmlSerializer> na třídu. Nejprve důrazně doporučujeme, aby všechny aplikace WCF, které tuto třídu <xref:System.Xml.Serialization.XmlSerializer> používají, byly podepsány klíčem, který je chráněn před zveřejněním. Toto doporučení platí v případě, že je proveden ruční <xref:System.Xml.Serialization.XmlSerializer> přepínač na, a když je proveden automatický přepínač (pomocí Svcutil. exe, přidat odkaz na službu nebo podobný nástroj). Důvodem je, že <xref:System.Xml.Serialization.XmlSerializer> Serializační modul podporuje načítání *předem generovaných sestavení serializace* , pokud jsou podepsány stejným klíčem jako aplikace. Nepodepsaná aplikace je zcela nechráněná proti škodlivému sestavení, které odpovídá očekávanému názvu předem generovaného sestavení serializace, které je umístěno ve složce aplikace nebo v globální mezipaměti sestavení (GAC). Před provedením této akce musí útočník nejprve získat přístup pro zápis do jednoho z těchto dvou umístění.  
  
 Jiná hrozba, která existuje pokaždé, když použijete <xref:System.Xml.Serialization.XmlSerializer> , souvisí s přístupem k zápisu do dočasné složky systému. Serializační modul vytvoří a použije dočasná sestavení serializace v této složce. <xref:System.Xml.Serialization.XmlSerializer> Měli byste si uvědomit, že každý proces s přístupem pro zápis do dočasné složky může přepsat tato sestavení serializace škodlivým kódem.  
  
## <a name="rules-for-xmlserializer-support"></a>Pravidla pro podporu XmlSerializer  
 Nelze použít <xref:System.Xml.Serialization.XmlSerializer>přímo kompatibilní atributy pro parametry operace kontraktu nebo návratové hodnoty. Lze je však použít na zadané zprávy (části těla zprávy), jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[c_XmlSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#3)]
 [!code-vb[c_XmlSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#3)]  
  
 Při použití u zadaných členů zprávy tyto atributy přepíší vlastnosti, které jsou v konfliktu s atributy typované zprávy. Například v následujícím kódu `ElementName` přepíše. `Name`  
  
 [!code-csharp[c_XmlSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#4)]
 [!code-vb[c_XmlSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#4)]  
  
 Atribut není podporován při <xref:System.Xml.Serialization.XmlSerializer>použití. <xref:System.ServiceModel.MessageHeaderArrayAttribute>  
  
> [!NOTE]
> V tomto případě <xref:System.Xml.Serialization.XmlSerializer> vyvolá následující výjimku, která je vydána před rozhraním WCF: "Element deklarovaný na nejvyšší úrovni schématu nemůže mít `maxOccurs` > 1. Poskytněte prvek obálky pro ' More ' pomocí `XmlArray` nebo `XmlArrayItem` místo `XmlElementAttribute`nebo pomocí zabaleného stylu parametru. "  
>   
>  Pokud obdržíte takovou výjimku, prozkoumejte, zda se jedná o tuto situaci.  
  
 WCF nepodporuje <xref:System.Xml.Serialization.SoapIncludeAttribute> atributy a <xref:System.Xml.Serialization.XmlIncludeAttribute> v kontraktech zpráv a kontraktech <xref:System.Runtime.Serialization.KnownTypeAttribute> operací; místo toho použijte atribut.  
  
## <a name="types-that-implement-the-ixmlserializable-interface"></a>Typy, které implementují rozhraní IXmlSerializable  
 Typy, které implementují `IXmlSerializable` rozhraní, jsou plně podporovány `DataContractSerializer`rozhraním. <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> Atribut by měl být vždy použit pro tyto typy pro kontrolu jejich schématu.  
  
> [!WARNING]
> Pokud provádíte serializaci polymorfních typů, je nutné <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> použít na typ pro zajištění, že je správně serializován typ.  
  
 Existují tři různé typy, které implementují `IXmlSerializable`: typy, které představují libovolný obsah, typy, které představují jeden element a starší <xref:System.Data.DataSet> typy.  
  
- Typy obsahu používají metodu poskytovatele schématu určenou `XmlSchemaProviderAttribute` atributem. Metoda nevrací `null` hodnotu <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> a vlastnost u atributu je ponechána `false`na výchozí hodnotě. Toto je nejběžnější využití `IXmlSerializable` typů.  
  
- Typy prvků se používají, když `IXmlSerializable` typ musí řídit svůj vlastní název kořenového elementu. Chcete-li označit typ jako typ prvku, buď <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> nastavte vlastnost <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> u atributu na `true` nebo vraťte `null` z metody poskytovatele schématu. Je-li metoda poskytovatele schématu pro typy prvků volitelná, můžete místo `null` názvu metody zadat `XmlSchemaProviderAttribute`v. Pokud `IsAny` `null`je `true` však a metoda poskytovatele schématu je určena, metoda musí vracet.  
  
- Zastaralé <xref:System.Data.DataSet> typy jsou `IXmlSerializable` typy, které nejsou označeny `XmlSchemaProviderAttribute` atributem. Místo toho spoléhají na <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> metodu generování schématu. Tento model se používá pro `DataSet` typ a jeho typová datová sada je odvozena od třídy v dřívějších verzích .NET Framework, ale je nyní zastaralá a je podporována pouze z dřívějších verzí. Nespoléhejte na tento model a vždy použít `XmlSchemaProviderAttribute` pro vaše `IXmlSerializable` typy.  
  
### <a name="ixmlserializable-content-types"></a>Typy obsahu IXmlSerializable  
 Při serializaci datového členu typu, který implementuje `IXmlSerializable` a je typ obsahu definovaný dříve, serializátor zapíše prvek obálky pro datový člen a předá řízení <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metodě. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> Implementace může zapisovat libovolné XML, které zahrnuje přidání atributů do prvku obálky. Po `WriteXml` dokončení se serializátor uzavře s prvkem.  
  
 Při deserializaci datového členu typu, který implementuje `IXmlSerializable` a je typ obsahu tak, jak byl definován dříve, odregistruje Nástroj pro čtení XML v prvku obálky pro datový člen a předá řízení <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> metodě. Metoda musí číst celý element, včetně počátečních a koncových značek. Ujistěte se, `ReadXml` že váš kód zpracovává případ, kde je element prázdný. Navíc by vaše `ReadXml` implementace neměla spoléhat na prvek obálky s názvem, který je pojmenován určitým způsobem. Název je zvolen serializátorem se může lišit.  
  
 Je povoleno přiřazovat `IXmlSerializable` typy obsahu polymorfní, například datovým členům typu <xref:System.Object>. Je také povoleno, aby instance typu měly hodnotu null. Nakonec je možné použít `IXmlSerializable` typy s povolenou možností zachování grafu objektů a <xref:System.Runtime.Serialization.NetDataContractSerializer>s. Všechny tyto funkce vyžadují serializátor WCF k připojení určitých atributů k elementu obálky ("Nil" a "Type" v oboru názvů instance schématu XML a "ID", "ref", "Type" a "Assembly" v oboru názvů specifického pro WCF).  
  
#### <a name="attributes-to-ignore-when-implementing-readxml"></a>Atributy, které se mají ignorovat při implementaci ReadXml  
 Před předáním řízení vašemu `ReadXml` kódu deserializátor prověřuje XML element, detekuje tyto speciální atributy XML a na nich funguje. Například pokud je `true`"Nil", hodnota null je deserializována a `ReadXml` není volána. Pokud je zjištěn polymorfismu, obsah elementu je deserializován, jako by byl jiný typ. `ReadXml` Je volána implementace polymorfního typu. V každém případě `ReadXml` by implementace měla ignorovat tyto speciální atributy, protože jsou zpracovávány deserializací.  
  
### <a name="schema-considerations-for-ixmlserializable-content-types"></a>Otázky schématu pro typy obsahu IXmlSerializable  
 Při exportování schématu a `IXmlSerializable` typu obsahu je volána metoda poskytovatele schématu. Metoda <xref:System.Xml.Schema.XmlSchemaSet> je předána metodě poskytovatele schématu. Metoda může do sady schémat přidat libovolné platné schéma. Sada schémat obsahuje schéma, které je již známo v době, kdy dojde k exportu schématu. Pokud metoda poskytovatele schématu musí do sady schémat přidat položku, musí určit, zda <xref:System.Xml.Schema.XmlSchema> již v sadě existuje odpovídající obor názvů. V takovém případě metoda poskytovatele schématu musí přidat novou položku do existující `XmlSchema`. V opačném případě musí vytvořit novou `XmlSchema` instanci. To je důležité, pokud jsou `IXmlSerializable` používána pole typů. Například pokud máte `IXmlSerializable` typ, který bude exportován jako typ "A" v oboru názvů "B", je možné, že v době, kdy se metoda poskytovatele schématu nazývá sada schémat, již obsahuje schéma pro "b" pro uchování typu "ArrayOfA".  
  
 Kromě přidávání typů do <xref:System.Xml.Schema.XmlSchemaSet>metody musí metoda poskytovatele schématu pro typy obsahu vracet hodnotu, která není null. Může vrátit <xref:System.Xml.XmlQualifiedName> , který určuje název typu schématu, který má být použit pro daný `IXmlSerializable` typ. Tento kvalifikovaný název slouží také jako název kontraktu dat a obor názvů pro daný typ. Je povoleno vrátit typ, který neexistuje v sadě schémat ihned při návratu metody poskytovatele schématu. Očekává se však, že v době, kdy jsou exportovány všechny související typy ( <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> metoda je volána pro všechny relevantní typy <xref:System.Runtime.Serialization.XsdDataContractExporter> v a <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> je k dispozici vlastnost), typ existuje v sadě schémat. Přístup k `Schemas` vlastnosti `Export` před<xref:System.Xml.Schema.XmlSchemaException>provedením všech relevantních volání může mít za následek. Další informace o procesu exportu naleznete v tématu [Export schémat ze tříd](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
 Metoda poskytovatele schématu může také vrátit <xref:System.Xml.Schema.XmlSchemaType> hodnotu, která má být použita. Typ může nebo nemusí být anonymní. Pokud je anonymní, schéma pro `IXmlSerializable` typ je exportováno jako anonymní typ pokaždé, `IXmlSerializable` když je typ použit jako datový člen. `IXmlSerializable` Typ má stále název kontraktu dat a obor názvů. (Tato <xref:System.Runtime.Serialization.DataContractAttribute> vlastnost je určena jak je popsáno v tématu [názvy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-names.md) s výjimkou toho, že atribut nelze použít k přizpůsobení názvu.) Pokud není anonymní, musí být jedním z typů v `XmlSchemaSet`. Tento případ je ekvivalentem vrácení `XmlQualifiedName` typu.  
  
 Kromě toho je pro daný typ exportována globální deklarace elementu. Pokud typ <xref:System.Xml.Serialization.XmlRootAttribute> nemá použit atribut, má element stejný název a obor názvů jako kontrakt dat a jeho vlastnost "nillable" je `true`. Jedinou výjimkou je obor názvů schématu (`http://www.w3.org/2001/XMLSchema`) – Pokud je kontrakt dat typu v tomto oboru názvů, odpovídající globální element je v prázdném oboru názvů, protože je zakázáno přidávat nové prvky do oboru názvů schématu. Je-li pro typ `XmlRootAttribute` použit atribut, je deklarace globálního prvku exportována pomocí následujících vlastností <xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> : <xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A>a <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A> . Ve výchozím nastavení `XmlRootAttribute` se používá název kontraktu dat, prázdný obor názvů a "nillable `true`".  
  
 Stejná pravidla deklarace globálních prvků se vztahují na typy datových sad typu Legacy. Všimněte si, `XmlRootAttribute` že deklarace globálních prvků nelze přepsat přidáním vlastního kódu, buď přidaných `XmlSchemaSet` na metodu pomocí metody poskytovatele schématu nebo `GetSchema` prostřednictvím pro typy starších datových sad.  
  
### <a name="ixmlserializable-element-types"></a>IXmlSerializable – typy prvků  
 `IXmlSerializable`typy prvků mají buď `IsAny` vlastnost nastavenou na `true` , nebo mají návrat `null`metody poskytovatele schématu.  
  
 Serializace a deserializace typu elementu je velmi podobná serializaci a deserializaci typu obsahu. Existují však některé důležité rozdíly:  
  
- Implementace `WriteXml` se očekává, že zapíše přesně jeden prvek (což může samozřejmě obsahovat více podřízených elementů). Neměl by zapisovat atributy mimo tento jediný element, více elementů na stejné úrovni nebo smíšený obsah. Element může být prázdný.  
  
- `ReadXml` Implementace by neměla číst prvek obálky. Očekává se, že si přečtete jeden prvek `WriteXml` , který vytvoří.  
  
- Při pravidelném serializaci typu elementu (například jako datový člen v kontraktu dat) vytvoří serializátor výstup prvku obálky před voláním `WriteXml`jako s typy obsahu. Při serializaci typu elementu na nejvyšší úrovni však serializátor obvykle nevytváří Obálkový prvek vůbec kolem elementu, který `WriteXml` zapisuje, pokud není kořenový název a obor názvů explicitně zadán při vytváření serializátoru v konstruktory `NetDataContractSerializer`nebo. `DataContractSerializer` Další informace naleznete v tématu [serializace a](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)deserializace.  
  
- Při serializaci typu <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> prvku na nejvyšší úrovni bez zadání kořenového názvu a oboru názvů v době konstrukce a <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> v podstatě neprovede žádné volání `WriteXml`. V tomto režimu nemůže být `null` serializovaný objekt a nelze jej polymorfním přiřadit. Také zachování grafu objektů nelze povolit a `NetDataContractSerializer` nelze jej použít.  
  
- Při deserializaci typu elementu na nejvyšší úrovni bez zadání kořenového názvu a oboru názvů v době konstrukce, vrátí <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> `true` , pokud může najít začátek libovolného elementu. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A>se sadou parametrů se chová stejně jako `IsStartObject` před skutečným čtením objektu. `true` `verifyObjectName` `ReadObject`poté předává řízení `ReadXml` metodě.  
  
 Schéma exportované pro typy elementů je stejné jako pro `XmlElement` typ, jak je popsáno v předchozí části, s výjimkou, že metoda poskytovatele schématu může přidat jakékoli další schéma <xref:System.Xml.Schema.XmlSchemaSet> jako s typy obsahu. `XmlRootAttribute` Použití atributu s typy prvků není povoleno a deklarace globálních prvků nejsou pro tyto typy nikdy generovány.  
  
### <a name="differences-from-the-xmlserializer"></a>Rozdíly mezi objektem XmlSerializer  
 Rozhraní a atributy a`XmlRootAttribute`jsou také srozumitelné pomocí <xref:System.Xml.Serialization.XmlSerializer>. `XmlSchemaProviderAttribute` `IXmlSerializable` Existují však určité rozdíly v tom, jak jsou tyto aplikace zpracovány v modelu kontraktu dat. Důležité rozdíly jsou shrnuty v následujícím seznamu:  
  
- Metoda poskytovatele schématu musí být veřejná pro použití v `XmlSerializer`, ale nemusí být veřejná pro použití v modelu kontraktu dat.  
  
- Metoda poskytovatele schématu je volána, když `IsAny` je `true` v `XmlSerializer`modelu kontraktu dat, ale nikoli s.  
  
- Pokud atribut není k dispozici pro obsah nebo starší typy datových sad `XmlSerializer` , exportuje deklaraci globálního prvku v prázdném oboru názvů. `XmlRootAttribute` V modelu kontraktu dat se používá obor názvů obvykle obor názvů kontraktu dat, jak je popsáno výše.  
  
 Pamatujte na tyto rozdíly při vytváření typů, které se používají v obou technologiích serializace.  
  
### <a name="importing-ixmlserializable-schema"></a>Importuje se schéma IXmlSerializable.  
 Při importu schématu vygenerovaného `IXmlSerializable` z typů existuje několik možností:  
  
- Vygenerované schéma může být platné schéma kontraktu dat, jak je popsáno v tématu [referenční informace schématu kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). V takovém případě se schéma dá importovat jako běžné a jsou vygenerované běžné typy kontraktů dat.  
  
- Vygenerované schéma nesmí být platným schématem kontraktu dat. Například metoda poskytovatele schématu může generovat schéma, které zahrnuje atributy XML, které nejsou podporovány v modelu kontraktu dat. V takovém případě můžete schéma importovat jako `IXmlSerializable` typy. Tento režim importu není ve výchozím nastavení zapnutý, ale dá se snadno povolit – například s `/importXmlTypes` přepínačem příkazového řádku, který se nachází v nástroji pro podporu [metadat ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Tato informace je podrobněji popsána v tématu [Import schématu pro generování tříd](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md). Všimněte si, že je nutné pracovat přímo s XML pro vaše instance typu. Je také vhodné zvážit použití jiné technologie serializace, která podporuje širší škálu schématu – viz téma o použití `XmlSerializer`.  
  
- Můžete chtít znovu použít stávající `IXmlSerializable` typy na proxy místo generování nových. V tomto případě lze pomocí odkazovaného typu, který je popsán v tématu Import schématu pro generování typů, použít k označení typu pro opakované použití. To odpovídá použití `/reference` přepínače na Svcutil. exe, který určuje sestavení, které obsahuje typy pro opakované použití.  
  
### <a name="xmlserializer-legacy-behavior"></a>Chování ve starších verzích XmlSerializer  
 V .NET Framework 4,0 a starších vygeneroval objekt XmlSerializer dočasná sestavení serializace zápisem C# kódu do souboru. Soubor byl poté zkompilován do sestavení.  Toto chování mělo nějaké nežádoucí důsledky, například zpomalení času spuštění serializátoru. V .NET Framework 4,5 bylo toto chování změněno, aby vygenerovalo sestavení bez nutnosti použití kompilátoru. Někteří vývojáři si můžou chtít zobrazit generovaný C# kód. Tuto starší verzi chování můžete určit pomocí následující konfigurace:  
  
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
  
 Pokud narazíte na problémy s kompatibilitou, `XmlSerializer` jako je selhání serializace odvozené třídy s neveřejným novým přepsáním, můžete přejít zpět `XMLSerializer` na starší verzi chování pomocí následující konfigurace:  
  
```xml  
<configuration>  
<appSettings>   
<add key="System:Xml:Serialization:UseLegacySerializerGeneration" value="true" />  
               </appSettings>  
</configuration>  
```  
  
 Jako alternativu k výše uvedené konfiguraci můžete použít následující konfiguraci na počítači, na kterém běží .NET Framework 4,5 nebo novější verze:  
  
```xml  
<configuration>  
<system.xml.serialization>  
<xmlSerializer useLegacySerializerGeneration="true"/>  
</system.xml.serialization>  
</configuration>  
```  
  
> [!NOTE]
> `<xmlSerializer useLegacySerializerGeneration="true"/>` Přepínač funguje pouze v počítači se systémem .NET Framework 4,5 nebo novější verzí. Výše uvedený `appSettings` postup funguje na všech .NET Framework verzích.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.DataContractFormatAttribute>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.XmlSerializer>
- <xref:System.ServiceModel.MessageHeaderArrayAttribute>
- [Určování přenosu dat v kontraktech služby](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
- [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Postupy: Zlepšení doby spuštění klientských aplikací WCF pomocí XmlSerializer](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
