---
title: Typy XML a ADO.NET v kontraktech dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2ce8461-3c15-4c41-8c81-1cb78f5b59a6
ms.openlocfilehash: 1053a543a23ed36a5c06c45044c8fdbe25a60538
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929516"
---
# <a name="xml-and-adonet-types-in-data-contracts"></a>Typy XML a ADO.NET v kontraktech dat
Datový model kontraktu Windows Communication Foundation (WCF) podporuje určité typy, které představují XML přímo. Pokud tyto typy jsou serializován do formátu XML, serializátoru, který zapíše obsah XML z těchto typů bez dalšího zpracování. Podporované typy jsou <xref:System.Xml.XmlElement>, pole <xref:System.Xml.XmlNode> (ale ne `XmlNode` zadejte vlastní), stejně jako typy, které implementují <xref:System.Xml.Serialization.IXmlSerializable>. <xref:System.Data.DataSet> a <xref:System.Data.DataTable> typ, jakož i typové datové sady, se běžně používají při programování pro databázi. Tyto typy implementace `IXmlSerializable` rozhraní a jsou proto serializovatelný v datech smlouvy modelu. Některé speciální aspekty pro tyto typy jsou uvedené na konci tohoto tématu.  
  
## <a name="xml-types"></a>Typy XML  
  
### <a name="xml-element"></a>– Element XML  
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
  
 Všimněte si, že element obálky, a datový člen `<myDataMember>` je stále k dispozici. Neexistuje žádný způsob odebrání tohoto elementu v modelu kontraktu. Serializátory, které zpracovávají tohoto modelu ( <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.NetDataContractSerializer>) může vysílat speciální atributy do tohoto prvku obálky. Tyto atributy zahrnout atribut "nulový" standardní Instance schématu XML (povolení `XmlElement` bude `null`) a atributu "typ" (povolení `XmlElement` použije polymorphically). Navíc následující atributy XML jsou specifické pro WCF: "Id", "Ref", "Type" a "Sestavení". Tyto atributy mohou být vygenerován pro podporovat použití `XmlElement` s povoleným režimem uchování objektu grafu, nebo se <xref:System.Runtime.Serialization.NetDataContractSerializer>. (Další informace o režimu objektu grafu a zachovávání s rozlišením, naleznete v tématu [serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).)  
  
 Pole nebo kolekce `XmlElement` jsou povolené a jsou zpracovány jako ostatní pole nebo kolekce. To znamená, je element obálky pro celou kolekci a element samostatné obálky (podobně jako `<myDataMember>` v předchozím příkladu) pro každý `XmlElement` v poli.  
  
 K deserializaci `XmlElement` vytvoří deserializátor z příchozí XML. Platný nadřazený <xref:System.Xml.XmlDocument> deserializátor poskytuje.  
  
 Ujistěte se, že XML fragment, který je deserializovat do `XmlElement` definuje všechny předpony, které používá a nevyžaduje žádné definice předponu od nadřazených elementů. Toto je problém, pouze pokud používáte `DataContractSerializer` pro přístup k XML z jiného (jinou hodnotu než`DataContractSerializer`) zdroje.  
  
 Při použití s `DataContractSerializer`, `XmlElement` může být přiřazen polymorphically, ale jenom na datový člen typu <xref:System.Object>. I v případě, že implementuje <xref:System.Collections.IEnumerable>, `XmlElement` nelze použít jako typ kolekce a nejde přiřadit <xref:System.Collections.IEnumerable> datový člen. Stejně jako u všech polymorfní přiřazení `DataContractSerializer` vysílá názvem kontraktu dat ve výsledném souboru XML – v takovém případě je "XmlElement" v "http://schemas.datacontract.org/2004/07/System.Xml" oboru názvů.  
  
 S `NetDataContractSerializer`, žádné platné polymorfní přiřazení `XmlElement` (k `Object` nebo `IEnumerable`) se nepodporuje.  
  
 Nepokoušejte se použít buď serializátory s typy odvozené od `XmlElement`, ať už jsou přiřazeny polymorphically nebo ne.  
  
