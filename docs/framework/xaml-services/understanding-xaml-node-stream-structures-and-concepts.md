---
title: Principy struktur a koncepcí datových proudů uzlů XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML node streams [XAML Services]
- nodes [XAML Services], XAML node stream
- XAML [XAML Services], XAML node streams
ms.assetid: 7c11abec-1075-474c-9d9b-778e5dab21c3
ms.openlocfilehash: 2c8093c3ef497bd836427f71098e62626f228e24
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733392"
---
# <a name="understanding-xaml-node-stream-structures-and-concepts"></a>Principy struktur a koncepcí datových proudů uzlů XAML

Čtečky XAML a zapisovače XAML, jak jsou implementovány v .NET Framework služby XAML, jsou založeny na konceptu návrhu datového proudu uzlu XAML. Datový proud uzlu XAML je koncepční sada uzlů XAML. V tomto principu provede procesor XAML strukturu vztahů uzlů v jazyce XAML v jednom okamžiku. V otevřeném datovém proudu uzlu XAML již existuje pouze jeden aktuální záznam nebo aktuální pozice, přičemž mnoho aspektů rozhraní API hlásí pouze informace, které jsou z této pozice k dispozici. Aktuální uzel v datovém proudu uzlu XAML lze popsat jako objekt, člen nebo hodnotu. Čtečky XAML mohou komunikovat s moduly pro zápis XAML a povolit programu zobrazení, interakci s nebo změnou obsahu datového proudu uzlu XAML během cesty načtení nebo operace uložení cesty, která zahrnuje XAML. Návrh rozhraní API pro čtení a zápis v XAML a koncept datového proudu uzlu XAML se podobá předchozím souvisejícím designům a návrhům pro zápis a k konceptům, jako je XML model DOM (Document Object Model) (DOM) a <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter> tříd. Toto téma popisuje koncepty pro streamy uzlu XAML a popisuje, jak můžete napsat rutiny, které pracují s reprezentacemi XAML na úrovni uzlu XAML.

<a name="loading_into_a_xaml_reader"></a>

## <a name="loading-xaml-into-a-xaml-reader"></a>Načtení XAML do čtečky XAML

Základní <xref:System.Xaml.XamlReader> třída nedeklaruje konkrétní techniku pro načtení počátečního XAML do čtečky XAML. Namísto toho odvozená třída deklaruje a implementuje techniku načítání, včetně obecných vlastností a omezení jejich vstupního zdroje pro jazyk XAML. Například <xref:System.Xaml.XamlObjectReader> čte graf objektu, počínaje zdrojem vstupu jednoho objektu, který představuje kořen nebo základ. <xref:System.Xaml.XamlObjectReader> potom vytvoří datový proud uzlu XAML z grafu objektu.

Nejvýraznější .NET Framework služby XAML – definovaná <xref:System.Xaml.XamlReader> podtřídou je <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader> načte počáteční kód XAML buď načtením textového souboru přímo pomocí datového proudu nebo cesty k souboru, nebo nepřímo prostřednictvím související třídy čtenářů, jako je například <xref:System.IO.TextReader>. <xref:System.Xaml.XamlReader> lze představit jako obsahující celou vstupní zdroj XAML poté, co byl načten. Rozhraní <xref:System.Xaml.XamlReader> Base API je však navrženo tak, aby čtenář komunikoval s jedním uzlem XAML. Při prvním načtení je prvním jedním uzlem, ke kterému se setkáte, kořenem XAML a jeho počátečním objektem.

### <a name="the-xaml-node-stream-concept"></a>Koncept datového proudu uzlu XAML

Pokud jste všeobecně obeznámeni s modelem DOM, metafora stromu nebo přístupem založenými na dotazech k přístupu k technologiím založeným na jazyce XML, je užitečný způsob, jak conceptualize datový proud uzlu XAML, je následující. Představte si, že načtený kód XAML je model DOM nebo strom, ve kterém je každý možný uzel rozbalený celým způsobem a následně zobrazený lineárně. Při přechodu mezi uzly můžete přecházet "in" nebo "out" úrovní, které by byly relevantní pro model DOM, ale datový proud uzlu XAML explicitně nesleduje, protože tyto koncepty úrovně nejsou relevantní pro datový proud uzlu. Datový proud uzlu má "aktuální" pozici, ale pokud jste sami neuložili jiné části streamu jako odkazy, každý aspekt streamu uzlu, který je jiný než aktuální pozice uzlu, je mimo zobrazení.

