---
title: Mapování mezi JSON a XML
ms.date: 03/30/2017
ms.assetid: 22ee1f52-c708-4024-bbf0-572e0dae64af
ms.openlocfilehash: 55812ad15d1f38bb0c295e6895dfff329035206d
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464068"
---
# <a name="mapping-between-json-and-xml"></a>Mapování mezi JSON a XML
Čtenáři a autoři <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory> vytvořené poskytují XML API přes JavaScript zápis objektu (JSON) obsah. JSON kóduje data pomocí podmnožiny literál objektu JavaScriptu. Čtenáři a autoři vyrobené v této továrně se také používají při json obsah je <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement> odesílán nebo přijímán Windows Communication Foundation (WCF) aplikace pomocí nebo <xref:System.ServiceModel.WebHttpBinding>.

Při inicializování s obsahem JSON se čtečka JSON chová stejným způsobem jako textová čtečka XML přes instanci XML. Zapisovač JSON, když dostal posloupnost volání, která na textové matné čtečce XML vytvoří určitou instanci XML, zapíše obsah JSON. Mapování mezi touto instancí XML a obsahem JSON je popsáno v tomto tématu pro použití v pokročilých scénářích.

Interně json je reprezentován jako xml infoset při zpracování WCF. Obvykle se nemusíte zabývat touto vnitřní reprezentací, protože mapování je pouze logické: JSON obvykle není fyzicky převeden na XML v paměti nebo převeden na JSON z XML. Mapování znamená, že rozhraní XML API se používají pro přístup k obsahu JSON.

Když WCF používá JSON, obvyklý <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> scénář je, že <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> je automaticky zapojen <xref:System.ServiceModel.Description.WebHttpBehavior> chování nebo chování v případě potřeby. Rozumí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> mapování mezi JSON a xml infoset a chová, jako by se zabývá JSON přímo. (Je možné použít <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> s libovolnou čtečku XML nebo zapisovatel, s vědomím, že XML odpovídá následující mapování.)

V pokročilých scénářích může být nutné získat přímý přístup k následujícímu mapování. Tyto scénáře nastat, pokud chcete serializovat a rekonstruovat JSON vlastní způsoby, bez spoléhání se na <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, nebo při práci s typem <xref:System.ServiceModel.Channels.Message> přímo pro zprávy obsahující JSON. Mapování JSON-XML se používá také pro protokolování zpráv. Při použití funkce protokolování zpráv v WCF, JSON zprávy jsou zaznamenány jako XML podle mapování popsaného v další části.

Chcete-li objasnit pojem mapování, následující příklad je dokumentu JSON.

```json
{"product":"pencil","price":12}
```

Chcete-li číst tento dokument JSON pomocí jednoho z čtenářů <xref:System.Xml.XmlDictionaryReader> výše uvedených, použijte stejnou posloupnost volání jako byste číst následující dokument XML.

```xml
<root type="object">
    <product type="string">pencil</product>
    <price type="number">12</price>
</root>
```

Kromě toho pokud zpráva JSON v příkladu je přijatwcf a zaznamenány, uvidíte fragment XML v předchozím protokolu.

## <a name="mapping-between-json-and-the-xml-infoset"></a>Mapování mezi jazykem JSON a informační sadou XML

