---
title: Samostatná serializace JSON pomocí DataContractJsonSerializer
ms.date: 03/30/2017
ms.assetid: 312bd7b2-1300-4b12-801e-ebe742bd2287
ms.openlocfilehash: 5561cddb22a02fdae9f792b1d1ec71d01c4fc916
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600903"
---
# <a name="stand-alone-json-serialization-using-datacontractjsonserializer"></a>Samostatná serializace JSON pomocí DataContractJsonSerializer

> [!NOTE]
> Tento článek se týká <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> . Pro většinu scénářů, které zahrnují serializaci a deserializaci JSON, doporučujeme rozhraní API v [oboru názvů System. text. JSON](../../../standard/serialization/system-text-json-overview.md).

JSON (JavaScript Object Notation) je formát dat, který je speciálně navržený tak, aby se používal v kódu JavaScriptu běžícím na webových stránkách v prohlížeči. Je to výchozí formát dat používaný službami ASP.NET AJAX vytvořenými v Windows Communication Foundation (WCF).

Tento formát lze použít také při vytváření služeb AJAX bez integrace s ASP.NET – v tomto případě je XML výchozí, ale může být zvolena hodnota JSON.

Nakonec, pokud požadujete podporu JSON, ale nevytváříte službu AJAX, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> umožňuje přímo serializovat objekty .NET do dat JSON a deserializovat taková data zpátky do instancí typů .NET. Popis toho, jak to provést, naleznete v tématu [How to: serializovat a deserializovat data JSON](how-to-serialize-and-deserialize-json-data.md).

Při práci s JSON jsou podporovány stejné typy rozhraní .NET, s několika výjimkami, jak jsou podporovány v <xref:System.Runtime.Serialization.DataContractSerializer> . Seznam podporovaných typů najdete v tématu [typy podporované serializátorem kontraktu dat](types-supported-by-the-data-contract-serializer.md). To zahrnuje většinu primitivních typů, většinu typů polí a kolekcí a také komplexní typy, které používají <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> .

## <a name="mapping-net-types-to-json-types"></a>Mapování typů .NET na typy JSON

Následující tabulka ukazuje korespondenci mezi typy rozhraní .NET a typy JSON/JavaScript, pokud jsou mapovány postupy serializace a deserializace.

|Typy .NET|JSON/JavaScript|Poznámky|
|----------------|----------------------|-----------|
|Všechny číselné typy, například <xref:System.Int32> <xref:System.Decimal> nebo<xref:System.Double>|Číslo|Speciální hodnoty jako `Double.NaN` , `Double.PositiveInfinity` a `Double.NegativeInfinity` nejsou podporovány a mají za následek neplatný formát JSON.|
|<xref:System.Enum>|Číslo|Viz část "výčty a JSON" dále v tomto tématu.|
|<xref:System.Boolean>|Logická hodnota|--|
|<xref:System.String>, <xref:System.Char>|Řetězec|--|
|<xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>|Řetězec|Formát těchto typů ve formátu JSON je stejný jako v jazyce XML (v podstatě se jedná o časový interval ve formátu ISO 8601 Duration, identifikátor GUID ve formátu "12345678-ABCD-ABCD-ABCD-1234567890AB" a identifikátor URI ve formě přirozeného řetězce, jako je " http://www.example.com "). Podrobné informace najdete v tématu [referenční informace o schématu kontraktu dat](data-contract-schema-reference.md).|
|<xref:System.Xml.XmlQualifiedName>|Řetězec|Formát je "název: obor názvů" (cokoli před první dvojtečkou je název). Název nebo obor názvů může chybět. Pokud obor názvů neexistuje, může být dvojtečka také vynechána.|
|<xref:System.Array>typu<xref:System.Byte>|Pole čísel|Každé číslo představuje hodnotu jednoho bajtu.|
|<xref:System.DateTime>|DateTime nebo String|Viz data a časy a JSON později v tomto tématu.|
|<xref:System.DateTimeOffset>|Komplexní typ|Viz data a časy a JSON později v tomto tématu.|
|Typy XML a ADO.NET ( <xref:System.Xml.XmlElement> ,<br /><br /> <xref:System.Xml.Linq.XElement>. Pole <xref:System.Xml.XmlNode> ,<br /><br /> <xref:System.Runtime.Serialization.ISerializable>,<br /><br /> <xref:System.Data.DataSet>).|Řetězec|Další informace najdete v části Typy XML a JSON tohoto tématu.|
|<xref:System.DBNull>|Prázdný komplexní typ|--|
|Kolekce, slovníky a pole|Pole|Viz část kolekce, slovníky a pole tohoto tématu.|
|Komplexní typy (s <xref:System.Runtime.Serialization.DataContractAttribute> použitím nebo <xref:System.SerializableAttribute> )|Komplexní typ|Datové členy se stanou členy komplexního typu JavaScriptu.|
|Komplexní typy implementující <xref:System.Runtime.Serialization.ISerializable> rozhraní)|Komplexní typ|Stejné jako u jiných složitých typů, ale některé <xref:System.Runtime.Serialization.ISerializable> typy nejsou podporované – Podívejte se na část podpora ISerializable v části Rozšířené informace v tomto tématu.|
|`Null`hodnota pro libovolný typ|Null|Podporují se i typy hodnot s možnou hodnotou null a mapují se na JSON stejným způsobem jako typy hodnot, které nejsou null.|

