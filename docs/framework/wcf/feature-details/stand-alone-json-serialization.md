---
title: Samostatná serializace JSON pomocí DataContractJsonSerializer
ms.date: 03/30/2017
ms.assetid: 312bd7b2-1300-4b12-801e-ebe742bd2287
ms.openlocfilehash: 412da71617a8627c47e877a75770271d9a3cf180
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976077"
---
# <a name="stand-alone-json-serialization-using-datacontractjsonserializer"></a>Samostatná serializace JSON pomocí DataContractJsonSerializer

> [!NOTE]
> Tento článek se týká <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. Pro většinu scénářů, které zahrnují serializaci a deserializaci JSON, doporučujeme použít nástroje v [oboru názvů System. text. JSON](../../../standard/serialization/system-text-json-overview.md). 

JSON (JavaScript Object Notation) je formát dat, který je speciálně navržený tak, aby se používal v kódu JavaScriptu běžícím na webových stránkách v prohlížeči. Je to výchozí formát dat používaný službami ASP.NET AJAX vytvořenými v Windows Communication Foundation (WCF).

Tento formát lze použít také při vytváření služeb AJAX bez integrace s ASP.NET – v tomto případě je XML výchozí, ale může být zvolena hodnota JSON.

Nakonec, pokud požadujete podporu JSON, ale nevytváříte službu AJAX, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> umožňuje přímo serializovat objekty .NET do dat JSON a deserializovat taková data zpátky do instancí typů .NET. Popis toho, jak to provést, naleznete v tématu [How to: serializovat a deserializovat data JSON](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).

Při práci s JSON jsou podporovány stejné typy rozhraní .NET, s několika výjimkami, které jsou podporovány <xref:System.Runtime.Serialization.DataContractSerializer>. Seznam podporovaných typů najdete v tématu [typy podporované serializátorem kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). To zahrnuje většinu primitivních typů, většinu typů polí a kolekcí a také komplexní typy, které používají <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute>.

## <a name="mapping-net-types-to-json-types"></a>Mapování typů .NET na typy JSON

Následující tabulka ukazuje korespondenci mezi typy rozhraní .NET a typy JSON/JavaScript, pokud jsou mapovány postupy serializace a deserializace.

|Typy .NET|JSON/JavaScript|Poznámky|
|----------------|----------------------|-----------|
|Všechny číselné typy, například <xref:System.Int32>, <xref:System.Decimal> nebo <xref:System.Double>|Číslo|Speciální hodnoty jako `Double.NaN`, `Double.PositiveInfinity` a `Double.NegativeInfinity` nejsou podporovány a mají za následek neplatný formát JSON.|
|<xref:System.Enum>|Číslo|Viz část "výčty a JSON" dále v tomto tématu.|
|<xref:System.Boolean>|Boolean|--|
|<xref:System.String><xref:System.Char>|String|--|
|<xref:System.TimeSpan>, <xref:System.Guid><xref:System.Uri>|String|Formát těchto typů ve formátu JSON je stejný jako v jazyce XML (v podstatě se jedná o časový interval ve formátu ISO 8601 Duration, identifikátor GUID ve formátu "12345678-ABCD-ABCD-ABCD-1234567890AB" a identifikátor URI ve formě přirozeného řetězce, jako je například "http://www.example.com"). Podrobné informace najdete v tématu [referenční informace o schématu kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).|
|<xref:System.Xml.XmlQualifiedName>|String|Formát je "název: obor názvů" (cokoli před první dvojtečkou je název). Název nebo obor názvů může chybět. Pokud obor názvů neexistuje, může být dvojtečka také vynechána.|
|<xref:System.Array> typu <xref:System.Byte>|Pole čísel|Každé číslo představuje hodnotu jednoho bajtu.|
|<xref:System.DateTime>|DateTime nebo String|Viz data a časy a JSON později v tomto tématu.|
|<xref:System.DateTimeOffset>|Komplexní typ|Viz data a časy a JSON později v tomto tématu.|
|Typy XML a ADO.NET (<xref:System.Xml.XmlElement>,<br /><br /> <xref:System.Xml.Linq.XElement>. Pole <xref:System.Xml.XmlNode>,<br /><br /> <xref:System.Runtime.Serialization.ISerializable>,<br /><br /> <xref:System.Data.DataSet>).|String|Další informace najdete v části Typy XML a JSON tohoto tématu.|
|<xref:System.DBNull>|Prázdný komplexní typ|--|
|Kolekce, slovníky a pole|Skupin|Viz část kolekce, slovníky a pole tohoto tématu.|
|Komplexní typy (s použitým <xref:System.Runtime.Serialization.DataContractAttribute> nebo <xref:System.SerializableAttribute>)|Komplexní typ|Datové členy se stanou členy komplexního typu JavaScriptu.|
|Komplexní typy implementující rozhraní <xref:System.Runtime.Serialization.ISerializable>)|Komplexní typ|Stejné jako u jiných složitých typů, ale některé typy <xref:System.Runtime.Serialization.ISerializable> nejsou podporované – Podívejte se na část podpora ISerializable v části Rozšířené informace v tomto tématu.|
|hodnota `Null` pro jakýkoliv typ|Null|Typy s možnou hodnotou null jsou také podporovány a mapovány na formát JSON stejným způsobem jako typy bez hodnoty null.|