Koncept datového proudu uzlu XAML má významnou výhodu, že pokud procházíte celým datovým proudem uzlu, máte jistotu, že jste zpracovali celé vyjádření reprezentace v jazyce XAML; Nemusíte se obávat, že dotaz, operace modelu DOM nebo nějaký jiný nelineární přístup ke zpracování informací neobsahují část úplné reprezentace XAML. Z tohoto důvodu je reprezentace datového proudu uzlu XAML ideální pro připojení čtenářů XAML a zapisovačů XAML a pro poskytnutí systému, kde můžete vložit vlastní proces, který funguje mezi fázemi čtení a zápisu operace zpracování XAML. V mnoha případech je pořadí uzlů v datovém proudu uzlu XAML záměrně optimalizováno nebo přeobjednáno čtečkami XAML a jak se může pořadí zobrazit ve zdrojovém textu, binárním souboru nebo grafu objektů. Toto chování je určeno k vykonání architektury zpracování XAML, kdy zapisovače XAML nejsou nikdy v pozici, kde se musí v proudu uzlů vrátit zpět. V ideálním případě by měly být všechny operace zápisu XAML schopny pracovat na kontextu schématu a na aktuální pozici datového proudu uzlu.

<a name="a_basic_reading_node_loop"></a>

## <a name="a-basic-reading-node-loop"></a>Základní smyčka uzlu čtení

Základní smyčka uzlu čtení pro zkoumání datového proudu uzlu XAML se skládá z následujících konceptů. Pro účely smyček uzlů, jak je popsáno v tomto tématu, Předpokládejme, že čtete textový soubor XAML čitelný pomocí <xref:System.Xaml.XamlXmlReader>. Odkazy v této části odkazují na konkrétní rozhraní API smyčky uzlu XAML implementované <xref:System.Xaml.XamlXmlReader>.

- Ujistěte se, že nejste na konci datového proudu uzlu XAML (Zkontrolujte <xref:System.Xaml.XamlXmlReader.IsEof%2A>, nebo použijte návratovou hodnotu <xref:System.Xaml.XamlXmlReader.Read%2A>). Pokud jste na konci streamu, neexistuje žádný aktuální uzel a měli byste skončit.

- Ověřte, jaký typ uzlu datový proud uzlu XAML aktuálně zpřístupňuje voláním <xref:System.Xaml.XamlXmlReader.NodeType%2A>.

- Pokud máte přidružený modul pro zápis objektů XAML, který je připojený přímo, obecně v tomto okamžiku zavoláte <xref:System.Xaml.XamlWriter.WriteNode%2A>.

- Na základě toho, které <xref:System.Xaml.XamlNodeType> jsou hlášeny jako aktuální uzel nebo aktuální záznam, zavolejte jednu z následujících hodnot pro získání informací o obsahu uzlu:

  - Pro <xref:System.Xaml.XamlXmlReader.NodeType%2A> <xref:System.Xaml.XamlNodeType.StartMember> nebo <xref:System.Xaml.XamlNodeType.EndMember>volejte <xref:System.Xaml.XamlXmlReader.Member%2A> pro získání <xref:System.Xaml.XamlMember> informací o členu. Všimněte si, že člen může být <xref:System.Xaml.XamlDirective>, a proto nemusí být nutně běžným uživatelem definovaným členem předchozího objektu. Například `x:Name` použít na objekt se zobrazí jako člen jazyka XAML, kde <xref:System.Xaml.XamlMember.IsDirective%2A> je true a <xref:System.Xaml.XamlMember.Name%2A> člena `Name`, s jinými vlastnostmi, které označují, že tato direktiva je v oboru názvů XAML jazyka XAML.

  - Pro <xref:System.Xaml.XamlXmlReader.NodeType%2A> <xref:System.Xaml.XamlNodeType.StartObject> nebo <xref:System.Xaml.XamlNodeType.EndObject>volejte <xref:System.Xaml.XamlXmlReader.Type%2A> pro získání <xref:System.Xaml.XamlType> informací o objektu.

  - Pro <xref:System.Xaml.XamlXmlReader.NodeType%2A> <xref:System.Xaml.XamlNodeType.Value>volejte <xref:System.Xaml.XamlXmlReader.Value%2A>. Uzel je hodnota pouze v případě, že se jedná o nejjednodušší výraz hodnoty pro člena nebo inicializační text pro objekt (Nicméně byste měli být vědomi chování převodu typů, jak je popsáno v nadcházející části tohoto tématu).

  - Pro <xref:System.Xaml.XamlXmlReader.NodeType%2A> <xref:System.Xaml.XamlNodeType.NamespaceDeclaration>volejte <xref:System.Xaml.XamlXmlReader.Namespace%2A> pro získání informací o oboru názvů uzlu oboru názvů.

