---
title: Principy struktur a koncepcí datových proudů uzlů XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML node streams [XAML Services]
- nodes [XAML Services], XAML node stream
- XAML [XAML Services], XAML node streams
ms.assetid: 7c11abec-1075-474c-9d9b-778e5dab21c3
ms.openlocfilehash: b3de3dca029c5e676fc7cdebc7735cfdade0228a
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071617"
---
# <a name="xaml-node-stream-structures-and-concepts"></a>Struktury a koncepty datových proudů uzlů XAML

Čtecí programy XAML a zapisovače XAML implementované ve službách .NET XAML jsou založeny na konceptu návrhu datového proudu uzlu XAML. Datový proud uzlu XAML je konceptualizace sady uzlů XAML. V této konceptualizaci xaml procesor prochází strukturu vztahů uzlů v XAML jeden po druhém. V otevřeném datovém proudu uzlu XAML existuje kdykoli pouze jeden aktuální záznam nebo aktuální pozice a mnoho aspektů sestavy rozhraní API pouze informace dostupné z této pozice. Aktuální uzel v datovém proudu uzlu XAML lze popsat jako objekt, člen nebo hodnotu. Zpracováním XAML jako datového proudu uzlu XAML mohou čtenáři XAML komunikovat se zapisovateli XAML a povolit programu zobrazení, interakci nebo změnu obsahu datového proudu uzlu XAML během cesty načítání nebo operace uložení cesty, která zahrnuje XAML. Návrh rozhraní API pro čtení a zapisovače XAML a koncept datového proudu uzlů XAML jsou podobné předchozím <xref:System.Xml.XmlReader> souvisejícím návrhům a konceptům pro čtení a zapisovače, jako je například xml document object model (DOM) a třídy a. <xref:System.Xml.XmlWriter> Toto téma popisuje koncepty datového proudu uzlů XAML a popisuje, jak můžete psát rutiny, které interagují s reprezentacemi XAML na úrovni uzlu XAML.

## <a name="loading-xaml-into-a-xaml-reader"></a>Načítání XAML do čtečky XAML

Základní <xref:System.Xaml.XamlReader> třída nedeklaruje konkrétní techniku pro načítání počáteční XAML do čtečky XAML. Místo toho odvozené třídy deklaruje a implementuje načítat techniku, včetně obecné charakteristiky a omezení jeho vstupní zdroj pro XAML. Například přečte <xref:System.Xaml.XamlObjectReader> objektgrafu, počínaje vstupní zdroj jednoho objektu, který představuje kořen nebo základnu. Potom <xref:System.Xaml.XamlObjectReader> vytvoří datový proud uzlu XAML z grafu objektu.

Nejvýznamnější podtřída služby .NET <xref:System.Xaml.XamlReader> XAML <xref:System.Xaml.XamlXmlReader>services je . <xref:System.Xaml.XamlXmlReader>načte počáteční XAML, buď načtením textového souboru přímo přes datový proud nebo <xref:System.IO.TextReader>cestu k souboru, nebo nepřímo prostřednictvím související třídy čtečky, jako je například . Lze <xref:System.Xaml.XamlReader> si myslet jako obsahující celý vstupní zdroj XAML po jeho načtení. <xref:System.Xaml.XamlReader> Základní rozhraní API je však navržentak, aby čtenář pracuje s jedním uzlem XAML. Při prvním načtení je prvním samostatným uzlovým uzlem kořen xaml a jeho počáteční objekt.

### <a name="the-xaml-node-stream-concept"></a>Koncept datového proudu uzlů XAML

Pokud jste více obeznámeni s DOM, strom metafora nebo přístup založený na dotazu k přístupu k technologiím založeným na XML, užitečný způsob, jak konceptualizovat datový proud uzlu XAML je následující. Představte si, že načtený XAML je DOM nebo strom, kde jsou všechny možné uzlení rozbaleny a pak prezentovány lineárně. Při postupu přes uzly, může být procházení "in" nebo "out" úrovní, které by byly relevantní pro DOM, ale datový proud uzlu XAML není explicitně sledovat, protože tyto koncepty úrovně nejsou relevantní pro datový proud uzlu. Datový proud uzlu má "aktuální" pozici, ale pokud jste uložili jiné části datového proudu sami jako odkazy, každý aspekt datového proudu uzlu než aktuální pozice uzlu je mimo zobrazení.