### <a name="enumerations-and-json"></a>Výčty a JSON

Hodnoty členů výčtu jsou považovány za čísla ve formátu JSON, což se liší od toho, jak se zpracovávají v kontraktech dat, kde jsou zahrnuty jako názvy členů. Další informace o zpracování kontraktu dat najdete v tématu [výčtové typy v kontraktech dat](enumeration-types-in-data-contracts.md).

- Například pokud máte `public enum Color {red, green, blue, yellow, pink}` , serializace `yellow` vytvoří číslo 3, nikoli řetězec "Yellow".

- Všichni `enum` Členové jsou serializovatelný. <xref:System.Runtime.Serialization.EnumMemberAttribute>A <xref:System.NonSerializedAttribute> atributy jsou ignorovány, pokud jsou použity.

- Je možné deserializovat neexistující `enum` hodnotu, například hodnotu 87 lze deserializovat do předchozího výčtu barev i v případě, že není definován žádný odpovídající název barvy.

- Příznaky `enum` nejsou speciální a jsou ošetřeny stejným způsobem jako jiné `enum` .

### <a name="datestimes-and-json"></a>Data a časy a JSON

Formát JSON přímo nepodporuje data a časy. Jsou však velmi často používány a ASP.NET AJAX poskytuje speciální podporu pro tyto typy. Při použití proxy ASP.NET AJAX je <xref:System.DateTime> typ v .NET plně odpovídající `DateTime` typu v JavaScriptu.

- Pokud nepoužíváte ASP.NET, <xref:System.DateTime> je typ reprezentován ve formátu JSON jako řetězec se speciálním formátem, který je popsán v části Rozšířené informace v tomto tématu.

- <xref:System.DateTimeOffset>je reprezentován ve formátu JSON jako komplexní typ: {"DateTime":d ateTime, "OffsetMinutes": offsetMinutes}. `offsetMinutes`Členem je místní časový posun od střední hodnoty času (GMT), který se teď označuje jako koordinovaný světový čas (UTC), který je přidružený k umístění události zájmu. `dateTime`Člen představuje instanci v čase, kdy došlo k události zájmu (znovu se spustí `DateTime` v JavaScriptu, když se ASP.NET AJAX používá a řetězec, pokud není). Při serializaci `dateTime` je člen vždy serializován v GMT. Takže pokud je to pro čas 3:00 až Praha, `dateTime` má časovou komponentu 8:00 a `offsetMinutes` je 300 (minus 300 minuty nebo 5 hodin od GMT).

  > [!NOTE]
  > <xref:System.DateTime>a <xref:System.DateTimeOffset> objekty, při serializaci do formátu JSON, zachovávají pouze informace na přesnost milisekund. Během serializace dojde ke ztrátě hodnot dílčích milisekund (mikro/nanosekunds).

### <a name="xml-types-and-json"></a>Typy XML a JSON

Typy XML se stávají řetězcem JSON.

- Například pokud datový člen "q" typu XElement obsahuje \<abc/> , je JSON {"q": " \<abc/> "}.