- Zavolejte <xref:System.Xaml.XamlXmlReader.Read%2A> pro posunutí čtečky XAML na další uzel v datovém proudu uzlu XAML a opakujte kroky znovu.

Datový proud uzlu XAML, který poskytuje .NET Framework XAML Services XAML Readers vždy poskytuje úplný a hlubokou procházejí všechny možné uzly. Typické techniky řízení toku pro smyčku uzlu XAML zahrnují definování těla v rámci `while (reader.Read())`a přepínání <xref:System.Xaml.XamlXmlReader.NodeType%2A> v jednotlivých uzlech smyčkou uzlu.

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

Tento základní příklad smyčky uzlu XAML zatížení je transparentně připojen ke čtečce XAML a zapisovači XAML, takže nic neliší od toho, pokud jste použili <xref:System.Xaml.XamlServices.Parse%2A?displayProperty=nameWithType>. Tato základní struktura se pak rozbalí, aby se mohla vztahovat na váš scénář čtení nebo zápisu. Některé možné scénáře jsou následující:

- Přepněte na <xref:System.Xaml.XamlXmlReader.NodeType%2A>. Provádění různých akcí v závislosti na tom, který typ uzlu je právě čten.

- Nevolejte <xref:System.Xaml.XamlWriter.WriteNode%2A> ve všech případech. V některých případech <xref:System.Xaml.XamlXmlReader.NodeType%2A> volat pouze <xref:System.Xaml.XamlWriter.WriteNode%2A>.

- V rámci logiky pro konkrétní typ uzlu Analyzujte specifiky daného uzlu a na nich budou pracovat. Můžete například zapsat pouze objekty, které pocházejí z konkrétního oboru názvů XAML, a pak vyřadit nebo odložit objekty, které nejsou z daného oboru názvů XAML. Případně můžete vyřadit nebo jinak znovu zpracovat všechny direktivy jazyka XAML, které váš systém XAML nepodporuje jako součást zpracování členů.

- Definujte vlastní <xref:System.Xaml.XamlObjectWriter>, který přepíše `Write*` metody, případně provede mapování typů, které obchází kontext schématu XAML.

- Sestavte <xref:System.Xaml.XamlXmlReader> pro použití nevýchozího kontextu schématu XAML, aby byly vlastní rozdíly v chování XAML použity čtenářem i zapisovačem.

### <a name="accessing-xaml-beyond-the-node-loop-concept"></a>Přístup k XAML za koncept smyčky uzlu

Existují potenciálně jiné způsoby, jak pracovat s reprezentacemi XAML jinou než jako smyčka uzlu XAML. Například je možné, že existuje čtečka XAML, která může číst indexovaný uzel nebo konkrétně přistupuje k uzlům přímo pomocí `x:Name`, pomocí `x:Uid`nebo prostřednictvím jiných identifikátorů. .NET Framework služby XAML neposkytuje úplnou implementaci, ale poskytuje navrhovaný vzor prostřednictvím služeb a typů podpory. Další informace naleznete v tématu <xref:System.Xaml.IXamlIndexingReader> a <xref:System.Xaml.XamlNodeList>.

<a name="working_with_the_current_node"></a>

## <a name="working-with-the-current-node"></a>Práce s aktuálním uzlem

Většina scénářů, které používají smyčku uzlu XAML, nečtou pouze uzly. Většina scénářů zpracovává aktuální uzly a každý uzel projde po jednom do implementace <xref:System.Xaml.XamlWriter>.