Koncept datového proudu uzlu XAML má významnou výhodu, že pokud procházíte celý datový proud uzlu, máte jistotu, že jste zpracovali celou reprezentaci XAML; nemusíte se obávat, že dotaz, operace DOM nebo jiný nelineární přístup ke zpracování informací vynechal některé části úplné reprezentace XAML. Z tohoto důvodu reprezentace datového proudu uzlu XAML je ideální pro připojení čteček XAML a zapisovačů XAML a pro poskytování systému, kde můžete vložit vlastní proces, který funguje mezi fázečtení a zápisu operace zpracování XAML. V mnoha případech je řazení uzlů v datovém proudu uzlu XAML záměrně optimalizováno nebo uspořádáno čtenáři XAML versus jak se pořadí může zobrazit ve zdrojovém textu, binárním nebo objektovém grafu. Toto chování je určena k vynucení architektury zpracování XAML, kdy autoři XAML nejsou nikdy v pozici, kde musí přejít "zpět" v datovém proudu uzlu. V ideálním případě by všechny operace zápisu XAML měly být schopny fungovat na základě kontextu schématu a aktuální pozice datového proudu uzlu.

## <a name="a-basic-reading-node-loop"></a>Smyčka základního čtecího uzlu

Základní smyčka čtecího uzlu pro zkoumání datového proudu uzlu XAML se skládá z následujících konceptů. Pro účely smyčků uzlů, jak je popsáno v tomto tématu, předpokládejme, že <xref:System.Xaml.XamlXmlReader>čtete textově čitelný soubor XAML založený na člověku pomocí . Odkazy v této části odkazují na konkrétní rozhraní API <xref:System.Xaml.XamlXmlReader>smyčky uzlů XAML implementované rozhraním .

- Ujistěte se, že nejste na konci datového proudu <xref:System.Xaml.XamlXmlReader.IsEof%2A>uzlu XAML (kontrola , nebo použijte vrácenou <xref:System.Xaml.XamlXmlReader.Read%2A> hodnotu). Pokud jste na konci datového proudu, neexistuje žádný aktuální uzel a měli byste ukončit.

- Zkontrolujte, jaký typ uzlu datový proud uzlu XAML <xref:System.Xaml.XamlXmlReader.NodeType%2A>aktuálně zveřejňuje voláním .

- Pokud máte přidružený zapisovač objektů XAML, <xref:System.Xaml.XamlWriter.WriteNode%2A> který je připojen přímo, obvykle voláte v tomto okamžiku.

- Na základě <xref:System.Xaml.XamlNodeType> toho, který je hlášen jako aktuální uzel nebo aktuální záznam, volejte jednu z následujících získat informace o obsahu uzlu:

  - Pro <xref:System.Xaml.XamlXmlReader.NodeType%2A> nebo <xref:System.Xaml.XamlNodeType.StartMember> <xref:System.Xaml.XamlNodeType.EndMember>, <xref:System.Xaml.XamlXmlReader.Member%2A> volání <xref:System.Xaml.XamlMember> získat informace o člen. Člen může být <xref:System.Xaml.XamlDirective>, a proto nemusí být nutně konvenční typově definovaný člen předchozího objektu. Například `x:Name` použít na objekt se zobrazí jako <xref:System.Xaml.XamlMember.IsDirective%2A> člen XAML, kde je true a <xref:System.Xaml.XamlMember.Name%2A> člen je `Name`, s dalšími vlastnostmi označující, že tato směrnice je pod xaml jazyk xaml oboru názvů.

  - Pro <xref:System.Xaml.XamlXmlReader.NodeType%2A> a <xref:System.Xaml.XamlNodeType.StartObject> <xref:System.Xaml.XamlNodeType.EndObject>nebo <xref:System.Xaml.XamlXmlReader.Type%2A> , <xref:System.Xaml.XamlType> volání získat informace o objektu.

  - Pro <xref:System.Xaml.XamlXmlReader.NodeType%2A> a, <xref:System.Xaml.XamlNodeType.Value> <xref:System.Xaml.XamlXmlReader.Value%2A>volejte . Uzel je hodnota pouze v případě, že se jedná o nejjednodušší výraz hodnoty pro člena nebo inicializační text pro objekt (měli byste však vědět o chování převodu typu, jak je popsáno v nadcházející části tohoto tématu).

  - V <xref:System.Xaml.XamlXmlReader.NodeType%2A> případě <xref:System.Xaml.XamlNodeType.NamespaceDeclaration>a <xref:System.Xaml.XamlXmlReader.Namespace%2A> od , volání získat informace o oboru názvů pro uzel oboru názvů.

