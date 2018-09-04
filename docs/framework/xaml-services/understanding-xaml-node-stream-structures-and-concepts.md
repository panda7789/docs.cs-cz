---
title: Principy struktur a koncepcí datových proudů uzlů XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML node streams [XAML Services]
- nodes [XAML Services], XAML node stream
- XAML [XAML Services], XAML node streams
ms.assetid: 7c11abec-1075-474c-9d9b-778e5dab21c3
ms.openlocfilehash: 100de0a897538527b76b1a53cf40d59a8804d3ae
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519444"
---
# <a name="understanding-xaml-node-stream-structures-and-concepts"></a>Principy struktur a koncepcí datových proudů uzlů XAML
XAML čtečky a zapisovače XAML, jak je implementován v rozhraní .NET Framework XAML Services jsou založeny na konceptu návrhu datový proud uzlu XAML. Datový proud uzlu XAML je koncepci sadu uzlů XAML. V tomto koncepci procesoru XAML vás provede struktura uzel vztahů v XAML, jeden najednou. V každém okamžiku v otevřít datový proud uzlu XAML jenom jednomu záznamu v aktuální nebo current pozici existuje a mnoho aspektů rozhraní API sestavy pouze informace k dispozici z této pozici. Aktuální uzel v datovém proudu uzlu XAML lze popsat jako objekt, člen nebo hodnota. Zpracováním XAML jako datový proud uzlu XAML XAML čtenáři komunikovat se zapisovači XAML a povolit program k zobrazení, pracovat s nebo změnit obsah datový proud uzlu XAML během cesta načtení nebo uložení cesta operace, která zahrnuje XAML. Návrh XAML čtečky a zapisovače rozhraní API a koncept datový proud uzlu XAML podobají předchozí související čtečky a zapisovače návrhy a koncepty, jako [!INCLUDE[TLA#tla_xmldom](../../../includes/tlasharptla-xmldom-md.md)] a <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter> třídy. Toto téma popisuje koncepty datový proud uzlu XAML a popisuje, jak může zapisovat rutiny, které pracují s reprezentací XAML na úrovni uzlu XAML.  
  
<a name="loading_into_a_xaml_reader"></a>   
## <a name="loading-xaml-into-a-xaml-reader"></a>Načítání XAML do čtečky XAML  
 Základní <xref:System.Xaml.XamlReader> třídy nedeklaruje konkrétní postup načítání počáteční XAML do čtečky XAML. Místo toho odvozená třída deklaruje a implementuje načítání techniku, včetně obecné vlastnosti a omezení v jeho vstupního zdroje pro XAML. Například <xref:System.Xaml.XamlObjectReader> přečte grafu objektů, spouští se ze vstupního zdroje jeden objekt, který představuje kořenový server WSUS nebo base. <xref:System.Xaml.XamlObjectReader> Pak vytvoří datový proud uzlu XAML z grafu objektů.  
  
 Většina viditelného definovaných rozhraní .NET Framework XAML Services <xref:System.Xaml.XamlReader> je podtřídou <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader> načte počáteční XAML, buď načtením do textového souboru přímo prostřednictvím datového proudu nebo souboru cesty nebo nepřímo prostřednictvím třídy související čtečky <xref:System.IO.TextReader>. <xref:System.Xaml.XamlReader> Si lze představit jako obsahující celého vstupního zdroje XAML po jeho načtení. Ale <xref:System.Xaml.XamlReader> základní rozhraní API je navržený tak, aby čtenář dixons carphone se jeden uzel XAML. Při prvním načtení, první jeden uzel, se kterými je kořenový adresář XAML a jeho spuštění objekt.  
  
### <a name="the-xaml-node-stream-concept"></a>Koncept Stream uzlu XAML  
 Pokud jste obecně více do hloubky modelu DOM, stromu jedná nebo založené na dotazech přístupu k přístupu k technologie založené na XML, je užitečný způsob, jak pohodlným datový proud uzlu XAML následujícím způsobem. Představte si, že je načteno XAML modelu DOM nebo stromové struktury, ve kterém je každý uzel je to možné úplně rozbalen a potom prezentovaná lineárně. Jako postupoval uzly vám může být procházení "v" nebo "out" úrovní, které by byly relevantní pro modelu DOM, ale datový proud uzlu XAML neudržuje explicitně sledování protože tyto koncepty úrovně nejsou relevantní pro datový proud uzlu. Datový proud uzlu má "aktuální" pozici, ale pokud jste uložili jiné části datového proudu sami sebe jako odkazy, každý aspekt datový proud uzlu, než je aktuální pozice uzlu je mimo zobrazení.  
  
 Koncept datový proud uzlu XAML má významné výhodu v tom, že pokud při procházení datový proud celého uzlu, budete mít jistotu, že mají zpracovat celou znázornění XAML; nemusíte se obávat, že dotaz, operace DOM nebo jiný nelineárních přístup k informacím o zpracování byl vynechán některá část dokončení zastoupení XAML. Z tohoto důvodu je reprezentace datový proud uzlu XAML ideální pro připojení XAML čtečky a zapisovače XAML i pro poskytování systému ve kterém můžete vložit vlastní proces, který funguje mezi jednotlivými fázemi pro čtení a zápisu operace zpracování XAML. V mnoha případech řazení uzly v datovém proudu uzlu XAML je úmyslně optimalizované nebo přeuspořádány čtenářům XAML a jak pořadí se může objevit zdrojový text, binární soubor nebo objekt grafu. Toto chování slouží vynutit architektuře zpracování s XAML, kterým jsou XAML zapisovače nikdy v umístění, které se mají vrátit "" v datovém proudu uzlu. V ideálním případě by všechny XAML operace zápisu by být možné tak, aby fungoval založená na schéma kontext a aktuální pozici datovém proudu uzlu.  
  
<a name="a_basic_reading_node_loop"></a>   
## <a name="a-basic-reading-node-loop"></a>Smyčku základní čtení uzlu  
 Základní čtení uzlu smyčky pro zkoumání datový proud uzlu XAML se skládá z následujících konceptů. Pro účely tohoto uzlu smyčky jak je popsáno v tomto tématu se předpokládá, že čtete založený na textu, čitelné XAML soubor pomocí <xref:System.Xaml.XamlXmlReader>. Odkazy v této části najdete konkrétní smyčky uzlu XAML rozhraní API implementované <xref:System.Xaml.XamlXmlReader>.  
  
-   Ujistěte se, že zatím nejste na konci datový proud uzlu XAML (zkontrolujte <xref:System.Xaml.XamlXmlReader.IsEof%2A>, nebo použijte <xref:System.Xaml.XamlXmlReader.Read%2A> návratová hodnota). Pokud jste na konci datového proudu, není aktuální uzel a má ukončit.  
  
-   Zkontrolujte, jaký typ uzlu datový proud uzlu XAML nyní poskytuje voláním <xref:System.Xaml.XamlXmlReader.NodeType%2A>.  
  
-   Pokud máte přidružených zapisovače objektu XAML, která je připojena přímo, obecně volání <xref:System.Xaml.XamlWriter.WriteNode%2A> v tomto okamžiku.  
  
-   Závislosti na němž <xref:System.Xaml.XamlNodeType> se ohlásí jako aktuální uzel nebo aktuální záznam volat jednu z následujících k získání informací o obsah uzlu:  
  
    -   Pro <xref:System.Xaml.XamlXmlReader.NodeType%2A> z <xref:System.Xaml.XamlNodeType.StartMember> nebo <xref:System.Xaml.XamlNodeType.EndMember>, volání <xref:System.Xaml.XamlXmlReader.Member%2A> získat <xref:System.Xaml.XamlMember> informace o členu. Všimněte si, že může být člen <xref:System.Xaml.XamlDirective>, a proto nemusí být nutně konvenční člen definován typ předchozí objektu. Například `x:Name` u objektu se zobrazí jako člena XAML kde <xref:System.Xaml.XamlMember.IsDirective%2A> má hodnotu true a <xref:System.Xaml.XamlMember.Name%2A> člena je `Name`, s jinými vlastnostmi označující, že tato direktiva je v oboru názvů XAML jazyka XAML.  
  
    -   Pro <xref:System.Xaml.XamlXmlReader.NodeType%2A> z <xref:System.Xaml.XamlNodeType.StartObject> nebo <xref:System.Xaml.XamlNodeType.EndObject>, volání <xref:System.Xaml.XamlXmlReader.Type%2A> získat <xref:System.Xaml.XamlType> informace o objektu.  
  
    -   Pro <xref:System.Xaml.XamlXmlReader.NodeType%2A> z <xref:System.Xaml.XamlNodeType.Value>, volání <xref:System.Xaml.XamlXmlReader.Value%2A>. Uzel je hodnota pouze v případě, že je nejjednodušší výraz hodnotu člena nebo textové inicializace pro objekt (ale byste měli vědět o chování převodu typu, jak je uvedeno v následující části tohoto tématu).  
  
    -   Pro <xref:System.Xaml.XamlXmlReader.NodeType%2A> z <xref:System.Xaml.XamlNodeType.NamespaceDeclaration>, volání <xref:System.Xaml.XamlXmlReader.Namespace%2A> získat informace o oboru názvů pro uzel oboru názvů.  
  
-   Volání <xref:System.Xaml.XamlXmlReader.Read%2A> čtečky XAML, přejděte k dalšímu uzlu v datovém proudu uzlu XAML, a opakujte znovu kroky.  
  
 Datový proud uzlu XAML poskytované rozhraní .NET Framework XAML Services XAML čtenáři vždy poskytuje úplné, podrobné procházení všech možných uzlů. Mezi dostupné techniky typické řízení toku pro smyčku uzlu XAML patří definování textu v rámci `while (reader.Read())`a přepnete <xref:System.Xaml.XamlXmlReader.NodeType%2A> v každém uzlu bodu ve smyčce uzlu.  
  
 Pokud datový proud uzlu je na konci souboru, aktuální uzel má hodnotu null.  
  
 Nejjednodušší smyčky, která používá čtečky a zapisovače vypadá podobně jako v následujícím příkladu.  
  
```  
XamlXmlReader xxr = new XamlXmlReader(new StringReader(xamlStringToLoad));  
//where xamlStringToLoad is a string of well formed XAML  
XamlObjectWriter xow = new XamlObjectWriter(xxr.SchemaContext);  
while (xxr.Read()) {  
  xow.WriteNode(xxr);  
}  
```  
  
 Tento základní příklad smyčku zatížení cesta XAML uzel připojí transparentně XAML čtečky a zapisovače XAML, to nic dělat jinak než v případě byste použili <xref:System.Xaml.XamlServices.Parse%2A?displayProperty=nameWithType>. Ale tato základní struktura je pak rozšířen použít pro čtení nebo zápis scénář. Některé možné scénáře jsou následující:  
  
-   Přepnout <xref:System.Xaml.XamlXmlReader.NodeType%2A>. Proveďte různé akce v závislosti na tom, který uzel typu načítán.  
  
-   Nevolejte <xref:System.Xaml.XamlWriter.WriteNode%2A> ve všech případech. Volat pouze <xref:System.Xaml.XamlWriter.WriteNode%2A> v některých <xref:System.Xaml.XamlXmlReader.NodeType%2A> případy.  
  
-   V rámci logiku pro konkrétní typ analyzovat specifika tento uzel a na jejich základě reagovat. Můžete například napsat pouze objekty, které pocházejí z konkrétní obor názvů XAML a potom vyřaďte nebo odložit všechny objekty nejsou z daného oboru názvů XAML. Nebo můžete vyřadit nebo jinak jako součást vaší člen zpracování znovu zpracovat všechny direktivy XAML, které váš systém XAML není podporováno.  
  
-   Definování vlastní <xref:System.Xaml.XamlObjectWriter> , která přepíše `Write*` metody, pravděpodobně provádí mapování typu, který obchází kontext schématu XAML.  
  
-   Vytvořit <xref:System.Xaml.XamlXmlReader> používat jiný než výchozí kontext schématu XAML tak, aby vlastní rozdíly v chování XAML se používají i tak, že čtečky a zapisovače.  
  
### <a name="accessing-xaml-beyond-the-node-loop-concept"></a>Přístup k XAML mimo smyčku koncept uzlu  
 Existují další způsoby, jak pracovat s XAML reprezentaci jiných než jako smyčky uzlu XAML. Například může existovat čtečku XAML, který může číst indexované uzlu nebo zejména přímo nástrojem přistupuje k uzly `x:Name`, `x:Uid`, nebo prostřednictvím další identifikátory. Rozhraní .NET framework XAML Services neposkytuje úplnou implementaci, ale poskytuje navrhovaný model prostřednictvím typů služeb a podpory. Další informace naleznete v tématu <xref:System.Xaml.IXamlIndexingReader> a <xref:System.Xaml.XamlNodeList>.  
  
> [!TIP]
>  Microsoft také vytváří o verzi out-of-band označuje jako Microsoft XAML Toolkit. Toto vydání out-of-band stále probíhá jeho fází předběžné verze. Ale pokud jste ochotní pro práci s předběžných komponenty, Microsoft XAML Toolkit poskytuje některé zajímavé prostředky pro nástroje XAML a statické analýzy XAML. Microsoft XAML Toolkit obsahuje API modelu DOM XAML, podporu pro analýzu FxCop a kontext schématu XAML pro technologii Silverlight. Další informace najdete v tématu [Microsoft XAML Toolkit](https://code.msdn.microsoft.com/XAML).  
  
<a name="working_with_the_current_node"></a>   
## <a name="working-with-the-current-node"></a>Práce s aktuální uzel  
 Většina scénářů, které používají smyčky uzlu XAML jenom nečtou uzlů. Většina scénářů zpracování aktuální uzly a předat každý uzel, jeden po druhém implementace <xref:System.Xaml.XamlWriter>.  
  
 Ve scénáři cesta obvyklém zatížení <xref:System.Xaml.XamlXmlReader> vytvoří datový proud uzlu XAML; uzlů XAML se zpracovávají podle logiky a kontext schématu XAML a uzly jsou předány <xref:System.Xaml.XamlObjectWriter>. Výsledný graf objektu se potom začlenit do vaší aplikace nebo rozhraní.  
  
 V typické Uložit cestu scénář <xref:System.Xaml.XamlObjectReader> přečte graf objektu, zpracování jednotlivých uzlů XAML a <xref:System.Xaml.XamlXmlWriter> výstupy serializovaná výsledek v podobě textového souboru XAML. Klíč je, že cesty a scénáře zahrnují práci se přesně jedna XAML uzlů najednou a uzlů XAML jsou k dispozici pro zpracování a standardizovaným způsobem, který je definován tak, že systém typů XAML a rozhraní.NET Framework XAML Services API.  
  
### <a name="frames-and-scope"></a>Rámce a oboru  
 Smyčka uzlu XAML vás provede datový proud uzlu XAML lineárním způsobem. Datový proud uzlu prochází do objektů do členů, které obsahují další objekty a tak dále. Často je užitečné udržovat přehled o oboru v rámci datový proud uzlu XAML implementací koncept rámec a v zásobníku. To platí zejména pokud jsou v něm jsou aktivně upravit datový proud uzlu. Rámce a zásobníku podporují implementovat jako součást logiky smyčky uzel může počítat `StartObject` (nebo `GetObject`) a `EndObject` obory, jako sestup do struktury uzlu XAML, pokud je struktura mluvit z hlediska modelu DOM.  
  
<a name="traversing_and_entering_object_nodes"></a>   
## <a name="traversing-and-entering-object-nodes"></a>Procházení a zadat uzly objektu  
 Prvním uzlem v datovém proudu uzlu při otevření čtečka XAML je uzel počáteční objekt kořenového objektu. Podle definice tento objekt je vždy jeden objekt uzlu a nemá žádné partnerské uzly. V XAML jakékoli reálný příklad kořenový objekt je definován s jednu nebo více vlastností, které obsahují další objekty a členskými uzly mají tyto vlastnosti. Členskými uzly potom mít jeden nebo více uzly objektu, nebo může také ukončit v uzlu s hodnotou, se místo toho. Kořenový objekt obvykle definuje obory názvů XAML, které jsou přiřazeny syntakticky jako atributy ve značce XAML text, ale mapování na `Namescope` typ uzlu v reprezentaci datový proud uzlu XAML.  
  
 Zvažte následující příklad XAML (to je libovolný XAML, nezálohované existující typy v rozhraní .NET Framework). Předpokládejme, že v tomto modelu objektu `FavorCollection` je `List<T>` z `Favor`, `Balloon` a `NoiseMaker` jsou přiřaditelné k `Favor`, `Balloon.Color` vlastnost tímto modulem stojí `Color` objekt podobný jak definuje WPF barvy jako názvy známé barev a `Color` podporuje konvertor typu pro syntaxi atributů.  
  
|Značky XAML|Výsledný datový proud uzlu XAML|  
|-----------------|--------------------------------|  
|`<Party`|`Namespace` uzel pro `Party`|  
|`xmlns="PartyXamlNamespace">`|`StartObject` uzel pro `Party`|  
|`<Party.Favors>`|`StartMember` uzel pro `Party.Favors`|  
||`StartObject` uzel pro implicitní `FavorCollection`|  
||`StartMember` uzel pro implicitní `FavorCollection` vlastnosti položky.|  
|`<Balloon`|`StartObject` uzel pro `Balloon`|  
|`Color="Red"`|`StartMember` uzel pro `Color`<br /><br /> `Value` uzel pro řetězec hodnoty atributu `"Red"`<br /><br /> `EndMember` pro `Color`|  
|`HasHelium="True"`|`StartMember` uzel pro `HasHelium`<br /><br /> `Value` uzel pro řetězec hodnoty atributu `"True"`<br /><br /> `EndMember` pro `HasHelium`|  
|`>`|`EndObject` pro `Balloon`|  
|`<NoiseMaker>Loudest</NoiseMaker>`|`StartObject` uzel pro `NoiseMaker`<br /><br /> `StartMember` uzel pro `_Initialization`<br /><br /> `Value` uzel pro hodnotu inicializačního řetězce `"Loudest"`<br /><br /> `EndMember` uzel pro `_Initialization`<br /><br /> `EndObject` pro `NoiseMaker`|  
||`EndMember` uzel pro implicitní `FavorCollection` vlastnosti položky.|  
||`EndObject` uzel pro implicitní `FavorCollection`|  
|`</Party.Favors>`|`EndMember` pro `Favors`|  
|`</Party>`|`EndObject` pro `Party`|  
  
 V datovém proudu uzlu XAML se spoléháte na toto chování:  
  
-   Pokud `Namespace` uzel existuje, přidá se do datového proudu bezprostředně před `StartObject` , který je deklarován obor názvů XAML s `xmlns`. Podívejte se na předchozí tabulky pomocí XAML a příklad datovém proudu uzlu znovu. Všimněte si, že jak `StartObject` a `Namespace` uzly zdá se, že přehození oproti deklarace pozice v textu značky. Toto je zástupce chování, ve kterém uzly oboru názvů vždy zobrazují před uzlem použijí v datovém proudu uzlu. Účelem tohoto návrhu je, informace o oboru názvů je důležité objektu zapisovače a musí být známo předtím, než objekt zapisovače objekt se pokusí provést typ mapování nebo jinak zpracovat. Uvedení informace oboru názvů XAML náskok před jeho oboru aplikace v datovém proudu zjednodušuje vždy zpracovat datový proud uzlu v jeho prezentované pořadí.  
  
-   Z důvodu výše zvážit, je jeden nebo více `Namespace` uzly, které si přečíst nejprve ve většině případů značkách reálného světa při procházení uzly od začátku, ne `StartObject` kořene.  
  
-   A `StartObject` uzlu může být následován `StartMember`, `Value`, nebo ihned `EndObject`. To se nikdy vzápětí jiného `StartObject`.  
  
-   A `StartMember` může být následován `StartObject`, `Value`, nebo ihned `EndMember`. To může být následován `GetObject`, pro členy, kde hodnota by měl pocházet z existující hodnoty nadřazeného objektu spíše než `StartObject` , které byste měli vytvořit instanci novou hodnotu. To může být následován znakem `Namespace` uzlu, která se vztahuje na nadcházející `StartObject`. To se nikdy vzápětí jiného `StartMember`.  
  
-   A `Value` samotná hodnota představuje uzel; není žádný "EndValue". To může následovat pouze `EndMember`.  
  
    -   Text XAML inicializace objektu by mohly používat konstrukce nemá za následek struktury hodnotu objektu. Místo toho uzel vyhrazené člena pro člena s názvem `_Initialization` se vytvoří. a tento člen uzel obsahuje inicializační řetězec hodnoty. Pokud existuje, `_Initialization` je vždy první `StartMember`. `_Initialization` může být kvalifikovaný v některých služeb reprezentace XAML s obor namescope XAML jazyka XAML pro vysvětlení, že `_Initialization` se nenachází ve vlastnosti definované v typy zálohování.  
  
    -   Hodnota člena kombinaci představuje nastavení atributu hodnoty. Nakonec pravděpodobně převaděč hodnot při zpracování tato hodnota a hodnota je prostý řetězec. Nicméně, který není vyhodnocen, dokud zapisovače objektu XAML zpracuje tento datový proud uzlu. Objekt zapisovače XAML má potřebné kontext schématu XAML, mapování typu systému a další podporu potřebné pro převody hodnot.  
  
-   `EndMember` Uzlu může být následován znakem `StartMember` uzel pro následující člen, nebo podle `EndObject` uzlu vlastníka člena.  
  
-   `EndObject` Uzlu může být následován `EndMember` uzlu. To může být následován znakem `StartObject` uzel pro případy, ve kterém jsou objekty partnerské uzly v položky kolekce. Nebo může být následován znakem `Namespace` uzlu, která se vztahuje na nadcházející `StartObject`.  
  
    -   Pro jedinečný případ ukončení datový proud celého uzlu `EndObject` z kořenové nenásleduje nic; čtecí modul je nyní end souboru, a <xref:System.Xaml.XamlReader.Read%2A> vrátí `false`.  
  
<a name="value_converters_and_the_xaml_node_stream"></a>   
## <a name="value-converters-and-the-xaml-node-stream"></a>Převaděče hodnot a Stream uzlu XAML  
 Převaděč hodnoty je obecný termín pro rozšíření značek, konvertor typu (včetně hodnoty serializátory) nebo jiný vyhrazený třídu, která se hlásí jako převaděč hodnoty prostřednictvím typu systému XAML. V datovém proudu uzlu XAML mají velmi odlišné reprezentace použití převaděče typů a použití rozšíření značky.  
  
### <a name="type-converters-in-the-xaml-node-stream"></a>Převaděče typů v Stream uzlu XAML  
 Atribut nastavit, že nakonec výsledkem použití převaděče typů v hlásí datový proud uzlu XAML jako hodnotu člena. Datový proud uzlu XAML se nebude pokoušet vytvořit objekt instance převaděče typů a do něj předáte hodnotu. Pomocí implementace převodu konvertor typu vyžaduje volání kontext schématu XAML a jeho použití pro mapování typu. Kontext schématu XAML dokonce určující, které třídy konvertor typu by měla sloužit ke zpracování hodnota vyžaduje nepřímo. Pokud použijete výchozí kontext schématu XAML, tyto informace jsou dostupné z typu systému XAML. Pokud potřebujete informace o převaděč třídy typu na úrovni datový proud uzlu XAML před připojení pro zápis XAML, získáte ho od <xref:System.Xaml.XamlMember> informace člen nastavena. Ale v opačném případě vstupní typ převaděče by měl být zachovaná v datovém proudu uzlu XAML jako obyčejný hodnotu, dokud se zbývající operace, které vyžadují systém mapování typů a kontext schématu XAML jsou prováděny, například vytvoření objektu pomocí XAML objekt zapisovače.  
  
 Představte si třeba následující osnova – třída definice a používání XAML pro něj:  
  
```  
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
  
 Textové vyjádření datový proud uzlu XAML pro toto použití může být vyjádřený jako následující:  
  
 `StartObject` s <xref:System.Xaml.XamlType> představující `GameBoard`  
  
 `StartMember` s <xref:System.Xaml.XamlMember> představující `BoardSize`  
  
 `Value` uzel textovým řetězcem "`8x8`"  
  
 `EndMember` Shody `BoardSize`  
  
 `EndObject` Shody `GameBoard`  
  
 Všimněte si, že neexistuje žádná instance konvertor typu v tomto datovém proudu uzlu. Ale můžete získat informace o typu konvertoru voláním <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> na <xref:System.Xaml.XamlMember> pro `BoardSize`. Pokud máte platný kontext schématu XAML, můžete také vyvolat metody převaděč získat instanci ze <xref:System.Xaml.Schema.XamlValueConverter%601.ConverterInstance%2A>.  
  
### <a name="markup-extensions-in-the-xaml-node-stream"></a>Rozšíření značek v Stream uzlu XAML  
 Použití rozšíření značky se hlásí v datovém proudu uzlu XAML jako uzel objektu v členu, kde objekt představuje instanci rozšíření značek. Proto použití rozšíření značky se zobrazí více explicitně v reprezentaci datový proud uzlu než je použití převaděče typů a provede další informace. <xref:System.Xaml.XamlMember> informace nelze mít uvedli jako vám nic o rozšíření značek, protože využití je povědomí a liší se v každém případě je to možné značek; není vyhrazené a implicitní za typ nebo člen stejně jako v případě pomocí převaděče typů.  
  
 Reprezentace datového proudu uzlu přípony označení jako uzly objektu platí i v případě použití rozšíření značky proběhla do formuláře atributů ve značkách XAML text (což se stává často). Použití rozšíření značky, které používají formuláři prvku objektu explicitní zachází stejně.  
  
 V rámci uzlu objektu rozšíření značek mohou být členy tohoto rozšíření značek. Reprezentace datový proud uzlu XAML zachová využití tohoto rozšíření značek, jestli používání pozičních parametrů více dopředu nebo využití pomocí explicitní pojmenované parametry.  
  
 Pro použití pozičních parametrů více dopředu, datový proud uzlu XAML obsahuje vlastnost definovaný jazyk XAML `_PositionalParameters` , který zaznamenává využití. Tato vlastnost je obecný <xref:System.Collections.Generic.List%601> s <xref:System.Object> omezení. Omezení je objekt a není řetězec, protože odcizenou pozičních parametrů více dopředu využití může zahrnovat použití rozšíření značky vnořené v něm. Pro přístup k poziční parametry z využití, může iteraci v rámci seznamu a pomocí indexerů seznamu jednotlivých hodnot.  
  
 Pojmenovaným parametrem využití každý pojmenovaný parametr reprezentované jako uzel člen s tímto názvem v datovém proudu uzlu. Člen hodnoty nejsou nutně řetězce, protože to může být použití rozšíření značky vnořené.  
  
 `ProvideValue` ještě není vyvolána rozšíření, od značky. Nicméně, je vyvolána, pokud připojíte XAML čtečky a zapisovače XAML tak, aby `WriteEndObject` vyvolání při zkoumání v datovém proudu uzlu na uzel rozšíření značek. Z tohoto důvodu musíte obecně stejné XAML schématu kontextu k dispozici, protože by se použily, aby bylo možné formulář grafu objektů v cestě zatížení. V opačném případě `ProvideValue` z jakoukoli marži rozšíření může vyvolat výjimky, protože nemá očekávaný služby, které jsou k dispozici.  
  
<a name="xaml_and_xml_languagedefined_members_in_the_xaml_node_stream"></a>   
## <a name="xaml-and-xml-language-defined-members-in-the-xaml-node-stream"></a>XAML a XML definice jazyk členy v Stream uzlu XAML  
 Některé členy zavedení do datový proud uzlu XAML z důvodu interpretace a konvence čtečku XAML namísto prostřednictvím explicitní <xref:System.Xaml.XamlMember> vyhledávání nebo konstrukce. Tyto členy jsou často, direktivy XAML. V některých případech je operace čtení XAML, který představuje direktivu do datový proud uzlu XAML. Jinými slovy, původní vstup XAML text nebyl explicitně zadat member – direktiva, ale čtečky XAML vloží směrnice splníte a strukturální XAML konvence a sestavy informace v datovém proudu uzlu XAML předtím, než dojde ke ztrátě informací.  
  
 Následující poznámky k seznamu, které jsou všechny případy, kde je očekávána čtečku XAML zavést direktiv uzel člena XAML, a jak se tento uzel člen identifikovat v implementacích rozhraní .NET Framework XAML Services.  
  
-   **Inicializace text pro objekt uzlu:** je název tohoto uzlu člen `_Initialization`, představuje direktivu XAML a je definován v oboru názvů jazyka XAML XAML. Statické entity můžete získat z <xref:System.Xaml.XamlLanguage.Initialization%2A>.  
  
-   **Poziční parametry pro rozšíření značek:** je název tohoto uzlu člen `_PositionalParameters`, a je definován v oboru názvů jazyka XAML XAML. Vždy obsahuje obecný seznam objektů, z nichž každý je poziční parametr předem oddělené rozdělení na `,` oddělovací znak jako dodaného vstup XAML. Statické entity můžete získat pro direktivu poziční parametry z <xref:System.Xaml.XamlLanguage.PositionalParameters%2A>.  
  
-   **Neznámá obsah:** je název tohoto uzlu člen `_UnknownContent`. Přesněji řečeno, jde <xref:System.Xaml.XamlDirective>, a je definován v oboru názvů jazyka XAML XAML. Tato direktiva se používá jako sentinel pro případy, kdy elementu objektu XAML obsahuje obsah, zdroje XAML, ale v tuto chvíli k dispozici kontext schématu XAML se dá určit bez vlastnost content. Tento případ, v datovém proudu uzlu XAML můžete zjistit kontrolou pro členy s názvem `_UnknownContent`. Pokud nebyla provedena žádná další akce v XAML uzel zatížení cesty toku, výchozí <xref:System.Xaml.XamlObjectWriter> vyvolá pokus o `WriteEndObject` když narazí `_UnknownContent` člen libovolného objektu. Výchozí hodnota <xref:System.Xaml.XamlXmlWriter> nevyvolá a považuje za člena implicitní. Můžete získat statické entity pro `_UnknownContent` z <xref:System.Xaml.XamlLanguage.UnknownContent%2A>.  
  
-   **Vlastnost kolekce kolekce:** i když má vyhrazené s názvem vlastnosti, která obsahuje položky kolekce základní typ CLR tohoto třídu kolekce, která se obvykle používá pro XAML, tato vlastnost není znám o typu systému XAML před zálohování typu řešení. Místo toho představuje datový proud uzlu XAML `Items` zástupný text jako člen kolekce typu XAML. V implementaci rozhraní .NET Framework XAML Services název této směrnice / člena v datovém proudu uzlu je `_Items`. Konstanty pro tuto direktivu lze získat z <xref:System.Xaml.XamlLanguage.Items%2A>.  
  
     Všimněte si, že datový proud uzlu XAML může obsahovat vlastnosti Items s položkami, které ukázat nebudou parseable podle typu řešení zálohování a kontext schématu XAML. Například  
  
-   **XML definované členy:** XML definované `xml:base`, `xml:lang` a `xml:space` členy označené jako s názvem direktivy XAML `base`, `lang`, a `space` v rozhraní .NET Framework XAML Services implementace. Obor názvů pro toto je obor názvů XML `http://www.w3.org/XML/1998/namespace`. Konstanty pro každou z nich můžete získat z <xref:System.Xaml.XamlLanguage>.  
  
## <a name="node-order"></a>Uzel pořadí  
 V některých případech <xref:System.Xaml.XamlXmlReader> změní pořadí uzlů XAML v proudu uzlu XAML, a pořadí uzly zobrazí-li zobrazit v kódu nebo pokud zpracování formátu XML. To se provádí, aby bylo možné pořadí uzly tak, aby <xref:System.Xaml.XamlObjectWriter> může zpracovat datový proud uzlu dopředné způsobem.  V rozhraní .NET Framework XAML Services čtečky XAML změní pořadí uzly spíše než byste museli opustit tuto úlohu do zapisovače XAML optimalizace výkonu pro spotřebitele zapisovače objektu XAML datový proud uzlu.  
  
 Některé direktivy jsou určené konkrétně pro zajištění Další informace pro vytvoření objektu z objektu elementu. Tyto směrnice jsou: `Initialization`, `PositionalParameters`, `TypeArguments`, `FactoryMethod`, `Arguments`. Pokus o tyto direktivy umístit jako první členy v datovém proudu uzlu po objektu rozhraní .NET Framework XAML Services XAML čtenáři `StartObject`, z důvodů, které jsou vysvětlené v následující části.  
  
### <a name="xamlobjectwriter-behavior-and-node-order"></a>Chování XamlObjectWriter a pořadí uzlů  
 `StartObject` k <xref:System.Xaml.XamlObjectWriter> není nutně signál, který objekt zapisovače XAML okamžitě vytvořit instanci objektu. XAML obsahuje několik funkcí jazyka, které umožňují inicializovat objekt s další vstupy a nespoléhala se výhradně na vyvolání výchozího konstruktoru vytvoří počáteční objekt a teprve pak nastavení vlastnosti. Tyto funkce patří: <xref:System.Windows.Markup.XamlDeferLoadAttribute>; inicializace textu. [x: TypeArguments](../../../docs/framework/xaml-services/x-typearguments-directive.md); poziční parametry rozšíření značek; metody pro vytváření objektů a související [x: Arguments](../../../docs/framework/xaml-services/x-arguments-directive.md) uzly (XAML 2009). Každá z těchto případů zpoždění konstrukce skutečný objekt a vzhledem k tomu, že je pořadí změníte datový proud uzlu, můžete zapisovače objektu XAML Spolehněte se na chování ve skutečnosti vytváření instance pokaždé, když se zjistila člen start, které nejsou konkrétně konstrukce směrnice pro tento typ objektu.  
  
### <a name="getobject"></a>Funkce GetObject  
 `GetObject` představuje uzel s XAML, kde místo vytváření nového objektu zapisovače objektu XAML by měl místo toho získat hodnoty vlastnosti nadřazeného objektu. Obvyklý případ kde `GetObject` nebude nalezen uzel v uzlu XAML je pro objekt kolekce nebo objekt slovníku při nadřazenou vlastnost je záměrně jen pro čtení v objektovém modelu základního typu. V tomto scénáři kolekci ani slovník často je vytvořen a inicializován (obvykle prázdná) logikou inicializace vlastnícího typu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xaml.XamlObjectReader>  
 [XAML Services](../../../docs/framework/xaml-services/index.md)  
 [Obory názvů jazyka XAML](../../../docs/framework/xaml-services/xaml-namespaces-for-net-framework-xaml-services.md)
