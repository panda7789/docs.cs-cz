---
title: Mapování mezi JSON a XML
ms.date: 03/30/2017
ms.assetid: 22ee1f52-c708-4024-bbf0-572e0dae64af
ms.openlocfilehash: db34161ad3e2f7d2c9737e6a456b27bd70c5ebfb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mapping-between-json-and-xml"></a>Mapování mezi JSON a XML
Čtení a zápis vyprodukované <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory> poskytují rozhraní API XML přes obsah JavaScript Object Notation (JSON). JSON kóduje dat pomocí podmnožinu literály objekt jazyka JavaScript. Čtení a zápis, které jsou vyprodukované tuto továrnu se také používají při obsah JSON se odesílat nebo přijímat aplikací Windows Communication Foundation (WCF) pomocí <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement> nebo <xref:System.ServiceModel.WebHttpBinding>.  
  
 Při inicializaci s obsah JSON, chová se stejným způsobem, který zajišťuje textovou čtečky XML přes instanci XML čtečka JSON. Zapisovač JSON, pokud zadané posloupnost volání, která na textovou čtečky XML vytváří určité instance XML, zapíše se obsah JSON. Mapování mezi tuto instanci XML a obsah JSON je popsaná v tomto tématu pro použití v pokročilých scénářích.  
  
 Interně JSON je reprezentován jako XML informační sadu při zpracování WCF. Normálně není nutné být problémem tento interního vyjádření jako mapování je pouze logické: JSON je obvykle není fyzicky převést do formátu XML v paměti nebo převést na JSON ze souboru XML. Mapování znamená, že rozhraní API XML se používají pro přístup k obsahu JSON.  
  
 Používá-li WCF JSON, obvyklé scénáře je, že <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> automaticky zapojen podle <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> chování, nebo <xref:System.ServiceModel.Description.WebHttpBehavior> chování, pokud je to vhodné. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Rozumí mapování mezi JSON a XML informační sadu a chová, jako je se zabývají JSON přímo. (Je možné použít <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> se čtecí modul XML nebo zapisovač s vědomím, že soubor XML, splňuje následující mapování.)  
  
 V pokročilých scénářích může být nezbytné přímý přístup k následující mapování. Tyto scénáře nastat, pokud chcete k serializaci a deserializaci JSON vlastní způsoby, bez nutnosti spoléhat se na <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, nebo při plánování práce s <xref:System.ServiceModel.Channels.Message> typu přímo pro zprávy obsahující JSON. Mapování JSON XML se také používá pro protokolování zpráv. Při použití funkce protokolování zpráv ve WCF, JSON zprávy se zaznamená jako XML podle mapování popsané v další části.  
  
 K objasnění konceptu mapování, v následujícím příkladu je dokumentu JSON.  
  
```json  
{"product":"pencil","price":12}  
```  
  
 Číst tento dokument JSON pomocí jednoho ze čtečky už jsme zmínili, použijte stejnou sekvenci <xref:System.Xml.XmlDictionaryReader> volání, jako byste to přečtěte si následující dokument XML.  
  
```xml  
<root type="object">  
    <product type="string">pencil</product>  
    <price type="number">12</price>  
</root>  
```  
  
 Kromě toho pokud zpráva JSON v příkladu je přijatých WCF a zaznamenávat, zobrazí se fragment XML v předchozím protokolu.  
  