V typickém scénáři cesty načtení <xref:System.Xaml.XamlXmlReader> vytvoří datový proud uzlu XAML; uzly XAML jsou zpracovávány podle vaší logiky a kontextu schématu XAML; a uzly jsou předány do <xref:System.Xaml.XamlObjectWriter>. Následně Integrujte výsledný graf objektů do vaší aplikace nebo architektury.

V typickém scénáři uložení <xref:System.Xaml.XamlObjectReader> čte graf objektů, zpracovává jednotlivé uzly XAML a <xref:System.Xaml.XamlXmlWriter> výstup serializovaného výsledku jako textový soubor XAML. Klíč spočívá v tom, že jak cesty i scénáře zahrnují práci s právě jedním uzlem jazyka XAML v čase, a uzly XAML jsou k dispozici pro zpracování standardizovaným způsobem, který je definován pomocí systému typů XAML a rozhraní API služby the.NET Framework XAML.

### <a name="frames-and-scope"></a>Rámce a rozsah

Smyčka uzlu XAML projde datovým proudem uzlu XAML lineárním způsobem. Datový proud uzlu se přesměruje do objektů, do členů, které obsahují jiné objekty atd. Je často vhodné sledovat obor v rámci datového proudu uzlu XAML implementací konceptu rámce a zásobníku. To platí zejména v případě, že aktivně nastavujete datový proud uzlu, který je v něm. Podpora rámce a zásobníku, kterou implementujete v rámci logiky smyčky uzlu, by mohla počítat `StartObject` (nebo `GetObject`) a obory `EndObject`, protože jste propadli do struktury uzlu XAML, pokud se na strukturu domníváme z perspektivy modelu DOM.

<a name="traversing_and_entering_object_nodes"></a>

## <a name="traversing-and-entering-object-nodes"></a>Procházení a zadávání uzlů objektů

První uzel v proudu uzlu, je-li otevřen čtečkou XAML, je uzel start-Object kořenového objektu. Podle definice je tento objekt vždy jediným uzlem objektu a nemá žádné partnerské uzly. V jakémkoli reálném příkladu XAML je kořenový objekt definován tak, aby obsahoval jednu nebo více vlastností, které obsahují více objektů, a tyto vlastnosti mají členské uzly. Členské uzly pak mají jeden nebo více uzlů objektů nebo mohou také končit místo toho v uzlu hodnoty. Kořenový objekt obvykle definuje XAML obory názvů WPF, které jsou syntakticky přiřazeny jako atributy v kódu jazyka XAML, ale mapovány na `Namescope` typ uzlu v reprezentaci datového proudu uzlu XAML.

Vezměte v úvahu následující příklad XAML (Jedná se o libovolný kód XAML, který není zálohovaný existujícími typy v .NET Framework). Předpokládejme, že v tomto objektovém modelu `FavorCollection` je `List<T>` `Favor`, `Balloon` a `NoiseMaker` lze přiřadit k `Favor`, `Balloon.Color` vlastnost je zajištěna `Color` objekt podobným tomu, jak WPF definuje jako názvy známých barev. a `Color` podporuje konvertor typu pro syntaxi atributů.

|Kód XAML|Výsledný datový proud uzlu XAML|
|-----------------|--------------------------------|
|`<Party`|uzel `Namespace` pro `Party`|
|`xmlns="PartyXamlNamespace">`|uzel `StartObject` pro `Party`|
|`<Party.Favors>`|uzel `StartMember` pro `Party.Favors`|
||uzel `StartObject` pro implicitní `FavorCollection`|
||uzel `StartMember` pro vlastnost implicitních `FavorCollection` položek.|
|`<Balloon`|uzel `StartObject` pro `Balloon`|
|`Color="Red"`|uzel `StartMember` pro `Color`<br /><br /> uzel `Value` pro řetězec hodnoty atributu `"Red"`<br /><br /> `EndMember` pro `Color`|
|`HasHelium="True"`|uzel `StartMember` pro `HasHelium`<br /><br /> uzel `Value` pro řetězec hodnoty atributu `"True"`<br /><br /> `EndMember` pro `HasHelium`|
|`>`|`EndObject` pro `Balloon`|
|`<NoiseMaker>Loudest</NoiseMaker>`|uzel `StartObject` pro `NoiseMaker`<br /><br /> uzel `StartMember` pro `_Initialization`<br /><br /> uzel `Value` pro řetězec hodnoty inicializace `"Loudest"`<br /><br /> uzel `EndMember` pro `_Initialization`<br /><br /> `EndObject` pro `NoiseMaker`|
||uzel `EndMember` pro vlastnost implicitních `FavorCollection` položek.|
||uzel `EndObject` pro implicitní `FavorCollection`|
|`</Party.Favors>`|`EndMember` pro `Favors`|
|`</Party>`|`EndObject` pro `Party`|