- Existují určitá zvláštní pravidla, která určují, jak je XML zabaleno. Další informace najdete v části Rozšířené informace dále v tomto tématu.

- Pokud používáte ASP.NET AJAX a nechcete používat řetězce v JavaScriptu, ale chcete místo toho použít XML DOM, nastavte <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> vlastnost na XML <xref:System.ServiceModel.Web.WebGetAttribute> nebo na <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> vlastnost na XML v <xref:System.ServiceModel.Web.WebInvokeAttribute> .

### <a name="collections-dictionaries-and-arrays"></a>Kolekce, slovníky a pole

Všechny kolekce, slovníky a pole jsou ve formátu JSON vyjádřené jako pole.

- Jakékoli vlastní nastavení, které používá, <xref:System.Runtime.Serialization.CollectionDataContractAttribute> se ignoruje v reprezentaci JSON.

- Slovníky nejsou způsobem, jak pracovat přímo s JSON. Slovník \<string,object> nemusí být podporován stejným způsobem ve službě WCF podle očekávání od práce s jinými technologiemi JSON. Například pokud je "ABC" mapován na "xyz" a "def", ve slovníku se namapuje na 42, reprezentace JSON není {"ABC": "xyz", "def": 42}, ale jedná se o [{"klíč": "ABC", "value": "xyz"}, {"Key": "def", "value": 42}] namísto.

- Pokud chcete pracovat s JSON přímo (dynamicky přistupovat k klíčům a hodnotám, aniž byste museli předem definovat pevný kontrakt), máte několik možností:

  - Zvažte použití ukázky [Neslabě typovaného serializace JSON (AJAX)](../samples/weakly-typed-json-serialization-sample.md) .

  - Zvažte použití <xref:System.Runtime.Serialization.ISerializable> konstruktorů rozhraní a deserializace – tyto dva mechanismy vám umožní přístup k párů klíč/hodnota JSON na serializaci a deserializaci, ale nefungují v scénářích s částečnou důvěryhodností.

  - Zvažte práci s [mapováním mezi JSON a XML](mapping-between-json-and-xml.md) namísto použití serializátoru.

  - *Polymorfismus* v kontextu serializace odkazuje na schopnost serializovat odvozený typ, kde je očekáván jeho základní typ. Existují zvláštní pravidla specifická pro JSON při použití kolekcí polymorfní, kdy například přiřadíte kolekci k <xref:System.Object> . Tento problém je podrobněji popsán v části Rozšířené informace dále v tomto tématu.

## <a name="additional-details"></a>Další podrobnosti

### <a name="order-of-data-members"></a>Pořadí datových členů

Pořadí datových členů není při použití JSON důležité. Konkrétně i v případě <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> , že je nastavená, můžete data JSON dál deserializovat v libovolném pořadí.

### <a name="json-types"></a>Typy JSON

Typ JSON nemusí odpovídat předchozí tabulce v deserializaci. Například `Int` obvykle se mapuje na číslo JSON, ale lze jej také úspěšně deserializovat z řetězce JSON, pokud tento řetězec obsahuje platné číslo. To znamená, že obě {"q": 42} a {"q": "42"} jsou platné, pokud existuje `Int` datový člen s názvem "q".

### <a name="polymorphism"></a>Polymorfismus

Polymorfní serializace je tvořena možností serializace odvozeného typu, kde je očekáván jeho základní typ. To je podporováno pro serializaci JSON pomocí WCF srovnatelné se způsobem, jakým je podporována serializace XML. Například můžete serializovat `MyDerivedType` `MyBaseType` , kde je očekáváno, kde je očekáváno, kde `Int` `Object` je očekáváno, kde je očekáváno.

Při deserializaci odvozeného typu může dojít ke ztrátě informací o typu, pokud se očekává základní typ, pokud neprovádíte deserializaci komplexního typu. Například pokud <xref:System.Uri> je serializován <xref:System.Object> , kde je očekáváno, je výsledkem řetězec JSON. Pokud je tento řetězec následně deserializován zpět do <xref:System.Object> , <xref:System.String> je vrácena technologie .NET. Deserializátor neví, že řetězec byl původně typu <xref:System.Uri> . Obecně, pokud je očekáváno <xref:System.Object> , všechny řetězce JSON jsou deserializovány jako řetězce .NET a všechna pole JSON používaná k serializaci kolekcí .NET, slovníky a pole jsou deserializovány jako rozhraní .NET <xref:System.Array> typu <xref:System.Object> bez ohledu na to, co byl skutečný původní typ. Logická hodnota JSON se mapuje na rozhraní .NET <xref:System.Boolean> . Pokud však očekáváte <xref:System.Object> , jsou deserializována čísla JSON buď jako rozhraní .NET <xref:System.Int32> , <xref:System.Decimal> nebo <xref:System.Double> , kde je nejvhodnější typ automaticky vybrán.