- Volání <xref:System.Xaml.XamlXmlReader.Read%2A> předem čtečky XAML na další uzel v datovém proudu uzlu XAML a opakujte kroky znovu.

Datový proud uzlu XAML poskytovaný čtenáři XAML služby .NET služby xaml vždy poskytuje úplný, hluboký průchod všech možných uzlů. Typické techniky řízení toku pro smyčku uzlu XAML zahrnují definování těla v rámci `while (reader.Read())`a zapnutí <xref:System.Xaml.XamlXmlReader.NodeType%2A> v každém bodě uzlu ve smyčce uzlu.

Pokud je datový proud uzlu na konci souboru, aktuální uzel má hodnotu null.

Nejjednodušší smyčka, která používá čtečku a zapisovač, se podobá následujícímu příkladu.

```csharp
XamlXmlReader xxr = new XamlXmlReader(new StringReader(xamlStringToLoad));
//where xamlStringToLoad is a string of well formed XAML
XamlObjectWriter xow = new XamlObjectWriter(xxr.SchemaContext);
while (xxr.Read()) {
  xow.WriteNode(xxr);
}
```

Tento základní příklad smyčky uzlu XAML cesty zatížení transparentně spojuje čtečku XAML a zapisovač <xref:System.Xaml.XamlServices.Parse%2A?displayProperty=nameWithType>XAML a nedělá nic jiného, než kdybyste použili . Ale tato základní struktura je pak rozšířena tak, aby se vztahovala na váš scénář čtení nebo psaní. Některé možné scénáře jsou následující:

- Zapněte <xref:System.Xaml.XamlXmlReader.NodeType%2A>. Proveďte různé akce v závislosti na typu uzlu, který se čte.

- Nevolejte <xref:System.Xaml.XamlWriter.WriteNode%2A> ve všech případech. Zavolej <xref:System.Xaml.XamlWriter.WriteNode%2A> jen <xref:System.Xaml.XamlXmlReader.NodeType%2A> v některých případech.

- V rámci logiky pro konkrétní typ uzlu analyzujte specifika tohoto uzlu a jednejte na ně. Můžete například zapisovat pouze objekty, které pocházejí z určitého oboru názvů XAML, a potom přetáhnout nebo odložit všechny objekty, které nejsou z tohoto oboru názvů XAML. Nebo můžete vynechat nebo jinak znovu zpracovat všechny direktivy XAML, které váš systém XAML nepodporuje jako součást zpracování členů.

- Definujte <xref:System.Xaml.XamlObjectWriter> vlastní, `Write*` která přepíše metody, případně provádění mapování typu, které obchází kontext schématu XAML.

- Vytvořte <xref:System.Xaml.XamlXmlReader> použít nevýchozí kontext schématu XAML tak, aby vlastní rozdíly v chování XAML jsou používány jak čtenář a zapisovač.

### <a name="accessing-xaml-beyond-the-node-loop-concept"></a>Přístup k XAML za konceptem smyčky uzlů

Existují potenciálně jiné způsoby práce s reprezentací XAML než jako smyčka uzlu XAML. Může například existovat čtečka XAML, která dokáže číst indexovaný uzel, nebo `x:Name`zejména `x:Uid`přistupuje k uzlům přímo pomocí , aplikacem nebo prostřednictvím jiných identifikátorů. Služby .NET XAML neposkytuje úplnou implementaci, ale poskytuje navrhovaný vzor prostřednictvím služeb a typů podpory. Další informace naleznete v tématech <xref:System.Xaml.IXamlIndexingReader> a <xref:System.Xaml.XamlNodeList>.

## <a name="working-with-the-current-node"></a>Práce s aktuálním uzlem

