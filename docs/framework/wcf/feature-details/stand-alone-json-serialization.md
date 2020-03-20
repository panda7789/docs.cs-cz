---
title: Samostatná serializace JSON pomocí datacontractjsonserializer
ms.date: 03/30/2017
ms.assetid: 312bd7b2-1300-4b12-801e-ebe742bd2287
ms.openlocfilehash: 36945f2d42f22ef3aa4f27bcbe403466f124a279
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184413"
---
# <a name="stand-alone-json-serialization-using-datacontractjsonserializer"></a>Samostatná serializace JSON pomocí datacontractjsonserializer

> [!NOTE]
> Tento článek <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>je o . Pro většinu scénářů, které zahrnují serializaci a rekonstrukci json, doporučujeme api v [oboru názvů System.Text.Json](../../../standard/serialization/system-text-json-overview.md).

JSON (JavaScript Object Notation) je formát dat, který je speciálně navržen pro použití kódem JavaScriptu běžícím na webových stránkách uvnitř prohlížeče. Jedná se o výchozí formát dat používaný službami ASP.NET AJAX vytvořenými v nadaci WCF (Windows Communication Foundation).

Tento formát lze také použít při vytváření služeb AJAX bez integrace s ASP.NET - v tomto případě je XML výchozí, ale JSON lze zvolit.

Nakonec pokud požadujete podporu JSON, ale nevytváříte službu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> AJAX, umožňuje přímo serializovat objekty .NET do dat JSON a rekonstruovat tato data zpět do instancí typů .NET. Popis, jak to provést, naleznete v [tématu Jak: Serializovat a rekonstruovat json data](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).

Při práci s JSON jsou podporovány stejné typy .NET, s několika <xref:System.Runtime.Serialization.DataContractSerializer>výjimkami, jak jsou podporovány . Seznam podporovaných typů naleznete v [tématu Typy podporované serializátorem datových smluv](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). To zahrnuje většinu primitivních typů, většinu typů polí a <xref:System.Runtime.Serialization.DataContractAttribute> kolekcí, stejně jako komplexní typy, které používají a <xref:System.Runtime.Serialization.DataMemberAttribute>.

## <a name="mapping-net-types-to-json-types"></a>Mapování typů .NET na typy JSON

V následující tabulce je uvedena shoda mezi typy .NET a JSON/JavaScript, pokud jsou mapovány postupy serializace a deserializace.

|Typy rozhraní .NET|JSON/JavaScript|Poznámky|
|----------------|----------------------|-----------|
|Všechny číselné typy, například <xref:System.Int32>, <xref:System.Decimal> nebo<xref:System.Double>|Číslo|Zvláštní hodnoty, `Double.NaN` `Double.PositiveInfinity` například , a `Double.NegativeInfinity` nejsou podporovány a výsledkem je neplatný JSON.|
|<xref:System.Enum>|Číslo|Viz "Výčty a JSON" dále v tomto tématu.|
|<xref:System.Boolean>|Logická hodnota|--|
|<xref:System.String>, <xref:System.Char>|Řetězec|--|
|<xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>|Řetězec|Formát těchto typů v JSON je stejný jako v XML (v podstatě TimeSpan ve formátu ISO 8601 Duration, GUID v "12345678-ABCD-ABCD-ABCD-1234567890AB" formátu a URI ve své přirozené formě řetězce jako "http://www.example.com"). Přesné informace naleznete v [tématu Data Contract Schema Reference](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).|
|<xref:System.Xml.XmlQualifiedName>|Řetězec|Formát je "name:namespace" (cokoli před první dvojtečka je název). Název nebo obor názvů mohou chybět. Pokud neexistuje žádný obor názvů dvojtečka může být vynechána také.|
|<xref:System.Array>typu<xref:System.Byte>|Pole čísel|Každé číslo představuje hodnotu jednoho bajtu.|
|<xref:System.DateTime>|DateTime nebo Řetězec|Viz Dates/Times a JSON dále v tomto tématu.|
|<xref:System.DateTimeOffset>|Komplexní typ|Viz Dates/Times a JSON dále v tomto tématu.|
|Typy XML a<xref:System.Xml.XmlElement>ADO.NET ( ,<br /><br /> <xref:System.Xml.Linq.XElement>. Pole , <xref:System.Xml.XmlNode><br /><br /> <xref:System.Runtime.Serialization.ISerializable>,<br /><br /> <xref:System.Data.DataSet>).|Řetězec|Podívejte se na část Typy XML a JSON v tomto tématu.|
|<xref:System.DBNull>|Prázdný komplexní typ|--|
|Kolekce, slovníky a pole|Pole|V tomto tématu najdete v části Kolekce, Slovníky a Pole.|
|Komplexní typy (s použitým <xref:System.Runtime.Serialization.DataContractAttribute> nebo <xref:System.SerializableAttribute> aplikovaným)|Komplexní typ|Datové členy se stanou členy komplexního typu JavaScript.|
|Komplexní typy implementace <xref:System.Runtime.Serialization.ISerializable> rozhraní)|Komplexní typ|Stejné jako u jiných <xref:System.Runtime.Serialization.ISerializable> typů komplex, ale některé typy nejsou podporovány – viz iSerializable Support část rozšířené informace části tohoto tématu.|
|`Null`hodnota pro libovolný typ|Null|Nullable typy jsou také podporovány a mapování JSON stejným způsobem jako typy s nulou.|