### <a name="enumerations-and-json"></a>Výčty a JSON

Hodnoty členů výčtu jsou považovány za čísla ve formátu JSON, což se liší od toho, jak se zpracovávají v kontraktech dat, kde jsou zahrnuty jako názvy členů. Další informace o zpracování kontraktu dat najdete v tématu [výčtové typy v kontraktech dat](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).

- Například pokud máte `public enum Color {red, green, blue, yellow, pink}`, serializace `yellow` vytvoří číslo 3, nikoli řetězec "Yellow".

- Všechny členy `enum` jsou serializovatelné. <xref:System.Runtime.Serialization.EnumMemberAttribute> a atributy <xref:System.NonSerializedAttribute> jsou při použití ignorovány.

- Je možné deserializovat neexistující `enum` hodnotu – například hodnotu 87 lze deserializovat do předchozího výčtu barev i v případě, že není definován žádný odpovídající název barvy.

- Příznaky `enum` nejsou speciální a jsou ošetřeny stejně jako všechny ostatní `enum`.

### <a name="datestimes-and-json"></a>Data a časy a JSON

Formát JSON přímo nepodporuje data a časy. Jsou však velmi často používány a ASP.NET AJAX poskytuje speciální podporu pro tyto typy. Pokud používáte proxy ASP.NET AJAX, typ <xref:System.DateTime> v rozhraní .NET plně odpovídá typu `DateTime` v JavaScriptu.

- Pokud nepoužíváte ASP.NET, je typ <xref:System.DateTime> reprezentován ve formátu JSON jako řetězec se speciálním formátem, který je popsán v části Rozšířené informace v tomto tématu.

- <xref:System.DateTimeOffset> je reprezentovaný ve formátu JSON jako komplexní typ: {"DateTime":d ateTime, "OffsetMinutes": offsetMinutes}. `offsetMinutes` člen je místní časový posun od střední hodnoty času (GMT), který se teď označuje jako koordinovaný světový čas (UTC), který je přidružený k umístění události zájmu. Člen `dateTime` představuje instanci v čase, kdy došlo k události zájmu (znovu se jedná o `DateTime` v JavaScriptu, když se ASP.NET AJAX používá a řetězec, pokud není). Při serializaci je člen `dateTime` vždy serializován v GMT. Takže pokud je to pro čas 3:00 až Praha, `dateTime` má časovou komponentu 8:00 AM a `offsetMinutes` je 300 (minus 300 minuty nebo 5 hodin od GMT).

  > [!NOTE]
  > objekty <xref:System.DateTime> a <xref:System.DateTimeOffset>, při serializaci do formátu JSON, zachovávají pouze informace na přesnost milisekund. Během serializace dojde ke ztrátě hodnot dílčích milisekund (mikro/nanosekunds).

### <a name="xml-types-and-json"></a>Typy XML a JSON

Typy XML se stávají řetězcem JSON.

- Například pokud datový člen "q" typu XElement obsahuje \<ABC/>, je JSON {"q": "\<ABC/>"}.

