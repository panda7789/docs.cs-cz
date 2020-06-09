---
title: Typy XML a ADO.NET v kontraktech dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2ce8461-3c15-4c41-8c81-1cb78f5b59a6
ms.openlocfilehash: 975d4f4f37bbbd895cab4e87686f15017e90f382
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600072"
---
# <a name="xml-and-adonet-types-in-data-contracts"></a>Typy XML a ADO.NET v kontraktech dat
Model kontraktu dat Windows Communication Foundation (WCF) podporuje určité typy, které přímo reprezentují XML. Pokud jsou tyto typy serializovány do XML, serializátor zapisuje obsah XML těchto typů bez dalšího zpracování. Podporované typy jsou <xref:System.Xml.XmlElement> , pole <xref:System.Xml.XmlNode> (ale ne `XmlNode` samotného typu) a také typy, které implementují <xref:System.Xml.Serialization.IXmlSerializable> . <xref:System.Data.DataSet>Typ a a <xref:System.Data.DataTable> také typové datové sady jsou běžně používány při programování databáze. Tyto typy implementují `IXmlSerializable` rozhraní a jsou proto serializovatelné v modelu kontraktu dat. Některé zvláštní okolnosti pro tyto typy jsou uvedené na konci tohoto tématu.  
  
## <a name="xml-types"></a>Typy XML  
  
