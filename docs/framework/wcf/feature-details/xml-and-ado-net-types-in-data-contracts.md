---
title: Typy XML a ADO.NET v kontraktech dat
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c2ce8461-3c15-4c41-8c81-1cb78f5b59a6
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7efef63668bb78bdc9a7d66654c9e33ef6c0138c
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="xml-and-adonet-types-in-data-contracts"></a>Typy XML a ADO.NET v kontraktech dat
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Modelu kontraktu dat podporuje určité typy, které představují XML přímo. Když jsou tyto typy serializován do formátu XML, serializátoru, který zapíše obsah XML z těchto typů bez dalšího zpracování. Podporované typy jsou <xref:System.Xml.XmlElement>, pole <xref:System.Xml.XmlNode> (ale ne `XmlNode` zadejte sám sebe), stejně jako typy, které implementují <xref:System.Xml.Serialization.IXmlSerializable>. <xref:System.Data.DataSet> a <xref:System.Data.DataTable> typu, jakož i typové datové sady, běžně se používají při programování pro databázi. Tyto typy implementovat `IXmlSerializable` rozhraní a jsou proto serializovatelný v datech smlouvy modelu. Na konci tohoto tématu jsou uvedeny některé důležité informace pro tyto typy.  
  
## <a name="xml-types"></a>Typy XML  
  