- Existují určitá zvláštní pravidla, která určují, jak je XML zabaleno. Další informace najdete v části Rozšířené informace dále v tomto tématu.

- Pokud používáte ASP.NET AJAX a nechcete používat řetězce v JavaScriptu, ale chcete místo toho použít XML DOM, nastavte vlastnost <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> na XML v <xref:System.ServiceModel.Web.WebGetAttribute> nebo vlastnost <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> na <xref:System.ServiceModel.Web.WebInvokeAttribute>XML.

### <a name="collections-dictionaries-and-arrays"></a>Kolekce, slovníky a pole

Všechny kolekce, slovníky a pole jsou ve formátu JSON vyjádřené jako pole.

- Jakékoli přizpůsobení, které používá <xref:System.Runtime.Serialization.CollectionDataContractAttribute>, je ignorováno v reprezentaci JSON.

- Slovníky nejsou způsobem, jak pracovat přímo s JSON. Řetězec\<slovníku, > objektů nemusí být ve službě WCF podporován stejným způsobem jako při práci s jinými technologiemi JSON. Například pokud je "ABC" mapován na "xyz" a "def", ve slovníku se namapuje na 42, reprezentace JSON není {"ABC": "xyz", "def": 42}, ale jedná se o [{"klíč": "ABC", "value": "xyz"}, {"Key": "def", "value": 42}] namísto.

- Pokud chcete pracovat s JSON přímo (dynamicky přistupovat k klíčům a hodnotám, aniž byste museli předem definovat pevný kontrakt), máte několik možností:

  - Zvažte použití ukázky [Neslabě typovaného serializace JSON (AJAX)](../../../../docs/framework/wcf/samples/weakly-typed-json-serialization-sample.md) .

  - Zvažte použití <xref:System.Runtime.Serialization.ISerializable> rozhraní a konstruktory deserializace – tyto dva mechanismy vám umožní přístup k párů klíč/hodnota JSON pro serializaci a deserializaci, ale nefungují v scénářích s částečnou důvěryhodností.

  - Zvažte práci s [mapováním mezi JSON a XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md) namísto použití serializátoru.

  - *Polymorfismus* v kontextu serializace odkazuje na schopnost serializovat odvozený typ, kde je očekáván jeho základní typ. Existují zvláštní pravidla specifická pro JSON při použití kolekcí polymorfní, kdy například přiřadíte kolekci k <xref:System.Object>. Tento problém je podrobněji popsán v části Rozšířené informace dále v tomto tématu.

## <a name="additional-details"></a>Další podrobnosti

### <a name="order-of-data-members"></a>Pořadí datových členů

Pořadí datových členů není při použití JSON důležité. Konkrétně i v případě, že je nastavena <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>, lze data JSON nadále deserializovat v libovolném pořadí.

### <a name="json-types"></a>Typy JSON

Typ JSON nemusí odpovídat předchozí tabulce v deserializaci. Například `Int` obvykle mapuje na číslo JSON, ale lze jej také úspěšně deserializovat z řetězce JSON, pokud tento řetězec obsahuje platné číslo. To znamená, že obě {"q": 42} a {"q": "42"} jsou platné, pokud je k dispozici datový člen `Int` s názvem "q".

### <a name="polymorphism"></a>Polymorfismus

Polymorfní serializace je tvořena možností serializace odvozeného typu, kde je očekáván jeho základní typ. To je podporováno pro serializaci JSON pomocí WCF srovnatelné se způsobem, jakým je podporována serializace XML. Například můžete serializovat `MyDerivedType`, kde je očekáváno `MyBaseType`, nebo serializovat `Int`, kde je `Object` očekáváno.

