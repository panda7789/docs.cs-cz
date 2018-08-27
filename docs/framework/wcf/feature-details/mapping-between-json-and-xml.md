---
title: Mapování mezi JSON a XML
ms.date: 03/30/2017
ms.assetid: 22ee1f52-c708-4024-bbf0-572e0dae64af
ms.openlocfilehash: e8cc356a30d11a6f07cf4444efbeda2faf5b0471
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931466"
---
# <a name="mapping-between-json-and-xml"></a>Mapování mezi JSON a XML
Čtečky a zapisovače vytvářených <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory> poskytují rozhraní API XML nad obsahem objektu zápis JSON (JavaScript). JSON zašifruje data pomocí některé podsady literálů objektů jazyka JavaScript. Čtečky a zapisovače vytvářených tento objekt pro vytváření se také používají při obsah JSON se odeslaný nebo přijatý aplikací Windows Communication Foundation (WCF) pomocí <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement> nebo <xref:System.ServiceModel.WebHttpBinding>.  
  
 Při inicializaci s obsah JSON, čtečky JSON chová stejně jako textové čtecí modul XML zajišťuje přes instanci XML. Zápis JSON, když pro konkrétní posloupnost volání, která na textový čtecí modul XML vytváří určité instance XML, zapíše obsah JSON. Mapování mezi tato instance XML a obsah JSON je popsané v tomto tématu pro použití v pokročilých scénářích.  
  
 Interně jsou JSON je vyjádřena jako XML informační sadu po zpracování službou WCF. Obvykle není potřeba zabývat tím tento vnitřní reprezentaci jako mapování je pouze logická: JSON je obvykle fyzicky převést na XML v paměti nebo převést na JSON ze souboru XML. Mapování znamená, že rozhraní API XML se používají pro přístup k obsahu JSON.  
  
 Při WCF používá JSON, je obvykle scénář, který <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> automaticky zapojené do elektrické zásuvky podle <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> chování, nebo <xref:System.ServiceModel.Description.WebHttpBehavior> chování v případě potřeby. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Rozumí mapování mezi JSON a XML informační sadu a pracuje, jako by ji se zabývají JSON přímo. (Je možné použít <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> se čtecí funkce XML či zapisovače s vědomím, že kódu XML odpovídá následující mapování.)  
  
 V pokročilých scénářích může být potřeba přímý přístup k následující mapování. Tyto scénáře dojít, pokud chcete k serializaci a deserializaci JSON vlastní způsobem, bez nutnosti spoléhat se na <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, nebo když se zabývají <xref:System.ServiceModel.Channels.Message> typ přímo pro zprávy obsahující JSON. Mapování JSON XML se také používá pro protokolování zpráv. Při použití funkce protokolování zpráv ve službě WCF, zprávy JSON se zaznamená jako XML podle mapování je popsáno v další části.  
  
 K objasnění konceptu mapování v následujícím příkladu je dokument JSON.  
  
```json  
{"product":"pencil","price":12}  
```  
  
 Přečtěte si tento dokument JSON pomocí jedné z čtečky už jsme zmínili, můžete stejnou sekvenci <xref:System.Xml.XmlDictionaryReader> volá stejně jako ke čtení následujícího dokumentu XML.  
  
```xml  
<root type="object">  
    <product type="string">pencil</product>  
    <price type="number">12</price>  
</root>  
```  
  
 Kromě toho pokud zprávu JSON v příkladu přijme službou WCF a přihlášení, zobrazí se fragment XML v předchozím protokolu.  
  