### <a name="xml-element"></a>XML – element  
 `XmlElement`Typ je serializován pomocí jeho obsahu XML. Například pomocí následujícího typu.  
  
 [!code-csharp[DataContractAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#4)]
 [!code-vb[DataContractAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#4)]  
  
 To je serializováno do XML následujícím způsobem:  
  
```xml  
<MyDataContract xmlns="http://schemas.contoso.com">  
    <myDataMember>  
        <myElement xmlns="" myAttribute="myValue">  
            myContents  
        </myElement>  
    </myDataMember>  
</MyDataContract>  
```  
  
 Všimněte si, že prvek datového člena obálky `<myDataMember>` je stále přítomen. Neexistuje žádný způsob, jak tento prvek odebrat v modelu kontraktu dat. Serializátory, které zpracovávají tento model ( <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.NetDataContractSerializer> ), mohou do tohoto prvku obálky generovat speciální atributy. Tyto atributy zahrnují standardní atribut instance schématu XML "Nil" (povoluje se `XmlElement` `null` ) a atribut "Type" (umožňující `XmlElement` použití polymorfní). Následující atributy XML jsou také specifické pro WCF: "ID", "ref", "Type" a "Assembly". Tyto atributy mohou být vygenerovány pro podporu pomocí `XmlElement` s povoleným režimem uchování grafu objektů nebo s <xref:System.Runtime.Serialization.NetDataContractSerializer> . (Další informace o režimu uchování grafu objektů naleznete v tématu [serializace a deserializace](serialization-and-deserialization.md).)  
  
 Pole nebo kolekce `XmlElement` jsou povoleny a jsou zpracovávány jako jiné pole nebo kolekce. To znamená, že je k dispozici element obálky pro celou kolekci a samostatný prvek obálky (podobný `<myDataMember>` v předchozím příkladu) pro každý `XmlElement` v poli.  
  
 Při deserializaci `XmlElement` vytvoří deserializátor z příchozího XML. Deserializace poskytne platnou nadřazenou položku <xref:System.Xml.XmlDocument> .  
  
 Ujistěte se, že fragment XML, který je deserializován na, `XmlElement` definuje všechny předpony, které používá a nespoléhá na jakékoli definice předpony z nadřazených prvků. Jedná se o problém pouze v případě, že používáte `DataContractSerializer` pro přístup k XML z jiného zdroje (nejedná se o `DataContractSerializer` ).  
  
 Při použití s `DataContractSerializer` , `XmlElement` může být přiřazena polymorfní, ale pouze pro datový člen typu <xref:System.Object> . I když to implementuje <xref:System.Collections.IEnumerable> , `XmlElement` nelze použít jako typ kolekce a nelze jej přiřadit <xref:System.Collections.IEnumerable> datovému členu. Stejně jako u všech polymorfních přiřazení `DataContractSerializer` emituje název kontraktu dat ve výsledném souboru XML – v tomto případě je to "XmlElement" v http://schemas.datacontract.org/2004/07/System.Xml oboru názvů "".  
  
 S `NetDataContractSerializer` , je podporováno jakékoli platné polymorfní přiřazení `XmlElement` (do `Object` nebo `IEnumerable` ).  
  
 Nepokoušejte se použít žádný ze serializátorů s typy odvozenými z, bez `XmlElement` ohledu na to, zda jsou přiřazeny polymorfní nebo ne.  
  
### <a name="array-of-xmlnode"></a>Pole XmlNode  
 Použití polí <xref:System.Xml.XmlNode> je velmi podobné použití `XmlElement` . Použití polí z `XmlNode` poskytuje větší flexibilitu než použití `XmlElement` . Do prvku obtékání datového člena můžete napsat více prvků. Můžete také vložit obsah jiný než prvky uvnitř elementu obtékání datového členu, jako jsou komentáře XML. Nakonec můžete vložit atributy do prvku členu data zalamování. To lze dosáhnout naplněním pole `XmlNode` se specifickými odvozenými třídami `XmlNode` , jako je <xref:System.Xml.XmlAttribute> například `XmlElement` nebo <xref:System.Xml.XmlComment> . Například pomocí následujícího typu.  
  
 [!code-csharp[DataContractAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#5)]
 [!code-vb[DataContractAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#5)]  
  
 Při serializaci je výsledný kód XML podobný následujícímu kódu.  
  
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
  
 Všimněte si, že prvek obálky datového člena `<myDataMember>` obsahuje atribut, komentář a dva prvky. Jedná se o čtyři `XmlNode` instance, které byly serializovány.  
  
 Pole `XmlNode` , jehož výsledkem je neplatný kód XML, nelze serializovat. Například pole dvou `XmlNode` instancí, kde je první z nich `XmlElement` , a druhý je <xref:System.Xml.XmlAttribute> neplatný, protože tato sekvence neodpovídá žádné platné instanci XML (k dispozici není místo pro připojení atributu).  
  
 Při deserializaci pole `XmlNode` uzlů se vytvoří uzly a naplní se informace z příchozího XML. Deserializace poskytne platnou nadřazenou položku <xref:System.Xml.XmlDocument> . Všechny uzly jsou deserializovány, včetně všech atributů na prvku souhrnný datový člen, ale s výjimkou atributů, které jsou umístěny v rámci služby WCF serializátory (například atributy používané pro indikaci polymorfního přiřazení). Upozornění na definování všech předpon oboru názvů v fragmentu XML se vztahuje na deserializaci polí `XmlNode` stejně jako na deserializaci `XmlElement` .  
  
 Při použití serializátorů se zapnutým uchováváním grafu objektů je rovnost objektů zachovaná pouze na úrovni `XmlNode` polí, nikoli v jednotlivých `XmlNode` instancích.  
  
 Nepokoušejte se serializovat pole, `XmlNode` kde jeden nebo více uzlů je nastaveno na `null` . Je povoleno, aby celý člen pole byl `null` , ale ne pro všechny uživatele `XmlNode` obsažené v poli. Pokud je celý člen pole null, prvek datového členu obálky obsahuje speciální atribut, který označuje, že je null. Při deserializaci se celý člen pole také stal hodnotou null.  
  
 `XmlNode`Serializátor je speciálně ošetřená pouze regulárními poli. Datové členy deklarované jako jiné typy kolekce, které obsahují `XmlNode` nebo datové členy deklarované jako pole typů odvozených z `XmlNode` , nejsou zpracovány speciálně. Proto jsou obvykle neserializovatelné, pokud také nesplňují jedno z dalších kritérií pro serializaci.  
  
 Pole nebo kolekce polí pro `XmlNode` jsou povoleny. K dispozici je prvek obálky pro celou kolekci a samostatný prvek obálky (podobně jako `<myDataMember>` v předchozím příkladu) pro každé pole `XmlNode` ve vnějším poli nebo kolekci.  
  
 Naplnění datového člena typu <xref:System.Array> `Object` nebo `Array` `IEnumerable` s `XmlNode` instancemi nevede k tomu, že datový člen bude považován za `Array` `XmlNode` instance. Každý člen pole je serializován samostatně.  
  
 Při použití s `DataContractSerializer` polem lze s poli `XmlNode` přiřadit polymorfní, ale pouze pro datový člen typu `Object` . I když to implementuje `IEnumerable` , pole `XmlNode` nemůže být použito jako typ kolekce a musí být přiřazeno `IEnumerable` datovému členu. Stejně jako u všech polymorfních přiřazení `DataContractSerializer` vygeneruje název kontraktu dat ve výsledném souboru XML – v tomto případě je to "ArrayOfXmlNode" v http://schemas.datacontract.org/2004/07/System.Xml oboru názvů "". Při použití s `NetDataContractSerializer` , je podporováno jakékoli platné přiřazení `XmlNode` pole.  
  
### <a name="schema-considerations"></a>Otázky schématu  
 Podrobnosti o mapování schématu typů XML najdete v tématu Referenční informace o [schématu kontraktu dat](data-contract-schema-reference.md). V této části najdete souhrn důležitých bodů.  
  
 Datový člen typu `XmlElement` je namapován na element definovaný pomocí následujícího anonymního typu.  
  
```xml  
<xsd:complexType>  
   <xsd:sequence>  
      <xsd:any minOccurs="0" processContents="lax" />  
   </xsd:sequence>  
</xsd:complexType>  
```  
  
 Datový člen typu pole `XmlNode` je namapován na element definovaný pomocí následujícího anonymního typu.  
  
```xml  
<xsd:complexType mixed="true">  
   <xsd:sequence>  
      <xsd:any minOccurs="0" maxOccurs="unbounded" processContents="lax" />  
   </xsd:sequence>  
   <xsd:anyAttribute/>  
</xsd:complexType>  
```  
  
## <a name="types-implementing-the-ixmlserializable-interface"></a>Typy implementující rozhraní IXmlSerializable  
 Typy, které implementují `IXmlSerializable` rozhraní, jsou plně podporovány rozhraním `DataContractSerializer` . <xref:System.Xml.Serialization.XmlSchemaProviderAttribute>Atribut by měl být vždy použit pro tyto typy pro kontrolu jejich schématu.  
  
 Existují tři různé typy, které implementují `IXmlSerializable` : typy, které představují libovolný obsah, typy, které představují jeden element a starší <xref:System.Data.DataSet> typy.  
  
- Typy obsahu používají metodu poskytovatele schématu určenou `XmlSchemaProviderAttribute` atributem. Metoda nevrací hodnotu `null` a <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> vlastnost na atributu je ponechána na výchozí hodnotě `false` . Toto je nejběžnější využití `IXmlSerializable` typů.  
  
- Typy prvků se používají, když `IXmlSerializable` typ musí řídit svůj vlastní název kořenového elementu. Chcete-li označit typ jako typ prvku, buď nastavte <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> vlastnost u <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atributu na `true` hodnotu nebo z metody poskytovatele schématu vraťte hodnotu null. Použití metody poskytovatele schématu je pro typy prvků nepovinné – místo názvu metody v zadejte hodnotu null `XmlSchemaProviderAttribute` . Nicméně pokud `IsAny` je `true` a je určena metoda poskytovatele schématu, metoda musí vracet hodnotu null.  
  
- Zastaralé <xref:System.Data.DataSet> typy jsou `IXmlSerializable` typy, které nejsou označeny `XmlSchemaProviderAttribute` atributem. Místo toho spoléhají na <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> metodu generování schématu. Tento model se používá pro `DataSet` typ a jeho typová datová sada je odvozena od třídy v dřívějších verzích .NET Framework, ale je nyní zastaralá a je podporována pouze z dřívějších verzí. Nespoléhejte na tento model a vždy použít `XmlSchemaProviderAttribute` pro vaše `IXmlSerializable` typy.  
  
### <a name="ixmlserializable-content-types"></a>Typy obsahu IXmlSerializable  
 Při serializaci datového členu typu, který implementuje `IXmlSerializable` a je typ obsahu definovaný dříve, serializátor zapíše prvek obálky pro datový člen a předá řízení <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metodě. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>Implementace může zapisovat libovolné XML, včetně přidání atributů do prvku obálky. Po `WriteXml` dokončení se serializátor uzavře s prvkem.  
  
 Při deserializaci datového členu typu, který implementuje `IXmlSerializable` a je typ obsahu tak, jak byl definován dříve, odregistruje Nástroj pro čtení XML v prvku obálky pro datový člen a předá řízení <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> metodě. Metoda musí číst celý element, včetně počátečních a koncových značek. Ujistěte se, že váš `ReadXml` kód zpracovává případ, kde je element prázdný. Navíc by vaše `ReadXml` implementace neměla spoléhat na prvek obálky s názvem, který je pojmenován určitým způsobem. Název je zvolen serializátorem se může lišit.  
  
 Je povoleno přiřazovat `IXmlSerializable` typy obsahu polymorfní, například datovým členům typu <xref:System.Object> . Je také povoleno, aby instance typu měly hodnotu null. Nakonec je možné použít `IXmlSerializable` typy s povolenou možností zachování grafu objektů a s <xref:System.Runtime.Serialization.NetDataContractSerializer> . Všechny tyto funkce vyžadují serializátor WCF k připojení určitých atributů k elementu obálky ("Nil" a "Type" v oboru názvů instance schématu XML a "ID", "ref", "Type" a "Assembly" v oboru názvů specifického pro WCF).  
  
#### <a name="attributes-to-ignore-when-implementing-readxml"></a>Atributy, které se mají ignorovat při implementaci ReadXml  
 Před předáním řízení vašemu `ReadXml` kódu deserializátor prověřuje XML element, detekuje tyto speciální atributy XML a na nich funguje. Například pokud je "Nil" `true` , hodnota null je deserializována a není `ReadXml` volána. Pokud je zjištěn polymorfismu, obsah elementu je deserializován, jako by byl jiný typ. Je volána implementace polymorfního přiřazeného typu `ReadXml` . V každém případě `ReadXml` by implementace měla ignorovat tyto speciální atributy, protože jsou zpracovávány deserializací.  
  
### <a name="schema-considerations-for-ixmlserializable-content-types"></a>Otázky schématu pro typy obsahu IXmlSerializable  
 Při exportování schématu `IXmlSerializable` typu obsahu je volána metoda poskytovatele schématu. <xref:System.Xml.Schema.XmlSchemaSet>Metoda je předána metodě poskytovatele schématu. Metoda může do sady schémat přidat libovolné platné schéma. Sada schémat obsahuje schéma, které je již známo v době, kdy dojde k exportu schématu. Pokud metoda poskytovatele schématu musí do sady schémat přidat položku, musí určit, zda objekt <xref:System.Xml.Schema.XmlSchema> s odpovídajícím oborem názvů již v sadě existuje. V takovém případě metoda poskytovatele schématu musí přidat novou položku do existující `XmlSchema` . V opačném případě musí vytvořit novou `XmlSchema` instanci. To je důležité `IXmlSerializable` , pokud jsou používána pole typů. Například pokud máte `IXmlSerializable` typ, který bude exportován jako typ "A" v oboru názvů "B", je možné, že v době, kdy se metoda poskytovatele schématu nazývá sada schémat, již obsahuje schéma pro "b" pro uchování typu "ArrayOfA".  
  
 Kromě přidávání typů do <xref:System.Xml.Schema.XmlSchemaSet> metody musí metoda poskytovatele schématu pro typy obsahu vracet hodnotu, která není null. Může vrátit <xref:System.Xml.XmlQualifiedName> , který určuje název typu schématu, který má být použit pro daný `IXmlSerializable` typ. Tento kvalifikovaný název slouží také jako název kontraktu dat a obor názvů pro daný typ. Je povoleno vrátit typ, který neexistuje v sadě schémat ihned při návratu metody poskytovatele schématu. Očekává se však, že v době, kdy jsou exportovány všechny související typy ( <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> Metoda je volána pro všechny relevantní typy v <xref:System.Runtime.Serialization.XsdDataContractExporter> a <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> je k dispozici vlastnost), typ existuje v sadě schémat. Přístup k `Schemas` vlastnosti před provedením všech relevantních `Export` volání může mít za následek <xref:System.Xml.Schema.XmlSchemaException> . Další informace o procesu exportu naleznete v tématu [Export schémat ze tříd](exporting-schemas-from-classes.md).  
  
 Metoda poskytovatele schématu může také vrátit hodnotu, <xref:System.Xml.Schema.XmlSchemaType> která má být použita. Typ může nebo nemusí být anonymní. Pokud je anonymní, schéma pro `IXmlSerializable` typ je exportováno jako anonymní typ pokaždé, když `IXmlSerializable` je typ použit jako datový člen. `IXmlSerializable`Typ má stále název kontraktu dat a obor názvů. (Tato vlastnost je určena jak je popsáno v tématu [názvy kontraktů dat](data-contract-names.md) s výjimkou toho, že <xref:System.Runtime.Serialization.DataContractAttribute> atribut nelze použít k přizpůsobení názvu.) Pokud není anonymní, musí být jedním z typů v `XmlSchemaSet` . Tento případ je ekvivalentem vrácení `XmlQualifiedName` typu.  
  
 Kromě toho je pro daný typ exportována globální deklarace elementu. Pokud pro daný typ není <xref:System.Xml.Serialization.XmlRootAttribute> použit atribut, má element stejný název a obor názvů jako kontrakt dat a jeho vlastnost "nillable" má hodnotu true. Jedinou výjimkou je obor názvů schématu (" http://www.w3.org/2001/XMLSchema ") – Pokud je kontrakt dat typu v tomto oboru názvů, odpovídající globální element je v prázdném oboru názvů, protože je zakázáno přidávat nové prvky do oboru názvů schématu. `XmlRootAttribute`Je-li pro typ použit atribut, je deklarace globálního prvku exportována pomocí následujících <xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A> vlastností: <xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> a <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A> . Výchozí hodnoty jsou nastavené `XmlRootAttribute` na název kontraktu dat, prázdný obor názvů a "nillable".  
  
 Stejná pravidla deklarace globálních prvků se vztahují na typy datových sad typu Legacy. Všimněte si, že `XmlRootAttribute` deklarace globálních prvků nelze přepsat přidáním vlastního kódu, buď přidaných na `XmlSchemaSet` metodu pomocí metody poskytovatele schématu nebo prostřednictvím `GetSchema` pro typy starších datových sad.  
  
### <a name="ixmlserializable-element-types"></a>IXmlSerializable – typy prvků  
 `IXmlSerializable`typy prvků mají buď `IsAny` vlastnost nastavenou na, `true` nebo mají návrat metody poskytovatele schématu `null` .  
  
 Serializace a deserializace typu elementu je velmi podobná serializaci a deserializaci typu obsahu. Existují však některé důležité rozdíly:  
  
- `WriteXml`Implementace se očekává, že zapíše přesně jeden prvek (což může samozřejmě obsahovat více podřízených elementů). Neměl by zapisovat atributy mimo tento jediný element, více elementů na stejné úrovni nebo smíšený obsah. Element může být prázdný.  
  
- `ReadXml`Implementace by neměla číst prvek obálky. Očekává se, že si přečtete jeden prvek, který `WriteXml` vytvoří.  
  
- Při pravidelném serializaci typu elementu (například jako datový člen v kontraktu dat) vytvoří serializátor výstup prvku obálky před voláním `WriteXml` jako s typy obsahu. Při serializaci typu elementu na nejvyšší úrovni však serializátor obvykle nevytváří Obálkový prvek vůbec kolem elementu, který `WriteXml` zapisuje, pokud kořenový název a obor názvů nebyl explicitně zadán při vytváření serializátoru v `DataContractSerializer` `NetDataContractSerializer` konstruktorech nebo. Další informace naleznete v tématu [serializace a deserializace](serialization-and-deserialization.md).  
  
- Při serializaci typu prvku na nejvyšší úrovni bez zadání kořenového názvu a oboru názvů v době konstrukce <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> a <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> v podstatě neprovede žádné <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> volání `WriteXml` . V tomto režimu nemůže být serializovaný objekt null a nelze jej polymorfním přiřadit. Také zachování grafu objektů nelze povolit a nelze jej `NetDataContractSerializer` použít.  
  
- Při deserializaci typu elementu na nejvyšší úrovni bez zadání kořenového názvu a oboru názvů v době konstrukce, <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> vrátí, `true` Pokud může najít začátek libovolného elementu. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A>se `verifyObjectName` sadou parametrů se `true` chová stejně jako `IsStartObject` před skutečným čtením objektu. `ReadObject`poté předává řízení `ReadXml` metodě.  
  
 Schéma exportované pro typy elementů je stejné jako pro typ, `XmlElement` jak je popsáno v předchozí části, s výjimkou, že metoda poskytovatele schématu může přidat jakékoli další schéma <xref:System.Xml.Schema.XmlSchemaSet> jako s typy obsahu. Použití `XmlRootAttribute` atributu s typy prvků není povoleno a deklarace globálních prvků nejsou pro tyto typy nikdy generovány.  
  
### <a name="differences-from-the-xmlserializer"></a>Rozdíly mezi objektem XmlSerializer  
 `IXmlSerializable`Rozhraní a `XmlSchemaProviderAttribute` `XmlRootAttribute` atributy a jsou také srozumitelné pomocí <xref:System.Xml.Serialization.XmlSerializer> . Existují však určité rozdíly v tom, jak jsou tyto aplikace zpracovány v modelu kontraktu dat. Důležité rozdíly jsou shrnuty v následujících:  
  
- Metoda poskytovatele schématu musí být veřejná, aby ji bylo možné použít v `XmlSerializer` , ale nemusí být veřejná, aby ji bylo možné použít v modelu kontraktu dat.  
  
- Metoda poskytovatele schématu je volána, když `IsAny` je hodnota true v modelu kontraktu dat, ale ne s `XmlSerializer` .  
  
- Pokud `XmlRootAttribute` atribut není k dispozici pro obsah nebo starší typy datových sad, `XmlSerializer` exportuje deklaraci globálního prvku v prázdném oboru názvů. V modelu kontraktu dat se používá obor názvů obvykle obor názvů kontraktu dat, jak je popsáno výše.  
  
 Pamatujte na tyto rozdíly při vytváření typů, které se používají v obou technologiích serializace.  
  
### <a name="importing-ixmlserializable-schema"></a>Importuje se schéma IXmlSerializable.  
 Při importu schématu vygenerovaného z `IXmlSerializable` typů existuje několik možností:  
  
- Vygenerované schéma může být platné schéma kontraktu dat, jak je popsáno v tématu [referenční informace schématu kontraktu dat](data-contract-schema-reference.md). V takovém případě se schéma dá importovat jako běžné a jsou vygenerované běžné typy kontraktů dat.  
  
- Vygenerované schéma nesmí být platným schématem kontraktu dat. Například metoda poskytovatele schématu může generovat schéma, které zahrnuje atributy XML, které nejsou podporovány v modelu kontraktu dat. V takovém případě můžete schéma importovat jako `IXmlSerializable` typy. Tento režim importu není ve výchozím nastavení zapnutý, ale dá se snadno povolit – například s `/importXmlTypes` přepínačem příkazového řádku, který se nachází v nástroji pro podporu [metadat ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Tato informace je podrobněji popsána v tématu [Import schématu pro generování tříd](importing-schema-to-generate-classes.md). Všimněte si, že je nutné pracovat přímo s XML pro vaše instance typu. Je také vhodné zvážit použití jiné technologie serializace, která podporuje širší škálu schématu – viz téma o použití `XmlSerializer` .  
  
- Můžete chtít znovu použít stávající `IXmlSerializable` typy na proxy místo generování nových. V tomto případě lze pomocí odkazovaného typu, který je popsán v tématu Import schématu pro generování typů, použít k označení typu pro opakované použití. To odpovídá použití `/reference` přepínače na Svcutil. exe, který určuje sestavení, které obsahuje typy pro opakované použití.  
  
## <a name="representing-arbitrary-xml-in-data-contracts"></a>Reprezentace libovolného XML v kontraktech dat  
 Pole `XmlElement` `XmlNode` a `IXmlSerializable` typy umožňují vložit libovolný kód XML do modelu kontraktu dat. `DataContractSerializer`A `NetDataContractSerializer` předá tento obsah XML zapisovači XML, který se používá, bez rušivého vlivu procesu. Zapisovače XML však může vyhovět určitým omezením v XML, která zapisuje. Konkrétně tady jsou některé důležité příklady:  
  
- Zapisovače XML obvykle nepovoluje deklaraci dokumentu XML (například \<?xml version=’1.0’ ?> ) v průběhu psaní jiného dokumentu. Nemůžete získat úplný dokument XML a serializovat ho jako `Array` `XmlNode` datový člen. Chcete-li to provést, musíte buď oddělit deklaraci dokumentu, nebo použít vlastní schéma kódování pro reprezentaci.  
  
- Všechny zapisovače XML dodávané pomocí WCF odmítnou instrukce pro zpracování XML ( \<? … ?> ) a definice typu dokumentu ( \<! … > ), protože nejsou ve zprávách SOAP povoleny. K tomuto omezení můžete využít vlastní mechanizmus kódování. Pokud je musíte zahrnout do výsledné XML, můžete napsat vlastní kodér, který používá zapisovače XML, které je podporují.  
  
- Při implementaci `WriteXml` , vyhněte se volání <xref:System.Xml.XmlWriter.WriteRaw%2A> metody do zapisovače XML. WCF používá nejrůznější kódování XML (včetně binárních), je velmi obtížné nebo nemožné použít `WriteRaw` tak, aby byl výsledek použitelný v jakémkoli kódování.  
  
- Při implementaci `WriteXml` , vyhněte se <xref:System.Xml.XmlWriter.WriteEntityRef%2A> použití <xref:System.Xml.XmlWriter.WriteNmToken%2A> metod a, které nejsou podporovány u zapisovačů XML dodaných pomocí WCF.  
  
## <a name="using-dataset-typed-dataset-and-datatable"></a>Použití datové sady, typované datové sady a DataTable  
 Použití těchto typů je plně podporováno v modelu kontraktu dat. Při použití těchto typů Vezměte v úvahu následující body:  
  
- Schéma pro tyto typy (zejména <xref:System.Data.DataSet> a jeho typové odvozené třídy) nemusí spolupracovat s některými platformami, které nepatří do WCF, nebo může při použití s těmito platformami způsobit špatnou použitelnost. Kromě toho může použití `DataSet` typu mít vliv na výkon. Nakonec může být obtížnější aplikaci v budoucnu napravit. Zvažte možnost použití explicitně definovaných typů kontraktů dat místo `DataSet` typů ve smlouvách.  
  
- Při importu `DataSet` nebo `DataTable` schématu je důležité odkázat na tyto typy. Pomocí nástroje příkazového řádku Svcutil. exe lze dosáhnout toho, že do přepínače předáte název sestavení System. data. dll `/reference` . Pokud importujete schéma typované datové sady, musíte odkazovat na typ typované datové sady. Pomocí Svcutil. exe předejte do přepínače umístění sestavení typové datové sady `/reference` . Další informace o odkazování typů naleznete v tématu [Import schématu pro generování tříd](importing-schema-to-generate-classes.md).  
  
 Podpora typových datových sad v modelu kontraktu dat je omezená. Typové datové sady lze serializovat a deserializovat a mohou exportovat své schéma. Import schématu kontraktu dat ale nemůže ze schématu generovat nové typy datových sad, protože můžou znovu použít jenom ty existující. Pomocí `/r` přepínače v Svcutil. exe můžete odkazovat na existující typovou datovou sadu. Pokud se pokusíte použít Svcutil. exe bez `/r` přepínače u služby, která používá typovou datovou sadu, je automaticky vybrán alternativní serializátor (XmlSerializer). Pokud je nutné použít DataContractSerializer a musí generovat datové sady ze schématu, můžete použít následující postup: vygenerujte typové typy datových sad (pomocí nástroje XSD. exe s `/d` přepínačem ve službě), zkompilujte typy a pak na ně nasměrujte pomocí `/r` přepínače v Svcutil. exe.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.IXmlSerializable>
- [Použití kontraktů dat](using-data-contracts.md)
- [Typy podporované serializátorem kontraktu dat](types-supported-by-the-data-contract-serializer.md)
