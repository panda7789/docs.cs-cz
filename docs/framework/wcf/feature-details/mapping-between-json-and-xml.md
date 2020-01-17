---
title: Mapování mezi JSON a XML
ms.date: 03/30/2017
ms.assetid: 22ee1f52-c708-4024-bbf0-572e0dae64af
ms.openlocfilehash: 0dbe37a07024ae70e574b92582715d2d2ef52e5c
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212084"
---
# <a name="mapping-between-json-and-xml"></a>Mapování mezi JSON a XML
Čtečky a zapisovače vytvářené <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory> poskytují obsah XML API pro JavaScript Object Notation (JSON). JSON kóduje data pomocí podmnožiny literálů objektů JavaScriptu. Čtenáři a zapisovače vytvořené pomocí této továrny se používají také v případě, že aplikace Windows Communication Foundation (WCF) odesílá nebo přijímá obsah JSON pomocí <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement> nebo <xref:System.ServiceModel.WebHttpBinding>.

Při inicializaci s obsahem JSON se čtečka JSON chová stejným způsobem jako textový čtecí modul XML, který se nachází v instanci XML. Zapisovač JSON, pokud je výsledkem posloupnosti volání, která na textovém čtecím modulu XML vytvoří určitou instanci XML, zapisuje obsah JSON. Mapování mezi touto instancí XML a obsahem JSON je popsané v tomto tématu, které se používá v pokročilých scénářích.

KÓD JSON je interně reprezentován jako informační sada XML při zpracování službou WCF. Obvykle se nemusíte zabývat těmito interními reprezentacemi, protože mapování je pouze logické: JSON obvykle není fyzicky převeden na XML v paměti nebo převeden na JSON z XML. Mapování znamená, že rozhraní API XML se používají pro přístup k obsahu JSON.

Pokud WCF používá JSON, je obvyklým scénářem, že je <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> automaticky zapojen do <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> chování, nebo podle potřeby <xref:System.ServiceModel.Description.WebHttpBehavior> chování. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> rozumí mapování mezi JSON a XML a funguje, jako by se jednalo přímo s JSON. (Je možné použít <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> s libovolným čtecím modulem XML nebo zapisovačem a pochopit, že XML odpovídá následujícímu mapování.)

V pokročilých scénářích může být nutné získat přímý přístup k následujícímu mapování. K těmto scénářům dochází v případě, že chcete serializovat a deserializovat JSON vlastními způsoby, aniž byste se museli spoléhat na <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, nebo při řešení <xref:System.ServiceModel.Channels.Message> typu přímo pro zprávy obsahující JSON. Mapování JSON-XML se používá také k protokolování zpráv. Při použití funkce protokolování zpráv ve službě WCF se zprávy JSON protokolují jako XML podle mapování popsaných v následující části.

Pro objasnění konceptu mapování je následující příklad dokumentu JSON.

```json
{"product":"pencil","price":12}
```

Chcete-li tento dokument JSON přečíst pomocí některého z výše zmíněných čtenářů, použijte stejné pořadí <xref:System.Xml.XmlDictionaryReader> volání jako při čtení následujícího dokumentu XML.

```xml
<root type="object">
    <product type="string">pencil</product>
    <price type="number">12</price>
</root>
```

Kromě toho, pokud je zpráva JSON v příkladu přijata službou WCF a protokoluje, zobrazí se v předchozím protokolu fragment XML.

## <a name="mapping-between-json-and-the-xml-infoset"></a>Mapování mezi JSON a dokumentovou informační sadu XML

