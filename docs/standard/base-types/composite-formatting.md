---
title: "Složené formátování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parameter specifiers
- strings [.NET Framework], alignment
- format specifiers, composite formatting
- strings [.NET Framework], composite
- composite formatting
- objects [.NET Framework], formatting multiple objects
ms.assetid: 87b7d528-73f6-43c6-b71a-f23043039a49
caps.latest.revision: "36"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: dae73a7ace3aac4e7d89ccba186fceacfe9898ae
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="composite-formatting"></a>Složené formátování
Funkce složeného formátování v rozhraní .NET Framework přebírá seznam objektů a složený řetězec formátu jako vstup. Složený řetězec formátu se skládá z pevného textu smíšeného s indexovanými zástupnými symboly nazvanými „položky formátu“, které odpovídají objektům v seznamu. Výsledkem operace formátování je výsledný řetězec, který se skládá z původního pevného textu smíšeného s řetězcovou reprezentací objektů v seznamu.  
  
 Funkce složeného formátování je podporována například následujícími metodami:  
  
-   <xref:System.String.Format%2A?displayProperty=nameWithType>, která vrací řetězec formátovaný výsledek.  
  
-   <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, který připojí řetězec formátovaný výsledek tak, aby <xref:System.Text.StringBuilder> objektu.  
  
-   Některé přetížení <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> metodu, která zobrazí řetězec formátovaný výsledek do konzoly.  
  
-   Některé přetížení <xref:System.IO.TextWriter.WriteLine%2A?displayProperty=nameWithType> metodu, která řetězec formátovaný výsledek zápisu do datového proudu nebo souboru. Třídy odvozené od <xref:System.IO.TextWriter>, jako například <xref:System.IO.StreamWriter> a <xref:System.Web.UI.HtmlTextWriter>, také sdílet tuto funkci.  
  
-   <xref:System.Diagnostics.Debug.WriteLine%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, který výstupy formátovaná zpráva k trasování – moduly naslouchání.  
  
-   <xref:System.Diagnostics.Trace.TraceError%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, A <xref:System.Diagnostics.Trace.TraceWarning%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metody, které výstup naformátovaný zpráv trasování – moduly naslouchání.  
  
-   <xref:System.Diagnostics.TraceSource.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> Metoda, který zapíše informační metoda trasování – moduly naslouchání.  
  
