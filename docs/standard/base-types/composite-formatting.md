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
ms.openlocfilehash: 93abf6e91c2e13173184faee281de52eb83e17f5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314006"
---
# <a name="composite-formatting"></a>Složené formátování

Funkce složeného formátování .NET přebírá seznam objektů a složený řetězec formátu jako vstup. Složený řetězec formátu se skládá z pevného textu smíšeného s indexovanými zástupnými symboly nazvanými „položky formátu“, které odpovídají objektům v seznamu. Výsledkem operace formátování je výsledný řetězec, který se skládá z původního pevného textu smíšeného s řetězcovou reprezentací objektů v seznamu.  
  
> [!IMPORTANT]
> Namísto použití složených formátovacích řetězců, můžete použít *interpolovaných řetězců* Pokud jazyk a jazykovou verzi, kterou používáte je podporují. Interpolovaný řetězec je řetězec, který obsahuje *interpolovaných výrazů*. Každý interpolovaný výraz je přeložit výraz hodnotu a zahrnuté ve výsledném řetězci, když se přiřadí řetězec. Další informace najdete v tématu [interpolace řetězců (C# odkaz)](../../csharp/language-reference/tokens/interpolated.md) a [interpolovaných řetězců (referenční dokumentace jazyka Visual Basic)](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md).

Funkce složeného formátování je podporována například následujícími metodami:  
  
- <xref:System.String.Format%2A?displayProperty=nameWithType>, která vrací formátovaný výsledný řetězec.  
  
- <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, která připojí formátovaný výsledný řetězec k <xref:System.Text.StringBuilder> objektu.   
- Některá přetížení <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> metodu, která zobrazí formátovaný výsledný řetězec do konzoly.  
  
- Některá přetížení <xref:System.IO.TextWriter.WriteLine%2A?displayProperty=nameWithType> metoda, která zapisují formátovaný výsledný řetězec do datového proudu nebo souboru. Třídy odvozené z <xref:System.IO.TextWriter>, jako například <xref:System.IO.StreamWriter> a <xref:System.Web.UI.HtmlTextWriter>, mají také tuto funkci.  
  
- <xref:System.Diagnostics.Debug.WriteLine%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, která vytvoří výstup formátovaných zpráv pro posluchače trasování.  
  
- <xref:System.Diagnostics.Trace.TraceError%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, A <xref:System.Diagnostics.Trace.TraceWarning%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> metody, které výstup formátovaných zpráv pro posluchače trasování.  
  
- <xref:System.Diagnostics.TraceSource.TraceInformation%28System.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> Metodu, která zapíše informační metodu pro posluchače trasování.  
  
## <a name="composite-format-string"></a>Složený řetězec formátu  
 Složený řetězec formátu a seznam objektů se používají jako argumenty metod, které podporují funkci složeného formátování. Složený řetězec formátu se skládá z žádného výskytu nebo několika výskytů pevného textu smíšeného s jednou nebo několika položkami formátu. Pevný text je jakýkoli řetězec, který si zvolíte, a jednotlivé položky formátu odpovídají objektu nebo ohraničené struktuře v seznamu. Funkce složeného formátování vrátí nový výsledný řetězec, kde každá položka formátu je nahrazena řetězcovou reprezentací odpovídajícího objektu v seznamu.  
  
 Vezměte v úvahu následující <xref:System.String.Format%2A> fragment kódu.  
  
 [!code-csharp[Formatting.Composite#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#1)]
 [!code-vb[Formatting.Composite#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#1)]  
  
 Pevný text je "`Name =` "a"`, hours =` ". Položkami formátu jsou "`{0}`", jejíž index je 0, což odpovídá objektu `name`, a "`{1:hh}`", jejíž index je 1, což odpovídá objektu `DateTime.Now`.  
  
## <a name="format-item-syntax"></a>Syntaxe položky formátu  
 Jednotlivé položky formátu mají následující podobu a skládají se z následujících součástí:  
  
 `{` *index*[`,`*alignment*][`:`*formatString*]`}`  
  
 Jsou požadovány odpovídající složené závorky ("{" a "}").  
  
### <a name="index-component"></a>Součást Index  
 Povinné *index* komponentu, také jako specifikátor parametru, je číslo od 0, které identifikuje odpovídající položku v seznamu objektů. To znamená, že položka formátu, jejíž specifikátor parametru je 0, formátuje první objekt v seznamu, položka formátu, jejíž specifikátor parametru je 1, formátuje druhý objekt v seznamu atd. Následující příklad obsahuje čtyři specifikátory parametrů, číslované nula až tři, představující prvočísel méně než 10:  
  
 [!code-csharp[Formatting.Composite#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#7)]
 [!code-vb[Formatting.Composite#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#7)]  
  
 Více položek formátu může odkazovat na stejný prvek v seznamu objektů zadáním stejného specifikátoru parametru. Například můžete formátovat stejnou číselnou hodnotu v šestnáctkovém, vědeckém a číselném formátu určením složeného řetězce formátu: "0 x{0:X} {0:E} {0:N}", jak ukazuje následující příklad.  
  
 [!code-csharp[Formatting.Composite#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/index1.cs#10)]
 [!code-vb[Formatting.Composite#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/index1.vb#10)]  
  
 Každá položka formátu může odkazovat na libovolný objekt v seznamu. Například, pokud existují tři objekty, můžete formátovat druhý, první a třetí objekt zadáním složeného řetězce formátu tímto způsobem: "{1} {0} {2}". Objekt, který není odkazován položkou formátu, je ignorován. A <xref:System.FormatException> dojde za běhu, pokud specifikátor parametru označí položku mimo rozsah seznamu objektů.  
  
### <a name="alignment-component"></a>Součást Zarovnání  
 Volitelný *zarovnání* součástí je celé číslo se znaménkem označující šířku pole upřednostňovaného formátu. Pokud hodnota *zarovnání* je menší než délka formátovaného řetězce, *zarovnání* je ignorována a délka formátovaného řetězce se používá jako šířka pole. Formátovaná data v poli jsou zarovnána doprava, pokud *zarovnání* kladné a zarovnána doleva, pokud *zarovnání* je záporný. Pokud je vyžadováno odsazení obsahu, jsou použity prázdné znaky. Čárka je povinná, pokud *zarovnání* je zadán.  
  
 Následující příklad definuje dvě pole, jeden obsahující názvy zaměstnanců a dalších obsahující hodiny, které to šlo během dvou týdnů. Složený formátovací řetězec vlevo zarovná názvy ve 20 znaků pole a vpravo zarovná jejich hodiny v poli 5 znaků. Všimněte si, že je řetězec standardního formátu "N1" také použita k formátování hodiny se jedno desetinné číslo.  
  
 [!code-csharp[Formatting.Composite#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/alignment1.cs#8)]
 [!code-vb[Formatting.Composite#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/alignment1.vb#8)]  
  
### <a name="format-string-component"></a>Součást Řetězec formátu  
 Volitelný *formatString* komponenta je řetězec formátu, který odpovídá typu formátovaného objektu. Zadejte řetězec standardního nebo vlastního číselného formátu. Pokud je odpovídajícím objektem číselná hodnota, standardní nebo vlastní data a času řetězec formátu Pokud je odpovídajícím objektem <xref:System.DateTime> objektu, nebo [řetězec formátu výčtu](../../../docs/standard/base-types/enumeration-format-strings.md)Pokud je odpovídajícím objektem hodnota výčtu. Pokud *formatString* není zadán, je použit specifikátor obecného formátu ("G") pro číselné, datum a čas nebo výčtového typu. Dvojtečka je povinná, pokud *formatString* je zadán.  
  
 Následující tabulka uvádí seznam typů nebo kategorií typů v knihovně tříd rozhraní .NET Framework, které podporují předdefinovanou množinu řetězců formátu, a obsahuje odkazy na témata, která poskytují seznam jednotlivých řetězců formátu. Formátování řetězců poskytuje rozšířitelný mechanismus, který umožňuje definovat nové řetězce formátu pro všechny existující typy a také definovat množinu řetězců formátu podporovaných typem definovaného aplikací. Další informace najdete v tématu <xref:System.IFormattable> a <xref:System.ICustomFormatter> rozhraní témata.  
  
|Typ nebo kategorie typů|Další informace naleznete v tématu|  
|---------------------------|---------|  
|Typy data a času (<xref:System.DateTime>, <xref:System.DateTimeOffset>)|[Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)<br /><br /> [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|  
|Výčtové typy (všechny typy odvozené z <xref:System.Enum?displayProperty=nameWithType>)|[Výčet řetězců formátu](../../../docs/standard/base-types/enumeration-format-strings.md)|  
|Číselné typy (<xref:System.Numerics.BigInteger>, <xref:System.Byte>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>)|[Standardní řetězce číselného formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md)<br /><br /> [Vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md)|  
|<xref:System.Guid>|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.TimeSpan>|[Standardní řetězce formátu TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)<br /><br /> [Vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|  
  
### <a name="escaping-braces"></a>Řídicí znaky pro složené závorky  
 Levá a pravá složená závorka se interpretuje jako počátek a konec položky formátu. V důsledku toho je nutné použít sekvenci řídicích znaků pro zobrazení literální levé a pravé složené závorky. Chcete-li zobrazit jednu levou složenou závorku ("{"), zadejte dvě levé složené závorky ("{{"); chcete-li zobrazit jednu pravou složenou závorku ("}"), zadejte dvě pravé závorky ("}}"). Složené závorky v položce formátu jsou interpretovány postupně v pořadí, v jakém se vyskytují. Interpretace vnořených složených závorek není podporována.  
  
 Způsob, jakým jsou interpretovány složené závorky vložené pomocí řídicích znaků, může vést k neočekávaným výsledkům. Představte si třeba položky formátu "{{{0:D}}}", který se má zobrazit levá složená závorka, číselnou hodnotu ve formátu jako desítkové číslo a pravou složenou závorku. Položka formátu je však ve skutečnosti interpretována následujícím způsobem:  
  
1. První dvě levé složené závorky ("{{") jsou tvořeny řídicími znaky, a proto je výsledkem jedna levá závorka.  
  
2. Následující tři znaky ("{0:") jsou interpretovány jako začátek položky formátu.  
  
3. Další znak ("D") je interpretován jako specifikátor standardního číselného desítkového formátu, ale další dvě závorky uvozené řídicími znaky ("}}") tvoří ve výsledku jednu složenou závorku. Vzhledem k tomu, že výsledný řetězec ("D}") není specifikátorem standardního číselného formátu, je výsledný řetězec interpretován jako řetězec vlastního formátu, což znamená, že se zobrazí řetězcový literál "D}".  
  
4. Poslední složená závorka ("}") je interpretována jako konec položky formátu.  
  
5. Konečný výsledek, který se zobrazí, je řetězcový literál "{D}". Číselná hodnota, která měla být formátována, se nezobrazí.  
  
 Jedním ze způsobů, jak napsat kód tak, aby nedocházelo k chybné interpretaci složených závorek s řídicími znaky, je provést formátování složených závorek a položek formátu odděleně. To znamená, že se v první operaci formátování zobrazí literální znak levé složené závorky, v další operaci se zobrazí výsledek položky formátu a nakonec se v poslední operaci zobrazí literální znak pravé složené závorky. Tento postup znázorňuje následující příklad.  
  
 [!code-csharp[Formatting.Composite#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Escaping1.cs#2)]
 [!code-vb[Formatting.Composite#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Escaping1.vb#2)]  
  
### <a name="processing-order"></a>Pořadí zpracování  
 Pokud volání metody složeného formátování zahrnuje <xref:System.IFormatProvider> argument, jehož hodnota není `null`, modul runtime zavolá jeho <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metodu pro žádost o <xref:System.ICustomFormatter> implementace. Pokud je metoda může vrátit <xref:System.ICustomFormatter> implementace, je tam uložena po dobu trvání volání metody složeného formátování.
  
 Každou hodnotu v seznamu parametrů, která odpovídá položce formátu, je převedena na řetězec následujícím způsobem:  
  
1. Pokud je hodnota má být formátováno `null`, prázdný řetězec <xref:System.String.Empty?displayProperty=nameWithType> je vrácena.  
  
2. Pokud <xref:System.ICustomFormatter> implementace je k dispozici, modul runtime zavolá jeho <xref:System.ICustomFormatter.Format%2A> metoda. Předá metodě položky formátu *formatString* hodnotu, pokud je k dispozici, nebo `null` Pokud ne, spolu s <xref:System.IFormatProvider> implementace. Pokud volání <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> vrátí metoda `null`, provádění pokračuje k dalšímu kroku; v opačném případě výsledek <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> volání se vrátí.
  
3. Pokud hodnota implementuje <xref:System.IFormattable> rozhraní, což je rozhraní <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29> metoda je volána. Metodě je předána *formatString* hodnotu, pokud je k dispozici v položce formátu, nebo `null` nesplnění. <xref:System.IFormatProvider> Argument je stanoven následujícím způsobem:  
  
    -   Pro číselnou hodnotu, pokud složeného formátování s nenulovým <xref:System.IFormatProvider> argument je volána, modul runtime požádá o <xref:System.Globalization.NumberFormatInfo> objekt z jeho <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metoda. Pokud nelze zadat, pokud je hodnota argumentu `null`, nebo pokud metody složeného formátování nemá <xref:System.IFormatProvider> parametr, <xref:System.Globalization.NumberFormatInfo> objektů pro aktuální jazykovou verzi vlákna se používá.  
  
    -   Pro hodnoty data a času, pokud složeného formátování s nenulovým <xref:System.IFormatProvider> argument je volána, modul runtime požádá o <xref:System.Globalization.DateTimeFormatInfo> objekt z jeho <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metoda. Pokud nelze zadat, pokud je hodnota argumentu `null`, nebo pokud metody složeného formátování nemá <xref:System.IFormatProvider> parametr, <xref:System.Globalization.DateTimeFormatInfo> objektů pro aktuální jazykovou verzi vlákna se používá.  
  
    -   Pro objekty jiných typů, pokud složené formátování metoda je volána pomocí <xref:System.IFormatProvider> argument, její hodnota je předána přímo <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> implementace. V opačném případě `null` je předán <xref:System.IFormattable.ToString%2A?displayProperty=nameWithType> implementace.  
  
4. Typ uživatele bez parametrů `ToString` metoda, která buď přepíše <xref:System.Object.ToString?displayProperty=nameWithType> nebo zdědí chování základní třídy, je volána. V takovém případě řetězec formátu zadaný součástí *formatString* komponenty v položce formátu, pokud je k dispozici, je ignorován.  
  
 Zarovnání se použije po provedení předchozích kroků.  
  
## <a name="code-examples"></a>Příklady kódu  
 Následující příklad ukazuje jeden řetězec vytvořený pomocí složeného formátování a další vytvořené pomocí objektu `ToString` metody. Oba typy formátování poskytují stejné výsledky.  
  
 [!code-csharp[Formatting.Composite#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#3)]
 [!code-vb[Formatting.Composite#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#3)]  
  
 Za předpokladu, že aktuálním dnem je čtvrtek v květnu, je hodnota obou řetězců v předchozím příkladu `Thursday May` v USA. Anglickou jazykovou verzi.  
  
 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> poskytuje stejné funkce jako <xref:System.String.Format%2A?displayProperty=nameWithType>. Jediným rozdílem mezi těmito dvěma metodami je, že <xref:System.String.Format%2A?displayProperty=nameWithType> vrátí výsledek jako řetězec, zatímco <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> zapíše výsledek do výstupního datového proudu spojené s <xref:System.Console> objektu. V následujícím příkladu <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> metody pro formátování hodnoty `MyInt` na hodnotu měny.  
  
 [!code-csharp[Formatting.Composite#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#4)]
 [!code-vb[Formatting.Composite#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#4)]  
  
 Následující příklad znázorňuje formátování většího počtu objektů, včetně formátování jednoho objektu dvěma různými způsoby.  
  
 [!code-csharp[Formatting.Composite#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#5)]
 [!code-vb[Formatting.Composite#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#5)]  
  
 Následující příklad znázorňuje použití zarovnání ve formátování. Formátované argumenty jsou umístěny mezi znaky svislé čáry (&#124;) pro zvýraznění výsledného zarovnání.  
  
 [!code-csharp[Formatting.Composite#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Composite/cs/Composite1.cs#6)]
 [!code-vb[Formatting.Composite#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Composite/vb/Composite1.vb#6)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Console.WriteLine%2A>
- <xref:System.String.Format%2A?displayProperty=nameWithType>
- [Interpolace řetězců (C#)](../../csharp/language-reference/tokens/interpolated.md)
- [Interpolace (Visual Basic)](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)
- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
- [Standardní řetězce číselného formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [Vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
- [Standardní řetězce formátu TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)
- [Vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)
- [Výčet řetězců formátu](../../../docs/standard/base-types/enumeration-format-strings.md)