### <a name="enumerations-and-json"></a>Výčty a JSON

Hodnoty členů výčtu jsou považovány za čísla v JSON, což se liší od způsobu, jakým jsou zpracovány ve smlouvách dat, kde jsou zahrnuty jako názvy členů. Další informace o zpracování smlouvy o datech naleznete v [tématu Typy výčtu v datových kontraktech](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).

- Například pokud máte `public enum Color {red, green, blue, yellow, pink}`, `yellow` serializace vytvoří číslo 3 a ne řetězec "žlutá".

- Všechny `enum` členy jsou serializovatelné. Atributy <xref:System.Runtime.Serialization.EnumMemberAttribute> <xref:System.NonSerializedAttribute> a jsou ignorovány, pokud jsou použity.

- Je možné rekonstruovat neexistující `enum` hodnotu - například hodnotu 87 lze rekonstruovat do předchozího výčtu Color, i když není definován žádný odpovídající název barvy.

- Příznaky `enum` nejsou zvláštní a je zacházeno stejně jako všechny ostatní `enum`.

### <a name="datestimes-and-json"></a>Termíny/časy a JSON

Formát JSON přímo nepodporuje data a časy. Nicméně, oni jsou velmi běžně používané a ASP.NET AJAX poskytuje speciální podporu pro tyto typy. Při použití ASP.NET proxy kódů AJAX <xref:System.DateTime> typ v rozhraní `DateTime` .NET plně odpovídá typu v jazyce JavaScript.

- Pokud nepoužíváte ASP.NET, <xref:System.DateTime> je typ v JSON reprezentován jako řetězec se speciálním formátem, který je popsán v části Rozšířené informace tohoto tématu.

- <xref:System.DateTimeOffset>je reprezentován v JSON jako komplexní typ: {"DateTime":dateTime,"OffsetMinutes":offsetMinutes}. Člen `offsetMinutes` je posun místního času od greenwichského středního času (GMT), který je nyní také označován jako koordinovaný světový čas (UTC), přidružený k umístění události zájmu. Člen `dateTime` představuje instanci v době, kdy došlo k `DateTime` události zájmu (opět se stane v Jazyce JavaScript, když ASP.NET AJAX je používán a řetězec, když není). Při serializaci `dateTime` je člen vždy serializován v GMT. Takže, pokud popisuje 3:00 AM `dateTime` New York čas, má časovou `offsetMinutes` složku 8:00 AM a jsou 300 (minus 300 minut nebo 5 hodin od GMT).

  > [!NOTE]
  > <xref:System.DateTime>a <xref:System.DateTimeOffset> objekty, při serializování do JSON, pouze zachovat informace o přesnostmi milisekund. Hodnoty podmisekund (mikro/nanosekundy) jsou během serializace ztraceny.

### <a name="xml-types-and-json"></a>Typy XML a JSON

