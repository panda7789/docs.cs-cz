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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8d0574c7e0910a658f1dc80d8394f55b472c31a3
ms.sourcegitcommit: 46c68557bf6395f0ab9915f7558f2faae0097695
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/12/2019
ms.locfileid: "64634557"
---
# <a name="composite-formatting"></a>Složené formátování

Funkce složeného formátování .NET přebírá seznam objektů a složený řetězec formátu jako vstup. Složený řetězec formátu se skládá z pevného textu smíšeného s indexovanými zástupnými symboly nazvanými „položky formátu“, které odpovídají objektům v seznamu. Výsledkem operace formátování je výsledný řetězec, který se skládá z původního pevného textu smíšeného s řetězcovou reprezentací objektů v seznamu.  
  
> [!IMPORTANT]
> Namísto použití složených formátovacích řetězců můžete použít interpolované *řetězce* , pokud jazyk a jazykovou verzi, kterou používáte, podporuje. Interpolovaný řetězec je řetězec, který obsahuje *interpolovaných výrazů*. Každý interpolovaný výraz je přeložit výraz hodnotu a zahrnuté ve výsledném řetězci, když se přiřadí řetězec. Další informace naleznete v tématu [interpolace řetězce (C# referenční)](../../csharp/language-reference/tokens/interpolated.md) a [interpolované řetězce (Visual Basic odkaz)](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md).

Funkce složeného formátování je podporována například následujícími metodami:  
  
- <xref:System.String.Format%2A?displayProperty=nameWithType>, který vrací formátovaný výsledný řetězec.  
  
- <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, který připojí formátovaný výsledný řetězec k <xref:System.Text.StringBuilder> objektu.   
- Některá přetížení <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> metody, která zobrazuje formátovaný výsledný řetězec do konzoly.  
  
- Některá přetížení <xref:System.IO.TextWriter.WriteLine%2A?displayProperty=nameWithType> metody, která zapisují formátovaný výsledný řetězec do datového proudu nebo souboru. Třídy odvozené z <xref:System.IO.TextWriter>, <xref:System.IO.StreamWriter> například a <xref:System.Web.UI.HtmlTextWriter>, sdílejí také tuto funkci.  
  
- <xref:System.Diagnostics.Debug.WriteLine%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, což výstupuje formátovanou zprávu pro trasování posluchačů.  
  
- Metody, a<xref:System.Diagnostics.Trace.TraceWarning%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> , které mají výstup formátované zprávy pro trasování posluchačů. <xref:System.Diagnostics.Trace.TraceError%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSource.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> Metoda, která zapisuje informační metodu pro trasování posluchačů.  
  
## <a name="composite-format-string"></a>Složený řetězec formátu  
 Složený řetězec formátu a seznam objektů se používají jako argumenty metod, které podporují funkci složeného formátování. Složený řetězec formátu se skládá z žádného výskytu nebo několika výskytů pevného textu smíšeného s jednou nebo několika položkami formátu. Pevný text je jakýkoli řetězec, který si zvolíte, a jednotlivé položky formátu odpovídají objektu nebo ohraničené struktuře v seznamu. Funkce složeného formátování vrátí nový výsledný řetězec, kde každá položka formátu je nahrazena řetězcovou reprezentací odpovídajícího objektu v seznamu.  
  
 Vezměte v úvahu <xref:System.String.Format%2A> následující fragment kódu.  
  
 [!code-csharp[Formatting.Composite#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#1)]
 [!code-vb[Formatting.Composite#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#1)]  
  
 Pevný text je`Name =` "" a "`, hours =` ". Položky formátu jsou`{0}`"", jejichž index je 0, který odpovídá objektu `name`a "`{1:hh}`", jehož index je 1, což odpovídá objektu `DateTime.Now`.  
  
## <a name="format-item-syntax"></a>Syntaxe položky formátu  
 Jednotlivé položky formátu mají následující podobu a skládají se z následujících součástí:  
  
 `{` *index*[`,`*alignment*][`:`*formatString*]`}`  
  
 Jsou požadovány odpovídající složené závorky ("{" a "}").  
  
### <a name="index-component"></a>Součást Index  
 Povinná součást *indexu* , označovaná také jako specifikátor parametru, je číslo od 0, které identifikuje odpovídající položku v seznamu objektů. To znamená, že položka formátu, jejíž specifikátor parametru je 0, formátuje první objekt v seznamu, položka formátu, jejíž specifikátor parametru je 1, formátuje druhý objekt v seznamu atd. Následující příklad obsahuje čtyři specifikátory parametrů, očíslované nula až tři, aby představovaly hlavní čísla menší než deset:  
  
 [!code-csharp[Formatting.Composite#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#7)]
 [!code-vb[Formatting.Composite#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#7)]  
  
 Více položek formátu může odkazovat na stejný prvek v seznamu objektů zadáním stejného specifikátoru parametru. Můžete například formátovat stejnou číselnou hodnotu v šestnáctkovém, vědeckém a číselném formátu zadáním složeného formátovacího řetězce, jako například: "0x{0:X} {0:E} ",jak{0:N}ukazuje následující příklad.  
  
 [!code-csharp[Formatting.Composite#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#10)]
 [!code-vb[Formatting.Composite#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#10)]  
  
 Každá položka formátu může odkazovat na libovolný objekt v seznamu. Například pokud existují tři objekty, lze naformátovat druhý, první a třetí objekt zadáním složeného formátu řetězce, například: "{1} {0} {2}". Objekt, který není odkazován položkou formátu, je ignorován. Výjimka <xref:System.FormatException> je vyvolána za běhu, pokud specifikátor parametru označuje položku mimo hranice seznamu objektů.  
  
### <a name="alignment-component"></a>Součást Zarovnání  
 Volitelná součást *Zarovnání* je celé číslo se znaménkem, které označuje upřednostňovanou šířku pole. Pokud je hodnota *Zarovnání* menší než délka formátovaného řetězce, *Zarovnání* je ignorováno a délka formátovaného řetězce se používá jako šířka pole. Formátovaná data v poli jsou zarovnána vpravo, pokud je *Zarovnání* kladné a zarovnané doleva, pokud je *Zarovnání* záporné. Pokud je vyžadováno odsazení obsahu, jsou použity prázdné znaky. Čárka je vyžadována, pokud je zadáno *Zarovnání* .  
  
 Následující příklad definuje dvě pole, jednu, která obsahuje jména zaměstnanců a druhý, které obsahují hodiny, které pracovaly po dobu dvou týdnů. Složený řetězec formátu vlevo zarovná názvy v poli o 20 znacích a v poli s pěti znaky Zarovná hodiny vpravo. Všimněte si, že standardní formátovací řetězec "N1" slouží také k formátování hodin s jednou zlomkovou číslicí.  
  
 [!code-csharp[Formatting.Composite#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/alignment1.cs#8)]
 [!code-vb[Formatting.Composite#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/alignment1.vb#8)]  
  
### <a name="format-string-component"></a>Součást Řetězec formátu  
 Volitelná komponenta *formatString* je řetězec formátu, který je vhodný pro typ objektu, který se formátuje. Zadejte standardní nebo vlastní řetězec číselného formátu, pokud je odpovídajícím objektem číselná hodnota, standardní nebo vlastní řetězec formátu data a času, pokud je odpovídajícím objektem <xref:System.DateTime> objekt nebo [řetězec formátu výčtu](../../../docs/standard/base-types/enumeration-format-strings.md) , pokud odpovídající objekt je hodnota výčtu. Pokud není zadán vlastnost *formatString* , je použit obecný specifikátor formátu ("G") pro číselný, datum a čas nebo typ výčtu. Dvojtečka je povinná, pokud je zadána vlastnost *formatString* .  
  
 Následující tabulka uvádí seznam typů nebo kategorií typů v knihovně tříd rozhraní .NET Framework, které podporují předdefinovanou množinu řetězců formátu, a obsahuje odkazy na témata, která poskytují seznam jednotlivých řetězců formátu. Formátování řetězců poskytuje rozšířitelný mechanismus, který umožňuje definovat nové řetězce formátu pro všechny existující typy a také definovat množinu řetězců formátu podporovaných typem definovaného aplikací. Další informace najdete v <xref:System.IFormattable> tématech rozhraní a. <xref:System.ICustomFormatter>  
  
|Typ nebo kategorie typů|Další informace naleznete v tématu|  
|---------------------------|---------|  
|Typy data a času (<xref:System.DateTime>, <xref:System.DateTimeOffset>)|[Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)<br /><br /> [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|  
|Výčtové typy (všechny typy odvozené <xref:System.Enum?displayProperty=nameWithType>od)|[Výčet řetězců formátu](../../../docs/standard/base-types/enumeration-format-strings.md)|  
|Číselné typy (<xref:System.Numerics.BigInteger>, <xref:System.Byte>, <xref:System.Decimal>, <xref:System.Double>, ,<xref:System.Int16> ,<xref:System.Int64>, ,<xref:System.Single>,, ,<xref:System.UInt32>) <xref:System.Int32> <xref:System.SByte> <xref:System.UInt16> <xref:System.UInt64>|[Standardní řetězce číselného formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md)<br /><br /> [Vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md)|  
|<xref:System.Guid>|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.TimeSpan>|[Standardní řetězce formátu TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)<br /><br /> [Vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|  
  
### <a name="escaping-braces"></a>Řídicí znaky pro složené závorky  
 Levá a pravá složená závorka se interpretuje jako počátek a konec položky formátu. V důsledku toho je nutné použít sekvenci řídicích znaků pro zobrazení literální levé a pravé složené závorky. Chcete-li zobrazit jednu levou složenou závorku ("{"), zadejte dvě levé složené závorky ("{{"); chcete-li zobrazit jednu pravou složenou závorku ("}"), zadejte dvě pravé závorky ("}}"). Složené závorky v položce formátu jsou interpretovány postupně v pořadí, v jakém se vyskytují. Interpretace vnořených složených závorek není podporována.  
  
 Způsob, jakým jsou interpretovány složené závorky vložené pomocí řídicích znaků, může vést k neočekávaným výsledkům. Zvažte například položku formátu "{{{0:D}}}", která je určena k zobrazení levé složené závorky, numerické hodnoty formátované jako desetinné číslo a uzavírací závorky. Položka formátu je však ve skutečnosti interpretována následujícím způsobem:  
  
1. První dvě levé složené závorky ("{{") jsou tvořeny řídicími znaky, a proto je výsledkem jedna levá závorka.  
  
2. Následující tři znaky ("{0:") jsou interpretovány jako začátek položky formátu.  
  
3. Další znak ("D") je interpretován jako specifikátor standardního číselného desítkového formátu, ale další dvě závorky uvozené řídicími znaky ("}}") tvoří ve výsledku jednu složenou závorku. Vzhledem k tomu, že výsledný řetězec ("D}") není specifikátorem standardního číselného formátu, je výsledný řetězec interpretován jako řetězec vlastního formátu, což znamená, že se zobrazí řetězcový literál "D}".  
  
4. Poslední složená závorka ("}") je interpretována jako konec položky formátu.  
  
5. Konečný výsledek, který se zobrazí, je řetězcový literál "{D}". Číselná hodnota, která měla být formátována, se nezobrazí.  
  
 Jedním ze způsobů, jak napsat kód tak, aby nedocházelo k chybné interpretaci složených závorek s řídicími znaky, je provést formátování složených závorek a položek formátu odděleně. To znamená, že se v první operaci formátování zobrazí literální znak levé složené závorky, v další operaci se zobrazí výsledek položky formátu a nakonec se v poslední operaci zobrazí literální znak pravé složené závorky. Tento postup znázorňuje následující příklad.  
  
 [!code-csharp[Formatting.Composite#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Escaping1.cs#2)]
 [!code-vb[Formatting.Composite#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Escaping1.vb#2)]  
  
### <a name="processing-order"></a>Pořadí zpracování  
 Pokud volání <xref:System.IFormatProvider> metody složeného formátování obsahuje argument `null`, jehož hodnota není, modul runtime volá <xref:System.ICustomFormatter> svou <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metodu pro vyžádání implementace. Pokud metoda může vracet <xref:System.ICustomFormatter> implementaci, je ukládána do mezipaměti po dobu trvání volání metody složeného formátování.
  
 Každá hodnota v seznamu parametrů, která odpovídá položce formátu, je převedena na řetězec následujícím způsobem:  
  
1. Pokud je `null`hodnota, která má být formátována, je <xref:System.String.Empty?displayProperty=nameWithType> vrácen prázdný řetězec.  
  
2. Je- <xref:System.ICustomFormatter> li k dispozici implementace, modul runtime <xref:System.ICustomFormatter.Format%2A> volá svou metodu. Předá metodu hodnoty *formatString* položky formátu, pokud je k dispozici, nebo `null` Pokud není <xref:System.IFormatProvider> , společně s implementací. Pokud volání <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> metody vrátí `null`, provádění pokračuje k dalšímu kroku. v opačném případě je vrácen výsledek <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> volání.
  
3. Pokud hodnota implementuje <xref:System.IFormattable> rozhraní, je volána <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29> Metoda rozhraní. Metodě je předána hodnota *formatString* , pokud je k dispozici ve formátu položky nebo `null` Pokud není. <xref:System.IFormatProvider> Argument je určen následujícím způsobem:  
  
    - Pro číselnou hodnotu, pokud je volána metoda složeného formátování s nenulovým <xref:System.IFormatProvider> argumentem, modul runtime požádá o <xref:System.Globalization.NumberFormatInfo> objekt z jeho <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metody. Pokud není možné ji dodat, pokud je `null`hodnota argumentu nebo pokud metoda <xref:System.IFormatProvider> složeného formátování nemá parametr, <xref:System.Globalization.NumberFormatInfo> je použit objekt pro aktuální jazykovou verzi vlákna.  
  
    - V případě hodnoty data a času, pokud je volána metoda složeného formátování s nenulovým <xref:System.IFormatProvider> argumentem, modul runtime požádá o <xref:System.Globalization.DateTimeFormatInfo> objekt z <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> jeho metody. Pokud není možné ji dodat, pokud je `null`hodnota argumentu nebo pokud metoda <xref:System.IFormatProvider> složeného formátování nemá parametr, <xref:System.Globalization.DateTimeFormatInfo> je použit objekt pro aktuální jazykovou verzi vlákna.  
  
    - Pro objekty jiných typů, pokud je metoda složeného formátování volána s <xref:System.IFormatProvider> argumentem, je jeho hodnota předána přímo <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> implementaci. V opačném případě <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> sepředávádoimplementace.`null`  
  
4. `ToString` Metoda bez parametrů typu, která buď Přepisuje <xref:System.Object.ToString?displayProperty=nameWithType> nebo dědí chování své základní třídy, je volána. V tomto případě je řetězec formátu určený komponentou *formatString* v položce formátu, pokud je přítomen, ignorován.  
  
 Zarovnání se použije po provedení předchozích kroků.  
  
## <a name="code-examples"></a>Příklady kódu  
 Následující příklad ukazuje jeden řetězec vytvořený pomocí složeného formátování a druhý vytvořený pomocí `ToString` metody objektu. Oba typy formátování poskytují stejné výsledky.  
  
 [!code-csharp[Formatting.Composite#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#3)]
 [!code-vb[Formatting.Composite#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#3)]  
  
 Za předpokladu, že aktuální den je čtvrtek v květnu, hodnota obou řetězců v předchozím příkladu je `Thursday May` v USA. Anglická jazyková verze.  
  
 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>zpřístupňuje stejné funkce jako <xref:System.String.Format%2A?displayProperty=nameWithType>. Jediným rozdílem mezi těmito dvěma metodami je <xref:System.String.Format%2A?displayProperty=nameWithType> , že vrátí výsledek jako řetězec, zatímco <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> zapíše výsledek do <xref:System.Console> výstupního datového proudu přidruženého k objektu. Následující příklad používá <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> metodu k naformátování `MyInt` hodnoty na hodnotu měny.  
  
 [!code-csharp[Formatting.Composite#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#4)]
 [!code-vb[Formatting.Composite#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#4)]  
  
 Následující příklad znázorňuje formátování většího počtu objektů, včetně formátování jednoho objektu dvěma různými způsoby.  
  
 [!code-csharp[Formatting.Composite#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#5)]
 [!code-vb[Formatting.Composite#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#5)]  
  
 Následující příklad znázorňuje použití zarovnání ve formátování. Argumenty, které jsou formátovány, jsou umístěny mezi znaky svislé&#124;čáry () pro zvýraznění výsledného zarovnání.  
  
 [!code-csharp[Formatting.Composite#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#6)]
 [!code-vb[Formatting.Composite#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#6)]  
  
## <a name="see-also"></a>Viz také:

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