Při deserializaci do typu rozhraní jsou <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> deserializace, jako by byl deklarovaný typ Object.

Při práci s vlastními základními a odvozenými typy použijte <xref:System.Runtime.Serialization.KnownTypeAttribute> <xref:System.ServiceModel.ServiceKnownTypeAttribute> nebo je obvykle vyžadován ekvivalentní mechanismus. Například pokud máte operaci, která má `Animal` návratovou hodnotu a ve skutečnosti vrátí instanci `Cat` (odvozenou od `Animal` ), měli byste buď použít <xref:System.Runtime.Serialization.KnownTypeAttribute> , na `Animal` typ nebo na <xref:System.ServiceModel.ServiceKnownTypeAttribute> operaci a zadat `Cat` typ v těchto atributech. Další informace najdete v tématu [známé typy kontraktu dat](data-contract-known-types.md).

Podrobnosti o tom, jak polymorfní serializace funguje a diskuzi o některých omezeních, která musí být při použití dodržena, najdete v části Rozšířené informace dále v tomto tématu.

### <a name="versioning"></a>Správa verzí

Funkce pro správu verzí kontraktů dat, včetně <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní, jsou ve formátu JSON plně podporované. Ve většině případů je také možné deserializovat typ v jednom formátu (například XML) a potom jej serializovat do jiného formátu (například JSON) a zachovat data v <xref:System.Runtime.Serialization.IExtensibleDataObject> . Další informace najdete v tématu [kontrakty dat kompatibilní s dopředné](forward-compatible-data-contracts.md). Mějte na paměti, že kód JSON je Neseřazený, takže dojde ke ztrátě informací o objednávkách. Kromě toho JSON nepodporuje více párů klíč/hodnota se stejným názvem klíče. Nakonec všechny operace na <xref:System.Runtime.Serialization.IExtensibleDataObject> jsou ve své podstatě polymorfní – to je jejich odvozený typ, který je přiřazený k <xref:System.Object> základnímu typu pro všechny typy.

## <a name="json-in-urls"></a>JSON v adresách URL

Při použití koncových bodů ASP.NET AJAX s příkazem HTTP GET (s <xref:System.ServiceModel.Web.WebGetAttribute> atributem) se příchozí parametry zobrazí v adrese URL namísto textu zprávy. JSON se podporuje i v adrese URL požadavku, takže pokud máte operaci, která přebírá `Int` "číslo" a `Person` komplexní typ s názvem "p", adresa URL může vypadat jako následující adresa URL.

```html
http://example.com/myservice.svc/MyOperation?number=7&p={"name":"John","age":42}
```

Pokud ke volání služby používáte ovládací prvek Správce skriptů ASP.NET AJAX a proxy server, tato adresa URL se automaticky vygeneruje proxy serverem a nezobrazuje se. JSON se nedá použít v adresách URL v koncových bodech non-ASP.NET AJAX.

## <a name="advanced-information"></a>Rozšířené informace

### <a name="iserializable-support"></a>Podpora ISerializable

#### <a name="supported-and-unsupported-iserializable-types"></a>Podporované a nepodporované typy ISerializable

Obecně platí, že typy, které implementují <xref:System.Runtime.Serialization.ISerializable> rozhraní, jsou plně podporované při serializaci nebo deserializaci JSON. Nicméně některé z těchto typů (včetně některých typů .NET Framework) jsou implementovány takovým způsobem, že aspekty serializace specifické pro JSON způsobují, že nejsou správně deserializovat:

