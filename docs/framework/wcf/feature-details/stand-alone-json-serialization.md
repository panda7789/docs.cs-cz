---
title: Samostatná serializace JSON
ms.date: 03/30/2017
ms.assetid: 312bd7b2-1300-4b12-801e-ebe742bd2287
ms.openlocfilehash: 5a157dfd55e722b3e7be967a26e8d2ff5fd54afe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509105"
---
# <a name="stand-alone-json-serialization"></a>Samostatná serializace JSON
JSON (JavaScript Object Notation) je formát dat, která je určená speciálně pro používat kód JavaScript spuštěný na webových stránkách otvírala v prohlížeči. Je výchozí formát dat používaný pomocí prvku ASP.NET AJAX služby vytvořené v systému Windows Communication Foundation (WCF).  
  
 Tento formát můžete použít také v případě vytváření služeb AJAX bez integrace s ASP.NET – v takovém případě XML je výchozí nastavení ale JSON je možné vybrat.  
  
 Nakonec, pokud nepožadujete podporu JSON, ale nejsou vytvoření služby AJAX <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> je možné přímo serializaci objektů .NET do JSON data a deserializuje taková data zpět do instance typy .NET. Popis toho, jak to provést, najdete v části [postup: serializaci a deserializaci JSON Data](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).  
  
 Při práci s JSON, stejné typy .NET jsou podporovány, s několika výjimkami, jako jsou podporovány <xref:System.Runtime.Serialization.DataContractSerializer>. Seznam typů podporovány, naleznete v části [typy nepodporuje serializátor kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). To zahrnuje nejvíce primitivní typy, většina pole a typy kolekcí, stejně jako komplexní typy, které používají <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
## <a name="mapping-net-types-to-json-types"></a>Mapování typů .NET pro typy JSON  
 Následující tabulka ukazuje souvislost mezi typy JSON nebo JavaScript při mapovat pomocí procedury serializace a deserializace a rozhraní .NET.  
  
|Typy .NET|JSON nebo JavaScript|Poznámky|  
|----------------|----------------------|-----------|  
|Všechny číselné typy, například <xref:System.Int32>, <xref:System.Decimal> nebo <xref:System.Double>|Číslo|Zvláštní hodnoty jako například `Double.NaN`, `Double.PositiveInfinity` a `Double.NegativeInfinity` nejsou podporovány a mít za následek neplatný JSON.|  
|<xref:System.Enum>|Číslo|Později v tomto tématu najdete v části "A výčty JSON".|  
|<xref:System.Boolean>|Boolean|--|  
|<xref:System.String>, <xref:System.Char>|String|--|  
|<xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>|String|Formát tyto typy ve formátu JSON je stejné jako XML (v podstatě časový interval ve formátu ISO 8601 trvání, GUID ve formátu "12345678-ABCD-ABCD-ABCD-1234567890AB" a identifikátor URI v podobě přirozené řetězec, například "http://www.example.com"). Přesné informace najdete v tématu [Přehled schématu kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).|  
|<xref:System.Xml.XmlQualifiedName>|String|Není ve formátu "název: obor názvů" (NIC před první dvojtečkou název). Název nebo obor názvů se může chybět. Pokud žádný obor názvů je lze vynechat také dvojtečkou.|  
|<xref:System.Array> typu <xref:System.Byte>|Pole čísla|Každé číslo představuje hodnotu jeden bajt.|  
|<xref:System.DateTime>|Data a času nebo řetězec|V tématu kalendářní data nebo časy a JSON později v tomto tématu.|  
|<xref:System.DateTimeOffset>|Komplexní typ|V tématu kalendářní data nebo časy a JSON později v tomto tématu.|  
|Typy XML a ADO.NET (<xref:System.Xml.XmlElement>,<br /><br /> <xref:System.Xml.Linq.XElement>. Pole <xref:System.Xml.XmlNode>,<br /><br /> <xref:System.Runtime.Serialization.ISerializable>,<br /><br /> <xref:System.Data.DataSet>).|String|Najdete v části typy XML a JSON v tomto tématu.|  
|<xref:System.DBNull>|Prázdný komplexní typ|--|  
|Kolekce, slovník a pole|Pole|Najdete v části kolekcí, slovník a pole v tomto tématu.|  
|Komplexní typy (s <xref:System.Runtime.Serialization.DataContractAttribute> nebo <xref:System.SerializableAttribute> použít)|Komplexní typ|Datové členy se stanou členy JavaScript komplexního typu.|  
|Komplexní typy implementace <xref:System.Runtime.Serialization.ISerializable> rozhraní)|Komplexní typ|Stejné jako ostatní komplexní typy, ale některé <xref:System.Runtime.Serialization.ISerializable> typy nejsou podporovány – viz část ISerializable podporu rozšířené informace o části tohoto tématu.|  
|`Null` hodnota pro jakýkoli typ|Null|Typy s možnou hodnotou Null jsou podporovány také a mapovat do formátu JSON stejným způsobem jako typy neumožňující hodnotu Null.|  
  