Typy XML se stanou řetězci JSON.

- Například pokud datový člen "q" typu \<XElement obsahuje abc/>, JSON\<je {"q":" abc/>"}.

- Existují některá zvláštní pravidla, která určují, jak je kód XML zabalen – další informace naleznete v části Upřesnit informace dále v tomto tématu.

- Pokud používáte ASP.NET AJAX a nechcete používat řetězce v jazyce JavaScript, ale <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> chcete místo <xref:System.ServiceModel.Web.WebGetAttribute> toho <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> xml dom, <xref:System.ServiceModel.Web.WebInvokeAttribute>nastavte vlastnost xml na nebo vlastnost XML na .

### <a name="collections-dictionaries-and-arrays"></a>Kolekce, slovníky a pole

Všechny kolekce, slovníky a pole jsou reprezentovány v JSON jako pole.

- Jakékoli vlastní nastavení, které používá <xref:System.Runtime.Serialization.CollectionDataContractAttribute> je ignorována v reprezentaci JSON.

- Slovníky nejsou způsob, jak pracovat přímo s JSON. Slovník\<řetězec, objekt> nemusí být podporovány stejným způsobem wcf podle očekávání z práce s jinými technologiemi JSON. Například pokud "abc" je mapována na "xyz" a "def" je mapována na 42 ve slovníku, reprezentace JSON není {"abc":"xyz","def":42} ale je [{"Key":"abc","Value":"xyz"},{"Key":"def","Value":42}] místo.

- Pokud byste chtěli pracovat se společností JSON přímo (dynamicky přistupovat ke klíčům a hodnotám, aniž byste předem definovali pevnou smlouvu), máte několik možností:

  - Zvažte použití [slabě typované ho json serializace (AJAX)](../../../../docs/framework/wcf/samples/weakly-typed-json-serialization-sample.md) ukázka.

  - Zvažte <xref:System.Runtime.Serialization.ISerializable> použití konstruktorů rozhraní a deserializace – tyto dva mechanismy umožňují přístup k párům klíčů a hodnot JSON při serializaci a deserializaci, ale nefungují v případě částečnédůvěryhodnosti.

  - Zvažte práci s [mapování mezi JSON a XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md) namísto použití serializátoru.

  - *Polymorfismus* v kontextu serializace odkazuje na schopnost serializovat odvozený typ, kde se očekává jeho základní typ. Existují speciální pravidla specifická pro JSON při použití kolekcí polymorfně, když <xref:System.Object>například přiřazení kolekce . Tento problém je podrobněji popsán v části Rozšířené informace dále v tomto tématu.

## <a name="additional-details"></a>Další podrobnosti

### <a name="order-of-data-members"></a>Pořadí datových členů

Pořadí datových členů není důležité při použití JSON. Konkrétně i <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> v případě, že je nastavena, JSON data lze stále rekonstruovat v libovolném pořadí.

### <a name="json-types"></a>Typy JSON

Typ JSON nemusí odpovídat předchozí tabulce při rekonstrukci. Například `Int` obvykle mapuje na číslo JSON, ale může být také úspěšně rekonstruovat z řetězce JSON tak dlouho, dokud tento řetězec obsahuje platné číslo. To znamená, že oba {"q":42} a {"q":"42"} jsou platné, pokud existuje `Int` datový člen s názvem "q".

### <a name="polymorphism"></a>Polymorfismus

Polymorfní serializace se skládá ze schopnosti serializovat odvozený typ, kde se očekává jeho základní typ. To je podporováno pro serializaci JSON wcf srovnatelné se způsobem, jakým je podporována serializace XML. Můžete například serializovat, `MyDerivedType` `MyBaseType` kde se očekává, `Int` nebo `Object` serializovat, kde se očekává.