Formálně je mapování mezi JSON, jak je popsáno v [RFC 4627](https://www.ietf.org/rfc/rfc4627.txt) (s výjimkou určitých omezení uvolněná a některá další omezení přidána) a XML infoset (a ne textové XML), jak je popsáno v [XML Information Set](https://www.w3.org/TR/2004/REC-xml-infoset-20040204/). Definice *informačních položek* a polí v [hranaté závorce].

Prázdný dokument JSON se mapuje na prázdný dokument XML a prázdný dokument XML se mapuje na prázdný dokument JSON. V mapování XML na JSON nejsou povoleny předchozí prázdné znaky a koncové prázdné znaky za dokumentem.

Mapování je definováno mezi položkou informace o dokumentu (DII) nebo položkou informací o prvku (EII) a jsonem. EII nebo DII [document element] vlastnost, se označuje jako kořenový prvek JSON. Všimněte si, že fragmenty dokumentu (XML s více kořenovými prvky) nejsou v tomto mapování podporovány.

Příklad: Následující dokument:

```xml
<?xml version="1.0"?>
<root type="number">42</root>
```

A následující prvek:

```xml
<root type="number">42</root>
```

Oba mají mapování na JSON. Prvek `root` <> je kořenový prvek JSON v obou případech.

Kromě toho by se v případě DII mělo zvážit:

- Některé položky v seznamu [podřízené] nesmí být k dispozici. Nespoléhejte na tuto skutečnost při čtení XML mapované z JSON.

- Seznam [podřízené] obsahuje žádné položky informací o komentářích.

- Seznam [podřízených] neobsahuje žádné položky informací DTD.

- Seznam [podřízených] neobsahuje žádné položky `<?xml…>` informací o osobních údajích (prohlášení není považováno za informační položku PI)

- Sada [notations] je prázdná.

- Sada [neanalyzovaných entit] je prázdná.

Příklad: Následující dokument nemá žádné mapování na JSON, protože [children] obsahuje PI a komentář.

```xml
<?xml version="1.0"?>
<!--comment--><?pi?>
<root type="number">42</root>
```

EII pro kořenový prvek JSON má následující charakteristiky:

- [místní název] má hodnotu "root".

- [název oboru názvů] nemá žádnou hodnotu.

- [prefix] nemá žádnou hodnotu.

- [podřízené] mohou obsahovat buď EII (které představují vnitřní prvky, jak je popsáno dále) nebo CII (položky informací o charakteru, jak je popsáno dále), nebo žádný z nich, ale ne obojí.

- [atributy] mohou obsahovat následující volitelné položky informací o atributech (AII)

- Atribut typu JSON ("typ"),jak je popsáno dále. Tento atribut se používá k zachování typu JSON (řetězec, číslo, logická hodnota, objekt, pole nebo null) v mapovaném XML.

- Atribut název kontraktu\_\_dat ("typ"), jak je popsáno dále. Tento atribut může být přítomen pouze v případě, že atribut typu JSON je také přítomen a jeho [normalizovaná hodnota] je "objekt". Tento atribut používá `DataContractJsonSerializer` k zachování informací o typu datové smlouvy – například v polymorfních případech, kdy je odvozený typ serializován a kde se očekává základní typ. Pokud nepracujete s `DataContractJsonSerializer`, ve většině případů je tento atribut ignorován.

- [in-scope namespaces] obsahuje vazbu "xml" na `http://www.w3.org/XML/1998/namespace` nařízeno specifikací infoset.

- [children], [attributes] a [in-scope namespaces] nesmí mít žádné jiné položky než jak bylo uvedeno dříve a [atributy oboru názvů] nesmí mít žádné členy, ale při čtení XML mapovaného z JSON se na tyto skutečnosti nespoléhají.

Příklad: Následující dokument nemá žádné mapování na JSON, protože [atributy oboru názvů] není prázdný.

```xml
<?xml version="1.0"?>
<root xmlns:a="myattributevalue">42</root>
```

AII pro atribut typu JSON má následující charakteristiky:

- [název oboru názvů] nemá žádnou hodnotu.
- [prefix] nemá žádnou hodnotu.
- [místní název] je "typ".
- [normalizovaná hodnota] je jednou z možných hodnot typu popsaných v následující části.
- [zadáno] `true`je .
- [typ atributu] nemá žádnou hodnotu.
- [reference] nemá žádnou hodnotu.

AII pro atribut název smlouvy dat má následující charakteristiky:

- [název oboru názvů] nemá žádnou hodnotu.
- [prefix] nemá žádnou hodnotu.
- [místní název]\_\_je " typ" (dvě podtržítka a pak "typ").
- [normalizovaná hodnota] je libovolný platný řetězec Unicode – mapování tohoto řetězce na JSON je popsáno v následující části.
- [zadáno] `true`je .
- [typ atributu] nemá žádnou hodnotu.
- [reference] nemá žádnou hodnotu.

Vnitřní prvky obsažené v kořenovém prvku JSON nebo jiné vnitřní prvky mají následující vlastnosti:

- [místní název] může mít libovolnou hodnotu, jak je popsáno dále.
- [název oboru názvů], [prefix], [children], [atributy], [atributy oboru názvů] a [in-scope namespaces] podléhají stejným pravidlům jako kořenový prvek JSON.

V root JSON element a vnitřní prvky Atribut typu JSON definuje mapování JSON a možné [podřízené] a jejich interpretace. Atribut [normalizované hodnoty] rozlišuje malá a velká písmena a musí být malá písmena a nesmí obsahovat prázdné znaky.

|[normalizovaná hodnota] AII atributu typu JSON|Povolené [děti] odpovídajícího EI|Mapování na JSON|
|---------------------------------------------------------|---------------------------------------------------|---------------------|
|`string`(nebo nepřítomnost typu JSON AII)<br /><br /> A `string` a absence typu JSON AII jsou `string` stejné dělá výchozí.<br /><br /> Takže `<root> string1</root>` mapy na JSON `string` "string1".|0 nebo více CII|A JSON `string` (JSON RFC, oddíl 2.5). Každý `char` je znak, který odpovídá [kód znaku] z CII. Pokud nejsou k dispozici žádné CII, mapuje se na prázdný JSON `string`.<br /><br /> Příklad: Následující prvek se mapuje na fragment JSON:<br /><br /> `<root type="string">42</root>`<br /><br /> Fragment JSON je "42".<br /><br /> Při mapování XML na JSON znaky, které musí být uvozeny mapování mazemi na uvozené znaky, všechny ostatní mapovat na znaky, které nejsou uvozeny. Znak "/" je zvláštní – je uvozen, i když nemusí\\být (zapsán jako " /").<br /><br /> Příklad: Následující prvek se mapuje na fragment JSON.<br /><br /> `<root type="string">the "da/ta"</root>`<br /><br /> Fragment JSON je \\"da\\/ta\\"".<br /><br /> Při mapování JSON na XML všechny řídicí znaky a znaky, které nejsou uvozeny mapování správně odpovídající [kód znaku].<br /><br /> Příklad: Fragment JSON "\u0041BC", mapuje na následující element XML.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Řetězec může být obklopen prázdné místo ('ws' v části 2 JSON RFC), který není získat mapovány na XML.<br /><br /> Příklad: Fragment JSON "ABC", (před první dvojitou uvozovkou jsou mezery), mapuje se na následující element XML.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Jakékoli prázdné místo ve formátu XML mapuje na prázdné místo v JSON.<br /><br /> Příklad: Následující element XML se mapuje na fragment JSON.<br /><br /> `<root type="string">  A BC      </root>`<br /><br /> Fragment JSON je " Bc ".|
|`number`|1 nebo více CII|JSON `number` (JSON RFC, sekce 2.4), případně obklopený mezerami. Každý znak v kombinaci number/white space je znak, který odpovídá [kód znaku] z CII.<br /><br /> Příklad: Následující prvek se mapuje na fragment JSON.<br /><br /> `<root type="number">    42</root>`<br /><br /> Fragment JSON je 42<br /><br /> (Prázdné místo je zachováno).|
|`boolean`|4 nebo 5 CII (což odpovídá `true` nebo `false`), případně obklopeno dalšími nebílými CII.|Sekvence CII, která odpovídá řetězci "true", je `true`mapována na literál a sekvence CII, která odpovídá `false`řetězci "false", je mapována na literál . Okolní prázdné místo je zachováno.<br /><br /> Příklad: Následující prvek se mapuje na fragment JSON.<br /><br /> `<root type="boolean"> false</root>`<br /><br /> Fragment JSON `false`je .|
|`null`|Nic není povoleno.|Literál `null`. Na JSON na XML `null` mapování, může být obklopen prázdné místo ('ws' v části 2), který není získat mapovány na XML.<br /><br /> Příklad: Následující prvek se mapuje na fragment JSON.<br /><br /> `<root type="null"/>`<br /><br /> – nebo –<br /><br /> `<root type="null"></root>`<br /><br /> :<br /><br /> Fragment JSON v obou `Null`případech je .|
|`object`|0 nebo více EII.|A `begin-object` (levá složená závorka) podle bodu 2.2 JSON RFC, následovaná záznamem člena pro každou EII, jak je popsáno dále. Pokud existuje více než jeden EII, existují oddělovače hodnot (čárky) mezi záznamy členů. To vše následuje koncový objekt (pravá složená závorka).<br /><br /> Příklad: Následující prvek se mapuje na fragment JSON.<br /><br /> `<root type="object">`<br /><br /> `<type1 type="string">aaa\</type1>`<br /><br /> `<type2 type="string">bbb\</type2>`<br /><br /> `</root >`<br /><br /> Fragment JSON `{"type1":"aaa","type2":"bbb"}`je .<br /><br /> Pokud je atribut typu datové smlouvy k dispozici v mapování XML na JSON, je na začátek vložen další záznam člena. Jeho název je [místní název] atributu typ\_\_datové smlouvy ("typ"), a jeho hodnota je atribut [normalizované hodnoty]. Naopak na JSON na XML mapování, pokud název prvního členského záznamu je [místní název] atributu\_\_typu datové smlouvy (to znamená " typ"), odpovídající atribut typu datové smlouvy je k dispozici v mapovaném XML, ale odpovídající EII není k dispozici. Všimněte si, že tento záznam člena musí dojít nejprve v objektu JSON pro toto speciální mapování použít. To představuje odklon od obvyklého zpracování JSON, kde pořadí záznamů členů není významné.<br /><br /> Příklad:<br /><br /> Následující fragment JSON se mapuje na XML.<br /><br /> `{"__type":"Person","name":"John"}`<br /><br /> Xml je následující kód.<br /><br /> `<root type="object" __type="Person">   <name type="string">John</name> </root>`<br /><br /> Všimněte \_ \_si, že typ AII \_ \_je k dispozici, ale neexistuje žádný typ EII.<br /><br /> Však pokud pořadí v JSON je obrácený, jak je znázorněno v následujícím příkladu.<br /><br /> `{"name":"John","\_\_type":"Person"}`<br /><br /> Zobrazí se odpovídající kód XML.<br /><br /> `<root type="object">   <name type="string">John</name>   <__type type="string">Person</__type> </root>`<br /><br /> To znamená, \_že _type přestává mít zvláštní význam a mapuje na EII jako obvykle, ne NaII.<br /><br /> Pravidla pro aii [normalizovanou hodnotu] při mapování na hodnotu JSON jsou stejná jako pro řetězce JSON zadaná v řádku "řetězec" této tabulky.<br /><br /> Příklad:<br /><br /> `<root type="object" __type="\abc" />`<br /><br /> na předchozí příklad lze mapovat na následující JSON.<br /><br /> `{"__type":"\\abc"}`<br /><br /> Při mapování XML na JSON nesmí být první [místní název]\_\_eII "type".<br /><br /> Prázdné znaky`ws`( ) se nikdy nevygenerují při mapování XML na JSON pro objekty a jsou ignorovány v mapování JSON na XML.<br /><br /> Příklad: Následující fragment JSON se mapuje na element XML.<br /><br /> `{ "ccc" : "aaa", "ddd" :"bbb"}`<br /><br /> Element XML je zobrazen v následujícím kódu.<br /><br /> `<root type="object">    <ccc type="string">aaa</ccc>    <ddd type="string">bbb</bar> </root >`|
|pole|0 nebo více EII|Počáteční pole (levá hranatá závorka) podle bodu 2.3 JSON RFC, následovaná záznamem pole pro každou EII, jak je popsáno dále. Pokud existuje více než jeden EII, existují oddělovače hodnot (čárky) mezi záznamy pole. To vše následuje koncové pole.<br /><br /> Příklad: Následující element XML se mapuje na fragment JSON.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`<br /><br /> Fragment JSON je`["aaa","bbb"]`<br /><br /> Prázdné znaky`ws`( ) se nikdy nevygenerují při mapování XML na JSON pro pole a jsou ignorovány v mapování JSON na XML.<br /><br /> Příklad: Fragment JSON.<br /><br />`["aaa", "bbb"]`<br /><br /> Element XML, na který se mapuje.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`|

Záznamy členů fungují takto:

- [místní název] vnitřního prvku `string` se mapuje na část, která je definována `member` v části 2.2 JSON RFC.

Příklad: Následující prvek se mapuje na fragment JSON.

```xml
<root type="object">
    <myLocalName type="string">aaa</myLocalName>
</root>
```

Zobrazí se následující fragment JSON.

```json
{"myLocalName":"aaa"}
```

- V mapování XML na JSON jsou uvozeny znaky, které musí být uvozeny v JSON a ostatní nejsou uvozeny. Znak "/", i když není znak, který musí být uvozen, je přesto uvozen (nemusí být uvozen na mapování Xml JSON). To je nutné pro podporu `DateTime` formátu ASP.NET AJAX pro data v JSON.

- Při mapování JSON na XML jsou všechny znaky (včetně neuvozených `string` znaků, pokud je to nutné) převzaty do tvaru a, který vytváří [místní název].

- Vnitřní prvky [děti] mapovat na hodnotu v `JSON Type Attribute` bodě 2.2, podle stejně jako pro `Root JSON Element`. Více úrovní vnoření EII (včetně vnoření v rámci polí) jsou povoleny.

Příklad: Následující prvek se mapuje na fragment JSON.

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

Následující fragment JSON je to, co mapuje.

```json
{"myLocalName1":"myValue1","myLocalName2":2,"myLocalName3":{"myNestedName1":true,"myNestedName2":null}}
```

> [!NOTE]
> V předchozím mapování není žádný krok kódování XML. Proto WCF podporuje pouze dokumenty JSON, kde všechny znaky v názvech klíčů jsou platné znaky v názvech elementů XML. Například dokument JSON {"<":"a"} není podporován, protože < není platný název elementu XML.

Reverzní situace (znaky platné v JAZYCE XML, ale ne v JSON) nezpůsobí žádné problémy, protože předchozí mapování zahrnuje Kroky uvození/neunikání JSON.

Array Records fungují následovně:

- Vnitřní prvek [místní název] je "položka".

- Vnitřní element je [podřízené] mapovat na hodnotu v části 2.3, podle Atribut typu JSON, jak je pro root JSON element. Více úrovní vnoření EII (včetně vnoření v rámci objektů) jsou povoleny.

Příklad: Následující prvek se mapuje na fragment JSON.

```xml
<root type="array">
    <item type="string">myValue1</item>
    <item type="number">2</item>
    <item type="array">
    <item type="boolean">true</item>
    <item type="null"/></item>
</root>
```

Následuje fragment JSON.

```json
["myValue1",2,[true,null]]
```

## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>
- [Samostatná serializace JSON](stand-alone-json-serialization.md)