V datovém proudu uzlu XAML můžete spoléhat na následující chování:

- Pokud uzel `Namespace` existuje, je přidán do datového proudu bezprostředně před `StartObject` deklarovaným oborem názvů XAML s `xmlns`. Prohlédněte si předchozí tabulku pomocí XAML a Ukázkový datový proud uzlu. Všimněte si, jak se `StartObject` a `Namespace` uzly zdají být přemístěné a jejich deklarace do značek textu. To je zástupce chování, kde se uzly oboru názvů vždy zobrazují před uzlem, na které se vztahují v proudu uzlů. Účelem tohoto návrhu je, že informace oboru názvů jsou zásadní pro zapisovače objektů a musí být známé před tím, než se zapisovač objektů pokusí provést mapování typů nebo jinak zpracovat objekt. Umístění informací o oboru názvů XAML před jeho rozsahem aplikace v datovém proudu usnadňuje vždy zpracování datového proudu uzlu v uvedeném pořadí.

- Vzhledem k výše uvedené úvahě je jedním nebo více `Namespace` uzly, které si přečtete poprvé ve většině případů reálného světa při procházení uzlů od spuštění, nikoli `StartObject` kořenového adresáře.

- `StartObject` uzel může následovat `StartMember`, `Value`nebo okamžitý `EndObject`. Nikdy nenásleduje další `StartObject`.

- `StartMember` může následovat `StartObject`, `Value`nebo okamžité `EndMember`. U členů, u kterých má být hodnota z existující hodnoty nadřazeného objektu místo `StartObject`, která by vytvořila novou hodnotu, může následovat `GetObject`. Může být také následován `Namespace`m uzlem, který se vztahuje na nadcházející `StartObject`. Nikdy nenásleduje další `StartMember`.

- Uzel `Value` představuje samotnou hodnotu; není k dispozici žádný "hodnota EndValue". Může následovat jenom `EndMember`.

  - Inicializační text XAML objektu, který může být použit konstrukcí, nemá za následek strukturu objektů a hodnot. Místo toho je vytvořen vyhrazený členský uzel pro člena s názvem `_Initialization`. a tento členský uzel obsahuje řetězec hodnoty inicializace. Pokud existuje, `_Initialization` je vždy první `StartMember`. `_Initialization` může být kvalifikována v některých reprezentacích služby XAML pomocí jazyka XAML XAML namescope, aby se vyjasnilo, že `_Initialization` není definovaná vlastnost v části typy zálohování.

  - Kombinace člen-hodnota představuje nastavení atributu hodnoty. Může se stát, že se do zpracování této hodnoty přinese konvertor hodnot a hodnota je prostý řetězec. Nicméně to není vyhodnoceno, dokud modul pro zápis objektů XAML nezpracovává tento datový proud uzlu. Modul pro zápis objektů XAML má nezbytný kontext schématu XAML, typ mapování systému a další podporu potřebnou pro převody hodnot.

- Za `EndMember` uzel může následovat `StartMember` uzel pro následného člena nebo uzel `EndObject` pro vlastníka člena.

- Za uzlem `EndObject` může následovat `EndMember` uzel. Může být také následován `StartObject`m uzlem pro případy, kdy objekty jsou partnerské uzly v položkách kolekce. Případně může následovat `Namespace` uzel, který se vztahuje na nadcházející `StartObject`.

  - V případě jedinečného případu zavření celého datového proudu uzlu nenásleduje u `EndObject` kořenu cokoli; čtenář je nyní konec souboru a <xref:System.Xaml.XamlReader.Read%2A> vrátí `false`.