Většina scénářů, které používají smyčku uzlu XAML, nečtou pouze uzly. Většina scénářů zpracovává aktuální uzly a předává <xref:System.Xaml.XamlWriter>každý uzel jeden po druhém implementaci aplikace .

V případě typické cesty <xref:System.Xaml.XamlXmlReader> zatížení vytvoří datový proud uzlu XAML; uzly XAML jsou zpracovány podle vaší logiky a kontextu schématu XAML; a uzly jsou <xref:System.Xaml.XamlObjectWriter>předány . Potom integrovat výsledný objekt grafu do aplikace nebo rozhraní.

V typickém scénáři <xref:System.Xaml.XamlObjectReader> cesty pro uložení přečte graf objektu, jednotlivé <xref:System.Xaml.XamlXmlWriter> uzly XAML jsou zpracovány a výstupy serializované výsledek jako textový soubor XAML. Klíčem je, že cesty i scénáře zahrnují práci s přesně jedním uzlem XAML najednou a uzly XAML jsou k dispozici pro zpracování standardizovaným způsobem, který je definován systémem typu XAML a the.NET rozhraní API služby XAML.

### <a name="frames-and-scope"></a>Rámce a rozsah

Smyčka uzlu XAML prochází datovým proudem uzlu XAML lineárním způsobem. Datový proud uzlu prochází do objektů, do členů, které obsahují jiné objekty a tak dále. Je často užitečné sledovat rozsah v rámci datového proudu uzlu XAML implementací konceptu rámce a zásobníku. To platí zejména v případě, že aktivně upravujete datový proud uzlu, když jste v něm. Podpora rámce a zásobníku, které implementujete jako `StartObject` součást `GetObject`logiky smyčky uzlu, může počítat (nebo ) a `EndObject` obory při sestupu do struktury uzlu XAML, pokud je struktura myšlenka z hlediska modelu DOM.

## <a name="traversing-and-entering-object-nodes"></a>Procházení a zadávání uzlů objektů

První uzel v datovém proudu uzlu při otevření čtečkou XAML je uzel počátečního objektu kořenového objektu. Podle definice je tento objekt vždy uzel jednoho objektu a nemá žádné partnery. V každém příkladu XAML reálného světa je kořenový objekt definován tak, aby měl jednu nebo více vlastností, které mají více objektů, a tyto vlastnosti mají členské uzly. Členské uzly pak mají jeden nebo více uzlů objektu nebo může také ukončit v uzlu hodnoty místo. Kořenový objekt obvykle definuje názvové obory XAML, které jsou syntakticky přiřazeny jako atributy v textové značce XAML, ale mapují se na typ `Namescope` uzlu v reprezentaci datového proudu uzlu XAML.

Vezměme si následující příklad XAML (to je libovolný XAML, není zálohována existující typy v .NET). `FavorCollection` Předpokládejme, že v `List<T>` tomto `Favor` `Balloon` objektovém modelu je , a `NoiseMaker` jsou přiřaditelné `Favor`k , `Balloon.Color` vlastnost je zálohována objekt podobný `Color` tomu, jak WPF definuje barvy jako známé názvy barev a `Color` podporuje převaděč typů pro syntaxi atributu.

|Značky XAML|Výsledný datový proud uzlu XAML|
|-----------------|--------------------------------|
|`<Party`|`Namespace`uzel pro`Party`|
|`xmlns="PartyXamlNamespace">`|`StartObject`uzel pro`Party`|
|`<Party.Favors>`|`StartMember`uzel pro`Party.Favors`|
||`StartObject`uzel pro implicitní`FavorCollection`|
||`StartMember`uzel pro `FavorCollection` vlastnost implicitní položky.|
|`<Balloon`|`StartObject`uzel pro`Balloon`|
|`Color="Red"`|`StartMember`uzel pro`Color`<br /><br /> `Value`uzel pro řetězec hodnoty atributu`"Red"`<br /><br /> `EndMember`Pro`Color`|
|`HasHelium="True"`|`StartMember`uzel pro`HasHelium`<br /><br /> `Value`uzel pro řetězec hodnoty atributu`"True"`<br /><br /> `EndMember`Pro`HasHelium`|
|`>`|`EndObject`Pro`Balloon`|
|`<NoiseMaker>Loudest</NoiseMaker>`|`StartObject`uzel pro`NoiseMaker`<br /><br /> `StartMember`uzel pro`_Initialization`<br /><br /> `Value`uzel pro řetězec hodnoty inicializace`"Loudest"`<br /><br /> `EndMember`uzel pro`_Initialization`<br /><br /> `EndObject`Pro`NoiseMaker`|
||`EndMember`uzel pro `FavorCollection` vlastnost implicitní položky.|
||`EndObject`uzel pro implicitní`FavorCollection`|
|`</Party.Favors>`|`EndMember`Pro`Favors`|
|`</Party>`|`EndObject`Pro`Party`|

