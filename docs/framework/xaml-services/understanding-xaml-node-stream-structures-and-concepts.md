---
title: Principy struktur a koncepcí datových proudů uzlů XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML node streams [XAML Services]
- nodes [XAML Services], XAML node stream
- XAML [XAML Services], XAML node streams
ms.assetid: 7c11abec-1075-474c-9d9b-778e5dab21c3
ms.openlocfilehash: d6b2975b8e0338b121d00f5ec7f4ffb69d32ab6a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400738"
---
# <a name="understanding-xaml-node-stream-structures-and-concepts"></a>Principy struktur a koncepcí datových proudů uzlů XAML

Čtečky XAML a zapisovače XAML, jak jsou implementovány v .NET Framework služby XAML, jsou založeny na konceptu návrhu datového proudu uzlu XAML. Datový proud uzlu XAML je koncepční sada uzlů XAML. V tomto principu provede procesor XAML strukturu vztahů uzlů v jazyce XAML v jednom okamžiku. V otevřeném datovém proudu uzlu XAML již existuje pouze jeden aktuální záznam nebo aktuální pozice, přičemž mnoho aspektů rozhraní API hlásí pouze informace, které jsou z této pozice k dispozici. Aktuální uzel v datovém proudu uzlu XAML lze popsat jako objekt, člen nebo hodnotu. Čtečky XAML mohou komunikovat s moduly pro zápis XAML a povolit programu zobrazení, interakci s nebo změnou obsahu datového proudu uzlu XAML během cesty načtení nebo operace uložení cesty, která zahrnuje XAML. Návrh rozhraní API pro čtení a zápis v XAML a koncept datového proudu uzlu XAML se podobá předchozím souvisejícím designům a návrhům pro [!INCLUDE[TLA#tla_xmldom](../../../includes/tlasharptla-xmldom-md.md)] zápis a <xref:System.Xml.XmlReader> k <xref:System.Xml.XmlWriter> konceptům, jako jsou třídy a a. Toto téma popisuje koncepty pro streamy uzlu XAML a popisuje, jak můžete napsat rutiny, které pracují s reprezentacemi XAML na úrovni uzlu XAML.

<a name="loading_into_a_xaml_reader"></a>

## <a name="loading-xaml-into-a-xaml-reader"></a>Načtení XAML do čtečky XAML

Základní <xref:System.Xaml.XamlReader> třída nedeklaruje konkrétní techniku pro načtení počátečního XAML do čtečky XAML. Namísto toho odvozená třída deklaruje a implementuje techniku načítání, včetně obecných vlastností a omezení jejich vstupního zdroje pro jazyk XAML. Například <xref:System.Xaml.XamlObjectReader> přečte graf objektu, počínaje zdrojem vstupu jednoho objektu, který představuje kořen nebo základní. <xref:System.Xaml.XamlObjectReader> Pak vytvoří datový proud uzlu XAML z grafu objektu.

Nejvýraznější .NET Framework služby XAML – definovaná <xref:System.Xaml.XamlReader> podtřída je. <xref:System.Xaml.XamlXmlReader> <xref:System.Xaml.XamlXmlReader>Načte počáteční kód XAML buď načtením textového souboru přímo pomocí datového proudu nebo cesty k souboru, nebo nepřímo prostřednictvím související třídy <xref:System.IO.TextReader>čtenář, jako je například. Lze <xref:System.Xaml.XamlReader> si představit jako obsahující celou vstupní zdroj XAML poté, co byl načten. <xref:System.Xaml.XamlReader> Základní rozhraní API je však navrženo tak, aby čtenář komunikoval s jedním uzlem XAML. Při prvním načtení je prvním jedním uzlem, ke kterému se setkáte, kořenem XAML a jeho počátečním objektem.

### <a name="the-xaml-node-stream-concept"></a>Koncept datového proudu uzlu XAML

Pokud jste všeobecně obeznámeni s modelem DOM, metafora stromu nebo přístupem založenými na dotazech k přístupu k technologiím založeným na jazyce XML, je užitečný způsob, jak conceptualize datový proud uzlu XAML, je následující. Představte si, že načtený kód XAML je model DOM nebo strom, ve kterém je každý možný uzel rozbalený celým způsobem a následně zobrazený lineárně. Při přechodu mezi uzly můžete přecházet "in" nebo "out" úrovní, které by byly relevantní pro model DOM, ale datový proud uzlu XAML explicitně nesleduje, protože tyto koncepty úrovně nejsou relevantní pro datový proud uzlu. Datový proud uzlu má "aktuální" pozici, ale pokud jste sami neuložili jiné části streamu jako odkazy, každý aspekt streamu uzlu, který je jiný než aktuální pozice uzlu, je mimo zobrazení.

Koncept datového proudu uzlu XAML má významnou výhodu, že pokud procházíte celým datovým proudem uzlu, máte jistotu, že jste zpracovali celé vyjádření reprezentace v jazyce XAML; Nemusíte se obávat, že dotaz, operace modelu DOM nebo nějaký jiný nelineární přístup ke zpracování informací neobsahují část úplné reprezentace XAML. Z tohoto důvodu je reprezentace datového proudu uzlu XAML ideální pro připojení čtenářů XAML a zapisovačů XAML a pro poskytnutí systému, kde můžete vložit vlastní proces, který funguje mezi fázemi čtení a zápisu operace zpracování XAML. V mnoha případech je pořadí uzlů v datovém proudu uzlu XAML záměrně optimalizováno nebo přeobjednáno čtečkami XAML a jak se může pořadí zobrazit ve zdrojovém textu, binárním souboru nebo grafu objektů. Toto chování je určeno k vykonání architektury zpracování XAML, kdy zapisovače XAML nejsou nikdy v pozici, kde se musí v proudu uzlů vrátit zpět. V ideálním případě by měly být všechny operace zápisu XAML schopny pracovat na kontextu schématu a na aktuální pozici datového proudu uzlu.

<a name="a_basic_reading_node_loop"></a>

## <a name="a-basic-reading-node-loop"></a>Základní smyčka uzlu čtení

Základní smyčka uzlu čtení pro zkoumání datového proudu uzlu XAML se skládá z následujících konceptů. Pro účely smyček uzlů, jak je popsáno v tomto tématu, Předpokládejme, že čtete textový soubor XAML čitelný pomocí <xref:System.Xaml.XamlXmlReader>. Odkazy v této části odkazují na konkrétní rozhraní API smyčky uzlu XAML implementované <xref:System.Xaml.XamlXmlReader>.

- Ujistěte se, že nejste na konci datového proudu uzlu XAML (Zkontrolujte <xref:System.Xaml.XamlXmlReader.IsEof%2A>nebo <xref:System.Xaml.XamlXmlReader.Read%2A> použijte návratovou hodnotu). Pokud jste na konci streamu, neexistuje žádný aktuální uzel a měli byste skončit.

- Ověřte, jaký typ uzlu datový proud uzlu XAML aktuálně zpřístupňuje voláním <xref:System.Xaml.XamlXmlReader.NodeType%2A>.

- Máte-li přidružený zapisovač objektů XAML, který je připojen přímo, obecně se na <xref:System.Xaml.XamlWriter.WriteNode%2A> tento bod volá.

- Na základě toho <xref:System.Xaml.XamlNodeType> , který je hlášen jako aktuální uzel nebo aktuální záznam, zavolejte jednu z následujících hodnot pro získání informací o obsahu uzlu:

  - <xref:System.Xaml.XamlXmlReader.NodeType%2A> Pro<xref:System.Xaml.XamlNodeType.EndMember>nebo volejte volání<xref:System.Xaml.XamlXmlReader.Member%2A> pro získání<xref:System.Xaml.XamlMember>informacíočlenu. <xref:System.Xaml.XamlNodeType.StartMember> Všimněte si, že člen může být <xref:System.Xaml.XamlDirective>, a proto nemusí být nutně běžným uživatelem definovaným členem předchozího objektu. Například `x:Name` použití na objekt se zobrazí jako člen jazyka XAML, kde <xref:System.Xaml.XamlMember.IsDirective%2A> je hodnota true a <xref:System.Xaml.XamlMember.Name%2A> člen je `Name`, s jinými vlastnostmi, které označují, že tato direktiva je v oboru názvů XAML jazyka XAML.

  - <xref:System.Xaml.XamlXmlReader.NodeType%2A> Pro<xref:System.Xaml.XamlNodeType.EndObject>nebo volejte volání<xref:System.Xaml.XamlXmlReader.Type%2A> k získání<xref:System.Xaml.XamlType>informacíoobjektu. <xref:System.Xaml.XamlNodeType.StartObject>

  - Pro, zavolejte<xref:System.Xaml.XamlXmlReader.Value%2A>. <xref:System.Xaml.XamlXmlReader.NodeType%2A> <xref:System.Xaml.XamlNodeType.Value> Uzel je hodnota pouze v případě, že se jedná o nejjednodušší výraz hodnoty pro člena nebo inicializační text pro objekt (Nicméně byste měli být vědomi chování převodu typů, jak je popsáno v nadcházející části tohoto tématu).

  - Pro je volána volání metody <xref:System.Xaml.XamlXmlReader.Namespace%2A> získání informací o oboru názvů pro uzel oboru názvů. <xref:System.Xaml.XamlXmlReader.NodeType%2A> <xref:System.Xaml.XamlNodeType.NamespaceDeclaration>

- Zavolejte <xref:System.Xaml.XamlXmlReader.Read%2A> k posunutí čtečky XAML na další uzel v datovém proudu uzlu XAML a opakujte kroky znovu.

Datový proud uzlu XAML, který poskytuje .NET Framework XAML Services XAML Readers vždy poskytuje úplný a hlubokou procházejí všechny možné uzly. Typické techniky řízení toku pro smyčku uzlu XAML zahrnují definování těla v rámci `while (reader.Read())`a přechod na <xref:System.Xaml.XamlXmlReader.NodeType%2A> každý bod uzlu ve smyčce uzlu.

Pokud je datový proud uzlu na konci souboru, aktuální uzel je null.

Nejjednodušší smyčka, která používá čtecí modul a zapisovač, se podobá následujícímu příkladu.

```csharp
XamlXmlReader xxr = new XamlXmlReader(new StringReader(xamlStringToLoad));
//where xamlStringToLoad is a string of well formed XAML
XamlObjectWriter xow = new XamlObjectWriter(xxr.SchemaContext);
while (xxr.Read()) {
  xow.WriteNode(xxr);
}
```

Tento základní příklad smyčky uzlů jazyka XAML pro načtení je transparentně připojen ke čtečce XAML a zapisovači XAML, takže nic neliší od toho, pokud <xref:System.Xaml.XamlServices.Parse%2A?displayProperty=nameWithType>jste použili. Tato základní struktura se pak rozbalí, aby se mohla vztahovat na váš scénář čtení nebo zápisu. Některé možné scénáře jsou následující:

- <xref:System.Xaml.XamlXmlReader.NodeType%2A>Zapnout. Provádění různých akcí v závislosti na tom, který typ uzlu je právě čten.

- Nevolejte <xref:System.Xaml.XamlWriter.WriteNode%2A> ve všech případech. Zavolá <xref:System.Xaml.XamlWriter.WriteNode%2A> se jenom <xref:System.Xaml.XamlXmlReader.NodeType%2A> v některých případech.

- V rámci logiky pro konkrétní typ uzlu Analyzujte specifiky daného uzlu a na nich budou pracovat. Můžete například zapsat pouze objekty, které pocházejí z konkrétního oboru názvů XAML, a pak vyřadit nebo odložit objekty, které nejsou z daného oboru názvů XAML. Případně můžete vyřadit nebo jinak znovu zpracovat všechny direktivy jazyka XAML, které váš systém XAML nepodporuje jako součást zpracování členů.

- Definujte vlastní <xref:System.Xaml.XamlObjectWriter> přepsání `Write*` metod, případně proveďte mapování typů, které obchází kontext schématu XAML.

- <xref:System.Xaml.XamlXmlReader> Vytvořte pro použití nevýchozího kontextu schématu XAML, aby byly přizpůsobené rozdíly v chování XAML použity čtenářem i zapisovačem.

### <a name="accessing-xaml-beyond-the-node-loop-concept"></a>Přístup k XAML za koncept smyčky uzlu

Existují potenciálně jiné způsoby, jak pracovat s reprezentacemi XAML jinou než jako smyčka uzlu XAML. Například může existovat čtečka XAML, která může číst indexovaný uzel nebo konkrétně přistupuje k uzlům, a to `x:Name` `x:Uid`přímo pomocí, nebo prostřednictvím jiných identifikátorů. .NET Framework služby XAML neposkytuje úplnou implementaci, ale poskytuje navrhovaný vzor prostřednictvím služeb a typů podpory. Další informace naleznete v tématu <xref:System.Xaml.IXamlIndexingReader> a <xref:System.Xaml.XamlNodeList>.

<a name="working_with_the_current_node"></a>

## <a name="working-with-the-current-node"></a>Práce s aktuálním uzlem

Většina scénářů, které používají smyčku uzlu XAML, nečtou pouze uzly. Většina scénářů zpracovává aktuální uzly a projde každý uzel po jednom do implementace <xref:System.Xaml.XamlWriter>.

V obvyklém scénáři <xref:System.Xaml.XamlXmlReader> zatížení vytvoří datový proud uzlu XAML; uzly XAML jsou zpracovány podle vaší logiky a kontextu schématu XAML a uzly jsou předány <xref:System.Xaml.XamlObjectWriter>do. Následně Integrujte výsledný graf objektů do vaší aplikace nebo architektury.

V typickém scénáři <xref:System.Xaml.XamlObjectReader> uložení cesty přečte graf objektů, jednotlivé uzly XAML <xref:System.Xaml.XamlXmlWriter> a výstup serializovaného výsledku jako textový soubor XAML. Klíč spočívá v tom, že jak cesty i scénáře zahrnují práci s právě jedním uzlem jazyka XAML v čase, a uzly XAML jsou k dispozici pro zpracování standardizovaným způsobem, který je definován pomocí systému typů XAML a rozhraní API služby the.NET Framework XAML.

### <a name="frames-and-scope"></a>Rámce a rozsah

Smyčka uzlu XAML projde datovým proudem uzlu XAML lineárním způsobem. Datový proud uzlu se přesměruje do objektů, do členů, které obsahují jiné objekty atd. Je často vhodné sledovat obor v rámci datového proudu uzlu XAML implementací konceptu rámce a zásobníku. To platí zejména v případě, že aktivně nastavujete datový proud uzlu, který je v něm. Podpora rámce a zásobníku, kterou implementujete v rámci logiky smyčky uzlu, by mohla `StartObject` počítat ( `GetObject`nebo) `EndObject` a rozsahy během navýšení struktury uzlu XAML, pokud je struktura považovat z perspektivy modelu DOM.

<a name="traversing_and_entering_object_nodes"></a>

## <a name="traversing-and-entering-object-nodes"></a>Procházení a zadávání uzlů objektů

První uzel v proudu uzlu, je-li otevřen čtečkou XAML, je uzel start-Object kořenového objektu. Podle definice je tento objekt vždy jediným uzlem objektu a nemá žádné partnerské uzly. V jakémkoli reálném příkladu XAML je kořenový objekt definován tak, aby obsahoval jednu nebo více vlastností, které obsahují více objektů, a tyto vlastnosti mají členské uzly. Členské uzly pak mají jeden nebo více uzlů objektů nebo mohou také končit místo toho v uzlu hodnoty. Kořenový objekt obvykle definuje XAML obory názvů WPF, které jsou syntakticky přiřazeny jako atributy v kódu jazyka XAML, ale mapovány na `Namescope` typ uzlu v reprezentaci datového proudu uzlu XAML.

Vezměte v úvahu následující příklad XAML (Jedná se o libovolný kód XAML, který není zálohovaný existujícími typy v .NET Framework). Předpokládejme, že v tomto objektovém `FavorCollection` modelu `List<T>` `Favor`je `Balloon` a `NoiseMaker` lze jej přiřadit k `Favor` `Balloon.Color` vlastnosti, která je zazálohována `Color` objektem podobným tomu, jak WPF definuje. barvy jako názvy známých barev a `Color` podporují konvertor typu pro syntaxi atributů.

|Kód XAML|Výsledný datový proud uzlu XAML|
|-----------------|--------------------------------|
|`<Party`|`Namespace`uzel pro`Party`|
|`xmlns="PartyXamlNamespace">`|`StartObject`uzel pro`Party`|
|`<Party.Favors>`|`StartMember`uzel pro`Party.Favors`|
||`StartObject`uzel pro implicitní`FavorCollection`|
||`StartMember`uzel pro vlastnost `FavorCollection` implicitních položek|
|`<Balloon`|`StartObject`uzel pro`Balloon`|
|`Color="Red"`|`StartMember`uzel pro`Color`<br /><br /> `Value`uzel pro řetězec hodnoty atributu`"Red"`<br /><br /> `EndMember` pro `Color`|
|`HasHelium="True"`|`StartMember`uzel pro`HasHelium`<br /><br /> `Value`uzel pro řetězec hodnoty atributu`"True"`<br /><br /> `EndMember` pro `HasHelium`|
|`>`|`EndObject` pro `Balloon`|
|`<NoiseMaker>Loudest</NoiseMaker>`|`StartObject`uzel pro`NoiseMaker`<br /><br /> `StartMember`uzel pro`_Initialization`<br /><br /> `Value`uzel pro řetězec inicializační hodnoty`"Loudest"`<br /><br /> `EndMember`uzel pro`_Initialization`<br /><br /> `EndObject` pro `NoiseMaker`|
||`EndMember`uzel pro vlastnost `FavorCollection` implicitních položek|
||`EndObject`uzel pro implicitní`FavorCollection`|
|`</Party.Favors>`|`EndMember` pro `Favors`|
|`</Party>`|`EndObject` pro `Party`|

V datovém proudu uzlu XAML můžete spoléhat na následující chování:

- Pokud uzel existuje, je přidán do datového proudu bezprostředně `StartObject` před `xmlns`deklarací, které jsou deklarovány v oboru názvů XAML. `Namespace` Prohlédněte si předchozí tabulku pomocí XAML a Ukázkový datový proud uzlu. Všimněte si, `StartObject` jak `Namespace` se uzly a zdají být přemístění a jejich deklarace do značek textu. To je zástupce chování, kde se uzly oboru názvů vždy zobrazují před uzlem, na které se vztahují v proudu uzlů. Účelem tohoto návrhu je, že informace oboru názvů jsou zásadní pro zapisovače objektů a musí být známé před tím, než se zapisovač objektů pokusí provést mapování typů nebo jinak zpracovat objekt. Umístění informací o oboru názvů XAML před jeho rozsahem aplikace v datovém proudu usnadňuje vždy zpracování datového proudu uzlu v uvedeném pořadí.

- Vzhledem k výše uvedenému aspektu je jeden nebo více `Namespace` uzlů, které si přečtete poprvé ve většině případů v reálném čase při procházení uzlů od začátku, `StartObject` nikoli z kořene.

- Za uzlem může `EndObject`následovat `Value`,nebobezprostřední `StartMember` `StartObject` . Nikdy není následován jiným `StartObject`.

- Může následovat a `StartObject`, `Value`nebo bezprostřední `EndMember`. `StartMember` Může následovat `GetObject`za členy, kde hodnota by měla pocházet z existující hodnoty nadřazeného objektu, nikoli pomocí `StartObject` , který by vytvořil instanci nové hodnoty. Může být také následován `Namespace` uzlem, který se vztahuje na nadcházející. `StartObject` Nikdy není následován jiným `StartMember`.

- `Value` Uzel představuje hodnotu samotnou; není k dispozici žádná "hodnota EndValue". Může následovat jenom `EndMember`.

  - Inicializační text XAML objektu, který může být použit konstrukcí, nemá za následek strukturu objektů a hodnot. Místo toho je vytvořen vyhrazený členský uzel pro člena s `_Initialization` názvem. a tento členský uzel obsahuje řetězec hodnoty inicializace. Pokud existuje, `_Initialization` je vždy první `StartMember`. `_Initialization`může být kvalifikován v některých reprezentacích služby XAML pomocí jazyka XAML namescope XAML pro objasnění, `_Initialization` že není definovaná vlastnost v typu zálohování.

  - Kombinace člen-hodnota představuje nastavení atributu hodnoty. Může se stát, že se do zpracování této hodnoty přinese konvertor hodnot a hodnota je prostý řetězec. Nicméně to není vyhodnoceno, dokud modul pro zápis objektů XAML nezpracovává tento datový proud uzlu. Modul pro zápis objektů XAML má nezbytný kontext schématu XAML, typ mapování systému a další podporu potřebnou pro převody hodnot.

- Za uzlem může následovat `StartMember` uzel pro následného `EndObject` člena nebo uzel pro vlastníka člena. `EndMember`

- Za uzlem může následovat `EndMember` uzel. `EndObject` Může být také následován `StartObject` uzlem pro případy, kdy objekty jsou partnerské uzly v položkách kolekce. Případně může následovat `Namespace` uzel, který se vztahuje na nadcházející `StartObject`.

  - V případě jedinečného případu zavření celého datového proudu `EndObject` uzlu nenásleduje žádná z nich. čtenář je nyní konec souboru a <xref:System.Xaml.XamlReader.Read%2A> vrátí `false`.

<a name="value_converters_and_the_xaml_node_stream"></a>

## <a name="value-converters-and-the-xaml-node-stream"></a>Převaděče hodnot a datový proud uzlu XAML

Konvertor hodnot je obecný termín pro rozšíření značek, konvertor typu (včetně serializátorů hodnot) nebo jiné vyhrazené třídy, která je hlášena jako konvertor hodnot pomocí systému typů XAML. V datovém proudu uzlu XAML mají použití konvertoru typu a použití rozšíření značek velmi odlišné reprezentace.

### <a name="type-converters-in-the-xaml-node-stream"></a>Převaděče typů v datovém proudu uzlu XAML

Sada atributů, která nakonec má za následek, že použití konvertoru typu je hlášeno v datovém proudu uzlu XAML jako hodnota člena. Datový proud uzlu XAML se nepokusí vytvořit objekt instance konvertoru typu a předat mu hodnotu. Použití implementace převodu konvertoru typu vyžaduje vyvolání kontextu schématu XAML a jeho použití pro mapování typů. Dokonce i určení, která třída konvertoru typů by měla být použita ke zpracování hodnoty, vyžaduje nepřímý kontext schématu XAML. Použijete-li výchozí kontext schématu XAML, jsou tyto informace k dispozici v systému typů XAML. Pokud potřebujete informace třídy konvertoru typu na úrovni datového proudu uzlu XAML před připojením k zapisovači XAML, můžete ho získat z <xref:System.Xaml.XamlMember> informací o nastavování člena. V opačném případě by vstup konvertoru typu měl být zachován v datovém proudu uzlu XAML jako jednoduchá hodnota, dokud nebudou provedeny zbývající operace, které vyžadují systém mapování typů a kontext schématu XAML, například vytvoření objektu modulem pro zápis objektů XAML.

Zvažte například následující osnova definice třídy a použití jazyka XAML:

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

Textová reprezentace datového proudu uzlu XAML pro toto použití může být vyjádřena jako následující:

`StartObject`<xref:System.Xaml.XamlType> představují`GameBoard`

`StartMember`<xref:System.Xaml.XamlMember> představují`BoardSize`

`Value`uzel s textovým řetězcem`8x8`""

`EndMember`vyhovují`BoardSize`

`EndObject`vyhovují`GameBoard`

Všimněte si, že v tomto datovém proudu uzlu není žádná instance převaděče typu. Můžete ale získat informace o převaděči typů voláním <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> metody <xref:System.Xaml.XamlMember> for `BoardSize`. Pokud máte platný kontext schématu XAML, můžete také vyvolat metody převaděče získáním instance z <xref:System.Xaml.Schema.XamlValueConverter%601.ConverterInstance%2A>.

### <a name="markup-extensions-in-the-xaml-node-stream"></a>Rozšíření značek v datovém proudu uzlu XAML

Použití rozšíření značek je hlášeno v proudu uzlu XAML jako uzel objektu v rámci člena, kde objekt představuje instanci rozšíření značek. Proto je použití rozšíření značek v rámci reprezentace streamu uzlu v případě, že je to více, uvedeno v reprezentaci, než je použití konvertoru typu, a další informace. <xref:System.Xaml.XamlMember>informace nemohly získat informaci o rozšíření značek, protože použití je situace a se liší v každém možném případu s kódem. není vyhrazen a implicitně na typ nebo člen, jako je to případ s konvertory typů.

Datový proud uzlu reprezentace rozšíření značek jako uzly objektů je případ i v případě, že využití rozšíření značek bylo provedeno ve formě atributu v kódu textu XAML (což je často případ). Použití rozšíření značek, které používaly explicitní formulář elementu Object, je ošetřeno stejným způsobem.

V rámci uzlu objektu rozšíření značek mohou být členy této přípony označení. Reprezentace datového proudu uzlu XAML zachovává použití této přípony označení, ať už se jedná o použití pozičního parametru, nebo použití s explicitními pojmenovanými parametry.

Pro použití pozičního parametru obsahuje datový proud uzlu XAML vlastnost `_PositionalParameters` definovanou v jazyce XAML, která zaznamenává využití. Tato vlastnost je obecná <xref:System.Collections.Generic.List%601> s <xref:System.Object> omezením. Omezení je Object a ne String, protože použití pozičního parametru může obsahovat vnořené použití rozšíření značek. Chcete-li získat přístup k pozičním parametrům z použití, můžete iterovat v seznamu a použít indexery pro jednotlivé hodnoty seznamu.

Pro použití pojmenovaných parametrů je každý pojmenovaný parametr reprezentován jako členský uzel daného názvu v datovém proudu uzlu. Hodnoty členů nejsou nutně řetězcem, protože by mohlo dojít k použití vloženého rozšíření značek.

`ProvideValue`z rozšíření značek se ještě nevolá. Je však vyvolána, pokud připojíte čtečku XAML a zapisovač XAML, `WriteEndObject` takže je vyvolána v uzlu rozšíření značek při jeho kontrole v proudu uzlů. Z tohoto důvodu je obecně potřeba, aby byl k dispozici stejný kontext schématu XAML, jako by byl použit k vytvoření grafu objektu v cestě načtení. V opačném případě může zevšechrozšířeníznačekvyvolatvýjimky,protoženejsoukdispoziciočekávanéslužby.`ProvideValue`

<a name="xaml_and_xml_languagedefined_members_in_the_xaml_node_stream"></a>

## <a name="xaml-and-xml-language-defined-members-in-the-xaml-node-stream"></a>Uživatelsky definované členy jazyka XAML a XML v datovém proudu uzlu XAML

Někteří členové jsou představeni do datového proudu uzlu XAML z důvodu interpretace a konvence čtečky XAML namísto explicitního <xref:System.Xaml.XamlMember> vyhledávání nebo konstrukce. Tyto členy jsou často direktivy XAML. V některých případech je to pro čtení jazyka XAML, který zavádí direktivu do datového proudu uzlu XAML. Jinými slovy, původní vstupní text XAML nespecifikuje explicitně členskou direktivu, ale čtečka XAML vloží direktivu, aby splňovala strukturální konvence XAML a informace sestavy v proudu uzlu XAML před tím, než dojde ke ztrátě těchto informací.

Následující seznam obsahuje poznámky ke všem případům, kde se očekává, že čtečka XAML zavádí členský uzel jazyka XAML a jak je tento členský uzel identifikovaný v .NET Framework implementaci služby XAML.

- **Inicializační text pro uzel objektu:** Název tohoto členského uzlu je `_Initialization`, představuje direktivu jazyka XAML a je definován v oboru názvů XAML jazyka XAML. Můžete získat statickou entitu z <xref:System.Xaml.XamlLanguage.Initialization%2A>.

- **Poziční parametry pro rozšíření značek:** Název tohoto členského uzlu je `_PositionalParameters`a je definován v oboru názvů XAML jazyka XAML. Vždy obsahuje obecný seznam objektů, z nichž každý je poziční parametr předem oddělený rozdělením na `,` znak oddělovače, který je zadán ve vstupním kódu XAML. Můžete získat statickou entitu pro direktivu pozičních parametrů z <xref:System.Xaml.XamlLanguage.PositionalParameters%2A>.

- **Neznámý obsah:** Název tohoto členského uzlu je `_UnknownContent`. Výhradně řečeno, <xref:System.Xaml.XamlDirective>je a je definována v oboru názvů XAML jazyka XAML. Tato direktiva se používá jako Sentinel pro případy, kdy prvek objektu XAML obsahuje obsah ve zdrojovém kódu XAML, ale nelze určit vlastnost Content v aktuálně dostupném kontextu schématu XAML. Tento případ můžete zjistit v datovém proudu uzlu XAML kontrolou členů s názvem `_UnknownContent`. Pokud není provedena žádná jiná akce v datovém proudu uzlu XAML zatížení, výchozí hodnota <xref:System.Xaml.XamlObjectWriter> je vyvolána, `WriteEndObject` `_UnknownContent` když dojde k pokusu o členství v jakémkoli objektu. Výchozí hodnota <xref:System.Xaml.XamlXmlWriter> nevyvolává a považuje člena za implicitní. Můžete získat statickou entitu pro `_UnknownContent` z. <xref:System.Xaml.XamlLanguage.UnknownContent%2A>

- **Vlastnost kolekce kolekce:** I když je typ CLR pro třídu kolekce, který se používá pro XAML, obvykle vyhrazená pojmenovaná vlastnost, která obsahuje položky kolekce, tato vlastnost není před rozlišením typu back-Type známa v systému typů XAML. Místo toho datový proud uzlu XAML zavádí `Items` zástupný symbol jako člen typu XAML kolekce. V .NET Framework implementaci XAML Services je `_Items`název této direktivy/členu v datovém proudu uzlu. Konstantu pro tuto direktivu lze získat z <xref:System.Xaml.XamlLanguage.Items%2A>.

    Všimněte si, že datový proud uzlu XAML může obsahovat vlastnost Items s položkami, které nemusejí být analyzovatelné na základě rozlišení typu zálohování a kontextu schématu XAML. Například

- **Členové definovaní XML:** `xml:base`Definované `lang` `space` `base`XML a členy`xml:space` jsou hlášeny jako direktivy XAML s názvem, a v implementacích .NET Framework XAML Services. `xml:lang` Obor názvů pro toto je obor názvů `http://www.w3.org/XML/1998/namespace`XML. Konstanty pro každý z nich lze získat z <xref:System.Xaml.XamlLanguage>.

## <a name="node-order"></a>Pořadí uzlů

V některých případech <xref:System.Xaml.XamlXmlReader> mění pořadí uzlů XAML v datovém proudu uzlu XAML, oproti pořadí, ve kterém se uzly zobrazí, pokud jsou zobrazeny ve značce nebo při zpracování jako XML. To se provádí, aby bylo <xref:System.Xaml.XamlObjectWriter> možné seřadit uzly tak, aby mohl zpracovat datový proud uzlu pouze s dopředné.  V .NET Framework služby XAML čtečka XAML změní pořadí uzlů místo toho, aby opouští tuto úlohu zapisovači XAML, jako optimalizaci výkonu pro uživatele modulu streamování objektů XAML.

Některé direktivy jsou určeny konkrétně k poskytnutí dalších informací pro vytvoření objektu z prvku objektu. Tyto direktivy jsou `Initialization`: `PositionalParameters`, `TypeArguments`, `FactoryMethod`, `Arguments`,. Čtečky XAML .NET Framework XAML Services se pokoušejí tyto direktivy umístit jako první členy proudu uzlů za objektem `StartObject`, z důvodů, které jsou vysvětleny v další části.

### <a name="xamlobjectwriter-behavior-and-node-order"></a>Chování XamlObjectWriter a pořadí uzlů

`StartObject`<xref:System.Xaml.XamlObjectWriter> do nemusí nutně signalizovat zapisovač objektů XAML pro okamžité vytvoření instance objektu. XAML obsahuje několik funkcí jazyka, které umožňují inicializaci objektu s dalšími vstupy a nespoléhat se výhradně na vyvolání konstruktoru bez parametrů k vytvoření počátečního objektu a nastavení vlastností. Mezi tyto funkce patří <xref:System.Windows.Markup.XamlDeferLoadAttribute>:; inicializační text; [x:TypeArguments –](x-typearguments-directive.md); poziční parametry rozšíření značek; metody pro vytváření a přidružené uzly [x:arguments –](x-arguments-directive.md) (XAML 2009). Každý z těchto případů zpozdí skutečnou konstrukci objektu a vzhledem k tomu, že je přeobjednán datový proud uzlu, může zapisovač objektů XAML spoléhat na chování ve skutečné konstrukci instance vždy, když se vyskytne počáteční člen, který není specificky konstrukcí. Direktiva pro tento typ objektu.

### <a name="getobject"></a>GetObject

`GetObject`představuje uzel XAML, kde místo vytváření nového objektu by měl zapisovač objektů XAML místo toho získat hodnotu obsahující vlastnosti objektu. Typický případ, kdy `GetObject` je uzel zjištěn v datovém proudu uzlu XAML, je pro objekt kolekce nebo objekt Dictionary, pokud je nadřazená vlastnost pouze pro čtení v objektovém modelu záložního typu. V tomto scénáři je kolekce nebo slovník často vytvořen a inicializován (obvykle prázdný) pomocí inicializační logiky vlastnícího typu.

## <a name="see-also"></a>Viz také:

- <xref:System.Xaml.XamlObjectReader>
- [XAML Services](index.md)
- [Obory názvů jazyka XAML](xaml-namespaces-for-net-framework-xaml-services.md)