<a name="value_converters_and_the_xaml_node_stream"></a>

## <a name="value-converters-and-the-xaml-node-stream"></a>Převaděče hodnot a datový proud uzlu XAML

Konvertor hodnot je obecný termín pro rozšíření značek, konvertor typu (včetně serializátorů hodnot) nebo jiné vyhrazené třídy, která je hlášena jako konvertor hodnot pomocí systému typů XAML. V datovém proudu uzlu XAML mají použití konvertoru typu a použití rozšíření značek velmi odlišné reprezentace.

### <a name="type-converters-in-the-xaml-node-stream"></a>Převaděče typů v datovém proudu uzlu XAML

Sada atributů, která nakonec má za následek, že použití konvertoru typu je hlášeno v datovém proudu uzlu XAML jako hodnota člena. Datový proud uzlu XAML se nepokusí vytvořit objekt instance konvertoru typu a předat mu hodnotu. Použití implementace převodu konvertoru typu vyžaduje vyvolání kontextu schématu XAML a jeho použití pro mapování typů. Dokonce i určení, která třída konvertoru typů by měla být použita ke zpracování hodnoty, vyžaduje nepřímý kontext schématu XAML. Použijete-li výchozí kontext schématu XAML, jsou tyto informace k dispozici v systému typů XAML. Pokud potřebujete informace třídy konvertoru typu na úrovni datového proudu uzlu XAML před připojením k zapisovači XAML, můžete jej získat z <xref:System.Xaml.XamlMember> informací o nastavování člena. V opačném případě by vstup konvertoru typu měl být zachován v datovém proudu uzlu XAML jako jednoduchá hodnota, dokud nebudou provedeny zbývající operace, které vyžadují systém mapování typů a kontext schématu XAML, například vytvoření objektu modulem pro zápis objektů XAML.

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

`StartObject` s <xref:System.Xaml.XamlType> reprezentujícím `GameBoard`

`StartMember` s <xref:System.Xaml.XamlMember> reprezentujícím `BoardSize`

`Value` uzel s textovým řetězcem "`8x8`"

`EndMember` odpovídá `BoardSize`

`EndObject` odpovídá `GameBoard`

Všimněte si, že v tomto datovém proudu uzlu není žádná instance převaděče typu. Můžete ale získat informace o převaděči typů voláním <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> na <xref:System.Xaml.XamlMember> pro `BoardSize`. Pokud máte platný kontext schématu XAML, můžete také vyvolat metody převaděče získáním instance z <xref:System.Xaml.Schema.XamlValueConverter%601.ConverterInstance%2A>.

### <a name="markup-extensions-in-the-xaml-node-stream"></a>Rozšíření značek v datovém proudu uzlu XAML

Použití rozšíření značek je hlášeno v proudu uzlu XAML jako uzel objektu v rámci člena, kde objekt představuje instanci rozšíření značek. Proto je použití rozšíření značek v rámci reprezentace streamu uzlu v případě, že je to více, uvedeno v reprezentaci, než je použití konvertoru typu, a další informace. informace <xref:System.Xaml.XamlMember> nemohly získat informaci o rozšíření značek, protože použití je situace a se liší v každém možném případu s kódem. není vyhrazen a implicitně na typ nebo člen, jako je to případ s konvertory typů.

Datový proud uzlu reprezentace rozšíření značek jako uzly objektů je případ i v případě, že využití rozšíření značek bylo provedeno ve formě atributu v kódu textu XAML (což je často případ). Použití rozšíření značek, které používaly explicitní formulář elementu Object, je ošetřeno stejným způsobem.

V rámci uzlu objektu rozšíření značek mohou být členy této přípony označení. Reprezentace datového proudu uzlu XAML zachovává použití této přípony označení, ať už se jedná o použití pozičního parametru, nebo použití s explicitními pojmenovanými parametry.

Pro použití pozičního parametru obsahuje datový proud uzlu XAML `_PositionalParameters`ovou vlastnost definovanou v jazyce XAML, která zaznamenává využití. Tato vlastnost je obecná <xref:System.Collections.Generic.List%601> s omezením <xref:System.Object>. Omezení je Object a ne String, protože použití pozičního parametru může obsahovat vnořené použití rozšíření značek. Chcete-li získat přístup k pozičním parametrům z použití, můžete iterovat v seznamu a použít indexery pro jednotlivé hodnoty seznamu.