## <a name="mapping-between-json-and-the-xml-infoset"></a>Mapování mezi JSON a XML informační sadu  
 Formálně, mapování je mezi JSON, jak je popsáno v [RFC 4627](http://go.microsoft.com/fwlink/?LinkId=98808) (s výjimkou určitá omezení volný a některé další omezení, přidá) a XML informační sada (a nikoli textovou XML) jako je popsáno v [informace XML Nastavte](http://go.microsoft.com/fwlink/?LinkId=98809) . V tomto tématu pro definice *informačních položek* a polí v [hranaté závorky].  
  
 Prázdný dokument JSON se mapuje na prázdný dokument XML a prázdný dokument XML, mapuje na prázdný dokument JSON. Na XML na JSON mapování nejsou povoleny mezery před a koncové prázdné znaky po dokumentu.  
  
 Mapování je definován mezi buď položku informace dokumentu (DII) nebo položek informací elementu (EII) a JSON. EII nebo DII [element dokumentu] vlastnosti, se označuje jako kořenový Element JSON. Všimněte si, že se fragmenty dokumentu (XML s více kořenových prvků) nepodporují toto mapování.  
  
 Příklad: V následujícím dokumentu:  
  
 `<?xml version="1.0"?>`  
  
 `<root type="number">42</root>`  
  
 A následující element:  
  
 `<root type="number">42</root>`  
  
 Mít mapování na JSON. <`root`> Prvek je kořenovým prvkem JSON v obou případech.  
  
 Kromě toho v případě DII, následující by měl být:  
  
-   Některé položky v seznamu [podřízené] nesmí být k dispozici. Nespoléhejte na tuto skutečnost při čtení XML je mapován z formátu JSON.  
  
-   Seznam [podřízené] obsahuje žádný komentář informačních položek.  
  
-   Seznam [podřízené] obsahuje žádné položky informace DTD.  
  
-   Seznam [podřízené] obsahuje žádné osobní informace položky informace (PÍ) ( \<? xml... > deklarace není považována za položku PI informace)  
  
-   Sada [zápisy] je prázdný.  
  
-   Sada [nezpracované entit] je prázdný.  
  
 Příklad: Následující dokument nemá žádné mapování do formátu JSON protože [podřízené] obsahuje číslo PÍ a komentář.  
  
 `<?xml version="1.0"?>`  
  
 `<!--comment--><?pi?>`  
  
 `<root type="number">42</root>`  
  
 EII pro kořenový Element JSON má následující vlastnosti:  
  
-   [místní název] má hodnotu "root".  
  
-   [název oboru názvů] nemá žádnou hodnotu.  
  
-   [prefix] nemá žádnou hodnotu.  
  
-   [podřízené] může obsahovat EIIs (které představují vnitřní elementy, jak je popsáno dále) nebo CIIs (znak položky informací jak je popsáno dále) nebo žádná z těchto, ale ne obojí.  
  
-   [atributy] může obsahovat následující položky informace volitelný atribut (AIIs)  
  
-   Atribut typu JSON ("type") jak je popsáno dále. Tento atribut se používá k zachování JSON typ (řetězec, číslo, logickou hodnotu, objekt, pole nebo null) v mapovaných XML.  
  
-   Název kontraktu dat atribut ("__type") jak je popsáno dále. Tento atribut je může být pouze přítomen atribut typu JSON je také k dispozici a je jeho [Normalizovaná hodnota] "objekt". Tento atribut se používá `DataContractJsonSerializer` zachovat kontraktů dat informace o typu – například v případech, polymorfní tam, kde je serializována odvozený typ, a tam, kde se očekává základního typu. Pokud nepracujete s `DataContractJsonSerializer`, ve většině případů se tento atribut se ignoruje.  
  
-   [v oboru oborů názvů] obsahuje vazbu "xml" k "http://www.w3.org/XML/1998/namespace" podle zákonného specifikaci informační sadu.  
  
-   [podřízené], [atributy] a [v oboru oborů názvů] nesmí obsahovat žádné položky jiný než jak je uvedeno dříve a [obor názvů atributů] musí mít žádné členy, ale nespoléhejte na tyto skutečnosti při čtení XML, namapované z formátu JSON.  
  
 Příklad: Následující dokument nemá žádné mapování do formátu JSON protože [obor názvů atributů] není prázdný.  
  
 `<?xml version="1.0"?>`  
  
 `<root  xmlns:a="myattributevalue">42</root>`  
  
 AII pro atribut typu JSON má následující vlastnosti:  
  
-   [název oboru názvů] nemá žádnou hodnotu.  
  
-   [prefix] nemá žádnou hodnotu.  
  
-   [místní název] je "type".  
  
-   [Normalizovaná hodnota] je jedním z možných typ hodnoty je popsáno v následující části.  
  
-   [zadaný] je `true`.  
  
-   [typ atributu] nemá žádnou hodnotu.  
  
-   [odkazy] nemá žádnou hodnotu.  
  
 AII pro atribut název kontraktu dat má následující vlastnosti:  
  
-   [název oboru názvů] nemá žádnou hodnotu.  
  
-   [prefix] nemá žádnou hodnotu.  
  
-   [místní název] je "__type" (dvěma podtržítky a potom "typ").  
  
-   [Normalizovaná hodnota] je libovolný platný řetězec znaků Unicode – mapování tento řetězec JSON je popsána v následující části.  
  
-   [zadaný] je `true`.  
  
-   [typ atributu] nemá žádnou hodnotu.  
  
-   [odkazy] nemá žádnou hodnotu.  
  
 Vnitřní elementů obsažených v rámci kořenového elementu JSON nebo další vnitřní prvky mají následující vlastnosti:  
  
-   [místní název] může mít libovolnou hodnotu, jak je popsáno dále  
  
-   [název oboru názvů], [prefix], [podřízené], [atributy], [obor názvů atributů] a [v oboru oborů názvů] se vztahují stejná pravidla jako kořenový Element JSON.  
  
 Kořenový Element JSON a vnitřní elementy atribut typu JSON definuje mapování do formátu JSON a možné [podřízené] a jejich interpretaci. Atributu [Normalizovaná hodnota] je velká a malá písmena a musí obsahovat malá písmena a nesmí obsahovat prázdné znaky.  
  
|[Normalizovaná hodnota] z `JSON Type Attribute`společnosti AII|Povolené [podřízené] odpovídající EII|Mapování do formátu JSON|  
|---------------------------------------------------------|---------------------------------------------------|---------------------|  
|`string` (nebo nepřítomnosti typu JSON AII)<br /><br /> A `string` a absence typu JSON AII jsou stejné díky `string` výchozí.<br /><br /> Ano `<root> string1</root>` JSON se mapuje `string` "Řetězec1".|0 nebo více CIIs|JSON `string` (RFC JSON, část 2.5). Každý `char` je znak, který odpovídá [kód znaku] z CÍ. Pokud neexistují žádné CIIs, mapuje se na prázdný objekt JSON `string`.<br /><br /> Příklad: Následující element mapuje na JSON fragment:<br /><br /> `<root type="string">42</root>`<br /><br /> JSON fragment je "42".<br /><br /> V XML na JSON mapování znaků, které musí být uvozena Mapa k řídicí znaky, všechny ostatní mapování znaků, které nejsou uvozeny zpětným lomítkem. Znak "/" je speciální – není uvozeno uvozovacím znakem i když nemusí být (přepsat si jako "\\/").<br /><br /> Příklad: Následující element mapuje na JSON fragment.<br /><br /> `<root type="string">the "da/ta"</root>`<br /><br /> JSON fragment je " \\" da\\/ta\\"".<br /><br /> Na formát JSON pro mapování XML žádné řídicí znaky a znaky, které nejsou správně uvozeny zpětným lomítkem mapování na odpovídající [kód znaku].<br /><br /> Příklad: Fragment JSON "\u0041BC" mapuje na následující element XML.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Řetězec může být uzavřen v prázdné znaky ("ws" v části 2 JSON RFC), která není mapována na XML.<br /><br /> Příklad: JSON fragment "ABC", (jsou mezery před první dvojité uvozovky), se mapuje na následující element XML.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Všechny prázdné znaky v kódu XML se mapuje na prázdné místo ve formátu JSON.<br /><br /> Příklad: Následující element XML se mapuje na JSON fragment.<br /><br /> `<root type="string">  A BC      </root>`<br /><br /> JSON fragment je "BC".|  
|`number`|1 nebo více CIIs|JSON `number` (RFC JSON, část 2.4), případně obklopený prázdné znaky. Každý znak v kombinaci číslo nebo prázdný znak je znak, který odpovídá [kód znaku] z CÍ.<br /><br /> Příklad: Následující element mapuje na JSON fragment.<br /><br /> `<root type="number">    42</root>`<br /><br /> JSON fragment je 42<br /><br /> (Prázdné znaky se zachovají).|  
|`boolean`|4 nebo 5 CIIs (který odpovídá `true` nebo `false`), případně ohraničený další CIIs prázdné znaky.|CÍ posloupnost, která odpovídá řetězci "true" je namapována na literál `true`, a CÍ posloupnost, která odpovídá řetězci "false" je namapována na literál `false`. Mezery kolem se zachovají.<br /><br /> Příklad: Následující element mapuje na JSON fragment.<br /><br /> `<root type="boolean"> false</root>`<br /><br /> JSON fragment je `false`.|  
|`null`|Není povoleno.|Literál `null`. Ve formátu JSON pro mapování XML `null` může být uzavřeny do prázdné znaky ("ws" v části 2), která není mapována na XML.<br /><br /> Příklad: Následující element mapuje na JSON fragment.<br /><br /> `<root type="null"/>`<br /><br /> or<br /><br /> `<root type="null"></root>`<br /><br /> :<br /><br /> Fragment JSON v obou případech je `Null`.|  
|`object`|0 nebo více EIIs.|A `begin-object` (levé složené závorky) jako v části 2.2 JSON RFC, za nímž následuje člen záznam pro každou EII jak je popsáno dále. Pokud existuje více než jeden EII, jsou mezi záznamů člena hodnota oddělovače (čárkami). To vše je následován end – objekt (pravá složená závorka).<br /><br /> Příklad: Následující element mapuje na JSON fragment.<br /><br /> \<kořenový typ = "objekt" ><br /><br /> \<Typ Type1 = "řetězec" > aaa\</type1 ><br /><br /> \<Typ Type2 = "řetězec" > bbb\</type2 ><br /><br /> \</ root ><br /><br /> JSON fragment je {"type1": "aaa", "type2": "bbb"}.<br /><br /> Pokud je k dispozici na XML na JSON mapování atribut Typ kontraktu dat, je vložen další záznam člena na začátku. Její název je [místní název] atributu typu kontraktu dat. ("__type") a jeho hodnotu atributu [Normalizovaná hodnota]. Naopak v JSON pro mapování XML, pokud je název prvního člena záznamu [místní název] atribut Typ kontraktu dat (tedy "\__typ"), je k dispozici v mapovaných XML odpovídající atribut Typ kontraktu dat, ale odpovídající EII není k dispozici. Všimněte si, že tento člen záznam musí objevit jako první v objektu JSON pro tento speciální mapování použít. To představuje odklon od obvykle zpracování JSON, ve kterém není důležité pořadí záznamů člena.<br /><br /> Příklad:<br /><br /> Následující fragment JSON se mapuje na XML.<br /><br /> `{"__type":"Person","name":"John"}`<br /><br /> XML je následující kód.<br /><br /> `<root type="object" __type="Person">   <name type="string">John</name> </root>`<br /><br /> Všimněte si, že \__typ AII je k dispozici, ale neexistuje žádná \__typ EII.<br /><br /> Nicméně pokud je obrácený pořadí v kódu JSON jako uvedené v následujícím příkladu.<br /><br /> {"name": "John","\__typ": "Osoba"}<br /><br /> Se zobrazí odpovídající kód XML.<br /><br /> `<root type="object">   <name type="string">John</name>   <__type type="string">Person</__type> </root>`<br /><br /> To znamená \__typ přestane jako obvykle mají zvláštní význam a mapuje EII AII není.<br /><br /> Uvozovací znaky/unescaping pravidla pro AII uživatele [Normalizovaná hodnota] při mapování na hodnotu JSON jsou stejné jako u řetězce JSON zadaný v "string" řádku této tabulky.<br /><br /> Příklad:<br /><br /> `<root type="object" __type="\abc" />`<br /><br /> v předchozím příkladu lze mapovat na následující JSON.<br /><br /> `{"__type":"\\abc"}`<br /><br /> Na XML na JSON mapování, nesmí být prvním EII společnosti [místní název] "\__typ".<br /><br /> Prázdné znaky (`ws`) nikdy vygenerovaný na XML na JSON mapování objektů a ignorován pro mapování XML na JSON.<br /><br /> Příklad: Následující fragment JSON se mapuje na XML element.<br /><br /> {"kopie": "aaa", "ddd": "bbb"}<br /><br /> XML element je znázorněno v následujícím kódu.<br /><br /> `<root type="object">    <ccc type="string">aaa</ccc>    <ddd type="string">bbb</bar> </root >`|  
Ray.|0 nebo více EIIs|Begin – pole s (levá hranatá závorka) jako v části 2.3 JSON RFC, za nímž následuje záznam pole pro každý EII jak je popsáno dále. Pokud existuje více než jeden EII, jsou mezi záznamy pole Hodnota oddělovače (čárkami). To vše je následován end pole.<br /><br /> Příklad: Následující element XML se mapuje na JSON fragment.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`<br /><br /> JSON fragment je ["aaa", "bbb"]<br /><br /> Prázdné znaky (`ws`) nikdy vygenerovaný na XML na JSON mapování polí a ignorován pro mapování XML na JSON.<br /><br /> Příklad: AJSON fragment.<br /><br /> ["aaa", "bbb"]<br /><br /> Element XML, který se mapuje na.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`|  
  
 Člen záznamy vypadat takto:  
  
-   Vnitřní prvku [místní název] se mapuje `string` součástí `member` definované v části 2.2 JSON RFC.  
  
 Příklad: Následující element mapuje na JSON fragment.  
  
 `<root type="object"/>`  
  
 `<myLocalName type="string">aaa</myLocalName>`  
  
 `</root >`  
  
 Zobrazí se následující fragment ve formátu JSON.  
  
 `{"myLocalName":"aaa"}`  
  
-   V XML na JSON mapování jsou uvozeny řídicími znaky, které musí být uvozena ve formátu JSON znaky a ostatní nejsou uvozeny zpětným lomítkem. Znak "/", i když není znak, který musí být uvozeny řídicími znaky, není uvozeno uvozovacím znakem přesto (nemusí být uvozena ve formátu JSON pro mapování XML). To je potřeba k podpoře technologie ASP.NET AJAX formát `DateTime` data ve formátu JSON.  
  
-   Na kód JSON pro mapování XML, všechny znaky (včetně nejsou řídicí znaky, v případě potřeby) přejdete do formuláře `string` , která vytváří [místní název].  
  
-   Vnitřní elementy [podřízené] namapovat na hodnotu v části 2.2, podle `JSON Type Attribute` stejně jako u `Root JSON Element`. Je povoleno více úrovní vnoření EIIs (včetně vnoření v rámci pole).  
  
 Příklad: Následující element mapuje na JSON fragment.  
  
 `<root type="object">`  
  
 `<myLocalName1 type="string">myValue1</myLocalName1>`  
  
 `<myLocalName2 type="number">2</myLocalName2>`  
  
 `<myLocalName3 type="object">`  
  
 `<myNestedName1 type="boolean">true</myNestedName1>`  
  
 `<myNestedName2 type="null"/>`  
  
 `</myLocalName3>`  
  
 `</root >`  
  
 Následující fragment JSON se mapuje na.  
  
 `{"myLocalName1":"myValue1","myLocalName2":2,"myLocalName3":{"myNestedName1":true,"myNestedName2":null}}`  
  
> [!NOTE]
>  V předchozím mapování neexistuje žádný krok kódování XML. Proto WCF podporuje pouze dokumenty JSON, ve kterém jsou všechny znaky v názvech klíčů znaky platné v názvech elementů XML. Například dokument JSON {"<": "a"} nepodporuje, protože < není platný název elementu XML.  
  
 Reverzní situace (znaky platné v XML, ale ne v JSON) nezpůsobí žádné problémy s, protože předchozí mapování zahrnuje kroky uvozovací znaky/unescaping JSON.  
  
 Pole záznamy vypadat takto:  
  
-   Vnitřní prvku [místní název] je "položka".  
  
-   Vnitřní prvku [podřízené] mapovat na hodnotu v části 2.3, podle atributu typu JSON, jak se provádí pro kořenový Element JSON. Je povoleno více úrovní vnoření EIIs (včetně vnoření v rámci objektů).  
  
 Příklad: Následující element mapuje na JSON fragment.  
  
 `<root type="array"/>`  
  
 `<item type="string">myValue1</item>`  
  
 `<item type="number">2</item>`  
  
 `<item type="array">`  
  
 `<item type="boolean">true</item>`  
  
 `<item type="null"/>`  
  
 `</item>`  
  
 `</root >`  
  
 Tady je JSON fragment.  
  
 `["myValue1",2,[true,null]]`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory>  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>  
 [Samostatná serializace JSON](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)