V datovém proudu uzlu XAML se můžete spolehnout na následující chování:

- Pokud `Namespace` uzel existuje, je přidán do datového `StartObject` proudu bezprostředně před, který `xmlns`deklaroval obor názvů XAML s . Podívejte se na předchozí tabulku s XAML a ukázkový datový proud uzlu znovu. Všimněte `StartObject` si, jak a `Namespace` uzly se zdají být provedeny oproti jejich prohlášení pozice v textové značky. Toto je zástupce chování, kde uzly oboru názvů vždy zobrazí před uzlu, které platí pro v datovém proudu uzlu. Účelem tohoto návrhu je, že informace o oboru názvů je důležité pro zapisovače objektů a musí být známy před objektem zapisovač pokusí provést mapování typu nebo jinak zpracovat objekt. Umístění informací o oboru názvů XAML před rozsah aplikace v datovém proudu usnadňuje vždy zpracování datového proudu uzlu v prezentovaném pořadí.

- Z důvodu výše uvedeného zvažování `Namespace` je jeden nebo více uzlů, které si přečtete jako první ve `StartObject` většině případů značek v reálném světě při procházení uzlů od začátku, nikoli kořenového adresáře.

- Uzel `StartObject` může být `StartMember`následován `Value`, nebo `EndObject`okamžité . Nikdy není bezprostředně následován jiným `StartObject`.

- A `StartMember` může následovat `StartObject`a `Value`, nebo `EndMember`okamžité . Může následovat `GetObject`, pro členy, kde hodnota má pocházet z existující hodnoty `StartObject` nadřazeného objektu, nikoli který by instanci nové hodnoty. Může také následovat `Namespace` uzel, který se vztahuje na `StartObject`nadcházející . Nikdy není bezprostředně následován jiným `StartMember`.

- Uzel `Value` představuje samotnou hodnotu; neexistuje žádná "EndValue". Může následovat pouze `EndMember`.

  - XAML inicializace text objektu, které mohou být použity konstrukce nemá za následek objekt value struktury. Místo toho je vytvořen uzel vyhrazeného člena pro člena s názvem. `_Initialization` a tento uzel člena obsahuje řetězec inicializační hodnoty. Pokud existuje, `_Initialization` je vždy `StartMember`první . `_Initialization`může být kvalifikován v některých reprezentacích služeb XAML s jazykem `_Initialization` XAML XAML namescope, aby bylo jasné, že není definovanou vlastností v typech zálohování.

  - Kombinace Člen-Hodnota představuje nastavení atributu hodnoty. Nakonec může být převaděč hodnoty zapojených do zpracování této hodnoty a hodnota je prostý řetězec. To však není vyhodnocena, dokud zapisovač objektu XAML zpracovává tento datový proud uzlu. Zapisovač objektů XAML má potřebný kontext schématu XAML, mapování systému typů a další podporu potřebnou pro převody hodnot.

- Uzel `EndMember` může být následován `StartMember` uztelem pro následující `EndObject` člen nebo uztelem pro vlastníka člena.

- Po `EndObject` uzlu může následovat `EndMember` uzel. Může také následovat `StartObject` uzel pro případy, kdy jsou objekty partnery v položkách kolekce. Nebo může následovat `Namespace` uzel, který se vztahuje na `StartObject`nadcházející .

  - Pro jedinečný případ uzavření celého datového `EndObject` proudu uzlu kořene není následován nic; čtečka je nyní konec souboru <xref:System.Xaml.XamlReader.Read%2A> `false`a vrátí .

## <a name="value-converters-and-the-xaml-node-stream"></a>Převaděče hodnot a datový proud uzlů XAML