- V systému se <xref:System.Runtime.Serialization.ISerializable> typ jednotlivých datových členů nikdy neoznačuje jako předem. To vede k polymorfní situaci, která je podobná deserializaci typů do objektu. Jak bylo zmíněno dříve, může to vést ke ztrátě informací o typu ve formátu JSON. Například typ, který serializace `enum` v jeho <xref:System.Runtime.Serialization.ISerializable> implementaci a pokusí se o deserializaci přímo do `enum` (bez správných přetypování), se nezdařil, protože `enum` je serializovaná pomocí čísel JSON a JSON čísla deserializována do předdefinovaných číselných typů .NET (Int32, Decimal nebo Double). Fakt, že číslo použité k `enum` hodnotě je ztraceno.

- <xref:System.Runtime.Serialization.ISerializable>Typ, který závisí na určitém pořadí deserializace v jeho konstruktoru deserializace, může také dojít k chybě při deserializaci některých dat JSON, protože většina serializátorů JSON nezaručuje konkrétní pořadí.

#### <a name="factory-types"></a>Typy továrny

I když <xref:System.Runtime.Serialization.IObjectReference> je rozhraní ve formátu JSON podporováno obecně, všechny typy, které vyžadují funkci "typ objektu pro vytváření" (vracející instance jiného typu <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%28System.Runtime.Serialization.StreamingContext%29> než typ, který implementuje rozhraní), nejsou podporovány.

### <a name="datetime-wire-format"></a>Formát vedení data a času

<xref:System.DateTime>hodnoty se zobrazí jako řetězce JSON ve formátu "/Date (700000 + 0500)/", kde první číslo (700000 v zadaném příkladu) je počet milisekund v časovém pásmu GMT, běžný (neletní) čas od půlnoci 1. ledna 1970. Počet může být záporný, aby představoval předchozí časy. Část, která se skládá z "+ 0500" v příkladu je volitelná a označuje, že doba je <xref:System.DateTimeKind.Local> typu – to znamená, že by mělo být převedeno na místní časové pásmo Při deserializaci. Pokud chybí, čas je deserializován jako <xref:System.DateTimeKind.Utc> . Skutečný počet ("0500" v tomto příkladu) a jeho znaménko (+ nebo-) se ignorují.

Při serializaci <xref:System.DateTime> <xref:System.DateTimeKind.Local> a <xref:System.DateTimeKind.Unspecified> časy jsou zapisovány s posunem a jsou <xref:System.DateTimeKind.Utc> zapsány bez.

Kód JavaScriptu klienta ASP.NET AJAX tyto řetězce automaticky převede na instance JavaScriptu `DateTime` . Pokud existují další řetězce, které mají podobný tvar, který není typu <xref:System.DateTime> v rozhraní .NET, jsou převedeny také.

Převod probíhá pouze v případě, že znaky "/" jsou uvozeny řídicím znakem (to znamená, že JSON vypadá jako " \\ /Date (700000 + 0500) \\ /") a z tohoto důvodu se vždy označí jako kodér JSON služby WCF (povolený <xref:System.ServiceModel.WebHttpBinding> ) znak "/".

### <a name="xml-in-json-strings"></a>XML v řetězcích JSON

#### <a name="xmlelement"></a>Třída

<xref:System.Xml.XmlElement>je serializován tak, jak je, bez zabalení. Například datový člen "x" typu <xref:System.Xml.XmlElement> , který obsahuje, \<abc/> je reprezentován následujícím způsobem:

```json
{"x":"<abc/>"}
```

#### <a name="arrays-of-xmlnode"></a>Pole XmlNode

<xref:System.Array>objekty typu <xref:System.Xml.XmlNode> jsou zabaleny do elementu s názvem ArrayOfXmlNode v oboru názvů kontraktu Standard data pro daný typ. Pokud "x" je pole, které obsahuje uzel atributu "N" v oboru názvů "NS", který obsahuje "value" a prázdný uzel elementu "M", reprezentace je následující.

```json
{"x":"<ArrayOfXmlNode xmlns=\"http://schemas.datacontract.org/2004/07/System.Xml\" a:N=\"value\" xmlns:a=\"ns\"><M/></ArrayOfXmlNode>"}
```

 Atributy v prázdném oboru názvů na začátku polí XmlNode (před jinými prvky) nejsou podporovány.

#### <a name="ixmlserializable-types-including-xelement-and-dataset"></a>Typy IXmlSerializable včetně XElement a DataSet

