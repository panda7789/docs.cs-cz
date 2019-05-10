---
title: Samostatná serializace JSON
ms.date: 03/30/2017
ms.assetid: 312bd7b2-1300-4b12-801e-ebe742bd2287
ms.openlocfilehash: 701ad05b7432c36950ff514ad8c7c18a54c7f020
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586185"
---
# <a name="stand-alone-json-serialization"></a>Samostatná serializace JSON
JSON (JavaScript Object Notation) je formát dat, která je navržená speciálně pro kód jazyka JavaScript na webových stránkách spuštěná v prohlížeči. Je výchozí formát dat používaný službou ASP.NET AJAX vytvořené ve Windows Communication Foundation (WCF).  
  
 Tento formát je také možné při vytváření služeb AJAX bez integrace s ASP.NET – v tomto případě XML je výchozí nastavení, ale JSON je možné zvolit.  
  
 Nakonec, pokud nepožadujete podporu JSON, ale nejsou vytvoření služby AJAX <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> díky tomu je možné přímo serializaci objektů .NET do JSON data a deserializuje taková data zpět do instance typů .NET. Popis toho, jak to provést, naleznete v tématu [jak: Serializace a deserializace dat protokolu JSON](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).  
  
 Při práci s JSON je stejné typy .NET jsou podporovány, s několika výjimkami, jako jsou podporovány <xref:System.Runtime.Serialization.DataContractSerializer>. Seznam typů, které jsou podporovány, naleznete v tématu [typy podporované serializátorem kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Jedná se o nejvíce primitivní typy, většina pole a typy kolekcí, stejně jako komplexní typy, které používají <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
## <a name="mapping-net-types-to-json-types"></a>Mapování typů .NET pro typy JSON  
 Následující tabulka ukazuje souvztažnost mezi typy rozhraní .NET a JSON nebo JavaScript při mapování řízení serializace a deserializace.  
  
|Typy rozhraní .NET|JSON a JavaScript|Poznámky|  
|----------------|----------------------|-----------|  
|Všechny číselné typy, například <xref:System.Int32>, <xref:System.Decimal> nebo <xref:System.Double>|Číslo|Zvláštní hodnoty jako `Double.NaN`, `Double.PositiveInfinity` a `Double.NegativeInfinity` nejsou podporovány a mít za následek neplatný JSON.|  
|<xref:System.Enum>|Číslo|Dále v tomto tématu naleznete v tématu "A výčty JSON".|  
|<xref:System.Boolean>|Boolean|--|  
|<xref:System.String>, <xref:System.Char>|String|--|  
|<xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>|String|Formát z těchto typů ve formátu JSON je stejný jako v XML (v podstatě časový interval ve formátu ISO 8601 trvání GUID ve formátu "12345678-ABCD-ABCD-ABCD-1234567890AB" a identifikátor URI v podobě přirozené řetězce, jako jsou "http://www.example.com"). Přesné informace najdete v tématu [schéma kontraktů dat – referenční informace](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).|  
|<xref:System.Xml.XmlQualifiedName>|String|Formát je "název: obor názvů" (jiném než první dvojtečku je název). Název nebo obor názvů může být chybějící. Pokud neexistuje žádný obor názvů může vynechat také dvojtečka.|  
|<xref:System.Array> typu <xref:System.Byte>|Pole čísel.|Každé číslo představuje hodnotu jeden bajt.|  
|<xref:System.DateTime>|Datum a čas nebo řetězec|Zobrazit data / časy a JSON dále v tomto tématu.|  
|<xref:System.DateTimeOffset>|komplexní typ|Zobrazit data / časy a JSON dále v tomto tématu.|  
|Typy XML a ADO.NET (<xref:System.Xml.XmlElement>,<br /><br /> <xref:System.Xml.Linq.XElement>. Pole <xref:System.Xml.XmlNode>,<br /><br /> <xref:System.Runtime.Serialization.ISerializable>,<br /><br /> <xref:System.Data.DataSet>).|String|V části typy XML a JSON tohoto tématu.|  
|<xref:System.DBNull>|Prázdný komplexní typ|--|  
|Kolekce, adresářů a pole|Pole|V části kolekcí, adresářů a pole tohoto tématu.|  
|Komplexní typy (s <xref:System.Runtime.Serialization.DataContractAttribute> nebo <xref:System.SerializableAttribute> použít)|komplexní typ|Datové členy se stanou členy komplexní typ jazyka JavaScript.|  
|Komplexní typy implementace <xref:System.Runtime.Serialization.ISerializable> rozhraní)|komplexní typ|Stejné jako jiné komplexní typy, ale některé <xref:System.Runtime.Serialization.ISerializable> typy nejsou podporované – viz část ISerializable podporu rozšířené informace o části tohoto tématu.|  
|`Null` hodnotu pro jakýkoli typ|Null|Typy s možnou hodnotou Null jsou podporovány také možnosti a mapovat do formátu JSON stejným způsobem jako typy neumožňující hodnotu.|  
  