Převaděč hodnot je obecný termín pro rozšíření značek, převaděč typu (včetně serializárů hodnot) nebo jinou vyhrazenou třídu, která je vykazována jako převaděč hodnot prostřednictvím systému typu XAML. V datovém proudu uzlu XAML mají použití převaděče typů a použití rozšíření značek velmi odlišné reprezentace.

### <a name="type-converters-in-the-xaml-node-stream"></a>Převaděče typů v datovém proudu uzlů XAML

Sada atributů, která nakonec vede k použití převaděče typu, je uvedena v datovém proudu uzlu XAML jako hodnota člena. Datový proud uzlu XAML se nepokouší vytvořit objekt instance převaděče typu a předat mu hodnotu. Použití implementace převodu typu převodu vyžaduje vyvolání kontextu schématu XAML a jeho použití pro mapování typů. I určení, která třída převaděče typu by měla být použita ke zpracování hodnoty, vyžaduje kontext schématu XAML nepřímo. Při použití výchozího kontextu schématu XAML jsou tyto informace k dispozici v systému typu XAML. Pokud potřebujete informace o třídě převaděče typu na úrovni datového proudu uzlu XAML před <xref:System.Xaml.XamlMember> připojením k zapisovateli XAML, můžete je získat z informací o nastaveném členu. Ale jinak by měl být vstup převaděče typu zachován v datovém proudu uzlu XAML jako prostá hodnota, dokud nebude provedena zbývající část operací, které vyžadují systém mapování typu a kontext schématu XAML, například vytvoření objektu zapisovačem objektu XAML.

Zvažte například následující osnovu definice třídy a použití XAML pro něj:

```csharp
public class BoardSizeConverter : TypeConverter {
  //converts from string to an int[2] by splitting on an "x" char
}
public class GameBoard {
  [TypeConverter(typeof(BoardSizeConverter))]
  public int[] BoardSize; //2x2 array, initialization not shown
}
```

```xaml
<GameBoard BoardSize="8x8"/>
```

Textová reprezentace datového proudu uzlu XAML pro toto použití může být vyjádřena takto:

`StartObject`s <xref:System.Xaml.XamlType> reprezentací`GameBoard`

`StartMember`s <xref:System.Xaml.XamlMember> reprezentací`BoardSize`

`Value`uzel s textovým`8x8`řetězcem " "

`EndMember`Odpovídá`BoardSize`

`EndObject`Odpovídá`GameBoard`

Všimněte si, že v tomto datovém proudu uzlu neexistuje žádná instance převaděče typu. Ale můžete získat informace převaděče <xref:System.Xaml.XamlMember> `BoardSize`typu voláním <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> na pro . Pokud máte platný kontext schématu XAML, můžete také vyvolat metody převaděče získáním instance z <xref:System.Xaml.Schema.XamlValueConverter%601.ConverterInstance%2A>.

### <a name="markup-extensions-in-the-xaml-node-stream"></a>Rozšíření značek v datovém proudu uzlů XAML

Použití rozšíření značek je hlášeno v datovém proudu uzlu XAML jako uzel objektu v rámci člena, kde objekt představuje instanci rozšíření značek. Proto je použití rozšíření značek je uveden a explicitněji v reprezentaci datového proudu uzlu než použití převaděče typu a nese další informace. <xref:System.Xaml.XamlMember>informace vám nemohly říct nic o rozšíření značek, protože použití je situační a liší se v každém možném případě značky; není vyhrazena a implicitní podle typu nebo člena, jako je tomu v případě převaděčů typu.

Reprezentace datového proudu uzlu rozšíření značek jako uzly objektu je případ i v případě, že použití rozšíření značky byla provedena ve formě atributu v text značky XAML (což je často případ). Použití rozšíření značek, která používají formulář elementu explicitní objekt, jsou zpracována stejným způsobem.

V rámci uzlu objektu rozšíření značek mohou být členy tohoto rozšíření značek. Reprezentace datového proudu uzlu XAML zachovává použití tohoto rozšíření značek, ať už se jedná o použití pozičního parametru nebo použití s explicitními pojmenovanými parametry.