Pro použití pojmenovaných parametrů je každý pojmenovaný parametr reprezentován jako členský uzel daného názvu v datovém proudu uzlu. Hodnoty členů nejsou nutně řetězcem, protože by mohlo dojít k použití vloženého rozšíření značek.

`ProvideValue` z rozšíření značek ještě není vyvoláno. Je však vyvolána, pokud připojíte čtečku XAML a zapisovač XAML, aby se `WriteEndObject` vyvolala v uzlu rozšíření značek při jejich kontrole v proudu uzlů. Z tohoto důvodu je obecně potřeba, aby byl k dispozici stejný kontext schématu XAML, jako by byl použit k vytvoření grafu objektu v cestě načtení. Jinak `ProvideValue` ze všech rozšíření značek může vyvolat výjimky, protože nemá očekávané služby, které jsou k dispozici.

<a name="xaml_and_xml_languagedefined_members_in_the_xaml_node_stream"></a>

## <a name="xaml-and-xml-language-defined-members-in-the-xaml-node-stream"></a>Uživatelsky definované členy jazyka XAML a XML v datovém proudu uzlu XAML

Někteří členové jsou představeni do datového proudu uzlu XAML z důvodu interpretace a konvence čtečky XAML namísto explicitního vyhledávání <xref:System.Xaml.XamlMember> nebo konstrukce. Tyto členy jsou často direktivy XAML. V některých případech je to pro čtení jazyka XAML, který zavádí direktivu do datového proudu uzlu XAML. Jinými slovy, původní vstupní text XAML nespecifikuje explicitně členskou direktivu, ale čtečka XAML vloží direktivu, aby splňovala strukturální konvence XAML a informace sestavy v proudu uzlu XAML před tím, než dojde ke ztrátě těchto informací.

Následující seznam obsahuje poznámky ke všem případům, kde se očekává, že čtečka XAML zavádí členský uzel jazyka XAML a jak je tento členský uzel identifikovaný v .NET Framework implementaci služby XAML.

- **Inicializační text pro uzel objektu:** Název tohoto členského uzlu je `_Initialization`, představuje direktivu XAML a je definován v oboru názvů XAML jazyka XAML. Z <xref:System.Xaml.XamlLanguage.Initialization%2A>můžete získat statickou entitu.

- **Poziční parametry pro rozšíření značek:** Název tohoto členského uzlu je `_PositionalParameters`a je definován v oboru názvů XAML jazyka XAML. Vždy obsahuje obecný seznam objektů, z nichž každý je poziční parametr předem oddělený rozdělením znaku oddělovače `,`, jak je uvedeno ve vstupním kódu XAML. Můžete získat statickou entitu pro direktivu pozičních parametrů z <xref:System.Xaml.XamlLanguage.PositionalParameters%2A>.

- **Neznámý obsah:** Název tohoto členského uzlu je `_UnknownContent`. Výhradně řečeno, je <xref:System.Xaml.XamlDirective>a je definována v oboru názvů XAML jazyka XAML. Tato direktiva se používá jako Sentinel pro případy, kdy prvek objektu XAML obsahuje obsah ve zdrojovém kódu XAML, ale nelze určit vlastnost Content v aktuálně dostupném kontextu schématu XAML. Tento případ můžete zjistit v datovém proudu uzlu XAML kontrolou členů s názvem `_UnknownContent`. Pokud není provedena žádná jiná akce v datovém proudu uzlu XAML, výchozí <xref:System.Xaml.XamlObjectWriter> vyvolá pokus o `WriteEndObject` při výskytu `_UnknownContent` člena na jakémkoli objektu. Výchozí <xref:System.Xaml.XamlXmlWriter> nevyvolává a považuje člena za implicitní. Můžete získat statickou entitu pro `_UnknownContent` z <xref:System.Xaml.XamlLanguage.UnknownContent%2A>.