## <a name="composite-format-string"></a>Složený řetězec formátu  
 Složený řetězec formátu a seznam objektů se používají jako argumenty metod, které podporují funkci složeného formátování. Složený řetězec formátu se skládá z žádného výskytu nebo několika výskytů pevného textu smíšeného s jednou nebo několika položkami formátu. Pevný text je jakýkoli řetězec, který si zvolíte, a jednotlivé položky formátu odpovídají objektu nebo ohraničené struktuře v seznamu. Funkce složeného formátování vrátí nový výsledný řetězec, kde každá položka formátu je nahrazena řetězcovou reprezentací odpovídajícího objektu v seznamu.  
  
 Vezměte v úvahu následující <xref:System.String.Format%2A> fragment kódu.  
  
 [!code-csharp[Formatting.Composite#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#1)]
 [!code-vb[Formatting.Composite#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#1)]  
  
 Pevný text je "`Name =` "a"`, hours =` ". Položky formátu jsou "`{0}`", jejíž index je 0, což odpovídá objektu `name`, a "`{1:hh}`", jejíž index je 1, která odpovídá objektu `DateTime.Now`.  
  
## <a name="format-item-syntax"></a>Syntaxe položky formátu  
 Jednotlivé položky formátu mají následující podobu a skládají se z následujících součástí:  
  
 `{`*index*[`,`*zarovnání*] [`:`*formatString*]`}`  
  
 Jsou požadovány odpovídající složené závorky ("{" a "}").  
  
### <a name="index-component"></a>Součást Index  
 Povinné *index* součást, také nazývaná specifikátor parametru, je číslo od 0, který identifikuje odpovídající položku v seznamu objektů. To znamená, že položka formátu, jejíž specifikátor parametru je 0, formátuje první objekt v seznamu, položka formátu, jejíž specifikátor parametru je 1, formátuje druhý objekt v seznamu atd. Následující příklad obsahuje čtyři specifikátory parametrů, číslované nula prostřednictvím tři, představují prvočísel méně než 10:  
  
 [!code-csharp[Formatting.Composite#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#7)]
 [!code-vb[Formatting.Composite#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#7)]  
  
 Více položek formátu může odkazovat na stejný prvek v seznamu objektů zadáním stejného specifikátoru parametru. Například můžete zadáním složený formátovací řetězec formátu stejnou číselnou hodnotu ve formátu hexadecimální, vědecké a číslo: "0 x {0: x} {0:E} {0: n}", jak ukazuje následující příklad.  
  
 [!code-csharp[Formatting.Composite#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#10)]
 [!code-vb[Formatting.Composite#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#10)]  
  
 Každá položka formátu může odkazovat na libovolný objekt v seznamu. Například pokud existují tři objekty, lze formátovat druhý, první a třetí objekt zadáním složeného řetězce formátu tímto způsobem: "{1} {0} {2}". Objekt, který není odkazován položkou formátu, je ignorován. A <xref:System.FormatException> je vyvolána za běhu, pokud specifikátor parametru označí položku mimo hranice seznamu objektů.  
  
### <a name="alignment-component"></a>Součást Zarovnání  
 Volitelné *zarovnání* součást je znaménkem udávající šířku pole upřednostňovaného formátu. Pokud hodnota *zarovnání* je menší než délka formátovaný řetězec *zarovnání* je ignorován a délka formátovaný řetězec se používá jako šířka pole. Formátovaná data v poli je zarovnaný doprava pokud *zarovnání* kladné a v případě zarovnaný doleva *zarovnání* záporné. Pokud je vyžadováno odsazení obsahu, jsou použity prázdné znaky. Čárkou je povinný, pokud *zarovnání* je zadán.  
  
 V následujícím příkladu definuje dvě pole, jeden obsahující názvy zaměstnanci a dalších obsahující hodiny, které šlo během dvou týdnů. Složený formátovací řetězec vlevo zarovná názvy v poli 20 znaků a právo-jejich čas v poli 5 znaků. Všimněte si, že standardní formátovací řetězec "N1" také použitá k formátování v hodinách, s desetinnou jednu číslici.  
  
 [!code-csharp[Formatting.Composite#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/alignment1.cs#8)]
 [!code-vb[Formatting.Composite#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/alignment1.vb#8)]  
  
### <a name="format-string-component"></a>Součást Řetězec formátu  
 Volitelné *formatString* součást je řetězec formátu, který je vhodný pro typ objektu, který je formátován. Zadejte řetězec standardními nebo vlastními číselného formátu Pokud číselnou hodnotu, odpovídající objekt standardní nebo vlastní formátu data a času řetězec Pokud odpovídající objekt <xref:System.DateTime> objekt, nebo [řetězec formátu výčtu](../../../docs/standard/base-types/enumeration-format-strings.md)Pokud odpovídající objekt hodnotou výčtu. Pokud *formatString* není zadán, se používá obecné ("") specifikátor formátu pro typ číselnou hodnotu, datum a čas nebo výčet. Dvojtečka je nutný, pokud *formatString* je zadán.  
  
 Následující tabulka uvádí seznam typů nebo kategorií typů v knihovně tříd rozhraní .NET Framework, které podporují předdefinovanou množinu řetězců formátu, a obsahuje odkazy na témata, která poskytují seznam jednotlivých řetězců formátu. Formátování řetězců poskytuje rozšířitelný mechanismus, který umožňuje definovat nové řetězce formátu pro všechny existující typy a také definovat množinu řetězců formátu podporovaných typem definovaného aplikací. Další informace najdete v tématu <xref:System.IFormattable> a <xref:System.ICustomFormatter> rozhraní témata.  
  
|Typ nebo kategorie typů|Další informace naleznete v tématu|  
|---------------------------|---------|  
|Typy data a času (<xref:System.DateTime>, <xref:System.DateTimeOffset>)|[Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)<br /><br /> [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|  
|Výčtové typy (všechny typy odvozené od <xref:System.Enum?displayProperty=nameWithType>)|[Výčet řetězců formátu](../../../docs/standard/base-types/enumeration-format-strings.md)|  
|Číselnými typy (<xref:System.Numerics.BigInteger>, <xref:System.Byte>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>)|[Standardní řetězce číselného formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md)<br /><br /> [Vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md)|  
|<xref:System.Guid>|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.TimeSpan>|[Standardní řetězce formátu TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)<br /><br /> [Vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|  
  
### <a name="escaping-braces"></a>Řídicí znaky pro složené závorky  
 Levá a pravá složená závorka se interpretuje jako počátek a konec položky formátu. V důsledku toho je nutné použít sekvenci řídicích znaků pro zobrazení literální levé a pravé složené závorky. Chcete-li zobrazit jednu levou složenou závorku ("{"), zadejte dvě levé složené závorky ("{{"); chcete-li zobrazit jednu pravou složenou závorku ("}"), zadejte dvě pravé závorky ("}}"). Složené závorky v položce formátu jsou interpretovány postupně v pořadí, v jakém se vyskytují. Interpretace vnořených složených závorek není podporována.  
  
 Způsob, jakým jsou interpretovány složené závorky vložené pomocí řídicích znaků, může vést k neočekávaným výsledkům. Předpokládejte například položku formátu {{{0:D}}}, která je určena k zobrazování levé složené závorky, číselnou hodnotu formátovanou jako desítkové číslo a pravou složenou závorku. Položka formátu je však ve skutečnosti interpretována následujícím způsobem:  
  
1.  První dvě levé složené závorky ("{{") jsou tvořeny řídicími znaky, a proto je výsledkem jedna levá závorka.  
  
2.  Následující tři znaky ("{0:") jsou interpretovány jako začátek položky formátu.  
  
3.  Další znak ("D") je interpretován jako specifikátor standardního číselného desítkového formátu, ale další dvě závorky uvozené řídicími znaky ("}}") tvoří ve výsledku jednu složenou závorku. Vzhledem k tomu, že výsledný řetězec ("D}") není specifikátorem standardního číselného formátu, je výsledný řetězec interpretován jako řetězec vlastního formátu, což znamená, že se zobrazí řetězcový literál "D}".  
  
4.  Poslední složená závorka ("}") je interpretována jako konec položky formátu.  
  
5.  Konečný výsledek, který se zobrazí, je řetězcový literál "{D}". Číselná hodnota, která měla být formátována, se nezobrazí.  
  
 Jedním ze způsobů, jak napsat kód tak, aby nedocházelo k chybné interpretaci složených závorek s řídicími znaky, je provést formátování složených závorek a položek formátu odděleně. To znamená, že se v první operaci formátování zobrazí literální znak levé složené závorky, v další operaci se zobrazí výsledek položky formátu a nakonec se v poslední operaci zobrazí literální znak pravé složené závorky. Tento postup znázorňuje následující příklad.  
  
 [!code-csharp[Formatting.Composite#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Escaping1.cs#2)]
 [!code-vb[Formatting.Composite#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Escaping1.vb#2)]  
  
### <a name="processing-order"></a>Pořadí zpracování  
 Pokud volání složené formátování metoda obsahuje <xref:System.IFormatProvider> argument jehož hodnota není `null`, volání modulu runtime jeho <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metodu pro žádosti o <xref:System.ICustomFormatter> implementace. Pokud je metoda moct vrátit <xref:System.ICustomFormatter> implementace, se uloží do mezipaměti pro pozdější použití.  
  
 Jednotlivé hodnoty v seznamu parametrů, které odpovídají položce formátu, jsou převedeny na řetězec podle následujícího postupu. Pokud je splněna některá z podmínek v prvních třech krocích, je v tomto kroku vrácena řetězcová reprezentace hodnoty a následné kroky již nejsou provedeny.  
  
1.  Pokud je hodnota, která má být ve formátu `null`, prázdný řetězec ("") je vrácen.  
  
2.  Pokud <xref:System.ICustomFormatter> implementace je k dispozici, volání modulu runtime jeho <xref:System.ICustomFormatter.Format%2A> metoda. Předává metodu položce formátu *formatString* hodnotu, pokud je přítomen, nebo `null` Pokud není, spolu s <xref:System.IFormatProvider> implementace.  
  
3.  Pokud hodnota implementuje <xref:System.IFormattable> rozhraní, rozhraní <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29> metoda je volána. Metoda je předána *formatString* hodnotu, pokud je přítomen v položce formátu nebo `null` Pokud není. <xref:System.IFormatProvider> Argument je stanoven následujícím způsobem:  
  
    -   Pro číselnou hodnotu, pokud složeného formátování metoda s jinou hodnotou null <xref:System.IFormatProvider> argument je volána, požadavky modulu runtime <xref:System.Globalization.NumberFormatInfo> objekt z jeho <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metoda. Pokud nelze zadat, pokud je hodnota argumentu `null`, nebo pokud složené formátování metoda nemá <xref:System.IFormatProvider> parametr <xref:System.Globalization.NumberFormatInfo> objektu pro aktuální jazykovou verzi vlákna se používá.  
  
    -   Pro hodnoty data a času, pokud složeného formátování metoda s jinou hodnotou null <xref:System.IFormatProvider> argument je volána, požadavky modulu runtime <xref:System.Globalization.DateTimeFormatInfo> objekt z jeho <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metoda. Pokud nelze zadat, pokud je hodnota argumentu `null`, nebo pokud složené formátování metoda nemá <xref:System.IFormatProvider> parametr <xref:System.Globalization.DateTimeFormatInfo> objektu pro aktuální jazykovou verzi vlákna se používá.  
  
    -   Pro jiné typy, pokud složené formátování volána s objekty <xref:System.IFormatProvider> argument, jeho hodnota (včetně `null`, pokud žádné <xref:System.IFormatProvider> zadaný objekt) je předán přímo na <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> implementace.  V opačném <xref:System.Globalization.CultureInfo> předaný objekt, který představuje aktuální jazykovou verzi vlákna <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> implementace.  
  
4.  Typ elementu bez parametrů `ToString` metoda, která buď přepisuje <xref:System.Object.ToString?displayProperty=nameWithType> nebo dědí chování její základní třída, je volána. V takovém případě řetězec formátu určeného *formatString* součástí položku formátu, pokud je k dispozici, je ignorováno.  
  
 Zarovnání se použije po provedení předchozích kroků.  
  
## <a name="code-examples"></a>Příklady kódu  
 Následující příklad ukazuje jeden řetězec vytvořený pomocí složeného formátování a další vytvořené pomocí objektu `ToString` metoda. Oba typy formátování poskytují stejné výsledky.  
  
 [!code-csharp[Formatting.Composite#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#3)]
 [!code-vb[Formatting.Composite#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#3)]  
  
 Za předpokladu, že aktuální den je čtvrtek v květnu, hodnota oba řetězce v předchozím příkladu je `Thursday May` v USA Jazykové verze Angličtina.  
  
 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>zpřístupňuje stejné funkce jako <xref:System.String.Format%2A?displayProperty=nameWithType>. Jediným rozdílem mezi tyto dvě metody je, že <xref:System.String.Format%2A?displayProperty=nameWithType> vrátí výsledek jako řetězec, při <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> zápisy výsledek, který má výstupní datový proud přidružený <xref:System.Console> objektu. Následující příklad používá <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> metoda k formátování hodnotu `MyInt` na hodnotu měny.  
  
 [!code-csharp[Formatting.Composite#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#4)]
 [!code-vb[Formatting.Composite#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#4)]  
  
 Následující příklad znázorňuje formátování většího počtu objektů, včetně formátování jednoho objektu dvěma různými způsoby.  
  
 [!code-csharp[Formatting.Composite#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#5)]
 [!code-vb[Formatting.Composite#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#5)]  
  
 Následující příklad znázorňuje použití zarovnání ve formátování. Argumenty, které jsou formátovány jsou umístěny mezi svislá čára znaků (&#124;) zvýrazněte výsledné zarovnání.  
  
 [!code-csharp[Formatting.Composite#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#6)]
 [!code-vb[Formatting.Composite#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#6)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Console.WriteLine%2A>  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 [Typy formátování](../../../docs/standard/base-types/formatting-types.md)  
 [Standardní řetězce číselného formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md)  
 [Vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
 [Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)  
 [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)  
 [Standardní řetězce formátu TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)  
 [Vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)  
 [Výčet řetězců formátu](../../../docs/standard/base-types/enumeration-format-strings.md)