### <a name="array-of-xmlnode"></a>Pole typu XmlNode  
 Pomocí pole <xref:System.Xml.XmlNode> je velmi podobný používání `XmlElement`. Pomocí pole `XmlNode` vám zajistí větší flexibilitu než použití `XmlElement`. Můžete napsat více elementů v rámci datový člen zabalení elementu. Můžete také vložit obsah než prvky uvnitř datový člen zabalení elementu, například pro komentáře XML. Nakonec můžete umístit atributy do obalu datový člen element. To vše lze dosáhnout vyplnění pole `XmlNode` s konkrétními odvozené třídy `XmlNode` například <xref:System.Xml.XmlAttribute>, `XmlElement` nebo <xref:System.Xml.XmlComment>. Například pomocí následujícího typu.  
  
 [!code-csharp[DataContractAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#5)]
 [!code-vb[DataContractAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#5)]  
  
 Při serializován, výsledný XML je podobná následující kód.  
  
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
  
 Všimněte si, že element obálky datový člen `<myDataMember>` obsahuje atribut, komentáře a dva elementy. Jedná se o čtyři `XmlNode` instancí, které byly serializovat.  
  
 Pole `XmlNode` , že výsledkem neplatný kód XML nejde serializovat. Například pole dvou `XmlNode` instance, kde je první z nich `XmlElement` a druhý je <xref:System.Xml.XmlAttribute> je neplatný, protože toto pořadí neodpovídá žádné platné instance XML (není žádné místo pro atribut, který chcete připojit).  
  
 Pro deserializaci pole `XmlNode`, uzly jsou vytvořeny a naplněny informace z příchozích XML. Platný nadřazený <xref:System.Xml.XmlDocument> deserializátor poskytuje. Všechny uzly jsou deserializovat, včetně všech atributů na elementu obálky datový člen, ale s výjimkou atributy tam umístili serializátory WCF (např. slouží k označení polymorfní přiřazení atributy). Platí výstrahou o definování všechny předpony oboru názvů ve fragmentu XML pro deserializaci pole `XmlNode` stejně to dělá k deserializaci `XmlElement`.  
  
 Při serializátory pomocí objektu grafu a zachovávání s rozlišením zapnuté, rovnost objektů je zachována pouze na úrovni `XmlNode` pole, nikoli jednotlivé `XmlNode` instancí.  
  
 Nepokoušejte se serializovat pole `XmlNode` kde jeden nebo více uzlů je nastaven na `null`. Je povolený pro člen celého pole bude `null`, ale ne pro každý jednotlivec `XmlNode` obsažené v poli. Pokud člen celého pole má hodnotu null, obsahuje element obálky datový člen speciální atribut, který označuje, že má hodnotu null. K deserializaci člen celého pole také změní na hodnotu null.  
  
 Pouze pravidelných polí z `XmlNode` zachází speciálně modulem pro serializaci. Datové členy deklarované jako typy kolekcí, které obsahují `XmlNode`, nebo datové členy deklarované jako pole typů odvozených z `XmlNode`, nejsou speciálně zpracovány. Proto nejsou obvykle serializovatelný nesplňují také jednu z jiných kritérií pro serializaci.  
  
 Pole nebo kolekce polí `XmlNode` jsou povoleny. Element obálky pro celou kolekci a element samostatné obálky (podobně jako `<myDataMember>` v předchozím příkladu) pro každé pole `XmlNode` vnější pole nebo kolekce.  
  
 Naplnění datový člen typu <xref:System.Array> z `Object` nebo `Array` z `IEnumerable` s `XmlNode` instance nemá za následek datový člen se zachází jako `Array` z `XmlNode` instancí. Každý člen pole je samostatně serializovat.  
  
 Při použití s `DataContractSerializer`, pole `XmlNode` je možné přiřadit polymorphically, ale jenom na datový člen typu `Object`. I v případě, že implementuje `IEnumerable`, pole `XmlNode` nelze použít jako typ kolekce a přiřadit `IEnumerable` datový člen. Stejně jako u všech polymorfní přiřazení `DataContractSerializer` vysílá názvem kontraktu dat ve výsledném souboru XML – v takovém případě je "ArrayOfXmlNode" v "http://schemas.datacontract.org/2004/07/System.Xml" oboru názvů. Při použití s `NetDataContractSerializer`, žádné platné přiřazení `XmlNode` pole je podporován.  
  
### <a name="schema-considerations"></a>Schema Considerations  
 Podrobnosti o mapování schématu XML typů najdete v tématu [schéma kontraktů dat – referenční informace](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Tato část poskytuje přehled důležitých bodů.  
  
 Datový člen typu `XmlElement` je mapován na prvek definované pomocí následující anonymního typu.  
  
```xml  
<xsd:complexType>  
   <xsd:sequence>  
      <xsd:any minOccurs="0" processContents="lax" />  
   </xsd:sequence>  
</xsd:complexType>  
```  
  
 Datový člen třídy zadejte pole `XmlNode` se mapuje na element definovány pomocí následující anonymního typu.  
  
```xml  
<xsd:complexType mixed="true">  
   <xsd:sequence>  
      <xsd:any minOccurs="0" maxOccurs="unbounded" processContents="lax" />  
   </xsd:sequence>  
   <xsd:anyAttribute/>  
</xsd:complexType>  
```  
  
## <a name="types-implementing-the-ixmlserializable-interface"></a>Typy implementující rozhraní IXmlSerializable  
 Typy, které implementují `IXmlSerializable` rozhraní jsou plně podporovány `DataContractSerializer`. <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> Atribut by měl vždy použít pro tyto typy řídit jejich schématu.  
  
 Existují tři typy prvků typy, které implementují `IXmlSerializable`: typy, které představují libovolného obsahu, typy, které představují jeden prvek a starší verze <xref:System.Data.DataSet> typy.  
  
- Typy obsahu použít metodu schématu poskytovatele určeného `XmlSchemaProviderAttribute` atribut. Metoda nevrací `null`a <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> vlastnost pro atribut je ponecháno na jeho výchozí hodnotu `false`. Toto je nejběžnější použití `IXmlSerializable` typy.  
  
- Typy elementů se používají při `IXmlSerializable` typ musí řídit svůj vlastní název kořenového elementu. K označení typu jako typ elementu, nastavte <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> vlastnost <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atribut `true` nebo vrátí hodnotu null z metody zprostředkovatele schématu. Metoda poskytovatele schématu je volitelné pro typy prvků – můžete zadat hodnotu null namísto názvu metody v `XmlSchemaProviderAttribute`. Nicméně pokud `IsAny` je `true` a metody zprostředkovatele schématu není zadána, metoda musí vracet hodnotu null.  
  
- Starší verze <xref:System.Data.DataSet> typy jsou `IXmlSerializable` typy, které nejsou označené `XmlSchemaProviderAttribute` atribut. Místo toho spoléhají na <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> metody pro generování schématu. Tento model se používá pro `DataSet` typu a jeho typové datové sady odvozená třída v dřívějších verzích rozhraní .NET Framework, ale je zastaralá a je podporován pouze kvůli starším verzím. Nezadávejte Spolehněte se na tento model a vždycky používat `XmlSchemaProviderAttribute` do vaší `IXmlSerializable` typy.  
  
### <a name="ixmlserializable-content-types"></a>Typy rozhraní IXmlSerializable obsahu  
 Při serializaci datový člen typu, který implementuje `IXmlSerializable` a je typem obsahu jako dříve definovali, serializátoru, který zapíše element obálky pro člen a předejte jí ovládací prvek dat <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metody. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> Implementace může zapisovat všechny XML, včetně přidávání atributů do element obálky. Po `WriteXml` je Hotovo, serializátor zavře elementu.  
  
 Při deserializaci datový člen typu, který implementuje `IXmlSerializable` a obsahu zadat jako definovaný dříve, pozice deserializátor čtecí funkce XML na element obálky pro datový člen a předejte ovládací prvek <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> metody. Metoda musí číst celý prvek, včetně počáteční a koncovou značku. Ujistěte se, že vaše `ReadXml` kód zpracovává případ, ve kterém je prázdný element. Kromě toho vaše `ReadXml` implementace neměli byste tedy spoléhat na element obálky jmenován určitým způsobem. Je název zvoleném serializátoru, který se může lišit.  
  
 Je povoleno přiřadit `IXmlSerializable` typy obsahu polymorphically, třeba k datům členy typu <xref:System.Object>. Může se také atribut instance typu mít hodnotu null. A konečně, je možné použít `IXmlSerializable` typy s objektu grafu a zachovávání s rozlišením povolen a <xref:System.Runtime.Serialization.NetDataContractSerializer>. Všechny tyto funkce vyžadují serializátor WCF připojit určité atributy do prvku obálky ("nulový" a "type" v oboru názvů Instance schématu XML a "Id", "Ref", "Type" a "Sestavení" v oboru názvů specifických WCF).  
  
#### <a name="attributes-to-ignore-when-implementing-readxml"></a>Atributy se mají ignorovat při implementaci ReadXml  
 Před předáním řízení pro vaše `ReadXml` kód, deserializátor zkontroluje prvek XML, zjistí tyto speciální atributy XML a funguje na ně. Například, pokud je "nulový" `true`, deserializovat hodnotu null a `ReadXml` není volána. Pokud se zjistí polymorfismus obsah elementu se deserializovat jako by to byla jiného typu. Implementace polymorphically přiřazený typ `ReadXml` je volána. V každém případě `ReadXml` implementace by měl ignorovat tyto speciální atributy, protože deserializátor zpracovává.  
  
### <a name="schema-considerations-for-ixmlserializable-content-types"></a>Důležité informace o schématu pro typy obsahu IXmlSerializable  
 Při exportu schématu `IXmlSerializable` typ obsahu, je volána metoda poskytovatele schématu. <xref:System.Xml.Schema.XmlSchemaSet> Se předá metodě poskytovatele schématu. Metodu můžete přidat libovolné platné schéma k sadě schémat. Sada schéma obsahuje schéma, které je již znám v době, kdy dojde k exportu schématu. Když metoda poskytovatele schématu musí přidat položku do sady schémat, musíte určit Pokud <xref:System.Xml.Schema.XmlSchema> s odpovídající obor názvů již existuje v sadě. Pokud ano, metoda poskytovatele schématu musí přidat novou položku do stávající `XmlSchema`. V opačném případě se musí vytvořit nový `XmlSchema` instance. To je důležité, pokud pole `IXmlSerializable` typy se používají. Pokud máte například `IXmlSerializable` typ, který získá exportovat jako typ "A" v oboru názvů "B", je možné, že podle času je volána metoda poskytovatele schématu schématu nastavení už obsahuje schéma pro "B" typ "ArrayOfA".  
  
 Kromě přidání typů, který chcete <xref:System.Xml.Schema.XmlSchemaSet>, metoda poskytovatele schématu pro typy obsahu musí vrátit nenulovou hodnotu. Může vrátit <xref:System.Xml.XmlQualifiedName> , který určuje název typu schématu pro daný `IXmlSerializable` typu. Tento kvalifikovaný název slouží taky jako data názvem a oborem názvů pro typ kontraktu. Je povoleno návratový typ, který neexistuje v sadě hned po návratu metody zprostředkovatele schématu schémat. Ale očekává se, že v době všechny související typy jsou exportovány ( <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> metoda je volána pro všechny typy relevantní na <xref:System.Runtime.Serialization.XsdDataContractExporter> a <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> získat přístup k vlastnosti), typ existuje v sadě schémat. Přístup k `Schemas` vlastnost před všechny relevantní `Export` byly provedeny volání může vést <xref:System.Xml.Schema.XmlSchemaException>. Další informace o procesu exportu, naleznete v tématu [export schémat ze tříd](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
 Metoda poskytovatele schéma může taky vrátit <xref:System.Xml.Schema.XmlSchemaType> používat. Typ může nebo nemusí být anonymní. Pokud je anonymní, schéma pro `IXmlSerializable` typu se exportuje jako anonymního typu pokaždé, když `IXmlSerializable` typ používá jako datový člen. `IXmlSerializable` Typ stále má název kontraktu dat a obor názvů. (Tím se určuje, jak je popsáno v [názvy datových kontraktů](../../../../docs/framework/wcf/feature-details/data-contract-names.md) s tím rozdílem, že <xref:System.Runtime.Serialization.DataContractAttribute> atributu nelze použít k přizpůsobení názvu.) Pokud není anonymní, musí být jeden z typů v `XmlSchemaSet`. Tento případ je ekvivalentní k vrácení `XmlQualifiedName` typu.  
  
 Kromě toho se pro typ exportuje globální prvek prohlášení. Pokud typ nemá <xref:System.Xml.Serialization.XmlRootAttribute> atribut WebMethod, element má stejný název a obor názvů jako kontraktu dat a jeho vlastnost "nillable" má hodnotu true. Jedinou výjimkou je obor názvů schématu ("http://www.w3.org/2001/XMLSchema") – Pokud typ kontraktu dat je v tomto oboru názvů, odpovídající globální element je v oboru názvů prázdné, protože je zakázaná pro přidání nových elementů do oboru názvů schématu. Pokud má typ `XmlRootAttribute` atribut WebMethod, globální prvek prohlášení je exportovat pomocí následující: <xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A>, <xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> a <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A> vlastnosti. Výchozí hodnoty s `XmlRootAttribute` použity jsou názvem kontraktu dat, prázdný obor názvů a "nillable" je true.  
  
 Stejná pravidla deklarace globální element se vztahují na typy starší datová sada. Všimněte si, že `XmlRootAttribute` nemůže přepsat globální prvek prohlášení přidané prostřednictvím vlastního kódu buď přidat do `XmlSchemaSet` pomocí metody poskytovatele schématu nebo prostřednictvím `GetSchema` pro datovou sadu starší verze typů.  
  
### <a name="ixmlserializable-element-types"></a>Typy elementů IXmlSerializable  
 `IXmlSerializable` typy elementů mít buď `IsAny` vlastnost nastavena na hodnotu `true` nebo jejich schématu poskytovatele metoda vrátit `null`.  
  
 Serializace a deserializace typ elementu je velmi podobná serializace a deserializace typu obsahu. Existují však několik důležitých rozdílů:  
  
- `WriteXml` Implementace má napsat přesně jeden element (který samozřejmě může obsahovat více podřízených prvků). To by neměl být zápis atributů mimo tento jeden element více na stejné úrovni elementy nebo smíšený obsah. Element může být prázdný.  
  
- `ReadXml` Implementace by neměla číst element obálky. Očekává se číst jeden element, který `WriteXml` vytvoří.  
  
- Při serializaci typ elementu pravidelně (například jako datový člen v kontraktu dat), serializátoru, který vypíše element obálky, a před voláním `WriteXml`, stejně jako u typů obsahu. Ale při serializaci typ elementu na nejvyšší úrovni, serializátoru, který je výstupem však nejsou obvykle element obálky, a po elementu, který `WriteXml` zapíše název kořenového adresáře a obor názvů byly explicitně určena při vytváření serializátoru v `DataContractSerializer` nebo `NetDataContractSerializer` konstruktory. Další informace najdete v tématu [serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
- Při serializaci typ elementu na nejvyšší úrovni bez zadání kořenový název a obor názvů v době konstrukce <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> a <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> v podstatě nic nedělá a <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> volání `WriteXml`. V tomto režimu serializovaného objektu nemůže mít hodnotu null a nemůže být přiřazen polymorphically. Navíc nelze povolit zachování graf objektu a `NetDataContractSerializer` nelze použít.  
  
- Při deserializaci typ elementu na nejvyšší úrovni bez zadání kořenový název a obor názvů v době konstrukce <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> vrátí `true` Pokud nemůže najít začátek libovolný element. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> s `verifyObjectName` parametr nastaven na `true` se chová stejně jako `IsStartObject` před skutečně čtení objektu. `ReadObject` ovládací prvek pak předá `ReadXml` metody.  
  
 Schéma exportovat pro typy prvků je stejné jako v případě `XmlElement` zadejte, jak je popsáno v předchozí části, s tím rozdílem, že metoda poskytovatele schématu můžete přidat žádné další schéma, aby <xref:System.Xml.Schema.XmlSchemaSet> stejně jako u typů obsahu. Použití `XmlRootAttribute` atribut s typy prvků není povoleno a globální prvek prohlášení jsou emitovány nikdy pro tyto typy.  
  
### <a name="differences-from-the-xmlserializer"></a>Rozdíl oproti třídy XmlSerializer  
 `IXmlSerializable` Rozhraní a `XmlSchemaProviderAttribute` a `XmlRootAttribute` atributy také rozumí <xref:System.Xml.Serialization.XmlSerializer> . Existují však určité rozdíly v tom, jak jsou považovány v datovém modelu smlouvy. Důležité rozdíly jsou shrnuté v následujících tématech:  
  
- Metoda poskytovatele schématu musí být veřejné má být použitelná ve `XmlSerializer`, ale nemusí být veřejné být použitelné v datovém modelu kontraktu.  
  
- Při volání metody zprostředkovatele schématu `IsAny` má hodnotu true v datovém modelu smlouvy, ale ne s `XmlSerializer`.  
  
- Když `XmlRootAttribute` atribut není k dispozici pro obsah nebo starší datová sada typů, `XmlSerializer` exportuje globální prvek prohlášení v oboru názvů prázdné. V datovém modelu smlouvy oboru názvů použitého je obvykle obor názvů kontraktu dat jak je popsáno výše.  
  
 Mějte na paměti tyto rozdíly při vytváření typů, které se používají u obou technologií serializace.  
  
### <a name="importing-ixmlserializable-schema"></a>Import schématu rozhraní IXmlSerializable  
 Při importu schématu generovaném z `IXmlSerializable` typy, existuje několik možností:  
  
- Generované schéma může být schématu platný datový kontrakt, jak je popsáno v [schéma kontraktů dat – referenční informace](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). V tomto případě obvyklým způsobem můžete importovat schéma a typy kontraktů běžných dat jsou generovány.  
  
- Generované schéma nemusí být platný datový kontrakt schéma. Například metodu schématu poskytovatele může vygenerovat schéma, které zahrnuje atributy XML, které nejsou podporovány v datovém modelu kontraktu. V takovém případě můžete importovat schéma jako `IXmlSerializable` typy. Tento režim importu se nenachází na ve výchozím nastavení lze snadno ji však povolit – například s `/importXmlTypes` přepínač příkazového řádku [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). To je podrobně popsáno [import schématu pro generování třídy](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md). Všimněte si, že musíte pracovat přímo s XML pro typ instance. Mohou také zvážit použití jiné technologie serializace, který podporuje používání nástroje většímu počtu schématu – naleznete v tématu o používání `XmlSerializer`.  
  
- Můžete chtít znovu použít stávající `IXmlSerializable` typy v proxy namísto generování nové. V takovém případě funkce odkazované typy popsaná v import schématu pro téma generovat typy lze označující typ, který chcete znovu použít. To odpovídá pomocí `/reference` zapnout svcutil.exe, který určuje sestavení, který obsahuje typy pro opětovné použití.  
  
## <a name="representing-arbitrary-xml-in-data-contracts"></a>Představuje libovolný dokument XML v kontraktech dat  
 `XmlElement`, Pole `XmlNode` a `IXmlSerializable` typy umožňují vložit libovolný dokument XML do datového modelu v kontraktu. `DataContractSerializer` a `NetDataContractSerializer` předat obsahu k zapisovací modul XML tohoto XML kódu používá, bez zásahů do procesu. Uživatelé vytvářející obsah XML však může vynutit určitá omezení na XML, které zapisují. Konkrétně tady jsou některé důležité příklady:  
  
- Zapisovače XML obvykle neumožňují deklarace dokumentu XML (například \<? xml verze = "1.0'? >) v průběhu psaní jiného dokumentu. Nelze provést úplné dokumentu XML a serializaci jako `Array` z `XmlNode` datový člen. K tomuto účelu musí buď pruhu deklaraci dokumentu nebo použijte vlastní schéma kódování který ho zastupuje.  
  
- Všechny zapisovače XML zadat s použitím technologie WCF odmítnout pokyny pro zpracování XML (\<? … ? >) a dokumentu definice typů (\<! … >), protože nejsou povoleny v zprávy protokolu SOAP. Znovu můžete použít vlastní kódovací mechanismus jsme toto omezení. Pokud je nutné zahrnout v výsledný soubor XML, můžete napsat vlastní kodér, který používá zapisovače XML, které je podporují.  
  
- Při implementaci `WriteXml`, vyhněte se volání <xref:System.Xml.XmlWriter.WriteRaw%2A> metoda zapisovače XML. WCF využívá širokou škálu kódování XML (včetně binární soubor), je velmi obtížné nebo nemožné používat `WriteRaw` tak, že výsledek je použitelná v jakémkoli kódování.  
  
- Při implementaci `WriteXml`, vyhněte se použití <xref:System.Xml.XmlWriter.WriteEntityRef%2A> a <xref:System.Xml.XmlWriter.WriteNmToken%2A> metody, které nejsou podporovány na zapisovače XML zadat s použitím technologie WCF.  
  
## <a name="using-dataset-typed-dataset-and-datatable"></a>Pomocí datové sady, typový DataSet a DataTable  
 Pomocí těchto typů se plně podporuje v datovém modelu kontraktu. Při použití těchto typů, zvažte následující body:  
  
- Schéma pro tyto typy (zejména <xref:System.Data.DataSet> a jeho typu odvozené třídy) možná vzájemná spolupráce s některé platformy bez WCF, nebo může mít za následek nízký použitelnost při použití s těmito platformami. Kromě toho používání `DataSet` typu může mít vliv na výkon. Nakonec ho může to ztížit za vás na verzi vaší aplikace v budoucnu. Zvažte použití explicitně definované datové typy kontraktů místo `DataSet` typy ve vašich smlouvách.  
  
- Při importu `DataSet` nebo `DataTable` schéma, je důležité, abyste tyto typy odkazů. Pomocí nástroje Svcutil.exe příkazového řádku, můžete to provést předáním názvu sestavení System.Data.dll `/reference` přepnout. Pokud importujete schéma typové datové sady, musí odkazovat typové datové sady typu. Pomocí Svcutil.exe, předat umístění sestavení typové datové sady, které chcete `/reference` přepnout. Další informace o odkazování na typy, najdete v článku [import schématu pro generování třídy](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 Podpora pro typové datové sady v datovém modelu smlouvy je omezená. Typové datové sady lze serializovat a deserializovat a můžete exportovat jejich schématu. Ale kontraktu dat. není schopna generovat nový import schématu zadané typy datové sady ze schématu, jako je jenom znovu použít existující. Může odkazovat na existující typové datové sady s použitím `/r` zapnout Svcutil.exe. Při pokusu o použití Svcutil.exe bez `/r` přepněte se na službu, která používá typové datové sady, alternativní serializátor (objekt XmlSerializer) je automaticky vybrána. Pokud musíte použít objektu DataContractSerializer a musí generovat datové sady ze schématu, můžete použít následující postup: generování typů typové datové sady (s použitím nástroje Xsd.exe s `/d` přepnout na službu), zkompilujte typy a pak přejděte na jejich použití `/r` zapnout Svcutil.exe.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.IXmlSerializable>
- [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Typy podporované serializátorem kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