- **Vlastnost kolekce kolekce:** I když je typ CLR pro třídu kolekce, který se používá pro XAML, obvykle vyhrazená pojmenovaná vlastnost, která obsahuje položky kolekce, tato vlastnost není před rozlišením typu back-Type známa v systému typů XAML. Místo toho datový proud uzlu XAML zavádí zástupný symbol `Items` jako člen typu XAML kolekce. V .NET Framework implementaci XAML Services je název této direktivy/členu v datovém proudu uzlů `_Items`. Konstanta této direktivy se dá získat z <xref:System.Xaml.XamlLanguage.Items%2A>.

    Všimněte si, že datový proud uzlu XAML může obsahovat vlastnost Items s položkami, které nemusejí být analyzovatelné na základě rozlišení typu zálohování a kontextu schématu XAML. Například

- **Členové definovaní XML:** `xml:base`definované XML `xml:lang` a `xml:space` jsou hlášeny jako direktivy jazyka XAML s názvem `base`, `lang`a `space` v implementacích .NET Framework XAML Services. Obor názvů pro tyto obory názvů XML `http://www.w3.org/XML/1998/namespace`. Konstanty pro každý z nich lze získat z <xref:System.Xaml.XamlLanguage>.

## <a name="node-order"></a>Pořadí uzlů

V některých případech <xref:System.Xaml.XamlXmlReader> mění pořadí uzlů XAML v datovém proudu uzlu XAML, oproti pořadí, ve kterém se uzly zobrazí, pokud jsou zobrazeny ve značce nebo při zpracování jako XML. K tomu je potřeba seřadit uzly tak, aby <xref:System.Xaml.XamlObjectWriter> mohl zpracovat datový proud uzlu pouze s dopředné.  V .NET Framework služby XAML čtečka XAML změní pořadí uzlů místo toho, aby opouští tuto úlohu zapisovači XAML, jako optimalizaci výkonu pro uživatele modulu streamování objektů XAML.

Některé direktivy jsou určeny konkrétně k poskytnutí dalších informací pro vytvoření objektu z prvku objektu. Tyto direktivy jsou: `Initialization`, `PositionalParameters`, `TypeArguments`, `FactoryMethod`, `Arguments`. Čtečky XAML .NET Framework XAML Services se pokoušejí tyto direktivy umístit jako první členové datového proudu uzlu za `StartObject`objektu z důvodů, které jsou vysvětleny v další části.

### <a name="xamlobjectwriter-behavior-and-node-order"></a>Chování XamlObjectWriter a pořadí uzlů

`StartObject` do <xref:System.Xaml.XamlObjectWriter> není nutně signálem zapisovače objektu XAML, aby bylo možné hned vytvořit instanci objektu. XAML obsahuje několik funkcí jazyka, které umožňují inicializaci objektu s dalšími vstupy a nespoléhat se výhradně na vyvolání konstruktoru bez parametrů k vytvoření počátečního objektu a nastavení vlastností. Mezi tyto funkce patří: <xref:System.Windows.Markup.XamlDeferLoadAttribute>; inicializační text; [x:TypeArguments –](x-typearguments-directive.md); poziční parametry rozšíření značek; metody pro vytváření a přidružené uzly [x:arguments –](x-arguments-directive.md) (XAML 2009). Každý z těchto případů zpozdí skutečnou konstrukci objektu a vzhledem k tomu, že je přeobjednán datový proud uzlu, může zapisovač objektů XAML spoléhat na chování ve skutečné konstrukci instance vždy, když se vyskytne počáteční člen, který není specificky konstrukcí. Direktiva pro tento typ objektu.

### <a name="getobject"></a>GetObject

`GetObject` představuje uzel XAML, kde spíše než vytváření nového objektu, by měl zapisovač objektů XAML místo toho získat hodnotu obsahující vlastnosti objektu. Typický případ, kde je nalezen uzel `GetObject` v datovém proudu uzlu XAML, je pro objekt kolekce nebo objekt Dictionary, pokud je nadřazená vlastnost v objektovém modelu typu zálohování záměrně jen pro čtení. V tomto scénáři je kolekce nebo slovník často vytvořen a inicializován (obvykle prázdný) pomocí inicializační logiky vlastnícího typu.

## <a name="see-also"></a>Viz také:

- <xref:System.Xaml.XamlObjectReader>
- [XAML Services](index.md)
- [Obory názvů jazyka XAML](xaml-namespaces-for-net-framework-xaml-services.md)