Při deserializaci odvozeného typu může dojít ke ztrátě informací o typu, pokud se očekává základní typ, pokud neprovádíte deserializaci komplexního typu. Například pokud je serializována <xref:System.Uri>, kde je očekáváno <xref:System.Object>, výsledkem je řetězec JSON. Pokud je tento řetězec následně deserializován zpět do <xref:System.Object>, bude vrácena <xref:System.String> .NET. Deserializátor neví, že řetězec byl zpočátku typu <xref:System.Uri>. Obecně platí, že při očekávání <xref:System.Object>všechny řetězce JSON jsou deserializovány jako řetězce .NET a všechna pole JSON používaná k serializaci kolekcí .NET, slovníky a pole jsou deserializovány jako rozhraní .NET <xref:System.Array> typu <xref:System.Object>, bez ohledu na to, co byl skutečný původní typ. Logická hodnota JSON se mapuje na <xref:System.Boolean>.NET. Pokud však očekává <xref:System.Object>, jsou deserializována čísla JSON buď jako rozhraní .NET <xref:System.Int32>, <xref:System.Decimal> nebo <xref:System.Double>, kde je nejvhodnější typ automaticky vybrán.

Při deserializaci do typu rozhraní <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> deserializace, jako by byl deklarovaný typ Object.

Při práci s vlastními základními a odvozenými typy pomocí <xref:System.Runtime.Serialization.KnownTypeAttribute>, je obvykle vyžadován <xref:System.ServiceModel.ServiceKnownTypeAttribute> nebo ekvivalentní mechanismus. Například pokud máte operaci, která má návratovou hodnotu `Animal` a ve skutečnosti vrátí instanci `Cat` (odvozenou z `Animal`), měli byste buď použít <xref:System.Runtime.Serialization.KnownTypeAttribute>, na `Animal` typ nebo <xref:System.ServiceModel.ServiceKnownTypeAttribute> na operaci a zadat typ `Cat` v těchto atributech. Další informace najdete v tématu [známé typy kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).

Podrobnosti o tom, jak polymorfní serializace funguje a diskuzi o některých omezeních, která musí být při použití dodržena, najdete v části Rozšířené informace dále v tomto tématu.

### <a name="versioning"></a>Správa verzí