<xref:System.Runtime.Serialization.ISerializable>typy se rozdělují na typy obsahu, datové sady a typy prvků. Definice těchto typů naleznete [v tématu Typy XML a ADO.NET v kontraktech dat](xml-and-ado-net-types-in-data-contracts.md).

Typy "obsah" a "DataSet" jsou serializovány podobně jako <xref:System.Array> objekty <xref:System.Xml.XmlNode> popsané v předchozí části. Jsou zabaleny do elementu, jehož název a obor názvů odpovídají názvu kontraktu dat a oboru názvů příslušného typu.

Typy "element", jako <xref:System.Xml.Linq.XElement> je například, jsou serializovány tak, jak je <xref:System.Xml.XmlElement> uvedeno dříve v tomto tématu.

### <a name="polymorphism"></a>Polymorfismus

#### <a name="preserving-type-information"></a>Zachování informací o typu

Jak bylo uvedeno dříve, polymorfismus je ve formátu JSON podporována s některými omezeními. Jazyk JavaScript je nebezpečným jazykem a identita typu obvykle není problémem. Pokud ale používáte JSON ke komunikaci mezi systémem silného typu (.NET) a systémem slabě typovaného systému (JavaScript), je vhodné zachovat identitu typu. Například typy s názvy kontraktů dat "čtvercový" a "Circle" jsou odvozeny z typu s názvem kontraktu dat "tvar". Pokud je "kruh" odesílán z rozhraní .NET do JavaScriptu a později se vrátí na metodu .NET, která očekává "tvar", je užitečné, aby strana technologie .NET věděla, že daný objekt byl původně "kruhem" – jinak mohou být ztraceny všechny informace specifické pro odvozený typ (například datový člen "RADIUS" na "Circle").

Chcete-li zachovat identitu typu při serializaci komplexních typů do formátu JSON, lze přidat "pomocný parametr" typu a deserializátor rozpoznává pomocný parametr a funguje správně. "Pomocný parametr typu" je dvojice klíč/hodnota JSON s názvem klíče \_ \_ typu "Type" (dvě podtržítka následovaná slovem "Type"). Hodnota je řetězec formátu JSON ve formátu "DataContract: DataContractNamespace" (cokoli až do první dvojtečky je název). Pomocí předchozího příkladu lze následujícím způsobem serializovat "kruh".

```json
{"__type":"Circle:http://example.com/myNamespace","x":50,"y":70,"radius":10}
```

Pomocný parametr typu se velmi podobá `xsi:type` atributu definovanému standardem instance schématu XML a používá se při serializaci nebo deserializaci kódu XML.

Datové členy s názvem " \_ \_ typ" jsou zakázány z důvodu možného konfliktu s pomocným parametrem typu.

#### <a name="reducing-the-size-of-type-hints"></a>Zmenšení velikosti parametrů typu