Pro použití pozičního parametru obsahuje datový proud uzlu XAML vlastnost `_PositionalParameters` definovanou jazykem XAML, která zaznamenává použití. Tato vlastnost je <xref:System.Collections.Generic.List%601> <xref:System.Object> obecný s omezením. Omezení je objekt a ne řetězec, protože je možné, že použití pozičního parametru může obsahovat vnořené použití rozšíření značek v něm. Chcete-li získat přístup k pozičníparametry z použití, můžete iterovat prostřednictvím seznamu a použít indexery pro jednotlivé hodnoty seznamu.

Pro použití pojmenovanéparametr, každý pojmenovaný parametr je reprezentován jako uzel člena tohoto názvu v datovém proudu uzlu. Hodnoty členů nejsou nutně řetězce, protože může být vnořené použití rozšíření značky.

`ProvideValue`z rozšíření značek ještě není vyvolána. Je však vyvolána, pokud připojíte čtečku XAML `WriteEndObject` a zapisovač XAML tak, aby byl vyvolán v uzlu rozšíření značek při jeho zkoumání v datovém proudu uzlu. Z tohoto důvodu obvykle potřebujete stejný kontext schématu XAML k dispozici jako by se použít k vytvoření grafu objektu na cestě zatížení. V `ProvideValue` opačném případě z jakékoli rozšíření značky může vyvolat výjimky zde, protože nemá očekávané služby k dispozici.

## <a name="xaml-and-xml-language-defined-members-in-the-xaml-node-stream"></a>Členové xaml a xml v datovém proudu uzlů XAML

Některé členy jsou zavedeny do datového proudu uzlu XAML z důvodu interpretace a konvence <xref:System.Xaml.XamlMember> čtečky XAML, namísto prostřednictvím explicitní vyhledávání nebo konstrukce. Často tyto členy jsou direktivy XAML. V některých případech je akt čtení XAML, který zavádí směrnice do datového proudu uzlu XAML. Jinými slovy původní vstupní text XAML explicitně nespecifikoval členské směrnice, ale čtečka XAML vloží direktivu, aby splnila strukturální konvence XAML a informace o sestavě v datovém proudu uzlu XAML před ztrátou této informace.

Následující seznam bere na vědomí všechny případy, kdy se očekává, že čtečka XAML zavede uzel člena xaml směrnice a jak je tento uzel člena identifikován v implementacích služby .NET XAML Services.

- **Inicializační text pro uzel objektu:** Název tohoto členského uzlu `_Initialization`je , představuje direktivu XAML a je definován v oboru názvů XAML jazyka XAML. Můžete získat statickou entitu pro něj z <xref:System.Xaml.XamlLanguage.Initialization%2A>.

- **Poziční parametry pro rozšíření značek:** Název tohoto členského uzlu `_PositionalParameters`je a je definován v oboru názvů XAML jazyka XAML. Vždy obsahuje obecný seznam objektů, z nichž každý je poziční `,` parametr předem oddělen rozdělením na znak oddělovače, jak je dodáván ve vstupním XAML. Můžete získat statickou entitu pro poziční parametry směrnice z <xref:System.Xaml.XamlLanguage.PositionalParameters%2A>.

- **Neznámý obsah:** Název tohoto uzlu člena `_UnknownContent`je . Přísně vzato, <xref:System.Xaml.XamlDirective>je to a , a je definovánv xaml jazyk xaml oboru názvů. Tato směrnice se používá jako sentinel pro případy, kdy element objektu XAML obsahuje obsah ve zdrojovém XAML, ale v kontextu aktuálně dostupného schématu XAML nelze určit žádnou vlastnost obsahu. Tento případ můžete zjistit v datovém proudu uzlu XAML kontrolou členů s názvem `_UnknownContent`. Pokud žádná jiná akce je přijata v datovém proudu <xref:System.Xaml.XamlObjectWriter> uzlu načíst `WriteEndObject` xaml, `_UnknownContent` výchozí vyvolá pokus o pokus, když narazí na člena na libovolný objekt. Výchozí <xref:System.Xaml.XamlXmlWriter> nevyvolá a považuje člen za implicitní. Můžete získat statickou `_UnknownContent` entitu z . <xref:System.Xaml.XamlLanguage.UnknownContent%2A>

