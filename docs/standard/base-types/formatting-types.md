---
title: Formátování typů v .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data formatting [.NET Framework]
- dates [.NET Framework], formatting
- date formatting [.NET Framework]
- number formatting [.NET Framework]
- ToString method
- custom cultural settings [.NET Framework]
- numbers [.NET Framework], formatting
- formatting strings [.NET Framework]
- time [.NET Framework], formatting
- currency [.NET Framework], formatting
- types [.NET Framework], formatting
- format specifiers [.NET Framework]
- times [.NET Framework], formatting
- culture [.NET Framework], formatting
- formatting [.NET Framework], types supported
- base types [.NET Framework], formatting
- custom formatting [.NET Framework]
- strings [.NET Framework], formatting
ms.assetid: 0d1364da-5b30-4d42-8e6b-03378343343f
ms.openlocfilehash: 20aa7ecd354ef1a8982ae75eda87275c80cdaaf6
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802463"
---
# <a name="format-types-in-net"></a>Typy formátů v .NET

Formátování je proces převodu instance třídy, struktury nebo výčtové hodnoty na řetězcové vyjádření často proto, aby mohl být výsledný řetězec zobrazen uživatelům nebo rekonstruován pro obnovení původního datového typu. Tento převod může představovat určitá úskalí:

- Způsob interního uložení hodnoty nutně neodráží způsob, kterým ho chtějí uživatelé zobrazit. Například telefonní číslo může být uloženo ve formě 8009999999, která není srozumitelná. Namísto toho má být zobrazeno jako 800-999-9999. V části [Vlastní řetězce formátu](#custom-format-strings) najdete příklad, který tímto způsobem formátuje číslo.

- Někdy není převod objektu na jeho řetězcovou reprezentaci intuitivní. Například není zřejmé, jak by měla být zobrazena řetězcová reprezentace objektu teplota nebo osoba. Příklad, který formátuje objekt teploty v různých způsobech, naleznete v oddílu [standardní formátovací řetězce](#standard-format-strings) .

- Hodnoty často vyžadují specifické formátování pro danou jazykovou verzi. Například v aplikaci, která používá čísla pro zobrazení peněžních hodnot, by měly číselné řetězce obsahovat symbol měny aktuální jazykové verze, oddělovač skupin (který je u většiny verzí oddělovač tisíců) a desetinný oddělovač. Příklad naleznete v části formátování zohledňující [jazykovou verzi s poskytovateli formátu](#culture-sensitive-formatting-with-format-providers) .

- Po aplikaci může být požadováno zobrazení stejné hodnoty různými způsoby. Například může aplikace vyjadřovat člen výčtového typu zobrazením řetězcové reprezentace jeho názvu nebo zobrazením jeho zadané hodnoty. Příklad, který formátuje člena <xref:System.DayOfWeek> výčtu různými způsoby, naleznete v oddílu [standardní formátovací řetězce](#standard-format-strings) .

> [!NOTE]
> Formátování převede hodnotu typu na řetězcovou reprezentaci. Analýza je k formátování inverzní. Operace analýzy vytváří instanci datového typu z jeho řetězcové reprezentace. Informace o převodu řetězců na jiné datové typy naleznete v tématu [Analýza řetězců](../../../docs/standard/base-types/parsing-strings.md).

Rozhraní .NET poskytuje bohatou podporu formátování, která vývojářům umožňuje řešit tyto požadavky.

## <a name="formatting-in-net"></a>Formátování v .NET

Základní mechanismus pro formátování je výchozí implementace metody <xref:System.Object.ToString%2A?displayProperty=nameWithType>, která je popsána v části [výchozí formátování pomocí metody ToString](#default-formatting-using-the-tostring-method) dále v tomto tématu. Rozhraní .NET však nabízí několik způsobů, jak upravit a zvětšit výchozí podporu formátování. Patří mezi ně například:

- Přepsání metody <xref:System.Object.ToString%2A?displayProperty=nameWithType> pro definování vlastní řetězcové reprezentace hodnoty objektu. Další informace naleznete v části [přepsání metody ToString](#override-the-tostring-method) dále v tomto tématu.

- Definování specifikátorů formátu pro umožnění toho, aby daná řetězcová reprezentace hodnoty objektu mohla mít více tvarů. Například specifikátor formátu "X" v následujícím příkazu převede celé číslo na řetězcovou reprezentaci šestnáctkové hodnoty.

     [!code-csharp[Conceptual.Formatting.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#3)]
     [!code-vb[Conceptual.Formatting.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#3)]

     Další informace o specifikátorech formátu naleznete v části [metoda ToString a formátovací řetězce](#the-tostring-method-and-format-strings) .

- Použití poskytovatelů formátu pro využití výhod konvencí formátování specifické jazykové verze. Následující příkaz například zobrazí hodnotu měny pomocí konvencí formátování jazykové verze en-US.

     [!code-csharp[Conceptual.Formatting.Overview#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#10)]
     [!code-vb[Conceptual.Formatting.Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#10)]

     Další informace o formátování s poskytovateli formátu najdete v části [poskytovatelé formátu](#culture-sensitive-formatting-with-format-providers) .

- Implementování rozhraní <xref:System.IFormattable> pro podporu převodu řetězce pomocí třídy <xref:System.Convert> i složeného formátování. Další informace najdete v části [rozhraní IFormattable](#the-iformattable-interface) .

- Použití složeného formátování pro vložení řetězcové reprezentace hodnoty do většího řetězce. Další informace najdete v oddílu [složené formátování](#composite-formatting) .

- Implementování <xref:System.ICustomFormatter> a <xref:System.IFormatProvider> pro poskytnutí kompletního vlastního řešení formátování. Další informace najdete v části [vlastní formátování pomocí ICustomFormatter](#custom-formatting-with-icustomformatter) .

V následujících oddílech jsou tyto metody pro převod objektu na řetězcovou reprezentaci probrány.

## <a name="default-formatting-using-the-tostring-method"></a>Výchozí formátování pomocí metody ToString

Každý typ, který je odvozen z <xref:System.Object?displayProperty=nameWithType>, automaticky dědí metodu `ToString` bez parametrů, která ve výchozím nastavení vrátí název typu. Následující příklad ukazuje takovouto výchozí metodu `ToString`. Je definována třída s názvem `Automobile`, která nemá žádnou implementaci. Když je vytvořena instance třídy a je zavolána její metoda `ToString`, zobrazí se název jejího typu. Všimněte si, že metoda `ToString` není explicitně volána v příkladu. Metoda <xref:System.Console.WriteLine%28System.Object%29?displayProperty=nameWithType> implicitně volá metodu `ToString` objektu, který je jí předán jako argument.

[!code-csharp[Conceptual.Formatting.Overview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/default1.cs#1)]
[!code-vb[Conceptual.Formatting.Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/default1.vb#1)]

> [!WARNING]
> Počínaje Windows 8.1 prostředí Windows Runtime obsahuje rozhraní <xref:Windows.Foundation.IStringable> s jedinou metodou, [IStringable. ToString](xref:Windows.Foundation.IStringable.ToString%2A), která poskytuje výchozí podporu formátování. Doporučujeme však, aby spravované typy rozhraní `IStringable` neimplementovaly. Další informace naleznete v části "prostředí Windows Runtime a `IStringable` Interface" na referenční stránce <xref:System.Object.ToString%2A?displayProperty=nameWithType>.

Protože všechny typy jiné než rozhraní jsou odvozeny z <xref:System.Object>, tato funkce je automaticky poskytnuta vlastním třídám nebo strukturám. Funkcionalita ve výchozím nastavení nabízená metodou `ToString` je však omezená. Přestože dokáže identifikovat typ, není schopna poskytnout žádné informace i jeho instanci. Chcete-li poskytnout řetězcovou reprezentaci objektu, který obsahuje informace o tomto objektu, musíte přepsat metodu `ToString`.

> [!NOTE]
> Struktury dědí z <xref:System.ValueType>, který je zase odvozen z <xref:System.Object>. Přestože <xref:System.ValueType> přepisuje <xref:System.Object.ToString%2A?displayProperty=nameWithType>, jejich implementace jsou totožné.

## <a name="override-the-tostring-method"></a>Přepsat metodu ToString

Zobrazení názvu typu má často omezené použití a neumožňuje odběratelům vašich typů rozlišit jednu instanci od druhé. Můžete však přepsat metodu `ToString` pro poskytnutí užitečnější reprezentace hodnoty objektu. V následujícím příkladu je definován objekt `Temperature` a je přepsána metoda `ToString` pro zobrazení teploty ve stupních Celsia.

[!code-csharp[Conceptual.Formatting.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/overrides1.cs#2)]
[!code-vb[Conceptual.Formatting.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/overrides1.vb#2)]

V rozhraní .NET byla přepsána metoda `ToString` každého primitivního hodnotového typu, aby se zobrazila hodnota objektu místo jejího názvu. V následující tabulce jsou uvedena přepsání pro každý primitivní typ. Povšimněte si, že většina přepsaných metod volá jiné přetížení metody `ToString` a předává ji specifikátoru formátu "G", který určuje obecný formát pro daný typ a objekt <xref:System.IFormatProvider>, který představuje aktuální jazykovou verzi.

|Type|přetížení metody ToString|
|----------|-----------------------|
|<xref:System.Boolean>|Vrátí buď <xref:System.Boolean.TrueString?displayProperty=nameWithType> nebo <xref:System.Boolean.FalseString?displayProperty=nameWithType>.|
|<xref:System.Byte>|Volá `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` pro zformátování hodnoty <xref:System.Byte> pro aktuální jazykovou verzi.|
|<xref:System.Char>|Vrátí znak jako řetězec.|
|<xref:System.DateTime>|Volá `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` pro zformátování hodnoty data a času pro aktuální jazykovou verzi.|
|<xref:System.Decimal>|Volá `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` pro zformátování hodnoty <xref:System.Decimal> pro aktuální jazykovou verzi.|
|<xref:System.Double>|Volá `Double.ToString("G", NumberFormatInfo.CurrentInfo)` pro zformátování hodnoty <xref:System.Double> pro aktuální jazykovou verzi.|
|<xref:System.Int16>|Volá `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` pro zformátování hodnoty <xref:System.Int16> pro aktuální jazykovou verzi.|
|<xref:System.Int32>|Volá `Int32.ToString("G", NumberFormatInfo.CurrentInfo)` pro zformátování hodnoty <xref:System.Int32> pro aktuální jazykovou verzi.|
|<xref:System.Int64>|Volá `Int64.ToString("G", NumberFormatInfo.CurrentInfo)` pro zformátování hodnoty <xref:System.Int64> pro aktuální jazykovou verzi.|
|<xref:System.SByte>|Volá `SByte.ToString("G", NumberFormatInfo.CurrentInfo)` pro zformátování hodnoty <xref:System.SByte> pro aktuální jazykovou verzi.|
|<xref:System.Single>|Volá `Single.ToString("G", NumberFormatInfo.CurrentInfo)` pro zformátování hodnoty <xref:System.Single> pro aktuální jazykovou verzi.|
|<xref:System.UInt16>|Volá `UInt16.ToString("G", NumberFormatInfo.CurrentInfo)` pro zformátování hodnoty <xref:System.UInt16> pro aktuální jazykovou verzi.|
|<xref:System.UInt32>|Volá `UInt32.ToString("G", NumberFormatInfo.CurrentInfo)` pro zformátování hodnoty <xref:System.UInt32> pro aktuální jazykovou verzi.|
|<xref:System.UInt64>|Volá `UInt64.ToString("G", NumberFormatInfo.CurrentInfo)` pro zformátování hodnoty <xref:System.UInt64> pro aktuální jazykovou verzi.|

## <a name="the-tostring-method-and-format-strings"></a>Metoda ToString a formátovací řetězce

Spoléhání se na výchozí metodu `ToString` nebo na přepsání `ToString` je vhodné v případě, kdy má objekt jedinou řetězcovou reprezentaci. Hodnota objektu má však často více reprezentací. Teplota může být například vyjádřena ve stupních Fahrenheita, stupních Celsia nebo Kelvinech. Podobně i celočíselná hodnota 10 může být reprezentována mnoha způsoby, včetně 10, 10.0, 1.0e01 nebo 10,00 USD.

Pokud chcete povolit, aby jedna hodnota měla více řetězcových reprezentací, používá rozhraní .NET řetězce formátu. Formátovací řetězec je řetězec, který obsahuje jeden nebo více předdefinovaných specifikátorů formátu, což jsou jednotlivé znaky nebo skupiny znaků, které definují způsob, jak má metoda `ToString` formátovat svůj výstup. Formátovací řetězec je pak předán jako parametr metodě `ToString` daného objektu a určuje, jak se má řetězcová reprezentace hodnoty tohoto objektu zobrazit.

Všechny číselné typy, typy data a času a výčtové typy v rozhraní .NET podporují předdefinovanou sadu specifikátorů formátu. Formátovací řetězce můžete také použít pro definování více řetězcových reprezentací datových typů definovaných vaší aplikací.

### <a name="standard-format-strings"></a>Standardní formátovací řetězce

Standardní formátovací řetězec obsahuje jediný specifikátor formátu, což je znak abecedy, který definuje řetězcovou reprezentaci objektu, na který je uplatněna, spolu s volitelným specifikátorem přesnosti, který ovlivňuje počet číslic zobrazovaných ve výsledném řetězci. Pokud je specifikátor přesnosti vynechán nebo není podporován, standardní specifikátor formátu pak odpovídá standardnímu formátovacímu řetězci.

Rozhraní .NET definuje sadu standardních specifikátorů formátu pro všechny číselné typy, všechny typy data a času a všechny typy výčtu. Každá z těchto kategorií například podporuje standardní specifikátor formátu "G", který definuje obecnou řetězcovou reprezentaci hodnoty daného typu.

Standardní formátovací řetězce pro výčtové typy přímo ovládají řetězcovou reprezentaci hodnoty. Formátovací řetězce předané metodě `ToString` výčtové hodnoty určují, zda je hodnota zobrazena pomocí jejího řetězcového názvu (specifikátory formátu "G" a "F"), její základní celočíselné hodnoty (specifikátor formátu "D") nebo její šestnáctkové hodnoty (specifikátor formátu "X"). Následující příklad ukazuje použití standardního formátovacího řetězce pro formátování výčtové hodnoty <xref:System.DayOfWeek>.

[!code-csharp[Conceptual.Formatting.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/standard1.cs#4)]
[!code-vb[Conceptual.Formatting.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/standard1.vb#4)]

Informace o formátovacích řetězcích výčtů naleznete v tématu [výčty formátu výčtu](../../../docs/standard/base-types/enumeration-format-strings.md).

Standardní formátovací řetězce pro číselné typy obvykle definují výsledný řetězec, jehož přesný vzhled je řízen jednou nebo více vlastnostmi. Specifikátor formátu "C" například zformátuje číslo jako hodnotu měny. Při zavolání metody `ToString` se specifikátorem formátu "C" jako jediným parametrem, jsou použity pro definování řetězcové reprezentace číselné hodnoty tyto vlastnosti objektu <xref:System.Globalization.NumberFormatInfo> aktuální jazykové verze:

- Vlastnost <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A>, která určuje symbol měny aktuální jazykové verze.

- Vlastnost <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> nebo <xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A> vracející celé číslo, které určuje následující:

  - Umístění symbolu měny.

  - Zda jsou záporné hodnoty znázorněny se záporným znaménkem na počátku, na konci nebo pomocí závorek.

  - Zda se mezi číselnou hodnotou a symbolem měny zobrazí mezera.

- Vlastnost <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A>, která definuje počet zlomkových číslic ve výsledném řetězci.

- Vlastnost <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A>, která definuje symbol desetinného oddělovače ve výsledném řetězci.

- Vlastnost <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A>, která definuje symbol oddělovače skupiny.

- Vlastnost <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A>, která definuje počet číslic v každé skupině číslic nalevo od desetinné čárky.

- Vlastnost <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>, která určuje záporné znaménko použité ve výsledném řetězci, pokud nejsou k označení záporné hodnoty použity závorky.

Kromě toho mohou formátovací řetězce čísel obsahovat specifikátor přesnosti. Význam tohoto specifikátoru závisí na použitém formátovacím řetězci, ale obvykle označuje buď celkový počet číslic nebo počet zlomkových číslic, které se mají zobrazit ve výsledném řetězci. V následujícím příkladu je například použit standardní číselný řetězec a specifikátor přesnosti "X4" pro vytvoření řetězcové hodnoty, která má čtyři šestnáctkové číslice.

[!code-csharp[Conceptual.Formatting.Overview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/precisionspecifier1.cs#6)]
[!code-vb[Conceptual.Formatting.Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/precisionspecifier1.vb#6)]

Další informace o standardních formátovacích řetězcích čísel naleznete v tématu [Standardní číselné formátovací řetězce](../../../docs/standard/base-types/standard-numeric-format-strings.md).

Standardní formátovací řetězce pro hodnoty data a času jsou zástupci pro vlastní formátovací řetězce uložené určitou vlastností <xref:System.Globalization.DateTimeFormatInfo>. Například volání metody `ToString` hodnoty data a času se specifikátorem formátu "D" zobrazí datum a čas pomocí vlastního formátovacího řetězce, který je uložen ve vlastnosti <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> aktuální jazykové verze. (Další informace o vlastních formátovacích řetězcích naleznete v [Další části](#custom-format-strings).) Následující příklad znázorňuje tuto relaci.

[!code-csharp[Conceptual.Formatting.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/alias1.cs#5)]
[!code-vb[Conceptual.Formatting.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/alias1.vb#5)]

Další informace o standardních formátovacích řetězcích data a času naleznete v tématu [Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md).

Standardní formátovací řetězce můžete také použít pro definování řetězcové reprezentace objektu definovaného aplikací, který je vytvořen metodou `ToString(String)` daného objektu. Můžete definovat určité standardní specifikátory formátu, které jsou podporovány vašim objektem, a můžete určit, zda rozlišují nebo nerozlišují velká a malá písmena. Vaše implementace metody `ToString(String)` by měla podporovat následující:

- Specifikátor formátu "G" představující obvyklý nebo obecný formát objektu. Přetížení metody `ToString` vašeho objektu bez parametrů by mělo volat přetížení `ToString(String)` a předat standardní formátovací řetězec "G".

- Podporu specifikátoru formátu, který je roven nulovému odkazu (`Nothing` v jazyce Visual Basic). Specifikátor formátu, který je roven nulovému odkazu, by měl být považován za ekvivalent specifikátoru formátu "G".

Třída `Temperature` například může interně uchovávat teplotu ve stupních Celsia a použít specifikátory formátu k zobrazení hodnoty objektu `Temperature` ve stupních Celsia, stupních Fahrenheita a kelvinech. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.Formatting.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/appstandard1.cs#7)]
[!code-vb[Conceptual.Formatting.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/appstandard1.vb#7)]

### <a name="custom-format-strings"></a>Vlastní řetězce formátování

Kromě standardních formátovacích řetězců definuje rozhraní .NET řetězce vlastního formátu pro číselné hodnoty a hodnoty data a času. Vlastní formátovací řetězec se skládá z jednoho nebo více vlastních specifikátorů formátu definujících řetězcovou reprezentaci hodnoty. Například vlastní formátovací řetězec pro datum a čas "rrrr/mm/dd hh:mm:ss.ffff t zzz" převede datum na řetězcovou reprezentaci ve tvaru "2008/11/15 07:45:00.0000 P-08: 00" pro jazykovou verzi en-US. Podobně, vlastní formátovací řetězec "0000" převede celočíselnou hodnotu 12 na "0012". Úplný seznam vlastních formátovacích řetězců naleznete v tématu [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) a [vlastní číselné formátovací řetězce](../../../docs/standard/base-types/custom-numeric-format-strings.md).

Pokud formátovací řetězec obsahuje jeden vlastní specifikátor formátu, měl by být tento specifikátor formátu uvozen symbolem procenta (%), aby nedocházelo k záměně se standardním specifikátorem formátu. V následujícím příkladu je použit vlastní specifikátor formátu "M" pro zobrazení jednociferného nebo dvojciferného čísla měsíce konkrétního data.

[!code-csharp[Conceptual.Formatting.Overview#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/singlecustom1.cs#8)]
[!code-vb[Conceptual.Formatting.Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/singlecustom1.vb#8)]

Mnoho standardních formátovacích řetězců pro hodnoty data a času jsou zástupci pro vlastní formátovací řetězce, které jsou definovány vlastnostmi objektu <xref:System.Globalization.DateTimeFormatInfo>. Vlastní formátovací řetězce také nabízejí značnou flexibilitu při poskytování formátování definovaného aplikací pro číselné hodnoty nebo pro hodnoty data a času. Kombinováním více vlastních specifikátorů formátu do jediného vlastního formátovacího řetězce můžete nadefinovat vlastní výsledný řetězec pro číselné hodnoty i pro hodnoty data a času. V následujícím příkladu je definován vlastní formátovací řetězec, který zobrazuje den v týdnu v závorkách za názvem měsíce, dnem a rokem.

[!code-csharp[Conceptual.Formatting.Overview#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/custom1.cs#9)]
[!code-vb[Conceptual.Formatting.Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/custom1.vb#9)]

Následující příklad definuje vlastní formátovací řetězec, který zobrazí hodnotu <xref:System.Int64> jako standardní, sedmičíselné americké telefonní číslo spolu se směrovým číslem oblasti.

[!code-csharp[Conceptual.Formatting.Overview#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/telnumber1.cs#21)]
[!code-vb[Conceptual.Formatting.Overview#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/telnumber1.vb#21)]

Ačkoli standardní formátovací řetězce mohou zpracovat většinu požadavků na formátování typů definovaných vaší aplikací, můžete také definovat vlastní specifikátory formátu pro formátování těchto typů.

### <a name="format-strings-and-net-types"></a>Řetězce formátu a typy .NET

Všechny číselné typy (tj. <xref:System.Byte>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>a <xref:System.Numerics.BigInteger> typy) a také <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, <xref:System.Guid>a všechny typy výčtu, podporují formátování pomocí formátovacích řetězců. Informace o konkrétních formátovacích řetězcích podporovaných jednotlivými typy naleznete v následujících tématech:

|Název|Definice|
|-----------|----------------|
|[Standardní řetězce číselného formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Popisuje standardní formátovací řetězce, které vytvářejí běžně používané řetězcové reprezentace číselných hodnot.|
|[Vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Popisuje vlastní formátovací řetězce, které vytvářejí formáty číselných hodnot specifické pro danou aplikaci.|
|[Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Popisuje standardní formátovací řetězce, které vytvářejí běžně používané řetězcové reprezentace <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty.|
|[Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Popisuje vlastní formátovací řetězce, které vytvářejí formáty pro <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty specifické pro aplikaci.|
|[Standardní řetězce formátu TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Popisuje standardní formátovací řetězce, které vytvářejí běžně používané řetězcové reprezentace časových intervalů.|
|[Vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Popisuje vlastní formátovací řetězce, které vytvářejí formáty časových intervalů specifické pro danou aplikaci.|
|[Výčet řetězců formátu](../../../docs/standard/base-types/enumeration-format-strings.md)|Popisuje standardní formátovací řetězce, které slouží k vytvoření řetězcové reprezentace hodnot výčtu.|
|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|Popisuje standardní formátovací řetězce pro hodnoty <xref:System.Guid>.|

## <a name="culture-sensitive-formatting-with-format-providers"></a>Formátování zohledňující jazykovou verzi s poskytovateli formátu

I když specifikátory formátu umožňují přizpůsobit formátování objektů, vytváření smysluplné řetězcové reprezentace objektů často vyžaduje další informace o formátování. Například formátování čísla jako hodnoty měny pomocí standardního formátovacího řetězce "C" nebo vlastního formátovacího řetězce, jako je "$ #,#.00", vyžaduje mít přinejmenším k dispozici informace o správném symbolu měny, oddělovači skupin a oddělovači desetinných míst, aby mohly být zahrnuty do formátovaného řetězce. V rozhraní .NET jsou tyto dodatečné informace o formátování zpřístupněny prostřednictvím rozhraní <xref:System.IFormatProvider>, které je k dispozici jako parametr pro jedno nebo více přetížení `ToString` metody číselných typů a typů data a času. implementace <xref:System.IFormatProvider> jsou používány v rozhraní .NET pro podporu formátování specifického pro jazykovou verzi. Následující příklad ukazuje, jak se řetězcová reprezentace objektu mění, je-li formátována pomocí tří objektů <xref:System.IFormatProvider> představujících různé jazykové verze.

[!code-csharp[Conceptual.Formatting.Overview#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformatprovider1.cs#11)]
[!code-vb[Conceptual.Formatting.Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformatprovider1.vb#11)]

Rozhraní <xref:System.IFormatProvider> zahrnuje jednu metodu <xref:System.IFormatProvider.GetFormat%28System.Type%29>, která má jeden parametr určující typ objektu, který poskytuje informace o formátování. Pokud může metoda poskytnout objekt tohoto typu, vrátí jej. V opačném případě vrátí odkaz s hodnotou null (`Nothing` v Visual Basic).

<xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> je metoda zpětného volání. Při zavolání přetížení metody `ToString` obsahující parametr <xref:System.IFormatProvider>, je volána metoda <xref:System.IFormatProvider.GetFormat%2A> objektu <xref:System.IFormatProvider>. Metoda <xref:System.IFormatProvider.GetFormat%2A> je zodpovědná za vrácení objektu, který obsahuje nezbytné informace o formátování specifikované parametrem `formatType` metody `ToString`.

Několik metod formátování nebo převodu řetězce obsahuje parametr typu <xref:System.IFormatProvider>, ale v mnoha případech je při volání metody hodnota parametru ignorována. V následující tabulce jsou uvedeny některé metody formátování, které používají tento parametr a typ objektu <xref:System.Type>, který předávají metodě <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType>.

|Metoda|Typ parametru `formatType`|
|------------|------------------------------------|
|Metoda `ToString` pro numerické typy|<xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>|
|Metoda `ToString` pro typy data a času|<xref:System.Globalization.DateTimeFormatInfo?displayProperty=nameWithType>|
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|

> [!NOTE]
> Metody `ToString` pro číselné typy a typy data a času jsou přetížené a pouze některá přetížení obsahují parametr <xref:System.IFormatProvider>. Pokud metoda nemá parametr typu <xref:System.IFormatProvider>, je místo něho předán objekt vrácený vlastností <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>. Například volání výchozí metody <xref:System.Int32.ToString?displayProperty=nameWithType> nakonec vyústí ve volání metod, jako je následující: `Int32.ToString("G", System.Globalization.CultureInfo.CurrentCulture)`.

Rozhraní .NET poskytuje tři třídy, které implementují <xref:System.IFormatProvider>:

- Třída <xref:System.Globalization.DateTimeFormatInfo>, která poskytuje informace o formátování hodnot data a času pro určitou jazykovou verzi. Jeho implementace <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> vrátí instanci sebe sama.

- Třída <xref:System.Globalization.NumberFormatInfo>, která poskytuje informace o formátování čísel pro konkrétní jazykovou verzi. Jeho implementace <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> vrátí instanci sebe sama.

- <xref:System.Globalization.CultureInfo>. Jeho implementace <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> může vrátit objekt <xref:System.Globalization.NumberFormatInfo>, který poskytuje informace o formátování čísel, nebo objekt <xref:System.Globalization.DateTimeFormatInfo>, který poskytuje informace o formátování hodnot data a času.

Můžete také implementovat vlastní třídu poskytovatele formátu pro nahrazení kterékoli z těchto tříd. Implementace vaši metody <xref:System.IFormatProvider.GetFormat%2A> však musí vrátit objekt typu, který je uveden v předchozí tabulce, pokud má poskytovat informace o formátování metodě `ToString`.

### <a name="culture-sensitive-formatting-of-numeric-values"></a>Formátování číselných hodnot zohledňující jazykovou verzi

Ve výchozím nastavení je formátování číselných hodnot závislé na jazykové verzi. Nezadáte-li při volání metody pro formátování jazykovou verzi, použijí se formátovací konvence aktuální jazykové verze vlákna. To je znázorněno v následujícím příkladu, který čtyřikrát změní aktuální jazykovou verzi vlákna a zavolá metodu <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>. V každém z těchto případů odráží výsledný řetězec formátovací úmluvy aktuální jazykové verze. Důvodem je, že metody `ToString` a `ToString(String)` obalují volání metod `ToString(String, IFormatProvider)` každého číselného typu.

[!code-csharp[Conceptual.Formatting.Overview#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific3.cs#19)]
[!code-vb[Conceptual.Formatting.Overview#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific3.vb#19)]

Číselnou hodnotu lze pro konkrétní jazykovou verzi formátovat také voláním přetížení `ToString` obsahujícího parametr `provider` a předáním některého z následujících objektů:

- Objekt <xref:System.Globalization.CultureInfo>, který představuje jazykovou verzi, jejíž úmluvy formátování se mají použít. Jeho metoda <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> vrátí hodnotu vlastnosti <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType>, kterou je objekt <xref:System.Globalization.NumberFormatInfo> poskytující informace o formátování číselných hodnot specifické pro jazykovou verzi.

- Objekt <xref:System.Globalization.NumberFormatInfo>, který definuje, jaké konvence formátování specifické pro jazykovou verzi mají být použity. Jeho metoda <xref:System.Globalization.NumberFormatInfo.GetFormat%2A> vrátí instanci sebe sama.

Následující příklad používá pro formátování čísla s plovoucí desetinnou čárkou objekty <xref:System.Globalization.NumberFormatInfo> představující jazykové verze Angličtina (Spojené státy) a Angličtina (Velká Británie) spolu s francouzskými a ruskými neutrálními verzemi.

[!code-csharp[Conceptual.Formatting.Overview#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific4.cs#20)]
[!code-vb[Conceptual.Formatting.Overview#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific4.vb#20)]

### <a name="culture-sensitive-formatting-of-date-and-time-values"></a>Formátování hodnot data a času zohledňující jazykovou verzi

Ve výchozím nastavení je formátování hodnot data a času závislé na jazykové verzi. Nezadáte-li při volání metody pro formátování jazykovou verzi, použijí se formátovací konvence aktuální jazykové verze vlákna. To je znázorněno v následujícím příkladu, který čtyřikrát změní aktuální jazykovou verzi vlákna a zavolá metodu <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>. V každém z těchto případů odráží výsledný řetězec formátovací úmluvy aktuální jazykové verze. Důvodem je, že metody <xref:System.DateTime.ToString?displayProperty=nameWithType>, <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType> a <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> obalují volání metod <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> a <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>.

[!code-csharp[Conceptual.Formatting.Overview#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific1.cs#17)]
[!code-vb[Conceptual.Formatting.Overview#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific1.vb#17)]

Hodnotu data a času lze pro konkrétní jazykovou verzi formátovat také voláním přetížení <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> obsahujícího parametr `provider` a předáním některého z následujících objektů:

- Objekt <xref:System.Globalization.CultureInfo>, který představuje jazykovou verzi, jejíž úmluvy formátování se mají použít. Jeho metoda <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> vrátí hodnotu vlastnosti <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>, kterou je objekt <xref:System.Globalization.DateTimeFormatInfo> poskytující informace o formátování hodnot data a času specifické pro jazykovou verzi.

- Objekt <xref:System.Globalization.DateTimeFormatInfo>, který definuje, jaké konvence formátování specifické pro jazykovou verzi mají být použity. Jeho metoda <xref:System.Globalization.DateTimeFormatInfo.GetFormat%2A> vrátí instanci sebe sama.

Následující příklad používá pro formátování data objekty <xref:System.Globalization.DateTimeFormatInfo> představující jazykové verze Angličtina (Spojené státy) a Angličtina (Velká Británie) spolu s francouzskými a ruskými neutrálními verzemi.

[!code-csharp[Conceptual.Formatting.Overview#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific2.cs#18)]
[!code-vb[Conceptual.Formatting.Overview#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific2.vb#18)]

## <a name="the-iformattable-interface"></a>Rozhraní IFormattable

Obvykle typy, které přetěžují metodu `ToString` pomocí formátovacího řetězce a parametru <xref:System.IFormatProvider>, také implementují rozhraní <xref:System.IFormattable>. Toto rozhraní má jediný člen <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> obsahující jak formátovací řetězec tak i poskytovatele formátu jako parametry.

Implementování rozhraní <xref:System.IFormattable> třídou definovanou vaší aplikací nabízí dvě výhody:

- Podpora převodu řetězce pomocí třídy <xref:System.Convert>. Volání metod <xref:System.Convert.ToString%28System.Object%29?displayProperty=nameWithType> a <xref:System.Convert.ToString%28System.Object%2CSystem.IFormatProvider%29?displayProperty=nameWithType> volá automaticky vaši implementaci <xref:System.IFormattable>.

- Podpora pro složené formátování. Pokud položka formátu, která obsahuje formátovací řetězec, slouží k formátování vašeho vlastního typu, modul CLR (Common Language Runtime) automaticky volá vaši implementaci <xref:System.IFormattable> a předává jí formátovací řetězec. Další informace o složeném formátování s metodami, jako jsou <xref:System.String.Format%2A?displayProperty=nameWithType> nebo <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, naleznete v oddílu [složené formátování](#composite-formatting) .

Následující příklad definuje třídu `Temperature`, která implementuje rozhraní <xref:System.IFormattable>. Podporuje specifikátory formátu "C" nebo "G" pro zobrazení teploty ve stupních Celsia, specifikátor formátu "F" pro zobrazení teploty ve stupních Fahrenheita a specifikátor formátu "K" pro zobrazení teploty ve stupních Kelvinů.

[!code-csharp[Conceptual.Formatting.Overview#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#12)]
[!code-vb[Conceptual.Formatting.Overview#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#12)]

V následujícím příkladu je vytvořena instance objektu `Temperature`. Potom je volána metoda <xref:System.Convert.ToString%2A> a je použito několik složených formátovacích řetězců pro získání různých řetězcových reprezentací objektu `Temperature`. Každé z těchto volání metod volá implementaci <xref:System.IFormattable> třídy `Temperature`.

[!code-csharp[Conceptual.Formatting.Overview#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#13)]
[!code-vb[Conceptual.Formatting.Overview#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#13)]

## <a name="composite-formatting"></a>Složené formátování

Některé metody, jako je například <xref:System.String.Format%2A?displayProperty=nameWithType> a <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, podporují také složené formátování. Složený formátovací řetězec je druh šablony, která vrátí jediný řetězec, který zahrnuje řetězcové vyjádření žádného, jednoho nebo více objektů. Každý objekt je reprezentován ve složeném formátovacím řetězci indexovanou položkou formátu. Index položky formátu odpovídá pozici objektu, který představuje v seznamu parametrů metody. Indexy jsou počítány od nuly. Například v následujícím volání metody <xref:System.String.Format%2A?displayProperty=nameWithType> je první položka formátu `{0:D}` nahrazena řetězcovou reprezentací `thatDate`; druhá položka formátu `{1}` je nahrazena řetězcovou reprezentací `item1`; a třetí položka formátu `{2:C2}` je nahrazena řetězcovou reprezentací `item1.Value`.

[!code-csharp[Conceptual.Formatting.Overview#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite1.cs#14)]
[!code-vb[Conceptual.Formatting.Overview#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite1.vb#14)]

Kromě nahrazení položky formátu řetězcovou reprezentací odpovídajícího objektu je také možné řídit následující:

- Konkrétní způsob, jakým je objekt reprezentován jako řetězec, pokud objekt implementuje rozhraní <xref:System.IFormattable> a podporuje řetězce formátu. Provedete to tak, že použijete index položky formátu s `:` (dvojtečka) následovaný platným formátovacím řetězcem. Předchozí příklad tohoto vedl naformátováním hodnoty data pomocí formátovacího řetězce "d" (vzor krátkého formátu data) (například `{0:d}`) a formátováním číselné hodnoty pomocí formátovacího řetězce "C2" (např. `{2:C2}` představuje číslo jako hodnotu měny se dvěma zlomky desítkových čísel.

- Šířka pole obsahujícího řetězcovou reprezentaci objektu a zarovnání řetězcové reprezentace v tomto poli. Provedete to tak, že použijete index položky formátu s `,` (čárka) následovaný šířkou pole. Řetězec je zarovnán vpravo v poli, pokud je šířka pole kladná hodnota a je zarovnána doleva, pokud je šířka pole záporná. Následující příklad Zarovná hodnoty data do pole o 20 znacích a v poli se 11 znaky Zarovná desítkové číslo s jednou zlomkovou hodnotou.

     [!code-csharp[Conceptual.Formatting.Overview#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite2.cs#22)]
     [!code-vb[Conceptual.Formatting.Overview#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite2.vb#22)]

     Všimněte si, že pokud jsou přítomny buď komponenty řetězce zarovnání, a formátovací řetězec komponenty, předchozí předchází druhý (například `{0,-20:g}`.

Další informace o složeném formátování najdete v tématu [složené formátování](../../../docs/standard/base-types/composite-formatting.md).

## <a name="custom-formatting-with-icustomformatter"></a>Vlastní formátování pomocí ICustomFormatter

Dvě metody pro složené formátování, jako například <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> a <xref:System.Text.StringBuilder.AppendFormat%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, zahrnují parametr poskytovatele formátu, který podporuje vlastní formátování. Když je zavolána některá z těchto metod formátování, předá objekt <xref:System.Type>, který představuje rozhraní <xref:System.ICustomFormatter>, metodě <xref:System.IFormatProvider.GetFormat%2A> poskytovatele formátu. Metoda <xref:System.IFormatProvider.GetFormat%2A> je pak zodpovědná za navrácení implementace <xref:System.ICustomFormatter>, která poskytuje vlastní formátování.

Rozhraní <xref:System.ICustomFormatter> obsahuje jedinou metodu <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29>, která je volána automaticky metodou složeného formátování pro každou položku formátu ve složeném formátovacím řetězci. Metoda <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29> má tři parametry: formátovací řetězec představující argument `formatString` v položce formátu, objekt pro formátování a objekt <xref:System.IFormatProvider> poskytující služby formátování. Obvykle třída, která implementuje <xref:System.ICustomFormatter> také implementuje <xref:System.IFormatProvider>, a proto je tento poslední parametr odkaz na danou třídu vlastního formátování. Metoda vrátí řetězcovou reprezentaci vlastního formátování objektu, který má být formátován. Pokud metoda nemůže objekt zformátovat, měl by být vrácen nulový odkaz (`Nothing` v jazyce Visual Basic).

Následující příklad uvádí implementaci <xref:System.ICustomFormatter> s názvem `ByteByByteFormatter` zobrazující celočíselné hodnoty jako sekvenci dvouciferných šestnáctkových hodnot následovanou mezerou.

[!code-csharp[Conceptual.Formatting.Overview#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#15)]
[!code-vb[Conceptual.Formatting.Overview#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#15)]

V následujícím příkladu je třída `ByteByByteFormatter` použita pro formátování celočíselné hodnoty. Všimněte si, že metoda <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> je ve druhém volání metody <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> volána více než jednou a že výchozí zprostředkovatel <xref:System.Globalization.NumberFormatInfo> je použit ve třetí volání metody, protože.`ByteByByteFormatter.Format` Metoda nerozpozná formátovací řetězec "N0" a vrátí odkaz s hodnotou null (`Nothing` v Visual Basic).

[!code-csharp[Conceptual.Formatting.Overview#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#16)]
[!code-vb[Conceptual.Formatting.Overview#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#16)]

## <a name="related-topics"></a>Příbuzná témata

|Název|Definice|
|-----------|----------------|
|[Standardní řetězce číselného formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Popisuje standardní formátovací řetězce, které vytvářejí běžně používané řetězcové reprezentace číselných hodnot.|
|[Vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Popisuje vlastní formátovací řetězce, které vytvářejí formáty číselných hodnot specifické pro danou aplikaci.|
|[Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Popisuje standardní formátovací řetězce, které vytvářejí běžně používané řetězcové reprezentace hodnot <xref:System.DateTime>.|
|[Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Popisuje vlastní formátovací řetězce, které vytvářejí formáty hodnot <xref:System.DateTime> specifické pro danou aplikaci.|
|[Standardní řetězce formátu TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Popisuje standardní formátovací řetězce, které vytvářejí běžně používané řetězcové reprezentace časových intervalů.|
|[Vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Popisuje vlastní formátovací řetězce, které vytvářejí formáty časových intervalů specifické pro danou aplikaci.|
|[Výčet řetězců formátu](../../../docs/standard/base-types/enumeration-format-strings.md)|Popisuje standardní formátovací řetězce, které slouží k vytvoření řetězcové reprezentace hodnot výčtu.|
|[Složené formátování](../../../docs/standard/base-types/composite-formatting.md)|Popisuje postup vložení jedné nebo více formátovaných hodnot do řetězce. Řetězec lze následně zobrazit na konzole nebo zapsat do datového proudu.|
|[Provádění operací formátování](../../../docs/standard/base-types/performing-formatting-operations.md)|Seznam témat, která poskytují podrobné pokyny pro provádění určitých operací formátování.|
|[Analýza řetězců](../../../docs/standard/base-types/parsing-strings.md)|Popisuje, jak inicializovat objekty s hodnotami popsanými řetězcovou interpretací těchto objektů. Analýza je inverzní operace k formátování.|

## <a name="reference"></a>Odkaz

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- <xref:System.ICustomFormatter?displayProperty=nameWithType>
