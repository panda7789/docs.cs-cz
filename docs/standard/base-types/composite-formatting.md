---
title: Složené formátování
ms.date: 10/26/2018
ms.technology: dotnet-standard
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
ms.openlocfilehash: b1ec8cfc0f8c6e660d716c51bf3c3387b73a278f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400342"
---
# <a name="composite-formatting"></a>Složené formátování

Funkce složeného formátování .NET přebírá jako vstup seznam objektů a složený formátovací řetězec. Složený řetězec formátu se skládá z pevného textu smíšeného s indexovanými zástupnými symboly nazvanými „položky formátu“, které odpovídají objektům v seznamu. Výsledkem operace formátování je výsledný řetězec, který se skládá z původního pevného textu smíšeného s řetězcovou reprezentací objektů v seznamu.  
  
> [!IMPORTANT]
> Místo použití složených formátovacích řetězců můžete použít *interpolované řetězce,* pokud je podporuje jazyková a jazyková verze, kterou používáte. Interpolovaný řetězec je řetězec, který obsahuje *interpolované výrazy*. Každý interpolovaný výraz je vyřešen s hodnotou výrazu a zahrnut do výsledného řetězce při přiřazení řetězce. Další informace naleznete [v tématu String interpolace (C# Reference)](../../csharp/language-reference/tokens/interpolated.md) a [interpolované řetězce (Visual Basic Reference)](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md).

Funkce složeného formátování je podporována například následujícími metodami:  
  
- <xref:System.String.Format%2A?displayProperty=nameWithType>, který vrátí formátovaný výsledný řetězec.  
  
- <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, který připojí formátovaný výsledný <xref:System.Text.StringBuilder> řetězec k objektu.
- Některé přetížení <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> metody, které zobrazují formátovaný výsledný řetězec do konzoly.  
  
- Některé přetížení <xref:System.IO.TextWriter.WriteLine%2A?displayProperty=nameWithType> metody, které zapisují formátovaný výsledný řetězec do datového proudu nebo souboru. Třídy odvozené <xref:System.IO.TextWriter>z <xref:System.IO.StreamWriter> , <xref:System.Web.UI.HtmlTextWriter>například a , také sdílet tuto funkci.  
  
- <xref:System.Diagnostics.Debug.WriteLine%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, který vyvodí formátovanou zprávu pro sledování posluchačů.  
  
- Aplikace <xref:System.Diagnostics.Trace.TraceError%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.TraceWarning%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> a metody, které výstup emitované zprávy pro trasování posluchačů.  
  
- Metoda, <xref:System.Diagnostics.TraceSource.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> která zapisuje informační metodu pro sledování posluchačů.  
  
## <a name="composite-format-string"></a>Složený řetězec formátu  
 Složený řetězec formátu a seznam objektů se používají jako argumenty metod, které podporují funkci složeného formátování. Složený řetězec formátu se skládá z žádného výskytu nebo několika výskytů pevného textu smíšeného s jednou nebo několika položkami formátu. Pevný text je jakýkoli řetězec, který si zvolíte, a jednotlivé položky formátu odpovídají objektu nebo ohraničené struktuře v seznamu. Funkce složeného formátování vrátí nový výsledný řetězec, kde každá položka formátu je nahrazena řetězcovou reprezentací odpovídajícího objektu v seznamu.  
  
 Zvažte <xref:System.String.Format%2A> následující fragment kódu.  
  
 [!code-csharp[Formatting.Composite#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#1)]
 [!code-vb[Formatting.Composite#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#1)]  
  
 Pevný text je`Name =` "`, hours =` " a " ". Položky formátu`{0}`jsou " ", jejichž index je `name`0,`{1:hh}`který odpovídá objektu , a " `DateTime.Now`", jehož index je 1, který odpovídá objektu .  
  
## <a name="format-item-syntax"></a>Syntaxe položky formátu  
 Jednotlivé položky formátu mají následující podobu a skládají se z následujících součástí:  
  
 `{`*index*`,`[*zarovnání*][`:`*formatString*]`}`  
  
 Jsou požadovány odpovídající složené závorky ("{" a "}").  
  
### <a name="index-component"></a>Součást Index  
 Povinná komponenta *indexu,* také nazývaná specifikátor parametrů, je číslo začínající od 0, které identifikuje odpovídající položku v seznamu objektů. To znamená, že položka formátu, jejíž specifikátor parametru je 0, formátuje první objekt v seznamu, položka formátu, jejíž specifikátor parametru je 1, formátuje druhý objekt v seznamu atd. Následující příklad obsahuje čtyři specifikátory parametrů s číslem od nuly do tří, které představují prvočísla menší než deset:  
  
 [!code-csharp[Formatting.Composite#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#7)]
 [!code-vb[Formatting.Composite#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#7)]  
  
 Více položek formátu může odkazovat na stejný prvek v seznamu objektů zadáním stejného specifikátoru parametru. Můžete například formátovat stejnou číselnou hodnotu v šestnáctkovém, vědeckém a číselném formátu zadáním{0:X} {0:E} {0:N}složeného formátovacího řetězce, například : "0x ", jak ukazuje následující příklad.  
  
 [!code-csharp[Formatting.Composite#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#10)]
 [!code-vb[Formatting.Composite#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#10)]  
  
 Každá položka formátu může odkazovat na libovolný objekt v seznamu. Pokud například existují tři objekty, můžete naformátovat druhý, první a třetí objekt zadáním složeného formátovacího řetězce takto: "{1} {0} {2}". Objekt, který není odkazován položkou formátu, je ignorován. A <xref:System.FormatException> je vyvolána za běhu, pokud specifikátor parametru označuje položku mimo hranice seznamu objektů.  
  
### <a name="alignment-component"></a>Součást Zarovnání  
 Volitelná součást *zarovnání* je celé číslo podepsané, které označuje upřednostňovanou šířku formátovaného pole. Pokud je hodnota *zarovnání* menší než délka formátovaného řetězce, *zarovnání* se ignoruje a jako šířka pole se použije délka formátovaného řetězce. Formátovaná data v poli jsou zarovnána doprava, pokud je *zarovnání* kladné, a zarovnáno doleva, pokud je *zarovnání záporné.* Pokud je vyžadováno odsazení obsahu, jsou použity prázdné znaky. Čárka je vyžadována, pokud je *zadáno zarovnání.*  
  
 Následující příklad definuje dvě pole, jedno obsahující jména zaměstnanců a druhé obsahující hodiny, které pracovali během dvou týdnů. Složený formátovací řetězec zarovná názvy v poli o 20 znacích a zarovná jejich hodiny v pětiznakovém poli doprava. Všimněte si, že standardní formátovací řetězec "N1" se také používá k formátování hodin jednou zlomkovou číslicí.  
  
 [!code-csharp[Formatting.Composite#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/alignment1.cs#8)]
 [!code-vb[Formatting.Composite#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/alignment1.vb#8)]  
  
### <a name="format-string-component"></a>Součást Řetězec formátu  
 Volitelná komponenta *formatString* je formátovací řetězec, který je vhodný pro formátovaný typ objektu. Zadejte standardní nebo vlastní číselný formátovací řetězec, pokud je odpovídající objekt číselnou hodnotou, <xref:System.DateTime> standardním nebo vlastním formátovacím řetězcem data a času, pokud je odpovídající objekt objektem, nebo [řetězec formátu výčtu,](../../../docs/standard/base-types/enumeration-format-strings.md) pokud je odpovídající objekt hodnotou výčtu. Pokud *formatString* není zadán, obecné ("G") specifikátor formátu pro číselný, datum a čas nebo typ výčtu se používá. Dvojtečka je vyžadována, pokud *formatString* je zadán.  
  
 Následující tabulka uvádí seznam typů nebo kategorií typů v knihovně tříd rozhraní .NET Framework, které podporují předdefinovanou množinu řetězců formátu, a obsahuje odkazy na témata, která poskytují seznam jednotlivých řetězců formátu. Formátování řetězců poskytuje rozšířitelný mechanismus, který umožňuje definovat nové řetězce formátu pro všechny existující typy a také definovat množinu řetězců formátu podporovaných typem definovaného aplikací. Další informace naleznete <xref:System.IFormattable> v <xref:System.ICustomFormatter> tématech a rozhraní.  
  
|Typ nebo kategorie typů|Seznamte se s |  
|---------------------------|---------|  
|Typy a časové kategorie (<xref:System.DateTime>, <xref:System.DateTimeOffset>)|[Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)<br /><br /> [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|  
|Typy výčtu (všechny typy <xref:System.Enum?displayProperty=nameWithType>odvozené z )|[Výčet řetězců formátu](../../../docs/standard/base-types/enumeration-format-strings.md)|  
|Číselné<xref:System.Numerics.BigInteger>typy <xref:System.Byte> <xref:System.Decimal>( <xref:System.Double> <xref:System.Int16>, <xref:System.Int32> <xref:System.Int64>, <xref:System.SByte> <xref:System.Single>, <xref:System.UInt16> <xref:System.UInt32>, <xref:System.UInt64>, , , , , , )|[Standardní řetězce číselného formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md)<br /><br /> [Vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md)|  
|<xref:System.Guid>|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.TimeSpan>|[Standardní řetězce formátu TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)<br /><br /> [Vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|  
  
### <a name="escaping-braces"></a>Řídicí znaky pro složené závorky  
 Levá a pravá složená závorka se interpretuje jako počátek a konec položky formátu. V důsledku toho je nutné použít sekvenci řídicích znaků pro zobrazení literální levé a pravé složené závorky. Chcete-li zobrazit jednu levou složenou závorku ("{"), zadejte dvě levé složené závorky ("{{"); chcete-li zobrazit jednu pravou složenou závorku ("}"), zadejte dvě pravé závorky ("}}"). Složené závorky v položce formátu jsou interpretovány postupně v pořadí, v jakém se vyskytují. Interpretace vnořených složených závorek není podporována.  
  
 Způsob, jakým jsou interpretovány složené závorky vložené pomocí řídicích znaků, může vést k neočekávaným výsledkům. Zvažte například položku formátu{0:D}{{ }}", která je určena k zobrazení počáteční složená závorka, číselné hodnoty formátované jako desetinné číslo a uzavírací složená závorka. Položka formátu je však ve skutečnosti interpretována následujícím způsobem:  
  
1. První dvě levé složené závorky ("{{") jsou tvořeny řídicími znaky, a proto je výsledkem jedna levá závorka.  
  
2. Následující tři znaky ("{0:") jsou interpretovány jako začátek položky formátu.  
  
3. Další znak ("D") je interpretován jako specifikátor standardního číselného desítkového formátu, ale další dvě závorky uvozené řídicími znaky ("}}") tvoří ve výsledku jednu složenou závorku. Vzhledem k tomu, že výsledný řetězec ("D}") není specifikátorem standardního číselného formátu, je výsledný řetězec interpretován jako řetězec vlastního formátu, což znamená, že se zobrazí řetězcový literál "D}".  
  
4. Poslední složená závorka ("}") je interpretována jako konec položky formátu.  
  
5. Konečný výsledek, který se zobrazí, je řetězcový literál "{D}". Číselná hodnota, která měla být formátována, se nezobrazí.  
  
 Jedním ze způsobů, jak napsat kód tak, aby nedocházelo k chybné interpretaci složených závorek s řídicími znaky, je provést formátování složených závorek a položek formátu odděleně. To znamená, že se v první operaci formátování zobrazí literální znak levé složené závorky, v další operaci se zobrazí výsledek položky formátu a nakonec se v poslední operaci zobrazí literální znak pravé složené závorky. Tento postup znázorňuje následující příklad.  
  
 [!code-csharp[Formatting.Composite#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Escaping1.cs#2)]
 [!code-vb[Formatting.Composite#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Escaping1.vb#2)]  
  
### <a name="processing-order"></a>Pořadí zpracování  
 Pokud volání metody složeného formátování obsahuje <xref:System.IFormatProvider> argument, jehož hodnota není `null` <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> , runtime <xref:System.ICustomFormatter> volá jeho metodu požádat o implementaci. Pokud metoda je schopna <xref:System.ICustomFormatter> vrátit implementaci, je uložena do mezipaměti po dobu trvání volání metody složeného formátování.
  
 Každá hodnota v seznamu parametrů, která odpovídá položce formátu, je převedena na řetězec následujícím způsobem:  
  
1. Pokud je `null`hodnota, která má být <xref:System.String.Empty?displayProperty=nameWithType> formátována , je vrácen prázdný řetězec.  
  
2. Pokud <xref:System.ICustomFormatter> je k dispozici implementace, <xref:System.ICustomFormatter.Format%2A> runtime volá jeho metodu. Předá metodu format item *formatString* hodnotu, pokud `null` je k dispozici, nebo <xref:System.IFormatProvider> pokud není, spolu s implementací. Pokud volání <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> metody vrátí `null`, exekuce pokračuje k dalšímu kroku; v opačném případě <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> je vrácen výsledek volání.
  
3. Pokud hodnota implementuje <xref:System.IFormattable> rozhraní, <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29> je volána metoda rozhraní. Metoda je *předánformatString* hodnotu, pokud je k dispozici `null` v položce formátu, nebo pokud není. Argument <xref:System.IFormatProvider> je určen takto:  
  
    - Pro číselnou hodnotu, pokud je volána metoda <xref:System.IFormatProvider> složeného formátování s argumentem <xref:System.Globalization.NumberFormatInfo> bez <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> null, runtime požaduje objekt z jeho metody. Pokud není schopen zadat jeden, pokud je `null`hodnota argumentu , nebo pokud metoda složenéformátování <xref:System.IFormatProvider> nemá <xref:System.Globalization.NumberFormatInfo> parametr, objekt pro aktuální jazykovou verzi vlákna se používá.  
  
    - Pro hodnotu data a času, pokud je volána <xref:System.IFormatProvider> metoda složeného formátování s argumentem bez null, runtime požaduje <xref:System.Globalization.DateTimeFormatInfo> objekt z jeho <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metody. Pokud není schopen zadat jeden, pokud je `null`hodnota argumentu , nebo pokud metoda složenéformátování <xref:System.IFormatProvider> nemá <xref:System.Globalization.DateTimeFormatInfo> parametr, objekt pro aktuální jazykovou verzi vlákna se používá.  
  
    - Pro objekty jiných typů, pokud je volána <xref:System.IFormatProvider> metoda složeného formátování s <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> argumentem, jeho hodnota je předána přímo do implementace. V `null` opačném případě <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> je předán a implementace.  
  
4. Metoda parametrless `ToString` typu, která přepíše <xref:System.Object.ToString?displayProperty=nameWithType> nebo zdědí chování jeho základní třídy, se nazývá. V tomto případě je ignorován formátovací řetězec určený komponentou *formatString* v položce formátu, pokud je k dispozici.  
  
 Zarovnání se použije po provedení předchozích kroků.  
  
## <a name="code-examples"></a>Příklady kódu  
 Následující příklad ukazuje jeden řetězec vytvořený pomocí složeného formátování a `ToString` jiný vytvořený metodou objektu. Oba typy formátování poskytují stejné výsledky.  
  
 [!code-csharp[Formatting.Composite#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#3)]
 [!code-vb[Formatting.Composite#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#3)]  
  
 Za předpokladu, že aktuální den je čtvrtek v květnu, `Thursday May` hodnota obou řetězců v předchozím příkladu je v jazykové verzi angličtiny v USA.  
  
 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>poskytuje stejné funkce jako <xref:System.String.Format%2A?displayProperty=nameWithType>. Jediný rozdíl mezi těmito <xref:System.String.Format%2A?displayProperty=nameWithType> dvěma metodami je, <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> že vrátí jeho výsledek jako <xref:System.Console> řetězec, zatímco zapíše výsledek do výstupního datového proudu přidruženého k objektu. Následující příklad používá <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> metodu k `MyInt` formátování hodnoty měny.  
  
 [!code-csharp[Formatting.Composite#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#4)]
 [!code-vb[Formatting.Composite#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#4)]  
  
 Následující příklad znázorňuje formátování většího počtu objektů, včetně formátování jednoho objektu dvěma různými způsoby.  
  
 [!code-csharp[Formatting.Composite#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#5)]
 [!code-vb[Formatting.Composite#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#5)]  
  
 Následující příklad znázorňuje použití zarovnání ve formátování. Argumenty, které jsou formátovány, jsou umístěny mezi znaky svislého pruhu (&#124;), aby se zvýraznilo výsledné zarovnání.  
  
 [!code-csharp[Formatting.Composite#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#6)]
 [!code-vb[Formatting.Composite#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#6)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Console.WriteLine%2A>
- <xref:System.String.Format%2A?displayProperty=nameWithType>
- [Interpolace řetězců (C#)](../../csharp/language-reference/tokens/interpolated.md)
- [Interpolace řetězců (Visual Basic)](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)
- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
- [Standardní řetězce číselného formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [Vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
- [Standardní řetězce formátu TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)
- [Vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)
- [Výčet řetězců formátu](../../../docs/standard/base-types/enumeration-format-strings.md)