- **Vlastnost kolekce kolekce:** Přestože záložní typ CLR třídy kolekce, která se používá pro XAML, má obvykle vyhrazenou pojmenovanou vlastnost, která obsahuje položky kolekce, tato vlastnost není známa systému typu XAML před rezolucí typu zálohování. Místo toho datový proud uzlu XAML zavádí zástupný `Items` symbol jako člen typu XAML kolekce. V implementaci služby .NET XAML Services je `_Items`název této směrnice nebo člena v datovém proudu uzlu . Konstanta pro tuto směrnici <xref:System.Xaml.XamlLanguage.Items%2A>lze získat z .

    Všimněte si, že datový proud uzlu XAML může obsahovat vlastnost Items s položkami, které se nedají analyzovat na základě rozlišení typu zálohování a kontextu schématu XAML. Například:

- **Členy definované jazykem XML:** Členové definovaní `xml:base` `xml:lang` jazykem `xml:space` XML a členové jsou `base`vykazovány jako direktivy XAML s názvem , `lang`a `space` v implementacích služby .NET XAML Services. Obor názvů pro tyto jsou `http://www.w3.org/XML/1998/namespace`soubory názvů XML . Konstanty pro každou z nich <xref:System.Xaml.XamlLanguage>lze získat z .

## <a name="node-order"></a>Pořadí uzlů

V některých <xref:System.Xaml.XamlXmlReader> případech změní pořadí uzlů XAML v datovém proudu uzlu XAML oproti pořadí, ve které se uzly zobrazí, pokud jsou zobrazeny ve značkách nebo pokud jsou zpracovány jako XML. To se provádí za účelem pořadí <xref:System.Xaml.XamlObjectWriter> uzlů tak, aby datový proud uzlu můžete zpracovat pouze pro předávání.  Ve službě .NET XAML služby čtecí zařízení XAML změní pořadí uzlů, nikoli ponechá tuto úlohu zapisovateli XAML jako optimalizaci výkonu pro spotřebitele zapisovače objektů XAML datového proudu uzlu.

Některé direktivy jsou určeny konkrétně poskytnout další informace pro vytvoření objektu z prvku objektu. Těmito směrnicemi `Initialization` `PositionalParameters`jsou: `FactoryMethod` `Arguments`, , `TypeArguments`, . . .NET XAML Services XAML čtenáři pokusí umístit tyto direktivy jako `StartObject`první členy v datovém proudu uzlu po objektu , z důvodů, které jsou vysvětleny v další části.

### <a name="xamlobjectwriter-behavior-and-node-order"></a>Chování a pořadí uzlů XamlObjectWriter

`StartObject`to <xref:System.Xaml.XamlObjectWriter> a není nutně signál pro zapisovač objektu XAML okamžitě vytvořit instanci objektu. XAML obsahuje několik funkcí jazyka, které umožňují inicializovat objekt s dalším vstupem a nespoléhat se zcela na vyvolání konstruktoru bez parametrů k vytvoření počátečního objektu a teprve potom nastavení vlastností. Mezi tyto <xref:System.Windows.Markup.XamlDeferLoadAttribute>funkce patří: ; inicializační text; [x:Argumenty typu](xtypearguments-directive.md); poziční parametry rozšíření značky; metody výroby a přidružené uzly [x:Arguments](xarguments-directive.md) (XAML 2009). Každý z těchto případů zpoždění skutečné konstrukce objektu a protože datový proud uzlu je přeuspořádaný, zapisovač objektu XAML může spoléhat na chování skutečně konstrukce instance vždy, když je zjištěn a start člen, který není konkrétně stavební směrnice pro tento typ objektu.

### <a name="getobject"></a>GetObject

`GetObject`představuje uzel XAML, kde místo vytváření nového objektu by měl zapisovač objektu XAML místo toho získat hodnotu vlastnosti obsahující objekt. Typický případ, `GetObject` kdy je uzel zjištěn v datovém proudu uzlu XAML je pro objekt kolekce nebo objekt slovníku, když je obsahující vlastnost záměrně jen pro čtení v objektovém modelu typu zálohování. V tomto scénáři kolekce nebo slovníku často je vytvořen a inicializován (obvykle prázdný) logikou inicializace vlastnícího typu.

## <a name="see-also"></a>Viz také

- <xref:System.Xaml.XamlObjectReader>
- [XAML Services](index.md)
- [Obory názvů jazyka XAML](namespaces.md)