## <a name="mapping-between-json-and-the-xml-infoset"></a>Mapování mezi JSON a XML informační sadu  
 Dříve, se mapování mezi JSON jak je popsáno v [RFC 4627](http://go.microsoft.com/fwlink/?LinkId=98808) (s výjimkou určitá omezení volný a některé další omezení přidat) a XML informační sadu (a ne textové XML) jako popsané v [informace XML Nastavit](http://go.microsoft.com/fwlink/?LinkId=98809) . V tomto tématu pro definice *informace položky* a polí v [hranaté závorky].  
  
 Prázdný dokument JSON mapuje prázdného dokumentu XML a prázdné dokumentu XML se mapuje na prázdné dokumentu JSON. Na XML pro mapování JSON předcházející prázdné znaky a koncové mezery po dokumentu nejsou povoleny.  
  
 Definuje mapování mezi buď položku dokumentu informace (DII) nebo Element informace položky (EII) a JSON. EII nebo DII [element dokumentu] vlastnosti, se označuje jako kořenový Element JSON. Všimněte si, že dokument fragmenty (s více kořenových elementů XML) nejsou podporovány v toto mapování.  
  
 Příklad: V následujících dokumentech:  
  
 `<?xml version="1.0"?>`  
  
 `<root type="number">42</root>`  
  
 A následující element:  
  
 `<root type="number">42</root>`  
  
 Mají obě mapování do formátu JSON. <`root`> Element není kořenovým elementem JSON v obou případech.  
  
 Kromě toho v případě DII, následující považovat za:  
  
-   Některé položky v seznamu [podřízené položky] nesmí existovat. Nespoléhejte na tuto skutečnost při čtení XML je mapován z formátu JSON.  
  
-   V seznamu [podřízené položky] obsahuje bez komentáře informace položky.  
  
-   V seznamu [podřízené položky] obsahuje žádné položky DTD informace.  
  
-   V seznamu [podřízené položky] obsahuje žádné osobní informace položky informace (PI) ( \<? xml... > deklarace se nepovažuje za položku informace platformy)  
  
-   Sada [zápisy] je prázdný.  
  
-   Sada [nezpracované entity] je prázdný.  
  
 Příklad: V následujících dokumentech nemá žádné mapování do formátu JSON protože blokování [podřízené položky] platformy a komentář.  
  
 `<?xml version="1.0"?>`  
  
 `<!--comment--><?pi?>`  
  
 `<root type="number">42</root>`  
  
 EII pro kořenový Element JSON má následující vlastnosti:  
  
-   [místní název] má hodnotu "root".  
  
-   [název oboru názvů] nemá žádnou hodnotu.  
  
-   [předpona] nemá žádnou hodnotu.  
  
-   [podřízené položky] může obsahovat buď EIIs (které představují vnitřní prvky, jak je popsáno dále) nebo CIIs (znak položky informací jak je popsáno dále) nebo žádná z těchto, ale ne obě.  
  
-   [atributy] může obsahovat následující položky informace volitelný atribut (AIIs)  
  
-   Atribut Type JSON ("typ") jak je popsáno dále. Tento atribut slouží k zachování typu JSON (řetězec, číslo, logickou hodnotu, objekt, pole nebo hodnotu null) v namapované XML.  
  
-   Název kontraktu dat atribut ("__type") jak je popsáno dále. Tento atribut je lze pouze přítomen Pokud atribut typu JSON je také k dispozici a jeho [Normalizovaná hodnota] je "objekt". Tento atribut je používán `DataContractJsonSerializer` zachovat kontraktů dat informací o typu – například v případech, polymorfní kde serializován odvozený typ a kde je očekávána základní typ. Pokud nepracujete s `DataContractJsonSerializer`, ve většině případů se tento atribut je ignorován.  
  
-   [obory názvů v oboru] obsahuje vazbu "xml" na "http://www.w3.org/XML/1998/namespace" podle podmínek specifikací informační sadu pověření.  
  
-   [podřízené položky], [atributy] a [obory názvů v oboru] nesmí mít všechny položky, jinak než uvedeného dříve a [atributy oboru názvů] musí mít žádné členy, ale nespoléhejte na tyto skutečnosti při čtení XML mapovat z formátu JSON.  
  
 Příklad: V následujících dokumentech nemá žádné mapování do formátu JSON protože [atributy oboru názvů] není prázdná.  
  
 `<?xml version="1.0"?>`  
  
 `<root  xmlns:a="myattributevalue">42</root>`  
  
 AII pro atribut typu JSON má následující vlastnosti:  
  
-   [název oboru názvů] nemá žádnou hodnotu.  
  
-   [předpona] nemá žádnou hodnotu.  
  
-   [místní název] je "typ".  
  
-   [Normalizovaná hodnota] je jedním z možných typ hodnoty popsané v následující části.  
  
-   [zadali] je `true`.  
  
-   [typ atributu] nemá žádnou hodnotu.  
  
-   [odkazy] nemá žádnou hodnotu.  
  
 AII pro atribut názvu kontraktu dat má následující vlastnosti:  
  
-   [název oboru názvů] nemá žádnou hodnotu.  
  
-   [předpona] nemá žádnou hodnotu.  
  
-   [místní název] je "__type" (dvě podtržítka a potom "typ").  
  
-   [Normalizovaná hodnota] je libovolný platný řetězec kódování Unicode – mapování tento řetězec do formátu JSON je popsaný v následující části.  
  
-   [zadali] je `true`.  
  
-   [typ atributu] nemá žádnou hodnotu.  
  
-   [odkazy] nemá žádnou hodnotu.  
  
 Vnitřní elementů obsažených v kořenovém elementu JSON nebo jiné vnitřní prvky mít následující vlastnosti:  
  
-   [místní název] může mít žádnou hodnotu, jak je popsáno dále  
  
-   [název oboru názvů], [předpona], [podřízené položky], [atributy], [obor názvů atributy,] a [obory názvů v oboru] podléhají stejná pravidla jako kořenový Element JSON.  
  
 V kořenovém elementu JSON a vnitřní prvky atribut Type JSON definuje mapování do formátu JSON a možné [podřízené položky] a jejich interpretace. Atributu [Normalizovaná hodnota] je malá a velká písmena a musí být psaný malými písmeny a nesmí obsahovat prázdné znaky.  
  
|[normalized hodnotu] z `JSON Type Attribute`na AII|Povolené [podřízené objekty] odpovídající EII|Mapování do formátu JSON|  
|---------------------------------------------------------|---------------------------------------------------|---------------------|  
|`string` (nebo absenci typu JSON AII)<br /><br /> A `string` a absence typu JSON AII jsou stejné díky `string` výchozí hodnota.<br /><br /> Ano `<root> string1</root>` mapuje JSON `string` "Řetězec1".|0 nebo více CIIs|JSON `string` (RFC JSON, část 2.5). Každý `char` je znak, který odpovídá [kód] z CÍ. Pokud žádné CIIs se mapuje na prázdný JSON `string`.<br /><br /> Příklad: Následující element mapuje JSON fragment:<br /><br /> `<root type="string">42</root>`<br /><br /> JSON fragment je "42".<br /><br /> Na XML tak, aby mapování JSON znaků, které musí být uvozené uvozovacími znaky znaků mapy, všechny ostatní znaky, které nejsou uvozené namapovat. Znak "/" je speciální – je řídicí sekvencí, i když nemá být (zapsaný se jako "\\/").<br /><br /> Příklad: Následující element mapuje JSON fragment.<br /><br /> `<root type="string">the "da/ta"</root>`<br /><br /> JSON fragment je " \\" da\\/ta\\"".<br /><br /> Na formát JSON pro mapování XML všechny uvozený znaky a znaky, které nejsou správně uvozeny zpětným lomítkem mapy na odpovídající [kód].<br /><br /> Příklad: Fragment JSON "\u0041BC" mapuje následující element XML.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Řetězec může být uzavřena do prázdné znaky ("ws" v části 2 v dokumentech RFC JSON) získat není mapováno na XML.<br /><br /> Příklad: JSON fragmentovat "ABC", (nejsou mezery před první dvojitých uvozovek), se mapuje na následující element XML.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Všechny prázdné znaky v kódu XML se mapuje na prázdné znaky na JSON.<br /><br /> Příklad: Následující element XML mapuje JSON fragment.<br /><br /> `<root type="string">  A BC      </root>`<br /><br /> JSON fragment je "BC".|  
|`number`|1 nebo více CIIs|JSON `number` (RFC JSON, část 2.4), které by mohly mít obklopená prázdný znak. Každý znak v kombinaci číslo nebo prázdný znak je znak, který odpovídá [kód] z CÍ.<br /><br /> Příklad: Následující element mapuje JSON fragment.<br /><br /> `<root type="number">    42</root>`<br /><br /> JSON fragment je 42<br /><br /> (Prázdný znak je zachovaná).|  
|`boolean`|4 nebo 5 CIIs (která odpovídá `true` nebo `false`), případně ovinutých podle dalších prázdné CIIs.|Pořadí CÍ, která odpovídá řetězec "true" je namapována na literálové `true`, a CÍ pořadí, které odpovídá řetězci, "Nepravda" je namapována na literálové `false`. Které obaluje prázdný znak je zachovaná.<br /><br /> Příklad: Následující element mapuje JSON fragment.<br /><br /> `<root type="boolean"> false</root>`<br /><br /> JSON fragment je `false`.|  
|`null`|Není povoleno.|Literálové `null`. Na JSON pro mapování XML `null` může být uzavřena do prázdné znaky ("ws" v části 2) získat není mapováno na XML.<br /><br /> Příklad: Následující element mapuje JSON fragment.<br /><br /> `<root type="null"/>`<br /><br /> or<br /><br /> `<root type="null"></root>`<br /><br /> :<br /><br /> Fragment JSON v obou případech je `Null`.|  
|`object`|0 nebo více EIIs.|A `begin-object` (left složené závorky) jako část 2.2 v dokumentu RFC JSON a následuje člen záznam pro každý EII jak je popsáno dále. Pokud existuje více než jeden EII, nejsou mezi záznamy člen hodnota oddělovače (čárkami). To vše následuje koncové – objekt (pravé složené závorky).<br /><br /> Příklad: Následující element mapuje JSON fragment.<br /><br /> \<kořenový typ = "objekt" ><br /><br /> \<Typ Type1 = "řetězec" > aaa\</type1 ><br /><br /> \<Typ Type2 = "řetězec" > bbb\</type2 ><br /><br /> \</ root ><br /><br /> JSON fragment je {"type1": "aaa", "type2": "bbb"}.<br /><br /> Pokud atribut typu kontraktu dat nachází na XML mapování JSON, další záznam člen vložit na začátku. Jeho název je [místní název] atribut typu kontraktu dat ("__type") a jeho hodnota může být atributu [Normalizovaná hodnota]. Naopak v JSON pro mapování XML, pokud je první člen – název záznamu [místní název] atribut typu kontraktu dat (tedy "\__zadejte"), odpovídající atribut typu kontraktu dat se nachází v namapované XML, ale odpovídající EII není existuje. Všimněte si, že tento záznam člena musí být nejprve v objektu JSON pro toto mapování speciální použít. To představuje rozdíl od obvyklé zpracování JSON, kde pořadí záznamů člen není důležité.<br /><br /> Příklad:<br /><br /> Následující fragment JSON se mapuje na XML.<br /><br /> `{"__type":"Person","name":"John"}`<br /><br /> XML je následující kód.<br /><br /> `<root type="object" __type="Person">   <name type="string">John</name> </root>`<br /><br /> Všimněte si, že \__zadejte AII je k dispozici, ale neexistuje žádné \__zadejte EII.<br /><br /> Ale pokud pořadí v kódu JSON je vrátit jako vidět v následujícím příkladu.<br /><br /> {"název": "Jan","\__zadejte": "Osoba"}<br /><br /> Zobrazí se odpovídající soubor XML.<br /><br /> `<root type="object">   <name type="string">John</name>   <__type type="string">Person</__type> </root>`<br /><br /> To znamená \__zadejte zastaví do mají zvláštní význam a je přiřazen EII jako obvykle není AII.<br /><br /> Uvozovací znaky unescaping pravidla pro AII aktivity [normalized hodnotu] při mapování na hodnotu JSON jsou stejné jako řetězce formátu JSON, zadaný v "řetězec" řádku této tabulky.<br /><br /> Příklad:<br /><br /> `<root type="object" __type="\abc" />`<br /><br /> v předchozím příkladu lze mapovat na následujícím kódu JSON.<br /><br /> `{"__type":"\\abc"}`<br /><br /> V XML pro mapování JSON, nesmí být první EII na [místní název] "\__zadejte".<br /><br /> Prázdné znaky (`ws`) se nikdy vygeneruje na XML pro mapování JSON pro objekty a je ignorován v JSON pro mapování XML.<br /><br /> Příklad: Následující fragment JSON se mapuje na XML element.<br /><br /> {"kopie": "aaa", "ddd": "bbb"}<br /><br /> XML element je znázorněno v následujícím kódu.<br /><br /> `<root type="object">    <ccc type="string">aaa</ccc>    <ddd type="string">bbb</bar> </root >`|  
Ray.|0 nebo více EIIs|Začátek pole (levou hranatou závorku) jako část 2.3 v dokumentech RFC JSON následuje záznam pole pro každý EII, jak je popsáno dále. Pokud existuje více než jeden EII, nejsou mezi záznamy pole Hodnota oddělovače (čárkami). To vše následuje koncoví pole.<br /><br /> Příklad: Následující element XML mapuje JSON fragment.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`<br /><br /> JSON fragment je ["aaa", "bbb"]<br /><br /> Prázdné znaky (`ws`) se nikdy vygeneruje na XML pro mapování JSON pro pole a je ignorován v JSON pro mapování XML.<br /><br /> Příklad: AJSON fragment.<br /><br /> ["aaa", "bbb"]<br /><br /> Element XML, které odpovídá.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`|  
  
 Člen záznamy práce následujícím způsobem:  
  
-   Vnitřní elementu [místní název] se mapuje `string` součástí `member` definovaným v části 2.2 JSON RFC.  
  
 Příklad: Následující element mapuje JSON fragment.  
  
 `<root type="object"/>`  
  
 `<myLocalName type="string">aaa</myLocalName>`  
  
 `</root >`  
  
 Zobrazí se následující fragment JSON.  
  
 `{"myLocalName":"aaa"}`  
  
-   V XML pro mapování JSON znaky, které ve formátu JSON, je nutné uvést jsou uvozeny uvozovacím znakem a ostatní nejsou uvozené. Znak "/", je uvozena nicméně Přestože se nejedná o znak, který je nutné uvést, (ho nemusí být uvozena ve formátu JSON pro mapování XML). Je to nutné pro podporu formát prvku ASP.NET AJAX pro `DateTime` data ve formátu JSON.  
  
-   Na formát JSON pro mapování XML, jsou všechny znaky (včetně není uvozené znaky, v případě potřeby) přesměrováni na formuláři `string` [místní název], která vyvolává.  
  
-   Vnitřní elementy [podřízené položky] namapovat na hodnotu v části 2.2, podle požadavků `JSON Type Attribute` pro stejně jako `Root JSON Element`. Více úrovní vnoření EIIs (včetně vnoření v rámci pole) jsou povoleny.  
  
 Příklad: Následující element mapuje JSON fragment.  
  
 `<root type="object">`  
  
 `<myLocalName1 type="string">myValue1</myLocalName1>`  
  
 `<myLocalName2 type="number">2</myLocalName2>`  
  
 `<myLocalName3 type="object">`  
  
 `<myNestedName1 type="boolean">true</myNestedName1>`  
  
 `<myNestedName2 type="null"/>`  
  
 `</myLocalName3>`  
  
 `</root >`  
  
 Následující fragment JSON je, co se mapuje na.  
  
 `{"myLocalName1":"myValue1","myLocalName2":2,"myLocalName3":{"myNestedName1":true,"myNestedName2":null}}`  
  
> [!NOTE]
>  V předchozí mapování neexistuje žádný krok kódování XML. Proto WCF podporuje pouze dokumentů JSON, kde všechny znaky v názvy klíčů jsou platné znaky v názvy elementů XML. Například dokument JSON {"<": "a"} není podporována, protože < není platný název elementu XML.  
  
 Zpětné situaci (znaky v kódu XML, ale není ve formátu JSON) nezpůsobí potíže, protože předchozí mapování obsahuje kroky uvozovací znaky unescaping JSON.  
  
 Pole záznamy práce následujícím způsobem:  
  
-   Vnitřní elementu [místní název] je "položky".  
  
-   Vnitřní elementu [podřízené položky] namapovat na hodnotu v části 2.3, podle typu atributu JSON, jak se nepodporuje pro kořenový Element JSON. Je povoleno více úrovní vnoření EIIs (včetně vnoření v rámci objektů).  
  
 Příklad: Následující element mapuje JSON fragment.  
  
 `<root type="array"/>`  
  
 `<item type="string">myValue1</item>`  
  
 `<item type="number">2</item>`  
  
 `<item type="array">`  
  
 `<item type="boolean">true</item>`  
  
 `<item type="null"/>`  
  
 `</item>`  
  
 `</root >`  
  
 Zde je JSON fragment.  
  
 `["myValue1",2,[true,null]]`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory>  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>  
 [Samostatná serializace JSON](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)