### <a name="enumerations-and-json"></a>Výčty a JSON  
 Hodnoty výčtu členů jsou považovány za čísla ve formátu JSON, který se liší od jak se zpracovávají v kontraktech dat, ve kterém jsou zahrnuty jako názvy členů. Další informace o zpracování kontraktu dat najdete v tématu [výčtové typy v kontraktech dat](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
- Pokud máte například `public enum Color {red, green, blue, yellow, pink}`, serializaci `yellow` vytváří není řetězec "yellow" a číslo 3.  
  
- Všechny `enum` členy jsou serializovatelné. <xref:System.Runtime.Serialization.EnumMemberAttribute> a <xref:System.NonSerializedAttribute> atributy se ignorují. Pokud se používá.  
  
- Je možné k deserializaci neexistující `enum` hodnota – například hodnota 87 může být deserializovat do předchozího výčtu barev i když není definován žádný odpovídající název barvy.  
  
- Příznaky `enum` není speciální a se chovají stejně jako jakýkoli jiný `enum`.  
  
### <a name="datestimes-and-json"></a>Data a času a JSON  
 Formát JSON přímo nepodporuje data a časy. Nicméně se často používají a technologie ASP.NET AJAX obsahuje speciální podporu pro tyto typy. Při použití technologie ASP.NET AJAX proxy servery, <xref:System.DateTime> typu v rozhraní .NET plně odpovídá `DateTime` typu v jazyce JavaScript.  
  
- Pokud nepoužíváte technologii ASP.NET <xref:System.DateTime> typ je vyjádřen v JSON jako řetězec s speciální formátu, který je popsaný v části Rozšířené informace o tomto tématu.  
  
- <xref:System.DateTimeOffset> je reprezentován ve formátu JSON jako komplexní typ: {"Data a času": datum a čas, "OffsetMinutes": offsetMinutes}. `offsetMinutes` Člen je posun místního času z greenwichský střední čas (GMT), také nyní označuje jako koordinovaný univerzální čas (UTC), přidružený k místu události, které vás zajímají. `dateTime` Člen představuje instanci v okamžiku, kdy došlo k události zájmu (znovu, bude `DateTime` v jazyce JavaScript, pokud je technologie ASP.NET AJAX se používají a řetězec, pokud není). Na serializaci `dateTime` člena je vždy serializován v GMT. Pokud popisující čas 3:00:00 Praha, tedy `dateTime` obsahuje komponentu času 8:00:00 a `offsetMinutes` jsou 300 (minus 300 minut nebo 5 hodin od GMT).  
  
    > [!NOTE]
    >  <xref:System.DateTime> a <xref:System.DateTimeOffset> objekty při serializován do formátu JSON, zachovat pouze informace, které přesností na milisekundy. Během serializace se ztratí hranicí milisekund hodnoty (mikro/nanosekundách).  
  
### <a name="xml-types-and-json"></a>Typy XML a JSON  
 Typy XML se stanou řetězci JSON.  
  
- Například pokud datový člen "q" z typu XElement obsahuje \<abc / >, ve formátu JSON je {"q": "\<abc / >"}.  
  
- Existují některé zvláštní pravidla, které určit, jak je zabalena XML – Další informace naleznete v části Rozšířené informace dále v tomto tématu.  
  
- Pokud používáte ASP.NET AJAX a nechcete použít řetězce v jazyce JavaScript, ale místo toho chcete modelu DOM jazyka XML, nastavte <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> vlastnosti XML v <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> vlastnost jazyka XML <xref:System.ServiceModel.Web.WebInvokeAttribute>.  
  
### <a name="collections-dictionaries-and-arrays"></a>Kolekce, adresáře a pole  
 Všechny kolekce, slovníky a pole jsou reprezentovány ve formátu JSON jako pole.  
  
- Jakéhokoli přizpůsobení, která používá <xref:System.Runtime.Serialization.CollectionDataContractAttribute> je ignorován v reprezentaci JSON.  
  
- Slovníky nejsou způsob, jak pracovat přímo s JSON. Slovník\<řetězec, objekt > nemusí být podporované stejně jako ve službě WCF dle očekávání od práce s jinými technologiemi JSON. Například pokud "abc" je namapovaná na "xyz" a "def" je namapována na 42 ve slovníku, reprezentaci JSON je {"abc": "xyz", "def": 42}, ale je [{"Klíče": "abc", "Hodnota": "xyz"}, {"Klíče": "def", "Value": 42}] místo.  
  
- Pokud chcete pracovat s JSON přímo (přístupu ke klíčům a hodnoty dynamicky, bez nutnosti předem definovat kontrakt od rigidních), máte několik možností:  
  
    - Zvažte použití [slabě typovaná serializace JSON (AJAX)](../../../../docs/framework/wcf/samples/weakly-typed-json-serialization-sample.md) vzorku.  
  
    - Zvažte použití <xref:System.Runtime.Serialization.ISerializable> rozhraní a deserializace konstruktory – tyto dva mechanismy umožňují přístup k páry klíč/hodnota JSON na serializaci a deserializaci v uvedeném pořadí, ale nebudou fungovat ve scénářích s částečnou důvěryhodností.  
  
    - Zvažte spolupráci s [mapování mezi JSON a XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md) namísto použití serializátor.  
  
    - *Polymorfismus* v kontextu serializace odkazuje na schopnost serializovat odvozeného typu, kde je očekávána jeho základního typu. Existují zvláštní pravidla specifická pro JSON při použití kolekce polymorphically, když je například přiřazení kolekce k <xref:System.Object>. Tento problém je podrobněji popsáno v části Rozšířené informace dále v tomto tématu.  
  
## <a name="additional-details"></a>Další podrobnosti  
  
### <a name="order-of-data-members"></a>Pořadí datových členů  
 Pořadí datových členů není důležité, jestli používáte JSON. Konkrétně, i když <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> nastavena JSON data lze deserializovat stále v libovolném pořadí.  
  
### <a name="json-types"></a>Typy JSON  
 Typ formátu JSON nemá tak, aby odpovídaly v předchozí tabulce k deserializaci. Například `Int` obvykle mapuje na číslo JSON, ale může být také úspěšně deserializovaný z řetězce JSON za předpokladu, že řetězec obsahuje platné číslo. To znamená, že oba {"q": 42} a {"q": "42"} jsou platné, pokud dojde `Int` datový člen s názvem "q".  
  
### <a name="polymorphism"></a>Polymorfismus  
 Polymorfní serializace se skládá z schopnost serializovat odvozeného typu, kde je očekávána jeho základního typu. To platí pro serializaci JSON ve WCF srovnatelné způsobu, jakým serializace XML je podporována. Například může serializovat `MyDerivedType` kde `MyBaseType` očekává nebo serializovat `Int` kde `Object` se očekává.  
  
 Při deserializaci odvozený typ, pokud je předpokládaná doba základního typu, pokud jsou deserializaci komplexní typ, může dojít ke ztrátě informací o typu. Například pokud <xref:System.Uri> kde serializován <xref:System.Object> se očekává, je výsledkem řetězec formátu JSON. Pokud se tento řetězec bude poté deserializován zpět do <xref:System.Object>, .NET <xref:System.String> je vrácena. Deserializátor nezná, řetězec byl zpočátku typu <xref:System.Uri>. Obecně platí ale očekával se <xref:System.Object>, jsou všechny řetězce JSON deserializovat jako řetězce, .NET a všechna pole JSON používaný k serializaci slovníky, kolekcích .NET a pole se deserializovat jako .NET <xref:System.Array> typu <xref:System.Object>bez ohledu na to, co původní skutečný typ byl. Logická hodnota JSON se mapuje na .NET <xref:System.Boolean>. Ale očekáváno <xref:System.Object>, jsou čísla JSON deserializovat jako buď .NET <xref:System.Int32>, <xref:System.Decimal> nebo <xref:System.Double>, kde je nejvhodnější typ automaticky rozpoznat.  
  
 Při deserializaci do typu rozhraní <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> deserializuje, jako kdyby byly deklarovaného typu objektu.  
  
 Při práci s vlastních základních a odvozených typů, pomocí <xref:System.Runtime.Serialization.KnownTypeAttribute>, <xref:System.ServiceModel.ServiceKnownTypeAttribute> nebo podobného mechanismu se obvykle vyžaduje. Například, pokud máte operace, která má `Animal` vrátí hodnotu, ve skutečnosti vrátí instanci `Cat` (odvozený od `Animal`), byste měli použít buď <xref:System.Runtime.Serialization.KnownTypeAttribute>do `Animal` typu nebo <xref:System.ServiceModel.ServiceKnownTypeAttribute> do operaci a zadejte `Cat` typ v těchto atributů. Další informace najdete v tématu [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
 Podrobnosti funguje jak polymorfní serializace a diskuzi o některá omezení, které musí dodržovat při jeho použití naleznete v části Rozšířené informace dále v tomto tématu.  
  
### <a name="versioning"></a>Správa verzí  
 Funkce správy verzí, včetně kontraktu dat <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní, jsou plně podporované ve formátu JSON. Ve většině případů je navíc možné deserializovat typ v jednoho formátu (například XML) a pak ho serializovat do jiného formátu (například JSON) a zároveň zachovat data v <xref:System.Runtime.Serialization.IExtensibleDataObject>. Další informace najdete v tématu [kontraktů dat dopřednou](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Mějte na paměti, že je JSON Neseřazený budou ztraceny žádné informace o objednávce. Kromě toho JSON nepodporuje více dvojic klíč/hodnota s názvem klíče. A konečně, všechny operace na <xref:System.Runtime.Serialization.IExtensibleDataObject> jsou ze své podstaty polymorfní –, který je jejich odvozený typ jsou přiřazeny k <xref:System.Object>, základní typ pro všechny typy.  
  
## <a name="json-in-urls"></a>JSON v adresách URL  
 Při použití s operací HTTP GET koncových bodů ASP.NET AJAX (pomocí <xref:System.ServiceModel.Web.WebGetAttribute> atribut), příchozí parametrů se zobrazí v adrese URL požadavku místo textu zprávy. JSON je podporován i v adrese URL žádosti, takže pokud máte operace, která přebírá `Int` nazývá "cislo" a `Person` složitý typ s názvem "p", adresa URL může vypadat podobně jako následující adresa URL.  
  
```  
http://example.com/myservice.svc/MyOperation?number=7&p={"name":"John","age":42}  
```  
  
 Pokud používáte proxy server a služby ovládací prvek správce skriptů ASP.NET AJAX k vyvolání služby, tato adresa URL je automaticky generován proxy server a není vidět. JSON nelze použít v adresách URL u koncových bodů ASP.NET AJAX.  
  
## <a name="advanced-information"></a>Další informace  
  
### <a name="iserializable-support"></a>Podpora iSerializable  
  
#### <a name="supported-and-unsupported-iserializable-types"></a>Podporované a nepodporované typy ISerializable  
 Obecně platí, typy, které implementují <xref:System.Runtime.Serialization.ISerializable> rozhraní jsou plně podporované při serializaci/deserializaci JSON. Ale některé z těchto typů (včetně některých typů rozhraní .NET Framework) jsou implementovány v tak, že aspekty serializace JSON konkrétní způsobit, že není správně deserializovat:  
  
- S <xref:System.Runtime.Serialization.ISerializable>, typ jednotlivých datových členů nikdy předem známý. To vede k polymorfní situace nějak deserializaci typy do objektu. Jak jsme zmínili, to může vést ke ztrátě informací o typu ve formátu JSON. Například typ, který serializuje `enum` v jeho <xref:System.Runtime.Serialization.ISerializable> provádění a pokusy o deserializaci zpět přímo do `enum` (bez správné přetypování) se nezdaří, protože `enum` serializován pomocí čísla ve formátu JSON a JSON čísla deserializovat do předdefinovaných typů .NET číselné (Int32, Decimal nebo Double). Tak skutečnost, že číslo používal `enum` dojde ke ztrátě hodnoty.  
  
- <xref:System.Runtime.Serialization.ISerializable> Typ, který závisí na konkrétní pořadí deserializace v jeho konstruktor deserializace může selhat také některá data JSON deserializovat, protože většina serializátory JSON není zaručena dodržovat konkrétní pořadí.  
  
#### <a name="factory-types"></a>Objekt pro vytváření typů  
 Zatímco <xref:System.Runtime.Serialization.IObjectReference> rozhraní není podporováno ve formátu JSON v obecné, všechny typy, které vyžadují funkci "typ objektu pro vytváření" (vrací instanci jiného typu než <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%28System.Runtime.Serialization.StreamingContext%29> než typ, který implementuje rozhraní) nejsou podporovány.  
  
### <a name="datetime-wire-format"></a>Formát data a času při přenosu  
 <xref:System.DateTime> Zobrazí hodnoty jako řetězce JSON ve formě "/ Date(700000+0500) /", kde první číslo (v uvedeném příkladu 700000) je počet milisekund v GMT časovém pásmu, pravidelně (úspora letního času) dobu od půlnoci 1. ledna 1970. Číslo může být záporná hodnota, při představují starší časy. Část, která se skládá z "+0500" v příkladu je volitelný a označuje, že je čas <xref:System.DateTimeKind.Local> druh – to znamená, že má být převedena na místní časové pásmo pro deserializaci. Pokud chybí, je čas deserializovat jako <xref:System.DateTimeKind.Utc>. Skutečný počet ("0500" v tomto příkladu) a jeho znaménko (+ nebo -) jsou ignorovány.  
  
 Při serializaci <xref:System.DateTime>, <xref:System.DateTimeKind.Local> a <xref:System.DateTimeKind.Unspecified> časy jsou zapsány s posunem, a <xref:System.DateTimeKind.Utc> je zapsán bez.  
  
 Klient technologie ASP.NET AJAX kódu jazyka JavaScript automaticky převede tyto řetězce do jazyka JavaScript `DateTime` instancí. Pokud existují další řetězce, které mají podobné formuláře, které nejsou typu <xref:System.DateTime> v .NET, jsou také převést.  
  
 Převod zabere jenom umístit Pokud "/" znaky jsou uvozeny řídicími znaky (to znamená, JSON vypadá jako "\\/Date(700000+0500)\\/") a tento důvod WCF JSON encoder (stará <xref:System.ServiceModel.WebHttpBinding>) vždy řídící znak "/".  
  
### <a name="xml-in-json-strings"></a>XML v řetězcích formátu JSON  
  
#### <a name="xmlelement"></a>Třída XmlElement  
 <xref:System.Xml.XmlElement> je serializovat, protože je není obtékané. Například datový člen "x" typ <xref:System.Xml.XmlElement> obsahující \<abc / > je reprezentovaný následujícím způsobem.  
  
```json  
{"x":"<abc/>"}  
```  
  
#### <a name="arrays-of-xmlnode"></a>Polí typu XmlNode  
 <xref:System.Array> objekty typu <xref:System.Xml.XmlNode> jsou zabaleny v elementu s názvem ArrayOfXmlNode v oboru názvů kontraktu standardní datového typu. Pokud "x" je pole, která obsahuje uzel atributu "N" v oboru názvů "ns", který obsahuje "value" a "M" uzlu prázdný elementu, je reprezentace následujícím způsobem.  
  
```  
{"x":"<ArrayOfXmlNode xmlns=\"http://schemas.datacontract.org/2004/07/System.Xml\" a:N=\"value\" xmlns:a=\"ns\"><M/></ArrayOfXmlNode>"}  
```  
  
 Atributy v prázdný obor názvů na začátku polí typu XmlNode (před další prvky) nejsou podporovány.  
  
#### <a name="ixmlserializable-types-including-xelement-and-dataset"></a>Typy rozhraní IXmlSerializable včetně XElement a datové sady  
 <xref:System.Runtime.Serialization.ISerializable> typy rozdělte "typy obsahu", "Typů datových sad" a "typy prvků". Tyto typy definice, naleznete v tématu [typy XML a ADO.NET v kontraktech dat](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).  
  
 "Obsah" a "Datovou sadu" typy serializují podobný <xref:System.Array> objekty <xref:System.Xml.XmlNode> popsané v předchozí části. Jsou zabaleny v elementu jehož názvu a oboru názvů odpovídá názvem kontraktu dat a obor názvů typu.  
  
 Typy, jako "Element" <xref:System.Xml.Linq.XElement> jsou serializovat, protože je podobný <xref:System.Xml.XmlElement> dřív popsané v tomto tématu.  
  
### <a name="polymorphism"></a>Polymorfismus  
  
#### <a name="preserving-type-information"></a>Zachování informací o typu  
 Jak bylo uvedeno dříve, se podporuje polymorfismus ve formátu JSON s určitými omezeními. JavaScript je jazyk slabě typovaná a typ identity není obvykle problém. Ale při použití formátu JSON pro komunikaci mezi systémem silného typu (.NET) a systém slabého typu (JavaScript), je užitečné pro zachování identity typu. Například typy s daty smlouvy názvy, které "Čtverec" a "Kroužek" odvozen z typu s názvem kontraktu dat "Tvar". Pokud "Kruh" se pošle z .NET jazyka JavaScript a později se vrátí do .NET metodu, která očekává, že "Tvar", je vhodné pro .NET na straně vědět, že u daného objektu byl původně "Kruh" – jinak jakékoli informace specifické pro odvozený typ (např. datový člen "radius" na "Kruh") mohou být ztraceny.  
  
 K zachování identity typ při serializaci složitých typů do formátu JSON nápovědu"typ" je možné přidat, a deserializátor rozpozná v pomocném parametru a funguje správně. Nápovědu"typ" je dvojice klíč/hodnota JSON s názvem klíče z "\_\_typu" (dvěma podtržítky následován znakem slova "type"). Hodnota je řetězec JSON ve formě "DataContractName:DataContractNamespace" (NIC až po první dvojtečku je název). Pomocí předchozího příkladu, "Kruh" lze serializovat následujícím způsobem.  
  
```json  
{"__type":"Circle:http://example.com/myNamespace","x":50,"y":70,"radius":10}  
```  
  
 Pomocný parametr typu je velmi podobný `xsi:type` atribut definované standardem Instance schématu XML a nepoužívá, pokud XML serializaci/deserializaci.  
  
 Členové dat s názvem "\_\_typu" jsou zakázáno z důvodu potenciální konflikt se v pomocném parametru typu.  
  
#### <a name="reducing-the-size-of-type-hints"></a>Zmenšení velikosti typu  
 Chcete-li snížit velikost JSON zprávy, předponu oboru názvů kontraktu dat výchozí (`http://schemas.datacontract.org/2004/07/`) se nahradí znak "#". (Chcete-li toto nahrazení vrátit zpět, se používá pravidlo útěku: Pokud obor názvů začíná znakem "#" nebo "\\" znaky, je připojen pomocí speciální "\\" znak). Proto pokud "Kruh" je typ v oboru názvů .NET "MyApp.Shapes", výchozí obor názvů kontraktu dat je `http://schemas.datacontract.org/2004/07/MyApp`. Tvary a reprezentaci JSON vypadá takto.  
  
```json  
{"__type":"Circle:#MyApp.Shapes","x":50,"y":70,"radius":10}  
```  
  
 Zkrácený (#MyApp.Shapes) a úplná (http://schemas.datacontract.org/2004/07/MyApp.Shapes) názvy odhalíte k deserializaci.  
  
#### <a name="type-hint-position-in-json-objects"></a>Pozice pomocný parametr typu v objektech JSON  
 Všimněte si, že v pomocném parametru typu musí být nejdříve uveden v reprezentaci JSON. To platí pouze pokud pořadí párů klíč/hodnota je důležité při zpracování JSON. Například následující není platný způsob, jak určit v pomocném parametru typu.  
  
```json  
{"x":50,"y":70,"radius":10,"__type":"Circle:#MyApp.Shapes"}  
```  
  
 Oba <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> používají WCF a ASP.NET AJAX stránky klienta vždy generovat v pomocném parametru typu nejprve.  
  
#### <a name="type-hints-apply-only-to-complex-types"></a>Pomocné parametry typu platí pouze pro komplexní typy  
 Neexistuje žádný způsob, jak generovat typ nápovědu pro jednoduché typy. Například, pokud je operace <xref:System.Object> návratový typ, ale vrátí kruh, může být reprezentaci JSON, jak je uvedeno výše a zachování informací o typu. Pokud se vrátí identifikátor Uri, reprezentaci JSON je však řetězce a skutečnost, že řetězec použitý k reprezentaci identifikátoru Uri je ztraceny. To platí nejen pro primitivní typy, ale také do kolekce a pole.  
  
#### <a name="when-are-type-hints-emitted"></a>Když jsou emitovány typu  
 Pomocné parametry typu může výrazně zvýšit velikost zprávy (jedním ze způsobů, jak zmírnit jde použít kratší obory názvů kontraktu dat, pokud je to možné). Proto následující pravidla určují, zda jsou emitovány typu:  
  
- Při použití technologie ASP.NET AJAX, typu jsou vždy, protože ho pokaždé, když je to možné, i v případě, že neexistuje žádná základní/odvozené přiřazení – třeba i v případě, že kruhu je přiřazená kruh. (To je potřeba povolit plně procesu volání z prostředí JSON slabého typu do prostředí .NET silného typu bez překvapivé ztráty informací.)  
  
- Pokud používáte služby AJAX bez integrace technologie ASP.NET, typu jsou emitovány pouze po přiřazení základní/odvozené –, který je vygenerován při kruhu je přiřazena tvaru nebo <xref:System.Object> , ale ne, když je přiřazený k kruh. To poskytuje minimální informace požadované pro správnou implementaci jazyka JavaScript klienta, tedy zvýšení výkonu, ale neposkytuje ochranu proti ztrátě informací typu v klientech nesprávně navržen. Pokud chcete se vyhnout s řešením tohoto problému na straně klienta, nepoužívejte na serveru zcela základní/odvozené přiřazení.  
  
- Při použití <xref:System.Runtime.Serialization.DataContractSerializer> typ, `alwaysEmitTypeInformation` parametr konstruktoru umožňuje výběr mezi předchozí dva režimy s výchozím nastavení je "`false`" (pouze generování pomocných parametrů typu v případě potřeby).  
  
#### <a name="duplicate-data-member-names"></a>Duplicitní názvy datových členů  
 Odvozený typ informace se nachází ve stejném objektu JSON spolu s informacemi v základním typu a může dojít v libovolném pořadí. Například `Shape` mohou být zastoupeny následujícím způsobem.  
  
```json  
{"__type":"Shape:#MyApp.Shapes","x":50,"y":70}  
```  
  
 Zatímco kruh může být reprezentován následujícím způsobem.  
  
```json  
{"__type":"Circle:#MyApp.Shapes","x":50, "radius":10,"y":70}  
```  
  
 Pokud základní `Shape` typ také obsažena datový člen s názvem "`radius`", tím dojde ke kolizi na obou serializace, (protože objekty JSON nemůže mít opakující se názvy klíčů) a deserializaci (protože nejasné, zda "radius" odkazuje na `Shape.radius` nebo `Circle.radius`). Proto při pojmu "vlastnost skrytí" (datové členy se stejným názvem na základě a odvozené třídy) se obecně nedoporučuje ve třídách kontraktu dat, je ve skutečnosti zakázaná v případě JSON.  
  
#### <a name="polymorphism-and-ixmlserializable-types"></a>Polymorfismus a IXmlSerializable typy  
 <xref:System.Xml.Serialization.IXmlSerializable> typy může být polymorphically přiřazen k sobě navzájem obvyklým za předpokladu splnění požadavků známé typy podle pravidel obvykle data smlouvy. Serializace však <xref:System.Xml.Serialization.IXmlSerializable> zadejte místo <xref:System.Object> vede ke ztrátě informací o typu jako výsledek je řetězec formátu JSON.  
  
#### <a name="polymorphism-and-certain-interface-types"></a>Polymorfismus a určitých typech rozhraní  
 Je zakázáno pro serializaci kolekce typu nebo typ, který implementuje <xref:System.Xml.Serialization.IXmlSerializable> tam, kde typ jiné kolekce, která není <xref:System.Xml.Serialization.IXmlSerializable> (s výjimkou <xref:System.Object>) se očekává. Například vlastní rozhraní názvem `IMyInterface` a typ `MyType` implementovat oba <xref:System.Collections.Generic.IEnumerable%601> typu `int` a `IMyInterface`. Je zakázáno vrácení `MyType` z operace jehož návratový typ je `IMyInterface`. Důvodem je, že `MyType` musí být serializován jako pole JSON a vyžaduje pomocného parametru typu a jak je uvedeno před nemůže obsahovat parametr typu s poli, jenom s komplexní typy.  
  
#### <a name="known-types-and-configuration"></a>Známé typy a konfigurace  
 Některé mechanismy známý typ používaný <xref:System.Runtime.Serialization.DataContractSerializer> jsou také podporovány stejným způsobem podle <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. Obě serializátory čtení stejného elementu konfigurace [ \<dataContractSerializer >](../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md) v [ \<system.runtime.serialization >](../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md), zjistit známé typy přidán pomocí konfiguračního souboru.  
  
#### <a name="collections-assigned-to-object"></a>Kolekce přiřazen objektu  
 Kolekce, které jsou přiřazeny k objektu serializují jako by šlo kolekce, které implementují <xref:System.Collections.Generic.IEnumerable%601>: pole JSON se každý záznam, který má pomocného parametru typu, pokud se jedná o komplexní typ. Například <xref:System.Collections.Generic.List%601> typu `Shape` přiřazená <xref:System.Object> vypadá podobně jako následující.  
  
```json  
[{"__type":"Shape:#MyApp.Shapes","x":50,"y":70},  
{"__type":"Shape:#MyApp.Shapes","x":58,"y":73},  
{"__type":"Shape:#MyApp.Shapes","x":41,"y":32}]  
```  
  
 Při deserializaci zpět do <xref:System.Object>:  
  
- `Shape` musí být v seznamu známé typy. S <xref:System.Collections.Generic.List%601> typu `Shape` ve známých typů nemá žádný vliv. Všimněte si, že není nutné přidat `Shape` pro známé typy v serializaci v tomto případě – to se provádí automaticky.  
  
- Kolekce je deserializovat jako <xref:System.Array> typu <xref:System.Object> obsahující `Shape` instancí.  
  
#### <a name="derived-collections-assigned-to-base-collections"></a>Odvozené kolekcích přiřazených základní kolekcí  
 Pokud odvozené kolekce je přiřazena k základní kolekce, kolekce obvykle serializován jako by to byla kolekce základního typu. Pokud typ položky kolekce odvozené nelze přiřadit typu položky základní kolekce, je vyvolána výjimka.  
  
#### <a name="type-hints-and-dictionaries"></a>Pomocné parametry typu a slovníky  
 Pokud je slovník přiřazená <xref:System.Object>, každá položka klíče a hodnoty ve slovníku je zpracováván stejně, jako by byla přiřazena <xref:System.Object> a získá pomocný parametr typu.  
  
 Při serializaci typů slovníku, je objekt JSON, který obsahuje členy "Klíče" a "Hodnota" nemá vliv `alwaysEmitTypeInformation` nastavení a pokud to vyžadují výše uvedená pravidla kolekce obsahuje pouze pomocného parametru typu.  
  
### <a name="valid-json-key-names"></a>Názvy klíčů platný kód JSON  
 Serializátor XML kóduje názvy klíčů, které nejsou platné názvy XML. Datový člen s názvem "123" byste mít například kódovaného názvu, jako "\_x0031\_\_x0032\_\_x0033\_" protože "123" je neplatný název elementu XML (začíná číslice). Podobná situace může nastat některých mezinárodních znakových sad v názvu XML není platný. Vysvětlení tohoto efektu XML na zpracování JSON najdete v tématu [mapování mezi JSON a XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
## <a name="see-also"></a>Viz také:

- [Podpora JSON a dalších formátů přenosu dat](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
