---
title: Principy struktur a koncepcí datových proudů uzlů XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML node streams [XAML Services]
- nodes [XAML Services], XAML node stream
- XAML [XAML Services], XAML node streams
ms.assetid: 7c11abec-1075-474c-9d9b-778e5dab21c3
ms.openlocfilehash: fc27426e4d48ae519fc743c8a4f7eb3d1e6a4e81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="understanding-xaml-node-stream-structures-and-concepts"></a>Principy struktur a koncepcí datových proudů uzlů XAML
XAML čtení a zápis XAML, jak jsou implementované v rozhraní .NET Framework XAML Services jsou založené na návrh konceptu datový proud uzlu XAML. Datový proud uzlu XAML je koncepci sady uzlů XAML. V této koncepci procesor XAML provede strukturu uzlu vztahy v jazyce XAML, jeden v čase. V každém okamžiku existuje pouze jeden záznam na aktuální nebo aktuální pozici v otevřít datový proud uzlu XAML a mnoho aspektů rozhraní API sestavy pouze informace k dispozici z této pozice. Aktuální uzel v datový proud uzlu XAML lze popsat jako objekt, člen nebo hodnota. Tak, že považuje XAML jako datový proud uzlu XAML, můžete XAML čtečky komunikovat s zapisovače XAML a povolit program k zobrazení, pracovat s nebo alter obsah datový proud uzlu XAML při zatížení cestu nebo uložení operace cestu, která zahrnuje XAML. Rozhraní API návrhu XAML čtení a zápis a koncept datový proud uzlu XAML jsou například podobné předchozí související čtečky a návrhy zapisovače a koncepty, [!INCLUDE[TLA#tla_xmldom](../../../includes/tlasharptla-xmldom-md.md)] a <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter> třídy. Toto téma popisuje koncepty datový proud uzlu XAML a popisuje, jak můžete napsat rutiny, které pracují se reprezentace XAML na úrovni uzlu XAML.  
  
<a name="loading_into_a_xaml_reader"></a>   
## <a name="loading-xaml-into-a-xaml-reader"></a>Načtení XAML do čtečky XAML  
 Základní <xref:System.Xaml.XamlReader> třída nedeklaruje konkrétní technika pro načtení počáteční XAML do čtečky XAML. Místo toho odvozené třídě deklaruje a implementuje načítání techniku, včetně obecné vlastnosti a omezení jeho vstupní zdroj pro jazyk XAML. Například <xref:System.Xaml.XamlObjectReader> čte grafu objektů, počínaje od vstupní zdroj jeden objekt, který reprezentuje kořenový server WSUS nebo základní. <xref:System.Xaml.XamlObjectReader> Pak vytvoří datový proud uzlu XAML z grafu objektu.  
  
 Většina viditelného rozhraní .NET Framework XAML Services – definované <xref:System.Xaml.XamlReader> je podtřídou <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader> načte počáteční XAML, buď načítání textového souboru přímo prostřednictvím datového proudu nebo cesta nebo nepřímo prostřednictvím čtečky související třídy, jako jsou například <xref:System.IO.TextReader>. <xref:System.Xaml.XamlReader> Si lze představit jako obsahující celého vstupní zdroj XAML po byl načten. Ale <xref:System.Xaml.XamlReader> základní rozhraní API je navržené tak, aby čtečka je interakci s jednoho uzlu XAML. Při prvním načtení první jeden uzel, na které narazíte je kořenem XAML a její spuštění objektu.  
  
### <a name="the-xaml-node-stream-concept"></a>Koncept datový proud uzlu XAML  
 Pokud znáte obecně více DOM, jedná stromu nebo na základě dotazů přístup k přístupu na základě XML technologie, užitečné způsob, jak conceptualize datový proud uzlu XAML je následující. Představte si, že je načteno XAML DOM nebo stromu, kde je každý uzel možné úplně rozbalen a poté jsou předloženy lineárně. Jako přechodu prostřednictvím uzly, vám může být procházení "v" nebo "na" úrovní, které by byly relevantní pro DOM, ale datový proud uzlu XAML by neměly být explicitně sledovat vzhledem k tomu, že tyto úrovně koncepty nejsou relevantní pro datový proud uzlu. Datový proud uzlu má "aktuální" pozice, ale pokud jsou uloženy dalších částí datového proudu sami jako odkazy, každý aspekt datový proud uzlu než aktuální umístění uzlu je mimo zobrazení.  
  
 Koncept datový proud uzlu XAML má významné výhody, pokud přejdete prostřednictvím datový proud celého uzlu, budete mít jistotu, že byl zpracován celý XAML reprezentace; nemusíte si dělat starosti dotazu, operace DOM nebo některé nelineární přístup k informacím zpracování se byl vynechán některé části dokončení reprezentace XAML. Z tohoto důvodu je reprezentace datový proud uzlu XAML ideální pro připojení XAML čtení a zápis XAML i pro poskytování systému kde můžete vložit vlastní proces, který funguje mezi jednotlivé fáze XAML zpracování operace čtení a zápis. V mnoha případech řazení uzly v datový proud uzlu XAML je úmyslně optimalizované nebo přeuspořádány čtenářům XAML a jak může vypadat pořadí v zdrojový text, binary nebo grafu objektu. Toto chování je určený k vynucení architektura zpracování XAML při němž jsou XAML zapisovače nikdy v pozici, které se mají vrátit "" v datovém proudu uzlu. V ideálním případě by všechny XAML operací zápisu by měla být schopný tak, aby fungoval založena na kontext schématu plus aktuální pozici datový proud uzlu.  
  
<a name="a_basic_reading_node_loop"></a>   
## <a name="a-basic-reading-node-loop"></a>Základní čtení uzly smyčka  
 Základní čtení uzly smyčka pro zkoumání datový proud uzlu XAML se skládá z následujících koncepty. Pro účely tohoto uzlu smyčky popsané v tomto tématu se předpokládá, že čtete založený na textu, čitelná pro člověka XAML souboru pomocí <xref:System.Xaml.XamlXmlReader>. Odkazy v této části najdete konkrétní smyčky uzlu XAML API implementované <xref:System.Xaml.XamlXmlReader>.  
  
-   Ujistěte se, že nejste na konci datový proud uzlu XAML (zkontrolujte <xref:System.Xaml.XamlXmlReader.IsEof%2A>, nebo použijte <xref:System.Xaml.XamlXmlReader.Read%2A> vrátit hodnotu). Pokud jste na konci tohoto datového proudu, není aktuální uzel a má ukončit.  
  
-   Zkontrolujte, jaký typ uzlu datový proud uzlu XAML zpřístupní aktuálně voláním <xref:System.Xaml.XamlXmlReader.NodeType%2A>.  
  
-   Pokud máte přidružené zapisovače XAML objektu, který je připojený přímo, obecně volání <xref:System.Xaml.XamlWriter.WriteNode%2A> v tomto okamžiku.  
  
-   Závislosti na němž <xref:System.Xaml.XamlNodeType> hlášení jako aktuální záznam na aktuální uzel volání jednoho z těchto způsobů získat informace o obsahu uzlu:  
  
    -   Pro <xref:System.Xaml.XamlXmlReader.NodeType%2A> z <xref:System.Xaml.XamlNodeType.StartMember> nebo <xref:System.Xaml.XamlNodeType.EndMember>, volání <xref:System.Xaml.XamlXmlReader.Member%2A> získat <xref:System.Xaml.XamlMember> informace o členem. Všimněte si, že může být člen <xref:System.Xaml.XamlDirective>, a proto nemusí být nutně konvenční člen definován typ předchozí objektu. Například `x:Name` u objektu se zobrazí jako člena XAML kde <xref:System.Xaml.XamlMember.IsDirective%2A> hodnotu true a <xref:System.Xaml.XamlMember.Name%2A> člena je `Name`, s jinými vlastnostmi označující, že tato direktiva je v rámci oboru názvů jazyka XAML jazyka XAML.  
  
    -   Pro <xref:System.Xaml.XamlXmlReader.NodeType%2A> z <xref:System.Xaml.XamlNodeType.StartObject> nebo <xref:System.Xaml.XamlNodeType.EndObject>, volání <xref:System.Xaml.XamlXmlReader.Type%2A> získat <xref:System.Xaml.XamlType> informace o objektu.  
  
    -   Pro <xref:System.Xaml.XamlXmlReader.NodeType%2A> z <xref:System.Xaml.XamlNodeType.Value>, volání <xref:System.Xaml.XamlXmlReader.Value%2A>. Uzel je hodnota, pouze pokud je nejjednodušší výrazu hodnoty pro člena nebo inicializace text pro objekt (ale byste měli znát typ převodu chování, jak je uvedeno v nadcházející část tohoto tématu).  
  
    -   Pro <xref:System.Xaml.XamlXmlReader.NodeType%2A> z <xref:System.Xaml.XamlNodeType.NamespaceDeclaration>, volání <xref:System.Xaml.XamlXmlReader.Namespace%2A> se získat informace o oboru názvů pro uzlu oboru názvů.  
  
-   Volání <xref:System.Xaml.XamlXmlReader.Read%2A> přechodu čtečky XAML na další uzel v datový proud uzlu XAML a znovu opakujte kroky.  
  
 Datový proud uzlu XAML poskytované rozhraní .NET Framework XAML Services XAML čtečky vždy poskytuje úplné, hloubkové traversal všech možných uzlů. Typické řízení toku techniky pro smyčku uzlu XAML zahrnuje definování text v rámci `while (reader.Read())`, vyhledávání a přepínání <xref:System.Xaml.XamlXmlReader.NodeType%2A> na každém uzlu bodu ve smyčce uzlu.  
  
 Pokud datový proud uzlu je na konci souboru, aktuální uzel má hodnotu null.  
  
 Nejjednodušší smyčky, který používá čtení a zápis se podobá následujícímu příkladu.  
  
```  
XamlXmlReader xxr = new XamlXmlReader(new StringReader(xamlStringToLoad));  
//where xamlStringToLoad is a string of well formed XAML  
XamlObjectWriter xow = new XamlObjectWriter(xxr.SchemaContext);  
while (xxr.Read()) {  
  xow.WriteNode(xxr);  
}  
```  
  
 Tady je příklad základní smyčku uzlu XAML cesta zatížení transparentně připojí XAML čtení a zápis XAML, jiné než v případě žádným způsobem při použití <xref:System.Xaml.XamlServices.Parse%2A?displayProperty=nameWithType>. Ale tato základní struktura je pak rozšířit tak, aby použít ke čtení nebo zápis scénář. Některé možné scénáře jsou následující:  
  
-   Přepnout <xref:System.Xaml.XamlXmlReader.NodeType%2A>. Provádění různých akcí v závislosti na tom, který uzel typu načítán.  
  
-   Nevolejte <xref:System.Xaml.XamlWriter.WriteNode%2A> ve všech případech. Volat pouze <xref:System.Xaml.XamlWriter.WriteNode%2A> v některých <xref:System.Xaml.XamlXmlReader.NodeType%2A> případech.  
  
-   V rámci logiku pro typ konkrétním uzlem analýza specifikace tento uzel a s nimi pracovat. Můžete například napsat pouze objekty, které pocházejí z konkrétní oboru názvů jazyka XAML a potom vyřaďte nebo odložení všechny objekty, nikoli z tohoto oboru názvů jazyka XAML. Nebo můžete vyřadit nebo jinak znovu zpracovat všechny direktivy jazyka XAML, které XAML systém nepodporuje v rámci vaší člena zpracování.  
  
-   Definovat vlastní <xref:System.Xaml.XamlObjectWriter> , přepíše `Write*` metody, které by mohly mít provádění mapování typu, který obchází kontext schématu XAML.  
  
-   Vytvořit <xref:System.Xaml.XamlXmlReader> používat kontext schématu XAML jiný než výchozí, tak přizpůsobené rozdíly v chování XAML se používají jak čtečka tak zapisovač.  
  
### <a name="accessing-xaml-beyond-the-node-loop-concept"></a>Přístup k nad rámec koncept smyčky uzlu XAML  
 Existují další způsoby, jak pracovat s znázornění XAML jinak než jako smyčku uzlu XAML. Například může existovat ke čtečku XAML, který může číst indexované uzlu, nebo na konkrétní přímo nástrojem přistupuje k uzly `x:Name`, pomocí `x:Uid`, nebo prostřednictvím jiné identifikátory. Rozhraní .NET framework XAML Services neposkytuje úplnou implementaci, ale poskytuje základní vzor navrhované prostřednictvím typů služeb a podpory. Další informace naleznete v tématu <xref:System.Xaml.IXamlIndexingReader> a <xref:System.Xaml.XamlNodeList>.  
  
> [!TIP]
>  Microsoft také vytváří o verzi out-of-band známé jako sada nástrojů pro XAML. Tato verze out-of-band je stále v jeho fází předběžné verze. Ale pokud jste ochotni pracovat s předběžné verze součásti, sada nástrojů pro XAML poskytuje některé zajímavé prostředky pro XAML nástrojů a statické analýzy XAML. Sada nástrojů pro XAML zahrnuje XAML DOM API, podpora pro FxCop analysis a kontext schématu XAML pro technologii Silverlight. Další informace najdete v tématu [sada nástrojů pro XAML](http://code.msdn.microsoft.com/XAML).  
  
<a name="working_with_the_current_node"></a>   
## <a name="working-with-the-current-node"></a>Práce s aktuálním uzlu  
 Většina scénáře, které používají smyčku uzlu XAML pouze nečtou uzly. Většina scénářů zpracovat aktuální uzly a předejte každý uzel, jeden v čase do implementace <xref:System.Xaml.XamlWriter>.  
  
 Ve scénáři, cesta typické zatížení <xref:System.Xaml.XamlXmlReader> vytvoří datový proud uzlu XAML; uzlů XAML se zpracovávají podle logiky a kontext schématu XAML a uzly jsou předány <xref:System.Xaml.XamlObjectWriter>. Výsledný objekt grafu se pak integrovat do vaší aplikace nebo framework.  
  
 V typické Uložit cestu scénáři <xref:System.Xaml.XamlObjectReader> čte grafu objektů, jsou zpracovávány jednotlivé uzly XAML a <xref:System.Xaml.XamlXmlWriter> výstupy serializovaných výsledek v podobě textového souboru XAML. Klíč je, že cesty a scénáře zahrnují práci s přesně jednou uzlu XAML najednou a XAML uzly jsou k dispozici pro zpracování a standardizovaným způsobem, který je definován typ systém XAML a rozhraní.NET Framework XAML Services API.  
  
### <a name="frames-and-scope"></a>Rámce a obor  
 Smyčku uzlu XAML provede datový proud uzlu XAML lineární způsobem. Datový proud uzlu prochází do objektů do členů, které obsahují další objekty a tak dále. Je často užitečné k udržování přehledu o oboru v rámci datový proud uzlu XAML implementací rámce zásobníku a koncept. To je zvlášť hodnota true, pokud jsou v ní jsou aktivně úpravě datový proud uzlu. Rámec a zásobníku podporovat, že můžete implementovat jako součást logiky smyčky uzlu může počet `StartObject` (nebo `GetObject`) a `EndObject` rozsahy jako sestup do struktury uzlu XAML, pokud je z hlediska DOM představit strukturu.  
  
<a name="traversing_and_entering_object_nodes"></a>   
## <a name="traversing-and-entering-object-nodes"></a>Procházení a zadáním objektu uzly  
 První uzel v uzlu datového proudu při otevření čtečkou XAML je objekt počáteční uzel kořenový objekt. Podle definice tento objekt je vždy jeden objekt uzel a nemá žádné partnerské publikace. V příkladu XAML žádné skutečné kořenový objekt je definován tak, aby měl jeden nebo více vlastností, které mají více objektů a tyto vlastnosti obsahovat člen uzly. Uzly člen pak máte jeden nebo více uzlů objektu, nebo může také ukončit v uzlu s hodnotou, se místo toho. Kořenový objekt obvykle definuje namescopes XAML, které jsou přiřazeny syntakticky jako atributy v text kód XAML ale mapování na `Namescope` typ uzlu v reprezentace datový proud uzlu XAML.  
  
 Prohlédněte si následující příklad XAML (to je libovolný XAML, není založenou na existující typy v rozhraní .NET Framework). Předpokládáme, že v tomto modelu objektu `FavorCollection` je `List<T>` z `Favor`, `Balloon` a `NoiseMaker` jsou přiřaditelný k `Favor`, `Balloon.Color` vlastnost je zálohovaný díky `Color` objekt podobná jak definuje WPF barvy jako názvy známé barev a `Color` podporuje převaděče typu atributu syntaxe.  
  
|Kód jazyka XAML|Výsledný datový proud uzlu XAML|  
|-----------------|--------------------------------|  
|`<Party`|`Namespace` uzel pro `Party`|  
|`xmlns="PartyXamlNamespace">`|`StartObject` uzel pro `Party`|  
|`<Party.Favors>`|`StartMember` uzel pro `Party.Favors`|  
||`StartObject` uzel pro implicitní `FavorCollection`|  
||`StartMember` uzel pro implicitní `FavorCollection` položky vlastnost.|  
|`<Balloon`|`StartObject` uzel pro `Balloon`|  
|`Color="Red"`|`StartMember` uzel pro `Color`<br /><br /> `Value` uzel pro řetězec hodnotu atributu `"Red"`<br /><br /> `EndMember` Pro `Color`|  
|`HasHelium="True"`|`StartMember` uzel pro `HasHelium`<br /><br /> `Value` uzel pro řetězec hodnotu atributu `"True"`<br /><br /> `EndMember` Pro `HasHelium`|  
|`>`|`EndObject` Pro `Balloon`|  
|`<NoiseMaker>Loudest</NoiseMaker>`|`StartObject` uzel pro `NoiseMaker`<br /><br /> `StartMember` uzel pro `_Initialization`<br /><br /> `Value` uzel pro hodnotu inicializačního řetězce `"Loudest"`<br /><br /> `EndMember` uzel pro `_Initialization`<br /><br /> `EndObject` Pro `NoiseMaker`|  
||`EndMember` uzel pro implicitní `FavorCollection` položky vlastnost.|  
||`EndObject` uzel pro implicitní `FavorCollection`|  
|`</Party.Favors>`|`EndMember` Pro `Favors`|  
|`</Party>`|`EndObject` Pro `Party`|  
  
 V datový proud uzlu XAML můžete spoléhat na následující chování:  
  
-   Pokud `Namespace` uzel existuje, přidá se do datového proudu bezprostředně před `StartObject` který deklarovaný oboru názvů jazyka XAML s `xmlns`. Podívejte se na předchozí tabulce s proud uzlu XAML a příklad znovu. Všimněte si jak `StartObject` a `Namespace` uzly se zdá, že se přehození a jejich deklarace pozice v textu značek. To je typický chování, kde uzly oboru názvů se vždy zobrazí před uzlu se vztahují na v datovém proudu uzlu. Účelem tohoto návrhu je, že informace oboru názvů je životně důležité objekt zapisovače a musí být známo před zapisovače objektu se pokusí provést typ mapování nebo jinak zpracování objektu. Umístění informací oboru názvů jazyka XAML před jeho oboru aplikace v datovém proudu usnadňuje vždy datový proud uzlu v jeho vidění pořadí zpracování.  
  
-   Z důvodu výše faktor je jeden nebo více `Namespace` uzlů, které si přečíst nejprve ve většině případů reálného značek při procházení uzly od začátku, není `StartObject` kořenu.  
  
-   A `StartObject` uzlu může následovat `StartMember`, `Value`, nebo okamžité `EndObject`. Nikdy následuje okamžitě jiné `StartObject`.  
  
-   A `StartMember` může následovat `StartObject`, `Value`, nebo okamžité `EndMember`. Můžete následuje `GetObject`, pro členy, kde hodnota by měla pocházet z existující hodnoty nadřazeného objektu, ne `StartObject` , by vytvořit instanci novou hodnotu. Můžete také provést pomocí `Namespace` uzlu, která se vztahuje na nadcházející `StartObject`. Nikdy následuje okamžitě jiné `StartMember`.  
  
-   A `Value` vlastní hodnota představuje uzel; neexistuje žádná hodnota "EndValue". Ho může následovat pouze `EndMember`.  
  
    -   Text XAML inicializace objektu jako může být používán konstrukce nevede strukturu hodnota objektu. Místo toho uzlem vyhrazené člena pro člena s názvem `_Initialization` je vytvořena. a tento uzel člen obsahuje hodnotu inicializačního řetězce. Pokud existuje, `_Initialization` je vždy první `StartMember`. `_Initialization` může být kvalifikovaný v některé reprezentace služby XAML s namescope XAML jazyka XAML, o vysvětlení, že `_Initialization` se nenachází ve vlastnosti definované v zálohování typy.  
  
    -   Hodnota člena kombinaci představuje nastavení atributu hodnoty. Nakonec pravděpodobně převaděč hodnoty účastnící se zpracování tato hodnota a hodnota je prostý řetězec. Ale, který není vyhodnocují až zpracuje tento datový proud uzlu XAML objekt zapisovač. Objekt zapisovače XAML má nezbytné kontext schématu XAML, mapování typu systému a další podporu potřebné pro převody hodnot.  
  
-   `EndMember` Uzlu může následovat `StartMember` uzel pro následné člena, nebo podle `EndObject` uzel vlastníka člen.  
  
-   `EndObject` Uzlu může následovat `EndMember` uzlu. Můžete také provést pomocí `StartObject` uzel pro případy, kdy objekty partnerské uzly v položky kolekce. Nebo můžete následované `Namespace` uzlu, která se vztahuje na nadcházející `StartObject`.  
  
    -   Pro jedinečný případ uzavření datový proud celého uzlu `EndObject` z kořenové nenásleduje nic; čtečka je nyní end souboru, a <xref:System.Xaml.XamlReader.Read%2A> vrátí `false`.  
  
<a name="value_converters_and_the_xaml_node_stream"></a>   
## <a name="value-converters-and-the-xaml-node-stream"></a>Převodníky hodnot a datový proud uzlu XAML  
 Převaděč hodnoty je obecný termín pro rozšíření značek, převaděče typu (včetně hodnota serializátorů) nebo jiné vyhrazené třídy, která je uvedená jako převaděč hodnoty prostřednictvím systému typ XAML. Datový proud uzlu XAML použití převaděče typu a použití rozšíření značek mít velmi různé reprezentace.  
  
### <a name="type-converters-in-the-xaml-node-stream"></a>Převaděče typů v datový proud uzlu XAML  
 Atribut nastavit, že server má za následek použití převaděče typu hlášení v datový proud uzlu XAML jako hodnotu člena. Datový proud uzlu XAML nebude pokoušet vytvořit objekt typ převaděče instance a předat hodnotu. Pomocí převaděče typů převod implementace vyžaduje vyvolání kontext schématu XAML a použití pro mapování typů. Kontext schématu XAML i určení, které třídy převaděč typ měli používá ke zpracování hodnota vyžaduje nepřímo. Pokud použijete výchozí kontext schématu XAML, tyto informace jsou dostupné z systém typů XAML. Pokud potřebujete informace o převaděč – třída typu na úrovni datový proud uzlu XAML před připojení k zapisovač XAML, můžete získat z <xref:System.Xaml.XamlMember> informace člena nastaveno. Ale, jinak hodnota vstup převaděče typu by měl být zachovaná v datový proud uzlu XAML jako hodnotu prostý, dokud zbývající operací, které vyžadují systém mapování typů a kontext schématu XAML se provádí, například vytvoření objektu podle XAML objekt zapisovače.  
  
 Zvažte například následující osnova – třída definice a použití XAML pro ni:  
  
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
  
 Reprezentace textu datový proud uzlu XAML pro toto použití může být vyjádřený jako následující:  
  
 `StartObject` s <xref:System.Xaml.XamlType> představující `GameBoard`  
  
 `StartMember` s <xref:System.Xaml.XamlMember> představující `BoardSize`  
  
 `Value` uzel textovým řetězcem "`8x8`"  
  
 `EndMember` Odpovídá `BoardSize`  
  
 `EndObject` Odpovídá `GameBoard`  
  
 Všimněte si tento datový proud uzlu je žádná instance typ převaděče. Ale můžete získat informace o typu převaděč voláním <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> na <xref:System.Xaml.XamlMember> pro `BoardSize`. Pokud máte platný kontext schématu XAML, můžete také vyvolat metodu převaděč získáním instance z <xref:System.Xaml.Schema.XamlValueConverter%601.ConverterInstance%2A>.  
  
### <a name="markup-extensions-in-the-xaml-node-stream"></a>Rozšíření značek v datový proud uzlu XAML  
 Použití rozšíření značek je uvedená v datový proud uzlu XAML jako uzel k objektu v rámci člena, kde objekt představuje instanci rozšíření značek. Proto použití rozšíření značek jsou poskytovány více explicitně reprezentace datový proud uzlu než použití převaděče typu je a představuje další informace. <xref:System.Xaml.XamlMember> informace nelze slyšeli, že jste nic o rozšíření značek, protože využití je situational a liší se v každém případě možné značek; není vyhrazené a implicitní na typ nebo člen stejně jako v případě pomocí převaděče typu.  
  
 Reprezentace datový proud uzlu Rozšíření značek jako uzly objekt je v případě i v případě použití rozšíření značek byl proveden v podobě atributu v text kód XAML (což je často případ). Použití rozšíření značek, které používají element formuláře explicitní objekt jsou zpracovány stejným způsobem.  
  
 V rámci uzlu objektu rozšíření značek může být členy této – rozšíření značek. Reprezentace datový proud uzlu XAML zachovává použití tohoto – rozšíření značek, zda který být poziční parametr využití nebo použití s explicitní pojmenované parametry.  
  
 Pro použití poziční parametr datový proud uzlu XAML obsahuje vlastnost definované jazyka XAML `_PositionalParameters` který zaznamenává využití. Tato vlastnost je obecný <xref:System.Collections.Generic.List%601> s <xref:System.Object> omezení. Omezení je objekt a není řetězec, protože opačném případě využití poziční parametru může obsahovat vnořené značek použití rozšíření v něm. K poziční parametry z použití může iteraci v rámci seznamu a používat indexery pro jednotlivé seznamu hodnot.  
  
 Pro použití s názvem parametru představuje všechny pojmenované parametry uzlu člen s tímto názvem v datovém proudu uzlu. Hodnoty členů, nemusí nutně být řetězce, protože může být použití rozšíření vnořené značek.  
  
 `ProvideValue` ještě není volá rozšíření se z kódu. Nicméně je volána, pokud připojíte XAML čtení a zápis XAML tak, aby `WriteEndObject` je volána v uzlu Rozšíření značek, když jej prozkoumat v datovém proudu uzlu. Z tohoto důvodu musíte obecně stejné XAML schématu kontext k dispozici, jako by se dají použít k formuláři grafu objektů v cestě zatížení. V opačném `ProvideValue` z všechny značky, rozšíření můžete vyvolat výjimky tady, protože nemá očekávaný služby, které jsou k dispozici.  
  
<a name="xaml_and_xml_languagedefined_members_in_the_xaml_node_stream"></a>   
## <a name="xaml-and-xml-language-defined-members-in-the-xaml-node-stream"></a>XAML a XML jazyk definovat členy v datový proud uzlu XAML  
 Některé členy vydávají na datový proud uzlu XAML z důvodu interpretace a konvence čtečku XAML místo prostřednictvím explicitního <xref:System.Xaml.XamlMember> lookup nebo konstrukce. Direktivy jazyka XAML jsou často členy. V některých případech je v rámci čtení XAML, který představuje direktivu do datový proud uzlu XAML. Jinými slovy, zadejte původní XAML text nebyla explicitně zadat direktivu člena, ale čtečky XAML vloží – direktiva splníte strukturální XAML názvů a sestavu informací o v datový proud uzlu XAML předtím, než dojde ke ztrátě těchto informací.  
  
 Následující seznam uvádí všechny případů, kde je očekávána čtečku XAML zavádět direktivy člen uzlu XAML a jak se tento uzel člen identifikovat v rozhraní .NET Framework XAML Services implementace.  
  
-   **Inicializace text pro uzel k objektu:** je název tohoto uzlu člen `_Initialization`, představuje direktivu XAML a je definován v oboru názvů jazyka XAML jazyka XAML. Můžete získat statické entity pro z <xref:System.Xaml.XamlLanguage.Initialization%2A>.  
  
-   **Poziční parametry pro rozšíření značek:** je název tohoto uzlu člen `_PositionalParameters`, a je definován v oboru názvů jazyka XAML jazyka XAML. Vždy obsahuje obecné seznam objektů, z nichž každý je poziční parametr předem oddělených rozdělení na `,` oddělovací znak dodávaný ve vstupu XAML. Můžete získat statické entity pro poziční parametry direktiva z <xref:System.Xaml.XamlLanguage.PositionalParameters%2A>.  
  
-   **Neznámý obsah:** je název tohoto uzlu člen `_UnknownContent`. Přesněji řečeno, je <xref:System.Xaml.XamlDirective>, a je definován v oboru názvů jazyka XAML jazyka XAML. Tato direktiva slouží jako sentinel pro případy, kdy element XAML objektu s obsahem ve zdroji XAML, ale žádná vlastnost obsahu lze určit podle aktuálně dostupné kontext schématu XAML. Tento případ můžete zjistit v datový proud uzlu XAML kontrolou pro členy s názvem `_UnknownContent`. Pokud nebyla provedena žádná další akce v zatížení cesta datový proud uzlu XAML, výchozí <xref:System.Xaml.XamlObjectWriter> vyvolá pokus o `WriteEndObject` když narazí `_UnknownContent` člen libovolného objektu. Výchozí hodnota <xref:System.Xaml.XamlXmlWriter> nevyvolá výjimku a považuje za implicitní člena. Můžete získat statické entity pro `_UnknownContent` z <xref:System.Xaml.XamlLanguage.UnknownContent%2A>.  
  
-   **Vlastnost kolekce kolekce:** i když má základní typ CLR kolekce třídu, která se obvykle používá pro jazyk XAML vyhrazené s názvem vlastnosti, která obsahuje položky kolekce, systém typů XAML před zálohování typu nezná tuto vlastnost rozlišení. Místo toho datový proud uzlu XAML zavádí `Items` zástupný text jako člena kolekce typ jazyka XAML. Implementace rozhraní .NET Framework XAML Services název tato direktiva je člen v datovém proudu uzlu `_Items`. Konstanty pro tato direktiva můžete získat z <xref:System.Xaml.XamlLanguage.Items%2A>.  
  
     Všimněte si, že datový proud uzlu XAML může obsahovat ve vlastnosti položky s položkami, které není budou parseable na základě typu řešení zálohování a kontext schématu XAML. Například  
  
-   **XML definované členy:** definované XML `xml:base`, `xml:lang` a `xml:space` členové jsou oznamovány klientu jako direktivy jazyka XAML s názvem `base`, `lang`, a `space` v rozhraní .NET Framework XAML Services implementace. Obor názvů XML je obor názvů pro tyto `http://www.w3.org/XML/1998/namespace`. Konstanty pro každou z nich můžete získat z <xref:System.Xaml.XamlLanguage>.  
  
## <a name="node-order"></a>Uzel pořadí  
 V některých případech <xref:System.Xaml.XamlXmlReader> změny pořadí uzlů XAML v datový proud uzlu XAML, a pořadí uzly zobrazí, pokud zobrazit do kódu nebo pokud zpracovat jako XML. Probíhá proto, aby bylo možné pořadí uzlů tak, aby <xref:System.Xaml.XamlObjectWriter> může zpracovat datový proud uzlu dopředné způsobem.  V rozhraní .NET Framework XAML Services čtečka XAML změní uzly místo opuštění této úlohy do zapisovače XAML jako optimalizace výkonu pro XAML objekt zapisovače příjemci datový proud uzlu.  
  
 Některé direktivy jsou určeny konkrétně k poskytují další informace pro vytvoření objektu z objektu elementu. Jsou tyto direktivy: `Initialization`, `PositionalParameters`, `TypeArguments`, `FactoryMethod`, `Arguments`. Rozhraní .NET Framework XAML Services XAML čtečky pokusí umístit tyto direktivy jako první členy v datovém proudu uzlu následující objektu `StartObject`, z důvodů, které jsou vysvětlené v další části.  
  
### <a name="xamlobjectwriter-behavior-and-node-order"></a>Chování XamlObjectWriter a pořadí uzlu  
 `StartObject` k <xref:System.Xaml.XamlObjectWriter> není nutně signálu do zapisovače objektu XAML můžete okamžitě vytvořit instanci objektu. XAML zahrnuje několik funkcí jazyka, které umožňují možné inicializovat objekt s další vstup a nespoléhala se zcela na vyvolání výchozí konstruktor k vytvoření počáteční objektu a teprve potom vlastnosti nastavení. Tyto funkce patří: <xref:System.Windows.Markup.XamlDeferLoadAttribute>; inicializace textu. [x: TypeArguments –](../../../docs/framework/xaml-services/x-typearguments-directive.md); poziční parametry rozšíření značek; metodami pro vytváření a přidružených [x: Arguments](../../../docs/framework/xaml-services/x-arguments-directive.md) uzly (XAML 2009). Jednotlivých případech zpoždění konstrukce vlastním objektu a protože je datový proud uzlu přeuspořádány, zapisovače objektu XAML můžete spoléhá na chování vždy, když je členem počáteční došlo ve skutečnosti vytváření instance, které nejsou konkrétně konstrukce směrnice pro tento typ objektu.  
  
### <a name="getobject"></a>Funkce GetObject  
 `GetObject` představuje uzel XAML kde místo vytváření nového objektu, zapisovač XAML objektu by měla místo toho získat hodnotu obsahující vlastnosti objektu. Obvyklý případ kde `GetObject` zjistil se uzel v uzlu XAML datový proud je pro objekt kolekce nebo objekt slovníku, pokud je vlastnost obsahující úmyslně jen pro čtení v základní typ objektu modelu. V tomto scénáři kolekce nebo slovník často je vytvořen a inicializován (obvykle prázdné) logikou inicializace vlastnícím typu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xaml.XamlObjectReader>  
 [XAML Services](../../../docs/framework/xaml-services/index.md)  
 [Obory názvů jazyka XAML](../../../docs/framework/xaml-services/xaml-namespaces-for-net-framework-xaml-services.md)