Funkce pro správu verzí kontraktů dat, včetně rozhraní <xref:System.Runtime.Serialization.IExtensibleDataObject>, jsou plně podporované ve formátu JSON. Ve většině případů je také možné deserializovat typ v jednom formátu (například XML) a potom jej serializovat do jiného formátu (například JSON) a nadále uchovávat data v <xref:System.Runtime.Serialization.IExtensibleDataObject>. Další informace najdete v tématu [kontrakty dat kompatibilní s dopředné](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Mějte na paměti, že kód JSON je Neseřazený, takže dojde ke ztrátě informací o objednávkách. Kromě toho JSON nepodporuje více párů klíč/hodnota se stejným názvem klíče. Nakonec všechny operace na <xref:System.Runtime.Serialization.IExtensibleDataObject> jsou v podstatě polymorfní – to je jejich odvozený typ přiřazený <xref:System.Object>, základní typ pro všechny typy.

## <a name="json-in-urls"></a>JSON v adresách URL

Při použití koncových bodů ASP.NET AJAX s příkazem HTTP GET (pomocí atributu <xref:System.ServiceModel.Web.WebGetAttribute>) se příchozí parametry zobrazí v adrese URL namísto textu zprávy. JSON se podporuje i v adrese URL požadavku, takže pokud máte operaci, která přebírá `Int` s názvem "Number" a `Person` komplexního typu s názvem "p", adresa URL se může podobat následující adrese URL.

```html
http://example.com/myservice.svc/MyOperation?number=7&p={"name":"John","age":42}
```

Pokud ke volání služby používáte ovládací prvek Správce skriptů ASP.NET AJAX a proxy server, tato adresa URL se automaticky vygeneruje proxy serverem a nezobrazuje se. JSON se nedá použít v adresách URL v koncových bodech non-ASP.NET AJAX.

## <a name="advanced-information"></a>Rozšířené informace

### <a name="iserializable-support"></a>Podpora ISerializable

#### <a name="supported-and-unsupported-iserializable-types"></a>Podporované a nepodporované typy ISerializable

Obecně platí, že typy, které implementují rozhraní <xref:System.Runtime.Serialization.ISerializable>, jsou plně podporovány při serializaci nebo deserializaci JSON. Nicméně některé z těchto typů (včetně některých typů .NET Framework) jsou implementovány takovým způsobem, že aspekty serializace specifické pro JSON způsobují, že nejsou správně deserializovat:

- V <xref:System.Runtime.Serialization.ISerializable>není typ jednotlivých datových členů nikdy znám. To vede k polymorfní situaci, která je podobná deserializaci typů do objektu. Jak bylo zmíněno dříve, může to vést ke ztrátě informací o typu ve formátu JSON. Například typ, který serializace `enum` v jeho <xref:System.Runtime.Serialization.ISerializable> implementaci a pokusí se o deserializaci přímo do `enum` (bez správných přetypování),, protože `enum` je serializovaná pomocí čísel v JSON a číslech JSON, které jsou deserializovány do předdefinovaných číselných typů .NET (Int32, Decimal nebo Double). Fakt, že číslo použité jako hodnota `enum` je ztraceno.

- Typ <xref:System.Runtime.Serialization.ISerializable>, který závisí na určitém pořadí deserializace v konstruktoru deserializace, může také dojít k chybě při deserializaci některých dat JSON, protože většina serializátorů JSON nezaručuje konkrétní pořadí.

#### <a name="factory-types"></a>Typy továrny

I když je rozhraní <xref:System.Runtime.Serialization.IObjectReference> podporováno ve formátu JSON obecně, všechny typy, které vyžadují funkci "typ objektu pro vytváření" (vracející instance jiného typu z <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%28System.Runtime.Serialization.StreamingContext%29>, než je typ, který implementuje rozhraní), nejsou podporovány.

### <a name="datetime-wire-format"></a>Formát vedení data a času

<xref:System.DateTime> hodnoty se zobrazí jako řetězce JSON ve formátu "/Date (700000 + 0500)/", kde první číslo (700000 v zadaném příkladu) je počet milisekund v časovém pásmu GMT (běžný (neletní) čas od půlnoci 1. ledna 1970. Počet může být záporný, aby představoval předchozí časy. Část, která se skládá z "+ 0500" v příkladu je volitelná a označuje, že čas je <xref:System.DateTimeKind.Local> typ – to znamená, že by měl být převeden na místní časové pásmo Při deserializaci. Pokud chybí, čas je deserializován jako <xref:System.DateTimeKind.Utc>. Skutečný počet ("0500" v tomto příkladu) a jeho znaménko (+ nebo-) se ignorují.

Při serializaci <xref:System.DateTime>, <xref:System.DateTimeKind.Local> a <xref:System.DateTimeKind.Unspecified> časy jsou zapisovány s posunem a <xref:System.DateTimeKind.Utc> je zapsán bez.

Kód JavaScriptu klienta ASP.NET AJAX tyto řetězce automaticky převede na instance JavaScriptu `DateTime`. Pokud existují další řetězce, které mají podobný tvar, který není typu <xref:System.DateTime> v rozhraní .NET, jsou převedeny také.

Převod probíhá pouze v případě, že jsou znaky "/" uvozeny řídicím znakem (to znamená, že JSON vypadá jako "\\/Date (700000 + 0500)\\/"), a z tohoto důvodu kodér JSON služby WCF (povolený <xref:System.ServiceModel.WebHttpBinding>) vždy řídí znak "/".

### <a name="xml-in-json-strings"></a>XML v řetězcích JSON

#### <a name="xmlelement"></a>Třída

<xref:System.Xml.XmlElement> je serializován tak, jak je, bez zabalení. Například datový člen "x" typu <xref:System.Xml.XmlElement>, který obsahuje \<ABC/>, je reprezentován následujícím způsobem:

```json
{"x":"<abc/>"}
```

#### <a name="arrays-of-xmlnode"></a>Pole XmlNode

<xref:System.Array> objekty typu <xref:System.Xml.XmlNode> jsou zabaleny do elementu s názvem ArrayOfXmlNode v oboru názvů kontraktu standardního data pro daný typ. Pokud "x" je pole, které obsahuje uzel atributu "N" v oboru názvů "NS", který obsahuje "value" a prázdný uzel elementu "M", reprezentace je následující.

```json
{"x":"<ArrayOfXmlNode xmlns=\"http://schemas.datacontract.org/2004/07/System.Xml\" a:N=\"value\" xmlns:a=\"ns\"><M/></ArrayOfXmlNode>"}
```

 Atributy v prázdném oboru názvů na začátku polí XmlNode (před jinými prvky) nejsou podporovány.

#### <a name="ixmlserializable-types-including-xelement-and-dataset"></a>Typy IXmlSerializable včetně XElement a DataSet

<xref:System.Runtime.Serialization.ISerializable> typy se rozdělují na typy obsahu, datové sady a typy prvků. Definice těchto typů naleznete [v tématu Typy XML a ADO.NET v kontraktech dat](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).

Typy "obsah" a "DataSet" jsou serializovány podobně jako <xref:System.Array> objektů <xref:System.Xml.XmlNode> popsaných v předchozí části. Jsou zabaleny do elementu, jehož název a obor názvů odpovídají názvu kontraktu dat a oboru názvů příslušného typu.

Typy "element", jako například <xref:System.Xml.Linq.XElement>, jsou serializovány tak, jak jsou, podobně jako <xref:System.Xml.XmlElement> dříve popsané v tomto tématu.

### <a name="polymorphism"></a>Polymorfismus

#### <a name="preserving-type-information"></a>Zachování informací o typu

Jak bylo uvedeno dříve, polymorfismus je ve formátu JSON podporována s některými omezeními. Jazyk JavaScript je nebezpečným jazykem a identita typu obvykle není problémem. Pokud ale používáte JSON ke komunikaci mezi systémem silného typu (.NET) a systémem slabě typovaného systému (JavaScript), je vhodné zachovat identitu typu. Například typy s názvy kontraktů dat "čtvercový" a "Circle" jsou odvozeny z typu s názvem kontraktu dat "tvar". Pokud je "kruh" odesílán z rozhraní .NET do JavaScriptu a později se vrátí na metodu .NET, která očekává "tvar", je užitečné, aby strana .NET věděla, že daný objekt byl původně "kruhem", jinak jakékoli informace, které jsou specifické pro odvozený typ (například může dojít ke ztrátě datového členu "poloměr" na "Circle").

Chcete-li zachovat identitu typu při serializaci komplexních typů do formátu JSON, lze přidat "pomocný parametr" typu a deserializátor rozpoznává pomocný parametr a funguje správně. "Pomocný parametr typu" je dvojice klíč/hodnota JSON s názvem klíče "\_\_typ" (dvě podtržítka následovaná slovem "Type"). Hodnota je řetězec formátu JSON ve formátu "DataContract: DataContractNamespace" (cokoli až do první dvojtečky je název). Pomocí předchozího příkladu lze následujícím způsobem serializovat "kruh".

```json
{"__type":"Circle:http://example.com/myNamespace","x":50,"y":70,"radius":10}
```

Pomocný parametr typu se velmi podobá atributu `xsi:type` definovanému standardem instance schématu XML a používá se při serializaci nebo deserializaci kódu XML.

Datové členy s názvem "\_\_typu" jsou zakázány z důvodu možného konfliktu s pomocným parametrem typu.

#### <a name="reducing-the-size-of-type-hints"></a>Zmenšení velikosti parametrů typu

Aby se snížila velikost zpráv JSON, nahradí se výchozí předpona oboru názvů kontraktu dat (`http://schemas.datacontract.org/2004/07/`) znakem "#". (Aby toto nahrazení bylo vratné, použije se pravidlo pro uvozovací znaky: Pokud obor názvů začíná znaky "#" nebo "\\", připojí se navíc znak "\\". Proto pokud "Circle" je typ v oboru názvů .NET "MyApp. Shapes", jeho výchozí obor názvů kontraktu dat je `http://schemas.datacontract.org/2004/07/MyApp`. Tvary a reprezentace JSON jsou následující.

```json
{"__type":"Circle:#MyApp.Shapes","x":50,"y":70,"radius":10}
```

Zkrácená (#MyApp. Shapes) i úplná (http://schemas.datacontract.org/2004/07/MyApp.Shapes) názvy se rozumí při deserializaci.

#### <a name="type-hint-position-in-json-objects"></a>Pozice nápovědy typu v objektech JSON

Všimněte si, že pomocný parametr typu musí být uveden jako první v reprezentaci JSON. Toto je jediný případ, ve kterém je pořadí párů klíč/hodnota důležité při zpracování JSON. Například následující není platný způsob, jak zadat pomocný parametr typu.

```json
{"x":50,"y":70,"radius":10,"__type":"Circle:#MyApp.Shapes"}
```

Jak <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> používá technologie WCF i stránky klienta ASP.NET AJAX, vždy nejprve vygeneruje pomocný parametr typu.

#### <a name="type-hints-apply-only-to-complex-types"></a>Parametry typu se použijí jenom pro komplexní typy.

Neexistuje žádný způsob, jak vygenerovat pomocný parametr typu pro nekomplexní typy. Například pokud má operace <xref:System.Object> návratový typ, ale vrátí kružnici, může být reprezentace JSON, jak je uvedeno výše, a informace o typu jsou zachovány. Pokud je však vrácen identifikátor URI, reprezentace JSON je řetězec a fakt, že řetězec použitý k reprezentaci identifikátoru URI je ztracen. To platí nejen pro primitivní typy, ale také pro kolekce a pole.

#### <a name="when-are-type-hints-emitted"></a>Kdy jsou vygenerovány pomocné parametry typu

Pomocné parametry typu můžou výrazně zvýšit velikost zprávy (jedním ze způsobů, jak to zmírnit, je použití kratších oborů názvů kontraktů dat, pokud je to možné). Proto následující pravidla určují, zda jsou vygenerovány pomocné parametry typu:

- Při použití ASP.NET AJAX jsou pomocné parametry typu vždy vydávány, kdykoli je to možné, i v případě, že není k dispozici žádné základní/odvozené přiřazení, a to i v případě, že je kruh přiřazený k kruhu. (To je nutné k úplnému povolení procesu volání ze slabě typovaného prostředí JSON do prostředí .NET se silným typem bez překvapivé ztráty informací.)

- Při použití služby AJAX Services bez integrace ASP.NET jsou pomocné parametry generovány pouze v případě, že je k dispozici základní nebo odvozené přiřazení – to je vygenerováno při přiřazení kruhu k obrazci nebo <xref:System.Object>, ale ne, je-li přiřazena kružnice. To poskytuje minimální informace potřebné k správné implementaci klienta jazyka JavaScript, což zvyšuje výkon, ale nechrání před ztrátou informací typu v nesprávně navržených klientech. Pokud se chcete vyhnout tomu, že se tento problém týká klienta, nepoužívejte na serveru zcela základní nebo odvozené přiřazení.

- Při použití <xref:System.Runtime.Serialization.DataContractSerializer>ho typu umožňuje parametr `alwaysEmitTypeInformation` konstruktoru zvolit mezi předchozími dvěma režimy s výchozí hodnotou "`false`" (v případě potřeby generuje pouze pomocné parametry typu).

#### <a name="duplicate-data-member-names"></a>Duplicitní názvy datových členů

Odvozené informace o typu jsou přítomny ve stejném objektu JSON spolu se základními informacemi o typu a můžou být v libovolném pořadí. `Shape` například může být reprezentována následujícím způsobem.

```json
{"__type":"Shape:#MyApp.Shapes","x":50,"y":70}
```

Vzhledem k tomu, že kruh může být reprezentován následujícím způsobem.

```json
{"__type":"Circle:#MyApp.Shapes","x":50, "radius":10,"y":70}
```

Pokud základní `Shape` typ také obsahovalo datový člen s názvem "`radius`", to vede k kolizi v serializaci (protože objekty JSON nemohou mít opakující se názvy klíčů) a deserializaci (protože je nejasné, zda "poloměr" odkazuje na `Shape.radius` nebo `Circle.radius`). Proto v případě JSON není obecně doporučován koncept "skrývání vlastností" (datové členy se stejným názvem na bázi a odvozených tříd), je ve skutečnosti v případě JSON zakázaná.

#### <a name="polymorphism-and-ixmlserializable-types"></a>Polymorfismus a typy IXmlSerializable

typy <xref:System.Xml.Serialization.IXmlSerializable> mohou být polymorfním způsobem přiřazeny jako obvykle, pokud jsou splněny požadavky na známé typy, podle obvyklých pravidel kontraktu dat. Nicméně serializace typu <xref:System.Xml.Serialization.IXmlSerializable> místo <xref:System.Object> vede ke ztrátě informací o typu, protože výsledkem je řetězec JSON.

#### <a name="polymorphism-and-certain-interface-types"></a>Polymorfismus a určité typy rozhraní

Je zakázáno serializovat typ kolekce nebo typ, který implementuje <xref:System.Xml.Serialization.IXmlSerializable>, kde je očekáván typ bez kolekce, který není <xref:System.Xml.Serialization.IXmlSerializable> (s výjimkou <xref:System.Object>). Například vlastní rozhraní s názvem `IMyInterface` a typ `MyType`, který implementuje <xref:System.Collections.Generic.IEnumerable%601> typu `int` a `IMyInterface`. Je zakázáno vracet `MyType` z operace, jejíž návratový typ je `IMyInterface`. Důvodem je, že `MyType` musí být serializován jako pole JSON a vyžadovat pomocný parametr typu, jak je uvedeno před tím, než nelze zahrnout pomocný parametr typu s poli, pouze se složitými typy.

#### <a name="known-types-and-configuration"></a>Známé typy a konfigurace

Všechny známé mechanizmy typů, které používá <xref:System.Runtime.Serialization.DataContractSerializer>, jsou podporovány také stejným způsobem <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. Serializátory čtou stejný element konfigurace [\<dataContractSerializer >](../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md) v [\<System. runtime. Serialization >](../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)pro zjišťování známých typů přidaných prostřednictvím konfiguračního souboru.

#### <a name="collections-assigned-to-object"></a>Kolekce přiřazené k objektu

Kolekce přiřazené k objektu jsou serializovány, jako by se jedná o kolekce, které implementují <xref:System.Collections.Generic.IEnumerable%601>: pole JSON se všemi položkami, které mají pomocný parametr typu, pokud se jedná o komplexní typ. Například <xref:System.Collections.Generic.List%601> typu `Shape` přiřazeno <xref:System.Object> vypadá následovně.

```json
[{"__type":"Shape:#MyApp.Shapes","x":50,"y":70},
{"__type":"Shape:#MyApp.Shapes","x":58,"y":73},
{"__type":"Shape:#MyApp.Shapes","x":41,"y":32}]
```

Při deserializaci zpět do <xref:System.Object>:

- `Shape` musí být v seznamu známých typů. <xref:System.Collections.Generic.List%601> typu `Shape` v známých typech nemá žádný vliv. Všimněte si, že v tomto případě není nutné přidávat `Shape` ke známým typům serializace. to je provedeno automaticky.

- Kolekce je deserializována jako <xref:System.Array> typu <xref:System.Object>, který obsahuje instance `Shape`.

#### <a name="derived-collections-assigned-to-base-collections"></a>Odvozené kolekce přiřazené ke základním kolekcím

Když je odvozená kolekce přiřazena ke základní kolekci, je kolekce obvykle serializována, jako by byla kolekcí základního typu. Nicméně, pokud typ položky odvozené kolekce nemůže být přiřazen k typu položky základní kolekce, je vyvolána výjimka.

#### <a name="type-hints-and-dictionaries"></a>Zadání tipů a slovníků

Když je slovník přiřazen k <xref:System.Object>, každá položka klíče a hodnoty ve slovníku je považována za, jako kdyby byla přiřazena <xref:System.Object> a získá pomocný parametr typu.

Při serializaci typů slovníku není objekt JSON, který obsahuje členy "klíč" a "value", nijak ovlivněn nastavením `alwaysEmitTypeInformation` a obsahuje pouze pomocný parametr typu, pokud je vyžaduje předchozí pravidla shromažďování.

### <a name="valid-json-key-names"></a>Platné názvy klíčů JSON

Serializátor XML – zakóduje názvy klíčů, které nejsou platnými názvy XML. Například datový člen s názvem "123" by měl kódovaný název, například "\_x0031\_\_x0032\_\_x0033\_", protože "123" je neplatný název elementu XML (začíná číslicí). Podobná situace může nastat v případě, že některé mezinárodní znakové sady nejsou platné v názvech XML. Vysvětlení tohoto účinku XML při zpracování JSON najdete v tématu [mapování mezi JSON a XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).

## <a name="see-also"></a>Viz také:

- [Podpora JSON a dalších formátů přenosu dat](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