Mapování je mezi JSON tak, jak je popsané v [dokumentu RFC 4627](https://www.ietf.org/rfc/rfc4627.txt) (s výjimkou některých omezení, která byla uvolněna a určitá jiná omezení), a XML data (a nikoli text XML), jak je popsáno v [sadě informací XML](https://www.w3.org/TR/2004/REC-xml-infoset-20040204/). V tomto tématu najdete definice *položek informací* a polí v [hranatých závorkách].

Prázdný dokument JSON se mapuje do prázdného dokumentu XML a do prázdného dokumentu JSON se mapuje prázdný dokument XML. V mapování XML na JSON před tím, než je dokument povolený, před prázdným prázdným znakem a koncovým prázdným znakem.

Mapování je definováno buď mezi položkou informací dokumentu (DII), nebo položkou informací o elementu (EII) a kódem JSON. Vlastnost EII nebo DII elementu [Document element] je označována jako kořenový element JSON. Všimněte si, že v tomto mapování nejsou podporovány fragmenty dokumentů (XML s více kořenovými prvky).

Příklad: následující dokument:

```xml
<?xml version="1.0"?>
<root type="number">42</root>
```

A následující element:

```xml
<root type="number">42</root>
```

Oba mají mapování na JSON. Prvek <`root`> je kořenovým elementem JSON v obou případech.

V případě DII je navíc vhodné zvážit následující:

- Některé položky v seznamu [children] nesmí být k dispozici. Nespoléhá na tento fakt při čtení XML mapovaných z JSON.

- V seznamu [children] jsou uloženy žádné položky s informacemi o komentářích.

- Seznam [children] obsahuje žádné položky informací DTD.

- Seznam [children] obsahuje žádné položky informací o osobní informaci (PI) (deklarace `<?xml…>` není považována za informační položku PI).

- Sada [Notations] je prázdná.

- Sada [nezpracované entity] je prázdná.

Příklad: následující dokument nemá mapování na JSON, protože [children] obsahuje PI a komentář.

```xml
<?xml version="1.0"?>
<!--comment--><?pi?>
<root type="number">42</root>
```

EII pro kořenový element JSON má následující vlastnosti:

- [místní název] má hodnotu root.

- [název oboru názvů] nemá žádnou hodnotu.

- [prefix] nemá žádnou hodnotu.

- [children] může buď obsahovat EIIs (reprezentující vnitřní prvky, jak je popsáno dále), nebo CIIs (položky informací o znacích jak je popsáno dále) nebo žádné z nich, ale ne obojí.

- [atributy] mohou obsahovat následující volitelné položky informací o atributu (AIIs).

- Atribut typu JSON ("Type"), jak je popsáno dále. Tento atribut se používá k zachování typu JSON (řetězec, číslo, logická hodnota, objekt, pole nebo hodnota null) v mapovaném XML.

- Atribut názvu kontraktu dat ("\_\_typ"), jak je popsáno dále. Tento atribut může být k dispozici pouze v případě, že je současně přítomen atribut typu JSON a jeho [normalizovaná hodnota] je "Object". Tento atribut je používán `DataContractJsonSerializer` k zachování informací o typu kontraktu dat – například v polymorfních případech, kde je odvozený typ serializován a kde je očekáván základní typ. Pokud s `DataContractJsonSerializer`nepracujete, ve většině případů se tento atribut ignoruje.

- [in-Scope Namespaces] obsahuje vazbu "XML" pro `http://www.w3.org/XML/1998/namespace` podle specifikace informační sady.

- [podřízené], [atributy] a [obor názvů v oboru] nesmí mít žádné jiné položky než uvedené dříve a [atributy oboru názvů] nesmí mít žádné členy, ale při čtení XML mapovaných z JSON nespoléhají na tyto fakty.

Příklad: následující dokument nemá mapování na JSON, protože [atributy oboru názvů] není prázdné.

```xml
<?xml version="1.0"?>
<root xmlns:a="myattributevalue">42</root>
```

VŠE pro atribut typu JSON má následující vlastnosti:

- [název oboru názvů] nemá žádnou hodnotu.
- [prefix] nemá žádnou hodnotu.
- [místní název] je "typ".
- [normalizovaná hodnota] je jednou z možných hodnot typu popsaných v následující části.
- [zadané] je `true`.
- [typ atributu] nemá žádnou hodnotu.
- [odkazy] nemá žádnou hodnotu.

VŠE pro atribut název kontraktu dat má následující vlastnosti:

- [název oboru názvů] nemá žádnou hodnotu.
- [prefix] nemá žádnou hodnotu.
- [místní název] je "\_\_typ" (dvě podtržítka a pak "Type").
- [normalizovaná hodnota] je libovolný platný řetězec Unicode – mapování tohoto řetězce na formát JSON je popsáno v následující části.
- [zadané] je `true`.
- [typ atributu] nemá žádnou hodnotu.
- [odkazy] nemá žádnou hodnotu.

Vnitřní prvky obsažené v kořenovém elementu JSON nebo jiné vnitřní prvky mají následující vlastnosti:

- [místní název] může mít libovolnou hodnotu, jak je popsáno dále.
- [název oboru názvů], [prefix], [podřízené], [atributy], [atributy oboru názvů] a [obor názvů v oboru] podléhá stejným pravidlům jako kořenový element JSON.

V kořenovém elementu JSON i v vnitřních prvcích definuje atribut typu JSON mapování na JSON a možné [podřízené] a jejich výklad. Atribut [normalizovaná hodnota] rozlišuje velká a malá písmena a musí být malými písmeny a nesmí obsahovat prázdné znaky.

|[normalizovaná hodnota] vše atributu typu JSON|Povoleno [children] odpovídající EII|Mapování na JSON|
|---------------------------------------------------------|---------------------------------------------------|---------------------|
|`string` (nebo absence vše typu JSON)<br /><br /> `string` a absence typu vše JSON jsou stejné, `string` výchozí.<br /><br /> Proto se `<root> string1</root>` mapuje na JSON `string` "řetězec1".|0 nebo více CIIs|`string` JSON (JSON RFC, oddíl 2,5). Každý `char` je znak, který odpovídá kódu [kód znaku] z CII. Pokud neexistují žádné CIIs, namapuje se na prázdný `string`JSON.<br /><br /> Příklad: následující element se mapuje na fragment JSON:<br /><br /> `<root type="string">42</root>`<br /><br /> Fragment kódu JSON je "42".<br /><br /> U mapování XML na JSON jsou znaky, které musí být uvozeny řídicími znaky, mapovány na řídicí znaky, všechny ostatní mapují na znaky, které nejsou uvozeny řídicími znaky. Znak "/" je zvláštní – je uvozený řídicím znakem, i když nemusí být (zapsán jako "\\/").<br /><br /> Příklad: následující element se mapuje na fragment JSON.<br /><br /> `<root type="string">the "da/ta"</root>`<br /><br /> Fragment kódu JSON je "\\" da\\/ta\\"".<br /><br /> U mapování JSON na XML jsou všechny řídicí znaky a znaky, které nejsou uvozeny řídicími znaky, správně mapovány na odpovídající [kód znaku].<br /><br /> Příklad: fragment JSON "\u0041BC", který se mapuje na následující XML element.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Řetězec může být obklopen prázdným znakem (' WS ' v sekci 2 specifikace RFC JSON), které není mapováno na XML.<br /><br /> Příklad: fragment kódu JSON "ABC", (existují mezery před první dvojitou uvozovkou), jsou mapovány na následující prvek XML.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Jakékoli prázdné znaky v XML mapuje na prázdné místo ve formátu JSON.<br /><br /> Příklad: následující element XML se mapuje na fragment JSON.<br /><br /> `<root type="string">  A BC      </root>`<br /><br /> Fragment kódu JSON je "A BC".|
|`number`|1 nebo více CIIs|`number` JSON (JSON RFC, oddíl 2,4), může být ohraničený prázdným znakem. Každý znak v kombinaci číslo/mezera je znak, který odpovídá kódu [kód znaku] z CII.<br /><br /> Příklad: následující element se mapuje na fragment JSON.<br /><br /> `<root type="number">    42</root>`<br /><br /> Fragment kódu JSON je 42.<br /><br /> (Prázdné místo se zachová).|
|`boolean`|4 nebo 5 CIIs (což odpovídá `true` nebo `false`), může být obklopeno dalšími prázdnými CIIs.|CII sekvence, která odpovídá řetězci "true", je namapována na literál `true`a sekvence CII, která odpovídá řetězci "false", je namapována na literální `false`. Okolní prázdné znaky jsou zachovány.<br /><br /> Příklad: následující element se mapuje na fragment JSON.<br /><br /> `<root type="boolean"> false</root>`<br /><br /> Fragment JSON je `false`.|
|`null`|Není povoleno.|Literál `null`. Při mapování JSON na XML může být `null` obklopen mezerou (' WS ' v sekci 2), která není mapována na XML.<br /><br /> Příklad: následující element se mapuje na fragment JSON.<br /><br /> `<root type="null"/>`<br /><br /> nebo<br /><br /> `<root type="null"></root>`<br /><br /> :<br /><br /> Fragment JSON v obou případech je `Null`.|
|`object`|0 nebo více EIIs.|`begin-object` (levá složená závorka) jako v sekci 2,2 specifikace RFC JSON následovaný záznamem člena pro každý EII, jak je popsáno dále. Pokud existuje více než jeden EII, jsou mezi záznamy členů tyto oddělovače hodnot (čárky). Vše je následováno koncovým objektem (pravá složená závorka).<br /><br /> Příklad: následující element se mapuje na fragment JSON.<br /><br /> `<root type="object">`<br /><br /> `<type1 type="string">aaa\</type1>`<br /><br /> `<type2 type="string">bbb\</type2>`<br /><br /> `</root >`<br /><br /> Fragment JSON je `{"type1":"aaa","type2":"bbb"}`.<br /><br /> Pokud je v mapování XML na JSON přítomen atribut typu kontraktu dat, vloží se na začátek záznam dalšího člena. Jeho název je [místní název] atributu typu kontraktu dat ("\_\_typ") a jeho hodnota je atribut [normalizovaná hodnota]. Naopak při mapování JSON na XML, pokud je první název záznamu člena [místní název] atributu typu kontraktu dat (to znamená "\_\_typ"), v mapovaném XML je přítomen odpovídající atribut typu kontraktu dat, ale odpovídající EII není k dispozici. Všimněte si, že tento záznam člena se musí nacházet jako první v objektu JSON, aby bylo toto speciální mapování použito. To představuje odchod z obvyklého zpracování JSON, kde pořadí záznamů členů není významné.<br /><br /> Příklad:<br /><br /> Následující fragment JSON mapuje na XML.<br /><br /> `{"__type":"Person","name":"John"}`<br /><br /> Kód XML je následující kód.<br /><br /> `<root type="object" __type="Person">   <name type="string">John</name> </root>`<br /><br /> Všimněte si, že \_typ \_vše je k dispozici, ale neexistuje žádný \_\_typ EII.<br /><br /> Pokud je však objednávka ve formátu JSON obrácena, jak je znázorněno v následujícím příkladu.<br /><br /> `{"name":"John","\_\_type":"Person"}`<br /><br /> Zobrazí se odpovídající XML.<br /><br /> `<root type="object">   <name type="string">John</name>   <__type type="string">Person</__type> </root>`<br /><br /> To znamená, \__type přestane mít zvláštní význam a mapuje se na EII jako obvykle, ne vše.<br /><br /> Pravidla uvozovacího a deuvozovacích znaků pro vše [normalizovaná hodnota] při mapování na hodnotu JSON jsou stejná jako u řetězců JSON, které jsou zadané v řadě "řetězec" této tabulky.<br /><br /> Příklad:<br /><br /> `<root type="object" __type="\abc" />`<br /><br /> na předchozí příklad lze namapovat na následující JSON.<br /><br /> `{"__type":"\\abc"}`<br /><br /> U mapování XML na JSON nesmí první EII [místní název] být "\_\_typ.<br /><br /> Prázdné znaky (`ws`) se nikdy negeneruje pro mapování XML na JSON pro objekty a v mapování JSON na XML se ignoruje.<br /><br /> Příklad: následující fragment JSON mapuje na XML element.<br /><br /> `{ "ccc" : "aaa", "ddd" :"bbb"}`<br /><br /> Element XML je zobrazen v následujícím kódu.<br /><br /> `<root type="object">    <ccc type="string">aaa</ccc>    <ddd type="string">bbb</bar> </root >`|
|pole|0 nebo více EIIs|Počáteční pole (levá hranatá závorka), jako v sekci 2,3 specifikace RFC JSON následovaný záznamem pole pro každý EII, jak je popsáno dále. Pokud existuje více než jeden EII, jsou mezi záznamy pole oddělovače hodnot (čárky). Vše je následováno koncovým polem.<br /><br /> Příklad: následující element XML se mapuje na fragment JSON.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`<br /><br /> Fragment JSON je `["aaa","bbb"]`.<br /><br /> Prázdné znaky (`ws`) se nikdy negeneruje pro mapování XML na JSON pro pole a v mapování JSON na XML se ignoruje.<br /><br /> Příklad: fragment JSON.<br /><br />`["aaa", "bbb"]`<br /><br /> Element XML, na který je namapován.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`|

Záznamy členů fungují následujícím způsobem:

- [Místní název] vnitřního elementu se mapuje na `string` část `member`, jak je definováno v sekci 2,2 dokumentu RFC JSON.

Příklad: následující element se mapuje na fragment JSON.

```xml
<root type="object"/>
<myLocalName type="string">aaa</myLocalName>
</root >
```

Zobrazí se následující fragment JSON.

```json
{"myLocalName":"aaa"}
```

- V mapování XML na JSON jsou znaky, které musí být uvozeny řídicími znaky ve formátu JSON, uvozeny řídicími znaky a ostatní nejsou uvozeny řídicími znaky. Znak "/", i když se nejedná o znak, který musí být uvozen řídicím znakem, je ale řídicí znak, který se nemusí nacházet při mapování JSON na XML. To je nutné pro podporu formátu ASP.NET AJAX pro `DateTime` data ve formátu JSON.

- V mapování JSON na XML jsou všechny znaky (včetně neřídicích znaků, pokud je potřeba) pořízeny `string`, který vytváří [místní název].

- Vnitřní prvky [children] se mapují na hodnotu v sekci 2,2, podle `JSON Type Attribute` stejně jako u `Root JSON Element`. Je povoleno více úrovní vnořování EIIs (včetně vnoření do polí).

Příklad: následující element se mapuje na fragment JSON.

```xml
<root type="object">
    <myLocalName1 type="string">myValue1</myLocalName1>
    <myLocalName2 type="number">2</myLocalName2>
    <myLocalName3 type="object">
        <myNestedName1 type="boolean">true</myNestedName1>
        <myNestedName2 type="null"/>
    </myLocalName3>
</root >
```

Následující fragment kódu JSON je namapován na.

```json
{"myLocalName1":"myValue1","myLocalName2":2,"myLocalName3":{"myNestedName1":true,"myNestedName2":null}}
```

> [!NOTE]
> V předchozím mapování není žádný krok XML kódování. Proto WCF podporuje pouze dokumenty JSON, kde všechny znaky v názvech klíčů jsou platné znaky v názvech prvků XML. Například dokument JSON {"<": "a"} není podporován, protože < není platným názvem elementu XML.

Zpětná situace (ve znacích XML, ale ne ve formátu JSON) nezpůsobí žádné problémy, protože předchozí mapování obsahuje kroky pro uvozovací a deuvozovací znaky JSON.

Záznamy pole fungují následujícím způsobem:

- [Místní název] vnitřního elementu je Item.

- Vnitřní prvek [children] je mapován na hodnotu v oddílu 2,3 podle atributu typu JSON, který je pro kořenový element JSON. Je povoleno více úrovní vnořování EIIs (včetně vnoření uvnitř objektů).

Příklad: následující element se mapuje na fragment JSON.

```xml
<root type="array"/>
    <item type="string">myValue1</item>
    <item type="number">2</item>
    <item type="array">
    <item type="boolean">true</item>
    <item type="null"/></item>
</root >
```

Následuje fragment kódu JSON.

```json
["myValue1",2,[true,null]]
```

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>
- [Samostatná serializace JSON](stand-alone-json-serialization.md)