Informace o typu mohou být ztraceny při rekonstrukci odvozeného typu, pokud je očekáván základní typ, pokud nerekonstruujete komplexní typ. Například pokud <xref:System.Uri> je serializován, kde <xref:System.Object> se očekává, výsledkem je řetězec JSON. Pokud je tento řetězec pak <xref:System.Object>reserializován <xref:System.String> zpět do , je vrácena .NET. Deserializer neví, že řetězec byl původně typu <xref:System.Uri>. Obecně platí, <xref:System.Object>že při očekávání jsou všechny řetězce JSON deserializovány jako řetězce .NET a všechna pole JSON používaná k serializaci <xref:System.Array> kolekcí.NET, slovníků a polí jsou deserializována jako typ <xref:System.Object>.NET bez ohledu na to, jaký byl skutečný původní typ. Logická hodnota JSON se <xref:System.Boolean>mapuje na rozhraní .NET . Však při <xref:System.Object>očekávání , JSON čísla jsou <xref:System.Int32>reserializovány jako buď .NET , <xref:System.Decimal> nebo <xref:System.Double>, kde je automaticky vybral nejvhodnější typ.

Při dekontování do <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> typu rozhraní, deklarovat typ byl objekt.

Při práci s vlastní základnu a <xref:System.Runtime.Serialization.KnownTypeAttribute>odvozené typy, pomocí , <xref:System.ServiceModel.ServiceKnownTypeAttribute> nebo ekvivalentní mechanismus je obvykle vyžadováno. Například pokud máte operaci, která `Animal` má vrácenou hodnotu `Cat` a ve `Animal`skutečnosti vrátí instanci (odvozené z ), měli byste buď použít <xref:System.Runtime.Serialization.KnownTypeAttribute>, na `Animal` typ nebo <xref:System.ServiceModel.ServiceKnownTypeAttribute> na operaci a určit `Cat` typ v těchto atributech. Další informace naleznete v [tématu Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).

Podrobnosti o tom, jak polymorfní serializace funguje a diskuse o některých omezení, které musí být respektovány při jeho použití, naleznete v části Rozšířené informace dále v tomto tématu.

### <a name="versioning"></a>Správa verzí