Pro snížení velikosti zpráv JSON je výchozí předpona oboru názvů kontraktu dat ( `http://schemas.datacontract.org/2004/07/` ) nahrazena znakem "#". (Aby toto nahrazení bylo vratné, použije se pravidlo pro uvozovací znaky: Pokud obor názvů začíná znaky "#" nebo " \\ ", připojí se znak navíc " \\ ". Proto pokud "Circle" je typ v oboru názvů .NET "MyApp. Shapes", jeho výchozí obor názvů kontraktu dat je `http://schemas.datacontract.org/2004/07/MyApp` . Tvary a reprezentace JSON jsou následující.

```json
{"__type":"Circle:#MyApp.Shapes","x":50,"y":70,"radius":10}
```

Zkrácení (#MyApp. Shapes) a úplný název ( <http://schemas.datacontract.org/2004/07/MyApp.Shapes> ) jsou srozumitelné Při deserializaci.

#### <a name="type-hint-position-in-json-objects"></a>Pozice nápovědy typu v objektech JSON

Všimněte si, že pomocný parametr typu musí být uveden jako první v reprezentaci JSON. Toto je jediný případ, ve kterém je pořadí párů klíč/hodnota důležité při zpracování JSON. Například následující není platný způsob, jak zadat pomocný parametr typu.

```json
{"x":50,"y":70,"radius":10,"__type":"Circle:#MyApp.Shapes"}
```

Jak se <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> používá na stránkách klienta WCF i ASP.NET AJAX, vždy nejprve vygeneruje pomocný parametr typu.

#### <a name="type-hints-apply-only-to-complex-types"></a>Parametry typu se použijí jenom pro komplexní typy.

Neexistuje žádný způsob, jak vygenerovat pomocný parametr typu pro nekomplexní typy. Například pokud má operace <xref:System.Object> návratový typ, ale vrátí kruh, reprezentace JSON může být jak je uvedeno výše a informace o typu jsou zachovány. Pokud je však vrácen identifikátor URI, reprezentace JSON je řetězec a fakt, že řetězec použitý k reprezentaci identifikátoru URI je ztracen. To platí nejen pro primitivní typy, ale také pro kolekce a pole.

#### <a name="when-are-type-hints-emitted"></a>Kdy jsou vygenerovány pomocné parametry typu

Pomocné parametry typu můžou výrazně zvýšit velikost zprávy (jedním ze způsobů, jak to zmírnit, je použití kratších oborů názvů kontraktů dat, pokud je to možné). Proto následující pravidla určují, zda jsou vygenerovány pomocné parametry typu:

- Při použití ASP.NET AJAX jsou pomocné parametry typu vždy vydávány, kdykoli je to možné, i v případě, že není k dispozici žádné základní/odvozené přiřazení, a to i v případě, že je kruh přiřazený k kruhu. (To je nutné k úplnému povolení procesu volání ze slabě typovaného prostředí JSON do prostředí .NET silného typu bez překvapivé ztráty informací.)

- Při použití služeb AJAX bez integrace ASP.NET jsou pomocné parametry generovány pouze v případě, že je k dispozici základní nebo odvozené přiřazení – to je vygenerováno při přiřazení kruhu k obrazci, <xref:System.Object> ale ne, je-li přiřazen k kruhu. To poskytuje minimální informace potřebné k správné implementaci klienta jazyka JavaScript, což zvyšuje výkon, ale nechrání před ztrátou informací typu v nesprávně navržených klientech. Pokud se chcete vyhnout tomu, že se tento problém týká klienta, nepoužívejte na serveru zcela základní nebo odvozené přiřazení.

- Při použití <xref:System.Runtime.Serialization.DataContractSerializer> typu `alwaysEmitTypeInformation` umožňuje parametr konstruktoru zvolit mezi předchozími dvěma režimy, přičemž výchozí hodnota je " `false` " (v případě potřeby pouze vygeneruje nápovědu typu).

#### <a name="duplicate-data-member-names"></a>Duplicitní názvy datových členů

Odvozené informace o typu jsou přítomny ve stejném objektu JSON spolu se základními informacemi o typu a můžou být v libovolném pořadí. Například `Shape` může být reprezentován následujícím způsobem.

```json
{"__type":"Shape:#MyApp.Shapes","x":50,"y":70}
```

Vzhledem k tomu, že kruh může být reprezentován následujícím způsobem.

```json
{"__type":"Circle:#MyApp.Shapes","x":50, "radius":10,"y":70}
```

Pokud základní `Shape` typ také obsahovalo datový člen s názvem " `radius` ", to vede k kolizi v serializaci (protože objekty JSON nemohou mít opakující se názvy klíčů) a deserializaci (protože je nejasné, zda je "poloměr" odkazuje na `Shape.radius` nebo `Circle.radius` ). Proto v případě JSON není obecně doporučován koncept "skrývání vlastností" (datové členy se stejným názvem na bázi a odvozených tříd), je ve skutečnosti v případě JSON zakázaná.

#### <a name="polymorphism-and-ixmlserializable-types"></a>Polymorfismus a typy IXmlSerializable

<xref:System.Xml.Serialization.IXmlSerializable>typy mohou být polymorfním způsobem přiřazeny jako obvykle, pokud jsou splněny požadavky na známé typy, podle obvyklých pravidel kontraktu dat. Nicméně serializace <xref:System.Xml.Serialization.IXmlSerializable> typu namísto <xref:System.Object> výsledků dojde ke ztrátě informací o typu, protože výsledkem je řetězec JSON.

#### <a name="polymorphism-and-certain-interface-types"></a>Polymorfismus a určité typy rozhraní

Je zakázáno serializovat typ kolekce nebo typ, který implementuje, <xref:System.Xml.Serialization.IXmlSerializable> kde je očekáván typ bez kolekce <xref:System.Xml.Serialization.IXmlSerializable> (s výjimkou <xref:System.Object> ). Například vlastní rozhraní s názvem `IMyInterface` a typ `MyType` , který implementuje oba <xref:System.Collections.Generic.IEnumerable%601> typy `int` i `IMyInterface` . Je zakázáno vracet `MyType` z operace, jejíž návratový typ je `IMyInterface` . Důvodem je, že `MyType` musí být serializován jako pole JSON a vyžadovat pomocný parametr typu, jak je uvedeno před tím, než nelze zahrnout pomocný parametr typu s poli, pouze se složitými typy.

#### <a name="known-types-and-configuration"></a>Známé typy a konfigurace

Všechny známé mechanizmy typů, které používá, <xref:System.Runtime.Serialization.DataContractSerializer> jsou také podporovány stejným způsobem jako <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> . Serializátory čtou stejný element konfigurace [\<dataContractSerializer>](../../configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md) v [\<system.runtime.serialization>](../../configure-apps/file-schema/wcf/system-runtime-serialization.md) , aby zjistily známé typy přidané prostřednictvím konfiguračního souboru.

#### <a name="collections-assigned-to-object"></a>Kolekce přiřazené k objektu

Kolekce přiřazené k objektu jsou serializovány, jako by se jedná o kolekce, které implementují <xref:System.Collections.Generic.IEnumerable%601> : pole JSON se všemi položkami, které mají pomocný parametr typu, pokud se jedná o komplexní typ. Například <xref:System.Collections.Generic.List%601> typ `Shape` přiřazeno může <xref:System.Object> vypadat jako následující.

```json
[{"__type":"Shape:#MyApp.Shapes","x":50,"y":70},
{"__type":"Shape:#MyApp.Shapes","x":58,"y":73},
{"__type":"Shape:#MyApp.Shapes","x":41,"y":32}]
```

Při deserializaci zpět do <xref:System.Object> :

- `Shape`musí být v seznamu známých typů. Existence <xref:System.Collections.Generic.List%601> typu `Shape` v známých typech nemá žádný vliv. Všimněte si, že `Shape` v tomto případě není nutné přidávat do serializace známé typy – to je provedeno automaticky.

- Kolekce je deserializována jako <xref:System.Array> typ <xref:System.Object> , který obsahuje `Shape` instance.

#### <a name="derived-collections-assigned-to-base-collections"></a>Odvozené kolekce přiřazené ke základním kolekcím

Když je odvozená kolekce přiřazena ke základní kolekci, je kolekce obvykle serializována, jako by byla kolekcí základního typu. Nicméně, pokud typ položky odvozené kolekce nemůže být přiřazen k typu položky základní kolekce, je vyvolána výjimka.

#### <a name="type-hints-and-dictionaries"></a>Zadání tipů a slovníků

Když je slovník přiřazen k <xref:System.Object> , každá položka klíče a hodnoty ve slovníku je považována za, jako by byla přiřazena k <xref:System.Object> a získá pomocný parametr typu.

Při serializaci typů slovníku není objekt JSON, který obsahuje členy "klíč" a "value", nijak ovlivněn `alwaysEmitTypeInformation` nastavením a obsahuje pouze pomocný parametr typu, pokud je vyžaduje předchozí pravidla shromažďování.

### <a name="valid-json-key-names"></a>Platné názvy klíčů JSON

Serializátor XML – zakóduje názvy klíčů, které nejsou platnými názvy XML. Například datový člen s názvem "123" by měl kódovaný název, například " \_ x0031 \_ \_ x0032 \_ \_ x0033 \_ ", protože "123" je neplatný název elementu XML (začíná číslicí). Podobná situace může nastat v případě, že některé mezinárodní znakové sady nejsou platné v názvech XML. Vysvětlení tohoto účinku XML při zpracování JSON najdete v tématu [mapování mezi JSON a XML](mapping-between-json-and-xml.md).

## <a name="see-also"></a>Viz také

- [Podpora formátu JSON a dalších formátů přenosu dat](support-for-json-and-other-data-transfer-formats.md)