### <a name="xml-element"></a>XML Element  
 `XmlElement` Typ serializován pomocí jeho obsah XML. Například pomocí následujícího typu.  
  
 [!code-csharp[DataContractAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#4)]
 [!code-vb[DataContractAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#4)]  
  
 To je serializován do formátu XML následujícím způsobem:  
  
```xml  
<MyDataContract xmlns="http://schemas.contoso.com">  
    <myDataMember>  
        <myElement xmlns="" myAttribute="myValue">  
            myContents  
        </myElement>  
    </myDataMember>  
</MyDataContract>  
```  
  
 Všimněte si, že element obálky data člena `<myDataMember>` se stále nachází. Neexistuje žádný způsob odebrání tohoto elementu v datovém modelu kontrakt. Serializátorů, které zpracovávají tento model ( <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.NetDataContractSerializer>) může vysílat speciální atributy do tohoto elementu obálku. Tyto atributy zahrnují standardní atribut "žádné" Instance schématu XML (povolení `XmlElement` být `null`) a podle atributu "typ" (povolení `XmlElement` použije polymorphically). Kromě toho jsou specifické pro následující atributy XML [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: "Id", "Ref", "Type" a "Sestavení". Tyto atributy mohou být vygenerované pro podporu použití `XmlElement` s povoleným režimem zachovávání objekt grafu nebo s <xref:System.Runtime.Serialization.NetDataContractSerializer>. (Další informace o režimu objekt grafu písmen a zachovávání s najdete v tématu [serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).)  
  
 Pole nebo kolekce `XmlElement` jsou povoleny a jsou zpracovávány jako ostatní pole nebo kolekce. To znamená, existuje element obálku pro celou kolekci a element samostatné obálkové (podobně jako `<myDataMember>` v předchozím příkladu) pro každý `XmlElement` v poli.  
  
 U deserializace `XmlElement` vytvoří deserializátor z příchozí XML. Platné nadřazené <xref:System.Xml.XmlDocument> zajišťuje deserializátor.  
  
 XML fragment, musí být deserializovat do `XmlElement` definuje všech předpon, které používá a nevyžaduje žádné definice předpony z nadřazenými prvky. Jedná se o problém jenom při použití `DataContractSerializer` k XML z jiné (jinou hodnotu než`DataContractSerializer`) zdroje.  
  
 Při použití s `DataContractSerializer`, `XmlElement` přiřazeni polymorphically, ale jenom na člena typu <xref:System.Object>. I když implementuje <xref:System.Collections.IEnumerable>, `XmlElement` nelze použít jako typ kolekce a nemůže být přiřazen <xref:System.Collections.IEnumerable> – datový člen. Stejně jako u všech polymorfní přiřazení, `DataContractSerializer` vysílá název kontraktu dat ve výsledném souboru XML – v takovém případě je "XmlElement" v "http://schemas.datacontract.org/2004/07/System.Xml" oboru názvů.  
  
 S `NetDataContractSerializer`, všechny platné polymorfní přiřazení `XmlElement` (na `Object` nebo `IEnumerable`) je podporováno.  
  
 Nepokoušejte se použít buď serializátorů s typy odvozené z `XmlElement`, zda jsou přiřazeny polymorphically nebo ne.  
  
### <a name="array-of-xmlnode"></a>XmlNode – pole  
 Pomocí pole <xref:System.Xml.XmlNode> je velmi podobný používání `XmlElement`. Pomocí pole `XmlNode` vám dává větší flexibilitu než použití `XmlElement`. Můžete napsat víc elementů uvnitř datového člena zabalení elementu. Můžete také vložit obsah než elementy uvnitř datového člena zabalení elementu, jako je například komentáře XML. Nakonec můžete vložit atributy do zabalenou datový prvek člena. To vše lze dosáhnout vyplní pole `XmlNode` v konkrétních odvozených tříd `XmlNode` například <xref:System.Xml.XmlAttribute>, `XmlElement` nebo <xref:System.Xml.XmlComment>. Například pomocí následujícího typu.  
  
 [!code-csharp[DataContractAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#5)]
 [!code-vb[DataContractAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#5)]  
  
 Když serializovat, výsledná XML je podobná následující kód.  
  
```xml  
<MyDataContract xmlns="http://schemas.contoso.com">  
  <myDataMember myAttribute="myValue">  
     <!--myComment-->  
     <myElement xmlns="" myAttribute="myValue">  
 myContents  
     </myElement>  
     <myElement xmlns="" myAttribute="myValue">  
       myContents  
     </myElement>  
  </myDataMember>  
</MyDataContract>  
```  
  
 Všimněte si, že datový prvek obálku člen `<myDataMember>` obsahuje atribut, komentáře a dva elementy. Toto jsou čtyři `XmlNode` instancí, které byly serializovat.  
  
 Pole `XmlNode` , má za následek neplatný kód XML nelze serializovat. Například o pole dvou `XmlNode` instance, kde je první z nich `XmlElement` a druhý <xref:System.Xml.XmlAttribute> je neplatný, protože toto pořadí neodpovídá žádné platnou instanci XML (neexistuje žádné místní připojit atribut, který se).  
  
 U deserializace pole `XmlNode`, uzly jsou vytvořeny a naplněny s informacemi z příchozí XML. Platné nadřazené <xref:System.Xml.XmlDocument> zajišťuje deserializátor. Všechny uzly jsou deserializovat, včetně žádné atributy v elementu obálku data člena, ale s výjimkou atributy tam umístí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serializátorů (například atributy slouží k určení, přiřazení polymorfní). Přímý přístup do paměti o definování všechny předpony oboru názvů XML fragment platí pro deserializaci pole `XmlNode` je stejný jako k deserializaci `XmlElement`.  
  
 Při použití serializátorů se zapnutým zachováním objekt grafu, rovnost objektů se zachová pouze na úroveň `XmlNode` pole, ne z individuálních `XmlNode` instance.  
  
 Nepokoušejte se serializovat pole `XmlNode` kde jeden nebo více uzlů je nastaven na `null`. Je povoleno pro člena celé pole jako `null`, ale ne pro všechny jednotlivé `XmlNode` obsažené v poli. Pokud je člen celé pole hodnotu null, element obálky data člena obsahuje speciální atribut, který označuje, že je null. U deserializace člen celé pole také se změní na hodnotu null.  
  
 Pouze regulární pole `XmlNode` nakládá speciálně serializátor. Datové členy deklarován jako ostatní typy kolekcí, které obsahují `XmlNode`, nebo datové členy deklarovány jako pole typů odvozené z `XmlNode`, nejsou považovány speciálně. Proto nejsou obvykle serializovatelný nesplňují-také jeden z jiných kritérií pro serializaci.  
  
 Pole nebo kolekce pole `XmlNode` jsou povoleny. Element obálku pro celou kolekci a element samostatné obálkové (podobně jako `<myDataMember>` v předchozím příkladu) pro každé pole `XmlNode` ve vnější pole nebo kolekce.  
  
 Naplnění dat člen typu <xref:System.Array> z `Object` nebo `Array` z `IEnumerable` s `XmlNode` instance nevede datový člen zacházeno jako `Array` z `XmlNode` instance. Každý člen pole je samostatně serializovat.  
  
 Při použití s `DataContractSerializer`, pole `XmlNode` lze přiřadit polymorphically, ale jenom na člena typu `Object`. I když implementuje `IEnumerable`, pole `XmlNode` nelze použít jako typ kolekce a přiřadit `IEnumerable` – datový člen. Stejně jako u všech polymorfní přiřazení, `DataContractSerializer` vysílá název kontraktu dat ve výsledném souboru XML – v takovém případě je "ArrayOfXmlNode" v "http://schemas.datacontract.org/2004/07/System.Xml" oboru názvů. Při použití s `NetDataContractSerializer`, všechny platné přiřazení `XmlNode` podporuje se pole.  
  
### <a name="schema-considerations"></a>Důležité informace o schématu  
 Podrobnosti o schéma mapování typů XML najdete v tématu [Přehled schématu kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Tato část obsahuje přehled důležitých bodů.  
  
 Člen datového typu `XmlElement` se mapuje na element definovat pomocí následující anonymního typu.  
  
```xml  
<xsd:complexType>  
   <xsd:sequence>  
      <xsd:any minOccurs="0" processContents="lax" />  
   </xsd:sequence>  
</xsd:complexType>  
```  
  
 Člen datového typu pole `XmlNode` se mapuje na element definovat pomocí následující anonymního typu.  
  
```xml  
<xsd:complexType mixed="true">  
   <xsd:sequence>  
      <xsd:any minOccurs="0" maxOccurs="unbounded" processContents="lax" />  
   </xsd:sequence>  
   <xsd:anyAttribute/>  
</xsd:complexType>  
```  
  
## <a name="types-implementing-the-ixmlserializable-interface"></a>Implementace rozhraní IXmlSerializable typy  
 Typy, které implementují `IXmlSerializable` rozhraní plně podporuje `DataContractSerializer`. <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> Atribut by měl vždy použít pro tyto typy k řízení jejich schématu.  
  
 Existují tři typy typy, které implementují `IXmlSerializable`: typy, které představují libovolný typy obsahu, které představují jeden element a starší verze <xref:System.Data.DataSet> typy.  
  
-   Typy obsahu použijte metodu schématu poskytovatele určeného `XmlSchemaProviderAttribute` atribut. Metoda nevrátí `null`a <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> vlastnost v atributu je ponechán v jeho výchozí hodnotu `false`. Toto je nejběžnější použití `IXmlSerializable` typy.  
  
-   Element typy se používají při `IXmlSerializable` typ se musí řídit svůj vlastní název kořenového elementu. Označit jako typ elementu typu, nastavte <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> vlastnost <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atribut `true` nebo vrátí hodnotu null z metody zprostředkovatele schématu. S metody zprostředkovatele schématu je pro typy elementů volitelné – můžete určit hodnotu null. namísto názvu metody v `XmlSchemaProviderAttribute`. Ale pokud `IsAny` je `true` a metody zprostředkovatele schématu je zadán, metoda musí vrátit hodnotu null.  
  
-   Starší verze <xref:System.Data.DataSet> typy jsou `IXmlSerializable` typy, které nejsou označené jako `XmlSchemaProviderAttribute` atribut. Místo toho spoléhají na <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> metoda pro generování schémat. Tento vzor slouží k `DataSet` typu a jeho typové datové sady odvozená třída v dřívějších verzích rozhraní .NET Framework, ale je nyní zastaralé a je podporována pouze pro starší verze důvodů. Nezadávejte závisí na tomto vzoru a vždy použít `XmlSchemaProviderAttribute` k vaší `IXmlSerializable` typy.  
  
### <a name="ixmlserializable-content-types"></a>Typy IXmlSerializable obsahu  
 Při serializaci členem datový typ, který implementuje `IXmlSerializable` a typu obsahu jako definované dříve, serializátoru, který zapisuje element obálku pro člena a předejte jí ovládací prvek dat <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metoda. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> Implementace můžete zapsat všechny XML, včetně přidání atributů do elementu obálku. Po `WriteXml` je Hotovo, serializátor zavře elementu.  
  
 Při deserializaci členem datový typ, který implementuje `IXmlSerializable` a je typ obsahu jak je definována dříve, pozice deserializátor čtečky XML pro element obálku pro – datový člen a předejte jí řídit k <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> metoda. Metoda musí čtení celý elementu, včetně počáteční a koncové značky. Zajistěte, aby vaše `ReadXml` kód zpracovává případě elementu je prázdný. Kromě toho vaší `ReadXml` implementace neměli spoléhat na element obálky se s názvem určitým způsobem. Název je zvolen podle serializátoru, který se může lišit.  
  
 Je povoleno přiřadit `IXmlSerializable` obsah typy polymorphically, například k datům členy typu <xref:System.Object>. Je také povoleno pro instance typu mít hodnotu null. Nakonec je možné použít `IXmlSerializable` typy s objekt grafu zachovávání povoleno a <xref:System.Runtime.Serialization.NetDataContractSerializer>. Všechny tyto funkce vyžadují [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serializátor připojit určité atributy do elementu obálku ("žádné" a "typ" v oboru názvů Instance schématu XML a "Id", "Ref", "Type" a "Sestavení" v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-konkrétní obor názvů).  
  
#### <a name="attributes-to-ignore-when-implementing-readxml"></a>Atributy, které mají ignorovat při implementaci ReadXml  
 Před předáním řízení pro vaše `ReadXml` kód, deserializátor prozkoumá XML element, zjistí tyto speciální atributy XML a funguje na ně. Například, pokud je "žádné" `true`, je deserializovat hodnotu null a `ReadXml` není volán. Pokud je zjištěn polymorfismus, obsah elementu se deserializovat, jako kdyby byl jiného typu. Implementace polymorphically přiřazené typu `ReadXml` je volána. V každém případě `ReadXml` implementace má tyto speciální atributy ignorovat, protože jsou zpracovávány deserializátor.  
  
### <a name="schema-considerations-for-ixmlserializable-content-types"></a>Důležité informace o schématu pro typy obsahu IXmlSerializable  
 Při exportu schématu `IXmlSerializable` typ obsahu, je volána metoda zprostředkovatele schématu. <xref:System.Xml.Schema.XmlSchemaSet> Předaný schématu metoda zprostředkovatele. Metodu můžete přidat všechny platné schéma do sady schématu. Sada schématu obsahuje schéma, které je již znám v době, kdy dojde k exportu schématu. Když metoda zprostředkovatele schématu musíte přidat položku do sady schéma, musíte určit Pokud <xref:System.Xml.Schema.XmlSchema> s odpovídající obor názvů již existuje v sadě. Pokud ano, metoda zprostředkovatele schématu musíte přidat novou položku do existující `XmlSchema`. V ostatních případech musíte vytvořit nový `XmlSchema` instance. To je důležité, pokud pole `IXmlSerializable` typy jsou používány. Pokud máte například `IXmlSerializable` typ, který získá exportovány jako typ "A" v oboru názvů "B", je možné, že na době metoda zprostředkovatele schématu se nazývá schéma nastavit již obsahuje schéma pro "B" typ "ArrayOfA".  
  
 Kromě přidání typů tak, aby <xref:System.Xml.Schema.XmlSchemaSet>, metoda zprostředkovatele schématu pro typy obsahu, musí vracet hodnotu než null. Můžete vrátit <xref:System.Xml.XmlQualifiedName> určující název typu schématu pro v dané `IXmlSerializable` typu. Tento kvalifikovaný název slouží taky jako data smlouvy názvem a oborem názvů pro typ. Je povoleno návratový typ, který neexistuje ve schématu nastavená, okamžitě, pokud metoda zprostředkovatele schématu vrátí. Ale očekává se, že na době, všechny související typy jsou exportovány ( <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> metoda je volána pro všechny typy relevantní na <xref:System.Runtime.Serialization.XsdDataContractExporter> a <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> získat přístup k vlastnosti), typ existuje v sadě schématu. Přístup k `Schemas` vlastnost před všechny relevantní `Export` byly provedeny volání může mít za následek <xref:System.Xml.Schema.XmlSchemaException>. Další informace o procesu exportu najdete v tématu [export schémat ze tříd](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
 Metoda zprostředkovatele schéma můžete se taky vrátit <xref:System.Xml.Schema.XmlSchemaType> používat. Typ může nebo nemusí být anonymní. Pokud je anonymní, schéma pro `IXmlSerializable` typu se exportuje jako anonymní typ pokaždé, když `IXmlSerializable` typ se používá jako člena. `IXmlSerializable` Typ stále má název kontraktu dat a oboru názvů. (To je určit, jak je popsáno v [názvy datových kontraktů](../../../../docs/framework/wcf/feature-details/data-contract-names.md) s tím rozdílem, že <xref:System.Runtime.Serialization.DataContractAttribute> nelze atribut použít k přizpůsobení názvu.) Pokud není anonymní, musí být jeden z typů v `XmlSchemaSet`. Tento případ je ekvivalentní vrací `XmlQualifiedName` typu.  
  
 Navíc se pro typ exportují deklaraci globálním elementem. Pokud typ nemá <xref:System.Xml.Serialization.XmlRootAttribute> atribut použitý k němu element se stejným názvem a oborem názvů jako kontrakt dat a jeho "povolenou" vlastnost na hodnotu true. Jedinou výjimkou je obor názvů schématu ("http://www.w3.org/2001/XMLSchema") – Pokud kontrakt dat typ je v tomto oboru názvů, odpovídající globální element je v oboru názvů prázdné, protože je zakázán pro přidání nových elementů do oboru názvů schématu. Pokud má typ `XmlRootAttribute` atribut použitý k němu deklaraci globální element exportu pomocí následujících: <xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A>, <xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> a <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A> vlastnosti. Výchozí hodnoty s `XmlRootAttribute` použít jsou název kontraktu dat, prázdné obor názvů a "povolenou" Probíhá hodnotu true.  
  
 Stejná pravidla deklarace globální element platí pro typy starší verze datové sady. Všimněte si, že `XmlRootAttribute` nejde přepsat globální element deklarace přidány prostřednictvím vlastní kód, buď přidat do `XmlSchemaSet` pomocí metody poskytovatele schématu nebo pomocí `GetSchema` pro typy starší verze datové sady.  
  
### <a name="ixmlserializable-element-types"></a>IXmlSerializable Element typy  
 `IXmlSerializable` Element typy mít buď `IsAny` vlastnost nastavena na hodnotu `true` nebo jejich metoda zprostředkovatele schématu vrátit `null`.  
  
 Serializace a deserializace typ elementu je velmi podobné serializaci a deserializaci typ obsahu. Existují však několik důležitých rozdílů:  
  
-   `WriteXml` Implementace budou zapisovat přesně jeden element (který samozřejmě může obsahovat více podřízených elementů). By neměl být zápis atributy mimo tento jeden element více prvků nebo smíšený obsah. Element může být prázdná.  
  
-   `ReadXml` Implementace by neměl čtení prvku obálku. Očekává se číst jeden element který `WriteXml` vytváří.  
  
-   Při serializaci typu elementu pravidelně (například jako člena dat ve smlouvě data), serializátor výstupy element obálky před voláním `WriteXml`, stejně jako u typy obsahu. Ale při serializaci typ elementu na nejvyšší úrovni, serializátoru, který není výstup normálně element obálku kolem elementu vůbec, `WriteXml` zapíše, pokud název kořenové domény a oboru názvů byly explicitně zadány při vytváření serializátor v `DataContractSerializer` nebo `NetDataContractSerializer` konstruktory. Další informace najdete v tématu [serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
-   Při serializaci typ elementu na nejvyšší úrovni bez zadání název kořenové domény a oboru názvů v době konstrukce <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> a <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> v podstatě neprovede žádnou akci a <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> volání `WriteXml`. V tomto režimu serializovaného objektu nemůže mít hodnotu null a nelze jí přiřadit polymorphically. Také, nemůže objekt grafu zachovávání povolena a `NetDataContractSerializer` nelze použít.  
  
-   Při deserializaci typ elementu na nejvyšší úrovni bez zadání název kořenové domény a oboru názvů v době konstrukce <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> vrátí `true` Pokud nemůže najít začátek libovolný element. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> pomocí `verifyObjectName` parametr nastaven na `true` se chová stejně jako `IsStartObject` před ve skutečnosti čtení objektu. `ReadObject` pak předá řízení `ReadXml` metoda.  
  
 Schéma exportovat za účelem typy elementu je stejná jako u `XmlElement` zadejte, jak je popsáno v předchozí části, s tím rozdílem, že metoda zprostředkovatele schéma můžete přidat žádné další schéma, aby <xref:System.Xml.Schema.XmlSchemaSet> stejně jako u typy obsahu. Pomocí `XmlRootAttribute` atribut s typy element není povolen, a globální element deklarace jsou nikdy vygenerované pro tyto typy.  
  
### <a name="differences-from-the-xmlserializer"></a>Rozdíl oproti třídy XmlSerializer  
 `IXmlSerializable` Rozhraní a `XmlSchemaProviderAttribute` a `XmlRootAttribute` atributy jsou také rozumí <xref:System.Xml.Serialization.XmlSerializer> . Existují však určité rozdíly v tom, jak jsou považovány v datovém modelu kontrakt. Důležité rozdíly jsou shrnuty v následující:  
  
-   Metoda zprostředkovatele schématu musí být možné používat v veřejné `XmlSerializer`, ale nemusí být možné používat v datovém modelu kontrakt veřejné.  
  
-   Metoda zprostředkovatele schématu je volána, když `IsAny` platí v datovém modelu kontrakt, ale ne `XmlSerializer`.  
  
-   Při `XmlRootAttribute` atribut není k dispozici pro obsah nebo typy starší verze datové sady, `XmlSerializer` exportuje deklaraci globální element v oboru názvů prázdné. V datovém modelu kontrakt používá obor názvů je obvykle obor názvů kontraktu dat jak bylo popsáno výše.  
  
 Pamatujte na tyto rozdíly při vytváření typů, které se používají u obou technologií serializace.  
  
### <a name="importing-ixmlserializable-schema"></a>Import schématu IXmlSerializable  
 Při importu schéma vygenerovat z `IXmlSerializable` typy, několik možností:  
  
-   Vygenerovaný schématu může být schématu kontrakt platná data, jak je popsáno v [Přehled schématu kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). V takovém případě schéma můžete importovat jako obvykle a typy kontraktů dat regulární se generují.  
  
-   Vygenerovaný schéma nemusí být schématu kontrakt platná data. Například metoda zprostředkovatele vašeho schématu může generovat schéma, které zahrnuje atributy XML, které nejsou podporovány v datovém modelu kontrakt. V takovém případě můžete importovat schéma jako `IXmlSerializable` typy. Tento režim import se nenachází na ve výchozím nastavení ale můžete snadno povolit – například `/importXmlTypes` přepínač příkazového řádku [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). To je podrobně popsaná v [import schématu pro generování tříd](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md). Všimněte si, že musí pracovat přímo se souborem XML pro vaše instance typu. Může také zvažte použití jiné serializace technologie, která podporuje širší rozsah schématu – naleznete v tématu o používání `XmlSerializer`.  
  
-   Možná budete chtít použít stávající `IXmlSerializable` typy proxy serveru, místo aby generovala nové. V takovém případě odkazované typy funkce popsaná v import schématu pro generování typy tématu slouží k označení typu znovu použít. To odpovídá pomocí `/reference` přepínač na svcutil.exe, který určuje sestavení, které obsahuje typy, které mají-li znovu použít.  
  
## <a name="representing-arbitrary-xml-in-data-contracts"></a>Představující libovolný XML v kontraktech dat  
 `XmlElement`, Pole `XmlNode` a `IXmlSerializable` typy umožňují vložit libovolný XML do datového modelu kontrakt. `DataContractSerializer` a `NetDataContractSerializer` předat tento XML obsahu k zapisovače XML používá, a to bez vzájemnému v procesu. Zapisovače XML však může vynutit určitá omezení XML, který budou zapisovat. Konkrétně zde jsou některé důležité příklady:  
  
-   Zapisovače XML neumožňují obvykle deklaraci dokumentu XML (například \<? xml verze = "1.0'? >) uprostřed zápis jiného dokumentu. Nelze provést úplné dokumentu XML a serializovat jej jako `Array` z `XmlNode` – datový člen. K tomuto účelu muset buď pruhu deklaraci dokumentu nebo představují ho pomocí vlastní schéma kódování.  
  
-   Všechny zapisovače XML dodává s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] odmítnout pokyny pro zpracování XML (\<? … ? >) a zadejte definice dokumentu (\<! … >), protože nejsou povoleny v protokolu SOAP zprávy. Znovu můžete použít vlastní kódování mechanismus k vyřešení tohoto omezení. Pokud musí obsahovat tyto v výsledný soubor XML, můžete napsat vlastní kodér, který používá zapisovače XML, které je podporují.  
  
-   Při implementaci `WriteXml`, vyhněte se volání <xref:System.Xml.XmlWriter.WriteRaw%2A> metoda zapisovače XML. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá různých XML kódování (včetně binární), je velmi obtížné nebo dokonce znemožňují použít `WriteRaw` tak, že výsledkem je použitelná v jakémkoli kódování.  
  
-   Při implementaci `WriteXml`, nepoužívejte <xref:System.Xml.XmlWriter.WriteEntityRef%2A> a <xref:System.Xml.XmlWriter.WriteNmToken%2A> metody, které jsou v zapisovače XML součástí podporována [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="using-dataset-typed-dataset-and-datatable"></a>Pomocí datové sady, typové datové sady a DataTable  
 Pomocí těchto typů je plně podporovaný v datový model kontrakt. Při použití těchto typů, zvažte následující:  
  
-   Schéma pro tyto typy (zejména <xref:System.Data.DataSet> a jeho typu odvozené třídy) nemusí být vzájemná spolupráce s některé jinou hodnotu než[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] platformy, nebo může mít za následek nízký použitelnost při použití s tyto platformy. Kromě toho používání `DataSet` typu může mít vliv na výkon. Nakonec se může to ztížit pro vás na verzi aplikace v budoucnu. Zvažte použití explicitně definované datové typy kontraktů místo `DataSet` typy v vaše smlouvy.  
  
-   Při importu `DataSet` nebo `DataTable` schématu, je důležité, chcete-li tyto typy. Pomocí příkazového řádku nástroje Svcutil.exe můžete to provést pomocí předání názvu sestavení System.Data.dll `/reference` přepínače. Pokud import schématu typové datové sady, musí být uveden typ typové datové sady. S Svcutil.exe, předat umístění sestavení typové datové sady `/reference` přepínače. Další informace o odkazující na typy najdete v tématu [import schématu pro generování tříd](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 Podpora pro typové datové sady v datovém modelu kontrakt je omezená. Typové datové sady lze serializovat a deserializovat a můžete exportovat jejich schématu. Kontrakt dat import schématu se nepodařilo vygenerovat nový však zadané datovou sadu typy ze schématu, jako je pouze znovu použít existující. Může ukazovat na existující typové datové sady pomocí `/r` přepínač na Svcutil.exe. Pokud pokus o použití Svcutil.exe bez `/r` přepnout na službu, která používá typové datové sady, je automaticky vybrána serializátor alternativní (XmlSerializer). Pokud musíte použít objektu DataContractSerializer a musíte vygenerovat datové sady ze schématu, můžete použít následující postup: generování typů typové datové sady (pomocí nástroje Xsd.exe s `/d` přepínač na službu), zkompilovat typy a pak přejděte na je pomocí `/r` přepínač na Svcutil.exe.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Xml.Serialization.IXmlSerializable>  
 [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Typy podporované serializátorem kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