### <a name="enumerations-and-json"></a>Výčty a JSON  
 Člen hodnoty výčtu jsou považovány za čísel ve formátu JSON, který se liší od jak jsou považovány v kontraktech dat tam, kde jsou zahrnuty jako názvy členů. Další informace o zacházení kontraktu dat najdete v tématu [výčtové typy v kontraktech dat](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
-   Pokud máte například `public enum Color {red, green, blue, yellow, pink}`, serializaci `yellow` vytvoří čísla 3 a není řetězec "žlutá".  
  
-   Všechny `enum` členové jsou serializable. <xref:System.Runtime.Serialization.EnumMemberAttribute> a <xref:System.NonSerializedAttribute> atributy jsou ignorovány, pokud se používá.  
  
-   Je možné k deserializaci neexistující `enum` hodnota – například hodnota 87 může být deserializovat do předchozí výčtu barva i když není žádný odpovídající název barev, které jsou definované.  
  
-   Příznaky `enum` není speciální a chovají stejně jako libovolný jiný `enum`.  
  
### <a name="datestimes-and-json"></a>Data/Times a JSON  
 Formát JSON nepodporuje přímo, data a časy. Ale se velmi často používají a prvku ASP.NET AJAX poskytuje speciální podporu pro tyto typy. Při použití ASP.NET AJAX proxy, <xref:System.DateTime> typu v rozhraní .NET plně odpovídá `DateTime` typ v jazyce JavaScript.  
  
-   Pokud nepoužíváte technologii ASP.NET <xref:System.DateTime> typ je ve formátu JSON reprezentován jako řetězec s speciální formátu, který je popsaný v části Upřesnit informace v tomto tématu.  
  
-   <xref:System.DateTimeOffset> představuje ve formátu JSON jako komplexní typ.: {"Datum a čas": dateTime, "OffsetMinutes": offsetMinutes}. `offsetMinutes` Člen je posun místního času z greenwichský střední čas (GMT), nyní také označuje jako koordinovaný světový čas (UTC), přidružená k umístění události, které vás zajímají. `dateTime` Člen reprezentuje instanci v čase, kdy došlo k události, které vás zajímají (znovu, bude `DateTime` v jazyce JavaScript Pokud prvku ASP.NET AJAX v řetězec a použijte, pokud není). V serializaci `dateTime` člen je vždy serializována v GMT. Pokud popisující 3:00 New Yorku času, tedy `dateTime` má čas součást 8:00 AM a `offsetMinutes` jsou 300 (minus 300 minut nebo 5 hodin od GMT).  
  
    > [!NOTE]
    >  <xref:System.DateTime> a <xref:System.DateTimeOffset> objekty, když serializovat na JSON, pouze zachovat informace, které přesnost milisekundu. Dílčí milisekundu hodnoty (micro/nanosekundách) jsou ztraceny během serializace.  
  
### <a name="xml-types-and-json"></a>Typy XML a JSON  
 Typy XML stát řetězce formátu JSON.  
  
-   Například pokud data člena "d:" z typu XElement obsahuje \<abc / >, JSON je {"d:": "\<abc / >"}.  
  
-   Existují některé speciální pravidla, které zadejte, jak zabalit XML - Další informace najdete v části Upřesnit informace dále v tomto tématu.  
  
-   Pokud jsou pomocí prvku ASP.NET AJAX a nechcete použít řetězce v jazyce JavaScript, ale místo toho chcete XML DOM, nastavte <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> vlastnost XML na <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> vlastnost XML na <xref:System.ServiceModel.Web.WebInvokeAttribute>.  
  
### <a name="collections-dictionaries-and-arrays"></a>Kolekce, slovník a pole  
 Všechny kolekce, slovník a pole jsou ve formátu JSON reprezentovány jako pole.  
  
-   Všechny vlastní nastavení, která používá <xref:System.Runtime.Serialization.CollectionDataContractAttribute> je ignorován v reprezentace JSON.  
  
-   Slovník nejsou způsob, jak pracovat přímo s JSON. Slovník\<řetězec, objekt > nemusí být podporována stejně jako ve WCF podle očekávání v práci s jinými technologiemi JSON. Například pokud "abc" je namapovaná na "xyz" a "def" je namapována na 42 ve slovníku, reprezentace JSON není {"abc": "xyz", "def": 42}, ale [{"Klíč": "abc", "Value": "xyz"}, {"Klíč": "def", "Value": 42}] místo.  
  
-   Pokud chcete pracovat přímo s JSON (přístup ke klíči a hodnotami dynamicky, bez předběžné definování kontraktu pevné), máte několik možností:  
  
    -   Zvažte použití [slabě typované serializace JSON (AJAX)](../../../../docs/framework/wcf/samples/weakly-typed-json-serialization-sample.md) ukázka.  
  
    -   Zvažte použití <xref:System.Runtime.Serialization.ISerializable> rozhraní a deserializace konstruktory - těchto dvou mechanismů vám umožní přístup k páry klíč – hodnota JSON na serializace a deserializace v uvedeném pořadí, ale nefungují ve scénářích s částečnou důvěryhodností.  
  
    -   Vezměte v úvahu práci s [mapování mezi JSON a XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md) místo použití označuje, že serializátor.  
  
    -   *Polymorfismus* v kontextu serializace odkazuje na schopnost odvozený typ, kde je očekávána jeho základní typ serializovat. Při používání kolekce polymorphically, když například přiřazení kolekce se zvláštní JSON specifická pravidla <xref:System.Object>. Tento problém je podrobněji popsán v části Upřesnit informace dále v tomto tématu.  
  
## <a name="additional-details"></a>Další podrobnosti  
  
### <a name="order-of-data-members"></a>Pořadí datových členů  
 Pořadí datových členů není důležité, pokud používáte JSON. Konkrétně, i když <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> nastavena JSON data lze deserializovat stále v libovolném pořadí.  
  
### <a name="json-types"></a>Typy JSON  
 Typ formátu JSON nemá tak, aby odpovídaly v předchozí tabulce k deserializaci. Například `Int` obvykle mapuje JSON číslo, ale může být také úspěšně deserializovaný z JSON řetězce tak dlouho, dokud tento řetězec obsahuje platné číslo. To znamená, i {"d:": 42} a {"d:": "42"} jsou platné, pokud dojde `Int` data člena s názvem "d:".  
  
### <a name="polymorphism"></a>Polymorfismus  
 Polymorfní serializace se skládá z možnost odvozený typ, kde je očekávána jeho základní typ serializovat. Toto je podporováno pro serializaci JSON technologie WCF porovnatelný z hlediska způsobem, jakým serializace XML je podporována. Například může serializovat `MyDerivedType` kde `MyBaseType` je očekávána nebo serializovat `Int` kde `Object` se očekává.  
  
 Při deserializaci odvozený typ, pokud základní typ je očekávané, pokud jsou deserializaci komplexního typu, může dojít ke ztrátě informací o typu. Například pokud <xref:System.Uri> kde serializován <xref:System.Object> je očekávané, výsledkem je to řetězec formátu JSON. Pokud se tento řetězec bude poté deserializován zpět do <xref:System.Object>, .NET <xref:System.String> je vrácen. Deserializátor nebude vědět, že řetězec byla původně typu <xref:System.Uri>. Obecně platí Pokud byla očekávána <xref:System.Object>, všechny řetězce JSON jsou deserializovat jako řetězce .NET a všechna pole JSON používaný k serializaci kolekcí .NET, slovníky, a pole jsou deserializovat jako .NET <xref:System.Array> typu <xref:System.Object>bez ohledu na to, co původní skutečným typem je. Logická hodnota JSON mapuje .NET <xref:System.Boolean>. Ale pokud byla očekávána <xref:System.Object>, JSON čísla se deserializovat jako buď .NET <xref:System.Int32>, <xref:System.Decimal> nebo <xref:System.Double>, kde je nejvhodnější typ automaticky vybráno.  
  
 Při deserializaci do typu rozhraní <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> deserializuje, jako kdyby deklarovaný typ objektu.  
  
 Při práci s vlastními základní a odvozené typy, pomocí <xref:System.Runtime.Serialization.KnownTypeAttribute>, <xref:System.ServiceModel.ServiceKnownTypeAttribute> nebo podobného mechanismu se obvykle vyžaduje. Například, pokud máte operace, která má `Animal` vracet hodnotu a je ve skutečnosti vrátí instanci `Cat` (odvozený od `Animal`), byste měli použít buď <xref:System.Runtime.Serialization.KnownTypeAttribute>do `Animal` typu nebo <xref:System.ServiceModel.ServiceKnownTypeAttribute> na operaci a zadejte `Cat` typu v těchto atributů. Další informace najdete v tématu [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
 Podrobnosti o tom, jak polymorfní serializace funguje a diskuzi o některá omezení, které je nutné dodržovat při používání najdete v části Upřesnit informace dále v tomto tématu.  
  
### <a name="versioning"></a>Správa verzí  
 Správa verzí funkce, včetně kontraktu dat <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní, jsou plně podporovány ve formátu JSON. Ve většině případů je navíc možné deserializovat typ v jednoho formátu (například XML) a pak se serializace do jiného formátu (například JSON) a současně zachovat data v <xref:System.Runtime.Serialization.IExtensibleDataObject>. Další informace najdete v tématu [kontrakty dat dopřednou](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Mějte na paměti, že JSON neuspořádaného, budou ztraceny všechny informace o objednávce. Kromě toho JSON nepodporuje více páry klíč/hodnota se stejným názvem klíče. Nakonec všechny operace v <xref:System.Runtime.Serialization.IExtensibleDataObject> jsou ze své podstaty polymorfní -, která je jejich odvozený typ přiřazené k <xref:System.Object>, základní typ pro všechny typy.  
  
## <a name="json-in-urls"></a>JSON v adresách URL  
 Při použití ASP.NET AJAX koncových bodů s příkazem GET protokolu HTTP (pomocí <xref:System.ServiceModel.Web.WebGetAttribute> atribut), příchozí parametry jsou v adrese URL žádosti místo textu zprávy. JSON je podporována i v adrese URL žádosti, takže pokud máte operace, která přebírá `Int` nazvané "number" a `Person` komplexní typ s názvem "p", adresa URL může být podobná následující adresu URL.  
  
```  
http://example.com/myservice.svc/MyOperation?number=7&p={"name":"John","age":42}  
```  
  
 Pokud používáte služby ovládacího prvku ASP.NET AJAX skript správce a proxy pro volání služby, tato adresa URL je automaticky generován proxy server a není vidět. JSON nelze použít v adresách URL na koncové body prvku ASP.NET AJAX.  
  
## <a name="advanced-information"></a>Informace pro pokročilé uživatele  
  
### <a name="iserializable-support"></a>Podpora iSerializable  
  
#### <a name="supported-and-unsupported-iserializable-types"></a>Podporované a nepodporované typy ISerializable  
 Obecně platí, které implementují typy <xref:System.Runtime.Serialization.ISerializable> rozhraní jsou plně podporované při serializaci nebo deserializaci JSON. Ale některé z těchto typů (včetně některé typy rozhraní .NET Framework) jsou implementované tak, že aspekty serializace JSON konkrétní způsobit není správně deserializovat:  
  
-   S <xref:System.Runtime.Serialization.ISerializable>, typ jednotlivých datových členů je nikdy předem známo. To vede k polymorfní situace podobná deserializaci typy do objektu. Jak je uvedeno nahoře, může to vést ke ztrátě informací o typu ve formátu JSON. Například typ, který serializuje `enum` v jeho <xref:System.Runtime.Serialization.ISerializable> implementace a pokusí se deserializovat zpět přímo do `enum` (bez správné přetypování) se nezdaří, protože `enum` serializován pomocí čísel ve formátu JSON a JSON deserializuje čísla do vestavěné typy rozhraní .NET číselné (Int32, Decimal nebo dvojitou). Proto fakt, že používá číslo jako `enum` dojde ke ztrátě hodnoty.  
  
-   <xref:System.Runtime.Serialization.ISerializable> Typ, který závisí na konkrétní pořadí deserializace v jeho konstruktor deserializace může selhat také k deserializaci některá data JSON, protože většina serializátorů JSON nezaručují dodržovat konkrétní pořadí.  
  
#### <a name="factory-types"></a>Objekt pro vytváření typů  
 Když <xref:System.Runtime.Serialization.IObjectReference> rozhraní se podporuje ve formátu JSON v obecné, všechny typy, které vyžadují funkci "typ objektu pro vytváření" (vrácení jiného typu z instance <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%28System.Runtime.Serialization.StreamingContext%29> než typ, který implementuje rozhraní) nejsou podporovány.  
  
### <a name="datetime-wire-format"></a>Data a času přenosový formát  
 <xref:System.DateTime> hodnoty se zobrazí jako řetězce JSON ve formě "/ Date(700000+0500) /", kde první číslo (700000 v uvedeném příkladu) je počet milisekund, po v GMT časovém pásmu, regulární (bez-letního) čas od půlnoci 1. ledna 1970. Číslo může být záporné představují starší časy. Část, která se skládá z "+0500" v příkladu je volitelný a označuje, že doba je z <xref:System.DateTimeKind.Local> druh – to znamená, by měla být převedena na místní časové pásmo pro deserializaci. Pokud chybí, je čas deserializovat jako <xref:System.DateTimeKind.Utc>. Skutečný počet ("0500" v tomto příkladu) a znaménka (+ nebo -) se ignorují.  
  
 Při serializaci <xref:System.DateTime>, <xref:System.DateTimeKind.Local> a <xref:System.DateTimeKind.Unspecified> časy jsou zapsány s posunem, a <xref:System.DateTimeKind.Utc> je zapsán bez.  
  
 Kód jazyka JavaScript klienta ASP.NET AJAX automaticky převede takové řetězce do jazyka JavaScript `DateTime` instance. Pokud existují další řetězce, které mají podobné formuláře, které nejsou typu <xref:System.DateTime> v rozhraní .NET, jsou také převést.  
  
 Převod pouze probíhá pokud "/" znaky jsou uvozeny uvozovacím znakem (tedy JSON vypadá jako "\\/Date(700000+0500)\\/") a pro tento důvod WCF JSON kodér (povolené ve <xref:System.ServiceModel.WebHttpBinding>) vždy řídicí sekvence znaků "/".  
  
### <a name="xml-in-json-strings"></a>XML v řetězcích JSON  
  
#### <a name="xmlelement"></a>XmlElement.  
 <xref:System.Xml.XmlElement> je serializováno, jako je tomu v žádné zabalení. Například – datový člen "x" typu <xref:System.Xml.XmlElement> obsahující \<abc / > je reprezentovaný následujícím způsobem.  
  
```json  
{"x":"<abc/>"}  
```  
  
#### <a name="arrays-of-xmlnode"></a>XmlNode – pole  
 <xref:System.Array> objekty typu <xref:System.Xml.XmlNode> je uzavřen do elementu s názvem ArrayOfXmlNode v oboru názvů kontraktu standardní data pro typ. Pokud "x" je pole, které obsahuje atribut uzel "N" v oboru názvů "ns", který obsahuje "value" a do uzlu prázdný element "M", reprezentace je následující.  
  
```  
{"x":"<ArrayOfXmlNode xmlns=\"http://schemas.datacontract.org/2004/07/System.Xml\" a:N=\"value\" xmlns:a=\"ns\"><M/></ArrayOfXmlNode>"}  
```  
  
 Atributy v prázdný oboru názvů na začátku XmlNode pole (před další prvky) nejsou podporovány.  
  
#### <a name="ixmlserializable-types-including-xelement-and-dataset"></a>Typy IXmlSerializable včetně XElement a datové sady  
 <xref:System.Runtime.Serialization.ISerializable> typy rozdělte "typy obsahu", "Datovou sadu typů" a "typů element". Definice z těchto typů naleznete v tématu [typy XML a ADO.NET v kontraktech dat](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).  
  
 "Obsah" a "Datovou sadu" typy jsou serializovat podobná <xref:System.Array> objekty <xref:System.Xml.XmlNode> popsané v předchozí části. Jsou zabaleny v elementu, jehož název a obor názvů odpovídá názvu kontraktu dat a obor názvů typu.  
  
 "Elementu" typy, jako <xref:System.Xml.Linq.XElement> jsou serializovat jako je podobná <xref:System.Xml.XmlElement> dřív popsané v tomto tématu.  
  
### <a name="polymorphism"></a>Polymorfismus  
  
#### <a name="preserving-type-information"></a>Zachování informací o typu  
 Jak jsme uvedli dříve, polymorfismus se podporuje ve formátu JSON s omezeními. JavaScript je slabě typované jazyk a typ identita je obvykle není problém. Ale při použití formátu JSON pro komunikaci mezi systémem silného typu (.NET) a systém slabě typované (JavaScript), je užitečná k zachování identity typu. Typy s daty smlouvy například názvy, které "Hranaté" a "V kruhu" jsou odvozeny od typu s názvem kontraktu dat. "Tvar". Pokud "Kruh" se odesílá z rozhraní .NET pro jazyk JavaScript a později je vrácen do .NET metodu, která očekává "Tvar", je vhodné pro rozhraní .NET straně vědět, že u daného objektu byl původně "Kruh" - jinak žádné informace, které jsou specifické pro odvozený typ (např. člen data "radius" na "Kruh") mohou být ztracena.  
  
 K zachování identity typu při serializaci složitých typů JSON nápovědu"typ" lze přidat, a deserializátor rozpozná pomocný parametr a funguje správně. "Pomocný parametr typu" je dvojice klíč/hodnota JSON s názvem klíče "__type" (dvě podtržítka a potom slovo "typ"). Hodnota je řetězec formátu JSON ve tvaru "DataContractName:DataContractNamespace" (NIC až první dvojtečkou je název). Pomocí předchozího příkladu, "Kruh" může serializovat následujícím způsobem.  
  
```json  
{"__type":"Circle:http://example.com/myNamespace","x":50,"y":70,"radius":10}  
```  
  
 Pomocný parametr typu je velmi podobné `xsi:type` atribut definované ve standardu Instance schématu XML a použít při serializaci nebo deserializaci XML.  
  
 Datové členy názvem "__type" jsou zakázáno z důvodu potenciální konfliktu s pomocným parametrem typu.  
  
#### <a name="reducing-the-size-of-type-hints"></a>Zmenšení velikosti této pomocné parametry typu  
 Chcete-li snížit velikost JSON zprávy, Předpona oboru názvů kontraktu dat výchozí (http://schemas.datacontract.org/2004/07/) se nahradí znak "#". (Chcete-li tento nahrazení reverzibilního, se používá pravidlo útěku: Pokud obor názvů začíná "#" nebo "\\" znaky, jsou připojeny navíc "\\" znak). Proto pokud "Kruh" je typu v oboru názvů .NET "MyApp.Shapes", výchozí obor názvů kontraktu dat je http://schemas.datacontract.org/2004/07/MyApp. Tvarů a reprezentace JSON je následující.  
  
```json  
{"__type":"Circle:#MyApp.Shapes","x":50,"y":70,"radius":10}  
```  
  
 Zkrácený (#MyApp.Shapes) a úplná (http://schemas.datacontract.org/2004/07/MyApp.Shapes) jména odhalíte k deserializaci.  
  
#### <a name="type-hint-position-in-json-objects"></a>Typ pozice pomocný parametr v objekty JSON  
 Všimněte si, že pomocný parametr typu musí být nejdříve uveden v reprezentace JSON. Toto je pouze případě, je důležité při zpracování JSON pořadí dvojic klíč/hodnota. Například následující není platný způsob, jak určit pomocný parametr typu.  
  
```json  
{"x":50,"y":70,"radius":10,"__type":"Circle:#MyApp.Shapes"}  
```  
  
 Jak <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> používané WCF a ASP.NET AJAX stránky klient vždy emitování pomocný parametr typu první.  
  
#### <a name="type-hints-apply-only-to-complex-types"></a>Pomocné parametry typu platí pouze pro komplexní typy  
 Neexistuje žádný způsob, jak emitování typ nápovědu pro jednoduché typy. Například, pokud má operace <xref:System.Object> návratový typ, ale vrátí kruh, může být reprezentace JSON, jako je uvedené výše a uchování informací o typu. Ale pokud identifikátor Uri je vrácena, reprezentace JSON je řetězec a skutečnost, že je řetězec představující identifikátoru Uri ztraceny. To platí pouze pro primitivní typy, ale také do kolekcí a pole.  
  
#### <a name="when-are-type-hints-emitted"></a>Když jsou pomocné parametry typu vygenerované  
 Pomocné parametry typu může výrazně zvýšit velikost zprávy (jeden ze způsobů, jak zmírnit jde použít kratší obory názvů kontraktu dat. Pokud je to možné). Proto platí následující pravidla, zda jsou vygenerované pomocné parametry typu:  
  
-   Když pomocí prvku ASP.NET AJAX, pomocné parametry typu jsou vždy vygenerované kdykoli je to možné, i v případě, že neexistuje žádná základní nebo odvozené přiřazení – například i v případě, že kroužek je přiřazena k kruh. (To je potřeba pro plné zpřístupnění proces volání z prostředí slabě typované JSON do prostředí .NET silného typu bez překvapivé ztráty informací.)  
  
-   Při použití služby AJAX s bez integrace ASP.NET, pomocné parametry typu jenom vygenerované při přiřazení základní nebo odvozené – který se vygenerované při kroužek je přiřazena k tvar nebo <xref:System.Object> ale ne v případě přiřazení ke kruh. To poskytuje minimální informace požadované pro správně implementace klienta JavaScript, tedy zvýšení výkonu, ale neposkytuje ochranu proti ztrátě informací typu v nesprávně určené klienty. Pokud chcete, aby se zabránilo s řešením tohoto problému v klientovi, vyhněte na serveru zcela základní nebo odvozené přiřazení.  
  
-   Při použití <xref:System.Runtime.Serialization.DataContractSerializer> typu, `alwaysEmitTypeInformation` parametr konstruktoru umožňuje výběr mezi předchozí dva režimy s výchozím nastavení se "`false`" (pouze emitování pomocné parametry typu případě potřeby).  
  
#### <a name="duplicate-data-member-names"></a>Duplicitní názvy datových členů  
 Odvozený typ informace se nachází ve stejném objektu JSON spolu s informacemi základní typ a může dojít v libovolném pořadí. Například `Shape` může být reprezentován následujícím způsobem.  
  
```json  
{"__type":"Shape:#MyApp.Shapes","x":50,"y":70}  
```  
  
 Zatímco kruh může být reprezentován následujícím způsobem.  
  
```json  
{"__type":"Circle:#MyApp.Shapes","x":50, "radius":10,"y":70}  
```  
  
 Pokud základní `Shape` typ také obsažená data člena s názvem "`radius`", to vede k kolize na obou serializace (protože objekty JSON nemůže mít opakující se názvy klíčů) a deserializace (protože je jasné, jestli se "radius" odkazuje na `Shape.radius` nebo `Circle.radius`). Proto při koncepci "vlastnost skrytí" (datové členy se stejným názvem na základě a odvozených třídách) se obecně nedoporučuje v třídách kontraktu dat, je ve skutečnosti zakázáno v případě JSON.  
  
#### <a name="polymorphism-and-ixmlserializable-types"></a>Polymorfismus a IXmlSerializable typy  
 <xref:System.Xml.Serialization.IXmlSerializable> typy polymorphically přiřazeni k sobě navzájem obvyklým tak dlouho, dokud známé typy požadavků, podle pravidel kontrakt obvykle data. Ale serializaci <xref:System.Xml.Serialization.IXmlSerializable> zadejte místě <xref:System.Object> vede ke ztrátě informací o typu jako výsledek je řetězec formátu JSON.  
  
#### <a name="polymorphism-and-certain-interface-types"></a>Polymorfismus a určitých typech rozhraní  
 Je zakázáno k serializaci kolekce typ nebo typ, který implementuje <xref:System.Xml.Serialization.IXmlSerializable> tam, kde typ není kolekce, který není <xref:System.Xml.Serialization.IXmlSerializable> (s výjimkou <xref:System.Object>) se očekává. Například vlastní rozhraní nazývá `IMyInterface` a typ `MyType` , jak implementovat <xref:System.Collections.Generic.IEnumerable%601> typu `int` a `IMyInterface`. Je zakázáno vrácení `MyType` z operace s návratovým typem `IMyInterface`. Důvodem je, že `MyType` musí být serializované jako pole JSON a vyžaduje typ nápovědu a jak je uvedeno před nesmí obsahovat nápovědu typ s poli jenom s komplexními typy.  
  
#### <a name="known-types-and-configuration"></a>Známé typy a konfigurace  
 Všechny mechanismů známý typ používané <xref:System.Runtime.Serialization.DataContractSerializer> jsou podporovány také stejným způsobem, pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. Obě serializátorů číst stejného elementu konfigurace [ \<dataContractSerializer >](../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md) v [ \<system.runtime.serialization >](../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md), ke zjištění známé typy přidán prostřednictvím konfiguračního souboru.  
  
#### <a name="collections-assigned-to-object"></a>Kolekcích přiřazených k objektu  
 Kolekce, které jsou přiřazeny k objektu se serializují jako v případě, že jsou kolekce, které implementují <xref:System.Collections.Generic.IEnumerable%601>: pole JSON s každou položku, která obsahuje pokyn typu, pokud je komplexního typu. Například <xref:System.Collections.Generic.List%601> typu `Shape` přiřazené <xref:System.Object> vypadá podobně jako následující.  
  
```json  
[{"__type":"Shape:#MyApp.Shapes","x":50,"y":70},  
{"__type":"Shape:#MyApp.Shapes","x":58,"y":73},  
{"__type":"Shape:#MyApp.Shapes","x":41,"y":32}]  
```  
  
 Při deserializaci zpět do <xref:System.Object>:  
  
-   `Shape` musí být v seznamu známé typy. S <xref:System.Collections.Generic.List%601> typu `Shape` v známé typy nemá žádný vliv. Všimněte si, že není třeba přidávat `Shape` na známé typy na serializaci v tomto případě - udělá se to automaticky.  
  
-   Kolekce se deserializovat jako <xref:System.Array> typu <xref:System.Object> obsahující `Shape` instance.  
  
#### <a name="derived-collections-assigned-to-base-collections"></a>Odvozené kolekcích přiřazených do základní kolekcí  
 Při odvozené kolekce je přiřazena k základní kolekce, kolekce obvykle serializovat, jako kdyby byl kolekce základního typu. Pokud typ položky odvozené kolekce nelze nastavit na typ položky základní kolekce, je vyvolána výjimka.  
  
#### <a name="type-hints-and-dictionaries"></a>Pomocné parametry typu a slovník  
 Když je slovník přiřazení <xref:System.Object>, každou položku klíče a hodnoty ve slovníku považuje, jako kdyby byl přiřazen <xref:System.Object> a získá pomocný parametr typu.  
  
 Při serializaci typy slovník, je objekt JSON, který obsahuje členy "Klíč" a "Value" nemá vliv `alwaysEmitTypeInformation` nastavení a pokud to vyžadují výše uvedená pravidla kolekce obsahuje pouze typ nápovědu.  
  
### <a name="valid-json-key-names"></a>Názvy klíčů platný kód JSON  
 Serializátor XML kóduje názvy klíčů, které nejsou platné názvy XML. Například datový člen s názvem "123" by mít kódovaného název jako "_x0031\__x0032\__x0033\_" protože "123" je neplatný název elementu XML (začíná číslice). Podobné situace může nastat u některé mezinárodní znakové sady v názvech XML není platná. Další informace o této účinku XML na zpracování JSON, najdete v části [mapování mezi JSON a XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
## <a name="see-also"></a>Viz také  
 [Podpora JSON a dalších formátů přenosu dat](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