Funkce správy verzí kontraktu <xref:System.Runtime.Serialization.IExtensibleDataObject> dat, včetně rozhraní, jsou plně podporovány v JSON. Kromě toho je ve většině případů možné rekonstruovat typ v jednom formátu (například XML) a pak jej serializovat do jiného formátu <xref:System.Runtime.Serialization.IExtensibleDataObject>(například JSON) a stále zachovat data v . Další informace naleznete v [tématu Forward-Compatible Data Contracts](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Nezapomeňte, že JSON je neuspořádaný, takže všechny informace o objednávce jsou ztraceny. Kromě toho JSON nepodporuje více párů klíč/hodnota se stejným názvem klíče. Nakonec jsou všechny <xref:System.Runtime.Serialization.IExtensibleDataObject> operace na ze své podstaty polymorfní <xref:System.Object>- to je jejich odvozený typ jsou přiřazeny , základní typ pro všechny typy.

## <a name="json-in-urls"></a>JSON v adresách URL

Při použití ASP.NET koncové body AJAX se <xref:System.ServiceModel.Web.WebGetAttribute> slovesem HTTP GET (pomocí atributu) se příchozí parametry zobrazí v adrese URL požadavku namísto textu zprávy. JSON je podporován i v url požadavku, takže pokud `Int` máte operaci, `Person` která má s názvem "číslo" a komplexní typ s názvem "p", může se adresa URL podobat následující adrese URL.

```html
http://example.com/myservice.svc/MyOperation?number=7&p={"name":"John","age":42}
```

Pokud používáte ovládací prvek ASP.NET AJAX Script Manager a proxy pro volání služby, tato adresa URL je automaticky generována proxy serverem a není vidět. JSON nelze použít v adresách URL na non-ASP.NET koncové body AJAX.

## <a name="advanced-information"></a>Pokročilé informace

### <a name="iserializable-support"></a>ISerializable Podpora

#### <a name="supported-and-unsupported-iserializable-types"></a>Podporované a nepodporované iSerializable typy

Obecně platí, že <xref:System.Runtime.Serialization.ISerializable> typy, které implementují rozhraní jsou plně podporovány při serializaci/deserializaci JSON. Některé z těchto typů (včetně některých typů rozhraní .NET Framework) jsou však implementovány takovým způsobem, že aspekty serializace specifické pro JSON způsobí, že nebudou správně rekonstruovány:

- S <xref:System.Runtime.Serialization.ISerializable>, typ jednotlivých datových členů není nikdy znám předem. To vede k polymorfní situaci podobné deserializaci typů do objektu. Jak již bylo zmíněno dříve, může to vést ke ztrátě informací o typu v JSON. Například typ, který serializuje `enum` v <xref:System.Runtime.Serialization.ISerializable> jeho implementaci a pokusí se rekonstruovat `enum` zpět přímo do (bez řádného přetypovávání) selže, protože `enum` je serializován pomocí čísel v JSON a JSON čísla rekonstruovat do vestavěných .NET číselné typy (Int32, decimal nebo Double). Takže skutečnost, že číslo bývalo hodnotou, `enum` je ztraceno.

- Typ, <xref:System.Runtime.Serialization.ISerializable> který závisí na určitém pořadí deserializace v jeho konstruktoru deserializace může také selhat rekonstruovat některá data JSON, protože většina serializátory JSON nezaručují žádné konkrétní pořadí.

#### <a name="factory-types"></a>Tovární typy

Zatímco <xref:System.Runtime.Serialization.IObjectReference> rozhraní je podporováno v JSON obecně, všechny typy, které vyžadují funkci "tovární <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%28System.Runtime.Serialization.StreamingContext%29> typ" (vrácení instance jiného typu než typ, který implementuje rozhraní) nejsou podporovány.

### <a name="datetime-wire-format"></a>Formát datatime drátu

<xref:System.DateTime>hodnoty se zobrazí jako řetězce JSON ve formě "/Date(700000+0500)/", kde první číslo (700000 v příkladu je uvedeno) je počet milisekund v časovém pásmu GMT, pravidelný čas (neletní) od půlnoci, 1. Číslo může být záporné, aby představovalo dřívější časy. Část, která se skládá z "+0500" v příkladu je <xref:System.DateTimeKind.Local> volitelné a označuje, že čas je druhu - to znamená, by měl být převeden na místní časové pásmo na deserializaci. Pokud chybí, čas je reserializován <xref:System.DateTimeKind.Utc>jako . Skutečné číslo ("0500" v tomto příkladu) a jeho znaménko (+ nebo -) jsou ignorovány.

Při <xref:System.DateTime>serializace <xref:System.DateTimeKind.Local> <xref:System.DateTimeKind.Unspecified> , a časy jsou <xref:System.DateTimeKind.Utc> zapsány s posunem a je zapsán bez.

ASP.NET kód javascriptu klienta AJAX automaticky převede tyto řetězce na instance JavaScriptu. `DateTime` Pokud existují jiné řetězce, které mají podobný formulář, které nejsou typu <xref:System.DateTime> v .NET, jsou převedeny také.

Převod probíhá pouze v případě, že jsou uvozeny znaky "/" (to znamená, že JSON vypadá jako "\\/Date(700000+0500)\\/"), a z tohoto důvodu kodér JSON WCF (povolený <xref:System.ServiceModel.WebHttpBinding>) vždy unikne znaku "/".

### <a name="xml-in-json-strings"></a>XML v řetězcích JSON

#### <a name="xmlelement"></a>Xmlelement

<xref:System.Xml.XmlElement>je serializován tak, jak je, bez obalu. Například datový člen "x" <xref:System.Xml.XmlElement> typu, který obsahuje \<abc/> je reprezentován takto:

```json
{"x":"<abc/>"}
```

#### <a name="arrays-of-xmlnode"></a>Pole xmlnode

<xref:System.Array>objekty <xref:System.Xml.XmlNode> typu jsou zabaleny do prvku nazvaného ArrayOfXmlNode ve standardním oboru názvů datové smlouvy pro daný typ. Pokud "x" je pole, které obsahuje uzel atributu "N" v oboru názvů "ns", který obsahuje "hodnotu" a uzel prázdného prvku "M", reprezentace je následující.

```json
{"x":"<ArrayOfXmlNode xmlns=\"http://schemas.datacontract.org/2004/07/System.Xml\" a:N=\"value\" xmlns:a=\"ns\"><M/></ArrayOfXmlNode>"}
```

 Atributy v prázdném oboru názvů na začátku polí XmlNode (před ostatními prvky) nejsou podporovány.

#### <a name="ixmlserializable-types-including-xelement-and-dataset"></a>Typy IXmlSerializable včetně XElement a DataSet

<xref:System.Runtime.Serialization.ISerializable>typy rozdělují na "typy obsahu", "Typy datových sad" a "typy prvků". Definice těchto typů naleznete v tématu [XML a ADO.NET Typy v datových kontraktech](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).

"Content" a "DataSet" typy jsou <xref:System.Array> serializovány podobné objekty <xref:System.Xml.XmlNode> popsané v předchozí části. Jsou zabaleny do prvku, jehož název a obor názvů odpovídá názvu datové smlouvy a oboru názvů daného typu.

"Element" typy, <xref:System.Xml.Linq.XElement> jako jsou serializovány, jak je, podobně jako <xref:System.Xml.XmlElement> dříve popsány v tomto tématu.

### <a name="polymorphism"></a>Polymorfismus

#### <a name="preserving-type-information"></a>Zachování informací o typu

Jak již bylo uvedeno dříve, polymorfismus je podporován v JSON s určitými omezeními. JavaScript je slabě napsaný jazyk a identita typu obvykle není problém. Však při použití JSON komunikovat mezi systémem silného typu (.NET) a slabě napsaný systém (JavaScript), je však užitečné zachovat identitu typu. Například typy s názvy datových smluv "Čtverec" a "Kruh" jsou odvozeny od typu s názvem kontraktu dat "Shape". Pokud "Circle" je odeslána z .NET do JavaScriptu a je později vrácena do .NET metoda, která očekává "Shape", je užitečné pro stranu .NET vědět, že dotyčný objekt byl původně "Circle" - jinak všechny informace specifické pro odvozený typ (například , "radius" datový člen na "Kruh") může být ztracena.

Chcete-li zachovat identitu typu, při serializaci složitých typů do JSON lze přidat "nápovědu typu" a deserializátor rozpozná nápovědu a funguje odpovídajícím způsobem. "Nápověda typu" je pár klíčů/hodnot JSON s\_\_názvem klíče "type" (dvě podtržítka následovaná slovem "typ"). Hodnota je řetězec JSON ve formuláři "DataContractName:DataContractNamespace" (cokoli až do prvnídvojtečky je název). Pomocí předchozího příkladu "Circle" lze serializovat následujícím způsobem.

```json
{"__type":"Circle:http://example.com/myNamespace","x":50,"y":70,"radius":10}
```

Nápověda typu je velmi `xsi:type` podobná atributu definovanému standardem instance schématu XML a použitá při serializaci/deserializaci XML.

Datové členy\_\_nazývané "typ" jsou zakázány z důvodu možného konfliktu s nápovědou typu.

#### <a name="reducing-the-size-of-type-hints"></a>Zmenšení velikosti návažek typu

Chcete-li zmenšit velikost zpráv JSON, výchozí`http://schemas.datacontract.org/2004/07/`předpona oboru názvů datové smlouvy ( ) je nahrazena znakem "#". (Chcete-li toto nahrazení reverzibilní, je použito pravidlo úniku: pokud\\obor názvů začíná znaky "#" nebo " , jsou připojeny s extra znakem "\\). Pokud je tedy "Circle" typem v oboru názvů .NET "MyApp.Shapes", `http://schemas.datacontract.org/2004/07/MyApp`je jeho výchozí obor názvů datové smlouvy . Tvary a reprezentace JSON jsou následující.

```json
{"__type":"Circle:#MyApp.Shapes","x":50,"y":70,"radius":10}
```

Jak zkrácené (#MyApp.Shapes) a úplnéhttp://schemas.datacontract.org/2004/07/MyApp.Shapes) (názvy jsou chápány na deserializaci.

#### <a name="type-hint-position-in-json-objects"></a>Pozice nápovědy typu v objektech JSON

Všimněte si, že nápověda typu se musí zobrazit jako první v reprezentaci JSON. Toto je jediný případ, kdy pořadí párů klíč/hodnota je důležité při zpracování JSON. Například následující není platný způsob, jak určit nápovědu typu.

```json
{"x":50,"y":70,"radius":10,"__type":"Circle:#MyApp.Shapes"}
```

Oba <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> používané WCF a ASP.NET ajax klientské stránky vždy vyzařují typ nápovědy jako první.

#### <a name="type-hints-apply-only-to-complex-types"></a>Rady pro typ platí pouze pro složité typy

Neexistuje žádný způsob, jak vyzařovat nápovědu typu pro nesložité typy. Například pokud operace má <xref:System.Object> návratový typ, ale vrátí Circle, reprezentace JSON může být, jak je uvedeno dříve a informace o typu je zachována. Však pokud uri je vrácena, reprezentace JSON je řetězec a skutečnost, že řetězec slouží k reprezentaci Uri je ztracena. To platí nejen pro primitivní typy, ale také pro kolekce a pole.

#### <a name="when-are-type-hints-emitted"></a>Když jsou vyzařovány rady typu

Typ rady mohou výrazně zvětšit velikost zprávy (jedním ze způsobů, jak to zmírnit, je použít kratší obory názvů smlouvy dat, pokud je to možné). Proto následující pravidla určují, zda jsou emitovány rady typu:

- Při použití ASP.NET AJAX, typ rady jsou vždy vydávány, kdykoli je to možné, i v případě, že neexistuje žádná základní/odvozené přiřazení - například i v případě, že Circle je přiřazen circle. (To je nutné plně povolit proces volání ze slabě typovaného prostředí JSON do prostředí silného typu .NET bez překvapivé ztráty informací.)

- Při použití služby AJAX bez ASP.NET integrace, typ rady jsou vydávány pouze v případě, že je základní/odvozené přiřazení - to znamená, že je vydáván při Circle je přiřazen k Shape nebo <xref:System.Object> ale ne při přiřazení circle. To poskytuje minimální informace potřebné ke správné implementaci klienta Jazyka JavaScript, čímž se zlepší výkon, ale nechrání před ztrátou informací o typu v nesprávně navržených klientech. Pokud se chcete vyhnout řešení tohoto problému na straně klienta, vyhněte se základním/odvozeným přiřazením na serveru.

- Při použití <xref:System.Runtime.Serialization.DataContractSerializer> typu `alwaysEmitTypeInformation` umožňuje parametr konstruktoru vybrat mezi předchozími dvěma režimy, přičemž výchozí je "`false`" (pouze vyzařují rady typu v případě potřeby).

#### <a name="duplicate-data-member-names"></a>Duplicitní názvy datových členů

Informace o odvozeném typu je k dispozici ve stejném objektu JSON spolu s informacemi o základním typu a může dojít v libovolném pořadí. Například `Shape` mohou být reprezentovány následujícím způsobem.

```json
{"__type":"Shape:#MyApp.Shapes","x":50,"y":70}
```

Vzhledem k tomu, Circle mohou být zastoupeny takto.

```json
{"__type":"Circle:#MyApp.Shapes","x":50, "radius":10,"y":70}
```

Pokud základní `Shape` typ také obsahoval datový`radius`člen s názvem " ", vede to ke kolizi při serializaci (protože objekty JSON nemohou mít `Shape.radius` `Circle.radius`opakující se názvy klíčů) a deserializaci (protože není jasné, zda "poloměr" odkazuje na nebo ). Proto zatímco koncept "vlastnost skrývání" (datové členy se stejným názvem na základě a odvozené třídy) se obecně nedoporučuje ve třídách smlouvy dat, je ve skutečnosti zakázáno v případě JSON.

#### <a name="polymorphism-and-ixmlserializable-types"></a>Polymorfismus a iXmlSerializable typy

<xref:System.Xml.Serialization.IXmlSerializable>typy mohou být polymorfně přiřazeny k sobě jako obvykle, pokud jsou splněny požadavky známé typy, v souladu s obvyklými pravidly smlouvy dat. Serializace <xref:System.Xml.Serialization.IXmlSerializable> typu namísto <xref:System.Object> výsledků ke ztrátě informací o typu jako výsledek je řetězec JSON.

#### <a name="polymorphism-and-certain-interface-types"></a>Polymorfismus a určité typy rozhraní

Je zakázáno serializovat typ kolekce nebo typ, <xref:System.Xml.Serialization.IXmlSerializable> který implementuje, kde <xref:System.Xml.Serialization.IXmlSerializable> se <xref:System.Object>očekává typ bez kolekce, který není (s výjimkou) . Například vlastní rozhraní `IMyInterface` s názvem `MyType` a <xref:System.Collections.Generic.IEnumerable%601> typ, `int` `IMyInterface`který implementuje typ a . Je zakázáno `MyType` vrátit se z operace, jejíž návratový typ je `IMyInterface`. Důvodem `MyType` je, že musí být serializován jako pole JSON a vyžaduje nápovědu typu a jak je uvedeno dříve, nelze zahrnout nápovědu typu s poli, pouze se složitými typy.

#### <a name="known-types-and-configuration"></a>Známé typy a konfigurace

Všechny známé typy mechanismy používané <xref:System.Runtime.Serialization.DataContractSerializer> jsou také podporovány <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>stejným způsobem . Oba serializátory číst stejný konfigurační prvek, [ \<dataContractSerializer>](../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md) v [ \<system.runtime.serialization>](../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md), chcete-li zjistit známé typy přidané prostřednictvím konfiguračního souboru.

#### <a name="collections-assigned-to-object"></a>Kolekce přiřazené k objektu

Kolekce přiřazené Object jsou serializovány, jako <xref:System.Collections.Generic.IEnumerable%601>by se jedná o kolekce, které implementují : pole JSON s každou položkou, která má nápovědu typu, pokud se jedná o komplexní typ. Například <xref:System.Collections.Generic.List%601> typ `Shape` přiřazený <xref:System.Object> k vypadá takto.

```json
[{"__type":"Shape:#MyApp.Shapes","x":50,"y":70},
{"__type":"Shape:#MyApp.Shapes","x":58,"y":73},
{"__type":"Shape:#MyApp.Shapes","x":41,"y":32}]
```

Při deserialikace zpět do <xref:System.Object>:

- `Shape`musí být v seznamu Známé typy. S <xref:System.Collections.Generic.List%601> typu `Shape` ve známých typů nemá žádný vliv. Všimněte si, že `Shape` není třeba přidávat do známých typů na serializaci v tomto případě - to se provádí automaticky.

- Kolekce je deserializována <xref:System.Array> jako <xref:System.Object> typ, který obsahuje `Shape` instance.

#### <a name="derived-collections-assigned-to-base-collections"></a>Odvozené kolekce přiřazené k základním kolekcím

Při odvozené kolekce je přiřazena k základní kolekci, kolekce je obvykle serializován, jako kdyby se jednalo o kolekci základního typu. Pokud však typ položky odvozené kolekce nelze přiřadit k typu položky základní kolekce, je vyvolána výjimka.

#### <a name="type-hints-and-dictionaries"></a>Nápovědy k typu a slovníky

Pokud je slovník přiřazen <xref:System.Object>k aplikaci , každá položka klíče a hodnoty ve <xref:System.Object> slovníku je považována za přiřazenou a získá nápovědu k typu.

Při serializaci typů slovníku, JSON objekt, který obsahuje "Klíč" a `alwaysEmitTypeInformation` "Hodnota" členy není ovlivněna nastavení a obsahuje pouze nápovědu typu, pokud předchozí pravidla kolekce vyžadují.

### <a name="valid-json-key-names"></a>Platné názvy klíčů JSON

Serializátor XML kóduje názvy klíčů, které nejsou platnými názvy XML. Například datový člen s názvem "123" by měl kódovaný název,\_například\_\_" x0031 x0032\_\_x0033\_", protože "123" je neplatný název prvku XML (začíná číslicí). Podobná situace může nastat s některými mezinárodními znakovými sadami, které nejsou platné v názvech XML. Vysvětlení tohoto vlivu xml na zpracování JSON naleznete v [tématu Mapování mezi json a XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).

## <a name="see-also"></a>Viz také

- [Podpora formátu JSON a dalších formátů přenosu dat](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
