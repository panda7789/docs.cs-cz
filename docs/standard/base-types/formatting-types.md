---
title: Typy formátování v rozhraní .NET
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
ms.openlocfilehash: a1f4d9107427140bcfa6b49bc8a850432fb204f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75348256"
---
# <a name="format-types-in-net"></a>Typy formátování v rozhraní .NET

Formátování je proces převodu instance třídy, struktury nebo hodnoty výčtu na její řetězcovou reprezentaci, často tak, aby výsledný řetězec mohl být zobrazen uživatelům nebo reserializován za účelem obnovení původního datového typu. Tento převod může představovat řadu výzev:

- Způsob, jakým jsou hodnoty uloženy interně, nemusí nutně odrážet způsob, jakým je uživatelé chtějí zobrazit. Telefonní číslo může být například uloženo ve formuláři 8009999999, což není uživatelsky přívětivé. Místo toho by měl být zobrazen jako 800-999-9999. Příklad, který tímto způsobem formátuje číslo, najdete v části [Vlastní formátovací řetězce.](#custom-format-strings)

- Někdy převod objektu na jeho řetězcovou reprezentaci není intuitivní. Například není jasné, jak by se měla zobrazit řetězcová reprezentace objektu Temperature nebo Objektu Person. Příklad, který formátuje objekt Temperature různými způsoby, najdete v části [Standardní formát řetězce.](#standard-format-strings)

- Hodnoty často vyžadují formátování citlivé na jazykovou verzi. Například v aplikaci, která používá čísla k odrážení peněžních hodnot, by číselné řetězce měly obsahovat symbol měny aktuální jazykové verze, oddělovač skupin (který je ve většině kultur oddělovačem tisíců) a desetinný symbol. Příklad naleznete v části [Formátování s informacemi o jazykové verzi s poskytovateli formátů.](#culture-sensitive-formatting-with-format-providers)

- Aplikace může mít zobrazit stejnou hodnotu různými způsoby. Aplikace může například představovat člen výčtu zobrazením řetězcové reprezentace jeho názvu nebo zobrazením jeho základní hodnoty. Příklad, který formátuje člen <xref:System.DayOfWeek> výčtu různými způsoby, naleznete v části [Standardní formát řetězce.](#standard-format-strings)

> [!NOTE]
> Formátování převede hodnotu typu na řetězcovou reprezentaci. Analýza je inverzní formátování. Operace analýzy vytvoří instanci datového typu z jeho řetězcové reprezentace. Informace o převodu řetězců na jiné datové typy naleznete v [tématu Analýza řetězců](../../../docs/standard/base-types/parsing-strings.md).

Rozhraní .NET poskytuje podporu bohatého formátování, která vývojářům umožňuje tyto požadavky řešit.

## <a name="formatting-in-net"></a>Formátování v rozhraní .NET

Základní mechanismus formátování je výchozí implementace <xref:System.Object.ToString%2A?displayProperty=nameWithType> metody, která je popsána v [části Výchozí formátování pomocí metody ToString](#default-formatting-using-the-tostring-method) dále v tomto tématu. Rozhraní .NET však poskytuje několik způsobů, jak upravit a rozšířit svou podporu výchozího formátování. Patří mezi ně například:

- Přepsání <xref:System.Object.ToString%2A?displayProperty=nameWithType> metody k definování vlastní řetězcové reprezentace hodnoty objektu. Další informace naleznete v části [Přepsat metodu ToString](#override-the-tostring-method) dále v tomto tématu.

- Definování specifikátorů formátu, které umožňují řetězcové reprezentaci hodnoty objektu mít více forem. Například specifikátor formátu "X" v následujícím příkazu převede celé číslo na řetězcovou reprezentaci šestnáctkové hodnoty.

     [!code-csharp[Conceptual.Formatting.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#3)]
     [!code-vb[Conceptual.Formatting.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#3)]

     Další informace o specifikátorech formátu naleznete v části [ToString Method a Format Strings](#the-tostring-method-and-format-strings) .

- Pomocí zprostředkovatelů formátu využít formátování konvencí konkrétní jazykové verze. Například následující příkaz zobrazí hodnotu měny pomocí konvencí formátování jazykové verze en US.

     [!code-csharp[Conceptual.Formatting.Overview#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#10)]
     [!code-vb[Conceptual.Formatting.Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#10)]

     Další informace o formátování s poskytovateli formátů naleznete v části [Zprostředkovatelé formátu.](#culture-sensitive-formatting-with-format-providers)

- Implementace <xref:System.IFormattable> rozhraní pro podporu převodu <xref:System.Convert> řetězce s třídou a složeným formátováním. Další informace naleznete v části [IFormattable Interface.](#the-iformattable-interface)

- Použití složeného formátování k vložení řetězcové reprezentace hodnoty do většího řetězce. Další informace naleznete v části [Složené formátování.](#composite-formatting)

- Implementace <xref:System.ICustomFormatter> a <xref:System.IFormatProvider> poskytnutí kompletního řešení vlastního formátování. Další informace naleznete v části [Vlastní formátování s iCustomFormatter.](#custom-formatting-with-icustomformatter)

Následující části zkoumají tyto metody pro převod objektu na jeho řetězcovou reprezentaci.

## <a name="default-formatting-using-the-tostring-method"></a>Výchozí formátování pomocí metody ToString

Každý typ, který <xref:System.Object?displayProperty=nameWithType> je odvozen z `ToString` automaticky zdědí metodu bez parametrů, která ve výchozím nastavení vrátí název typu. Následující příklad ilustruje výchozí `ToString` metodu. Definuje třídu s `Automobile` názvem, která nemá žádnou implementaci. Když je instance třídy a `ToString` její metoda je volána, zobrazí její název typu. Všimněte `ToString` si, že metoda není explicitně volána v příkladu. Metoda <xref:System.Console.WriteLine%28System.Object%29?displayProperty=nameWithType> implicitně volá `ToString` metodu objektu, který jí byl předán jako argument.

[!code-csharp[Conceptual.Formatting.Overview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/default1.cs#1)]
[!code-vb[Conceptual.Formatting.Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/default1.vb#1)]

> [!WARNING]
> Počínaje windows 8.1, prostředí Windows <xref:Windows.Foundation.IStringable> Runtime obsahuje rozhraní s jedinou [metodou, IStringable.ToString](xref:Windows.Foundation.IStringable.ToString%2A), který poskytuje výchozí podporu formátování. Doporučujeme však spravované typy neimplementují `IStringable` rozhraní. Další informace naleznete v části "Prostředí `IStringable` Windows Runtime <xref:System.Object.ToString%2A?displayProperty=nameWithType> a rozhraní" na referenční stránce.

Vzhledem k tomu, že jsou <xref:System.Object>odvozeny všechny typy než rozhraní , je tato funkce automaticky poskytována vašim vlastním třídám nebo strukturám. Funkce nabízené výchozí `ToString` metodou je však omezená: Přestože identifikuje typ, neposkytne žádné informace o instanci typu. Chcete-li poskytnout řetězcovou reprezentaci objektu, který poskytuje `ToString` informace o tomto objektu, musíte přepsat metodu.

> [!NOTE]
> Struktury dědí <xref:System.ValueType>z , který je <xref:System.Object>odvozen z . I <xref:System.ValueType> když <xref:System.Object.ToString%2A?displayProperty=nameWithType>přepíše , jeho implementace je identická.

## <a name="override-the-tostring-method"></a>Přepsat metodu ToString

Zobrazení názvu typu je často omezené použití a neumožňuje spotřebitelům typů odlišit jednu instanci od druhé. Můžete však přepsat `ToString` metodu a poskytnout tak užitečnější reprezentaci hodnoty objektu. Následující příklad definuje `Temperature` objekt a přepíše jeho `ToString` metodu pro zobrazení teploty ve stupních Celsia.

[!code-csharp[Conceptual.Formatting.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/overrides1.cs#2)]
[!code-vb[Conceptual.Formatting.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/overrides1.vb#2)]

V rozhraní .NET byla `ToString` metoda každého typu primitivní hodnoty přepsána tak, aby zobrazovala hodnotu objektu namísto jeho názvu. V následující tabulce je uvedeno přepsání pro každý primitivní typ. Všimněte si, že většina přepsaných metod volat jiné přetížení `ToString` metody a předat ji specifikátor formátu "G", který definuje obecný formát pro jeho typ a <xref:System.IFormatProvider> objekt, který představuje aktuální jazykovou verzi.

|Typ|Přepsání řetězce|
|----------|-----------------------|
|<xref:System.Boolean>|Vrátí <xref:System.Boolean.TrueString?displayProperty=nameWithType> buď <xref:System.Boolean.FalseString?displayProperty=nameWithType>nebo .|
|<xref:System.Byte>|Volání `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` k <xref:System.Byte> formátování hodnoty pro aktuální jazykovou verzi.|
|<xref:System.Char>|Vrátí znak jako řetězec.|
|<xref:System.DateTime>|Volání `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` k formátování hodnoty data a času pro aktuální jazykovou verzi.|
|<xref:System.Decimal>|Volání `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` k <xref:System.Decimal> formátování hodnoty pro aktuální jazykovou verzi.|
|<xref:System.Double>|Volání `Double.ToString("G", NumberFormatInfo.CurrentInfo)` k <xref:System.Double> formátování hodnoty pro aktuální jazykovou verzi.|
|<xref:System.Int16>|Volání `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` k <xref:System.Int16> formátování hodnoty pro aktuální jazykovou verzi.|
|<xref:System.Int32>|Volání `Int32.ToString("G", NumberFormatInfo.CurrentInfo)` k <xref:System.Int32> formátování hodnoty pro aktuální jazykovou verzi.|
|<xref:System.Int64>|Volání `Int64.ToString("G", NumberFormatInfo.CurrentInfo)` k <xref:System.Int64> formátování hodnoty pro aktuální jazykovou verzi.|
|<xref:System.SByte>|Volání `SByte.ToString("G", NumberFormatInfo.CurrentInfo)` k <xref:System.SByte> formátování hodnoty pro aktuální jazykovou verzi.|
|<xref:System.Single>|Volání `Single.ToString("G", NumberFormatInfo.CurrentInfo)` k <xref:System.Single> formátování hodnoty pro aktuální jazykovou verzi.|
|<xref:System.UInt16>|Volání `UInt16.ToString("G", NumberFormatInfo.CurrentInfo)` k <xref:System.UInt16> formátování hodnoty pro aktuální jazykovou verzi.|
|<xref:System.UInt32>|Volání `UInt32.ToString("G", NumberFormatInfo.CurrentInfo)` k <xref:System.UInt32> formátování hodnoty pro aktuální jazykovou verzi.|
|<xref:System.UInt64>|Volání `UInt64.ToString("G", NumberFormatInfo.CurrentInfo)` k <xref:System.UInt64> formátování hodnoty pro aktuální jazykovou verzi.|

## <a name="the-tostring-method-and-format-strings"></a>Metoda ToString a formátovací řetězce

Spoléhání se `ToString` na výchozí `ToString` metodu nebo přepsání je vhodné, pokud má objekt reprezentaci jednoho řetězce. Hodnota objektu však má často více reprezentací. Například teplota může být vyjádřena ve stupních Fahrenheita, stupních Celsia nebo kelvinech. Podobně celá hodnota 10 může být reprezentována mnoha způsoby, včetně 10, 10.0, 1.0e01 nebo $10.00.

Chcete-li povolit jednu hodnotu mít více řetězcových reprezentací, rozhraní .NET používá formátovací řetězce. Formátovací řetězec je řetězec, který obsahuje jeden nebo více předdefinovaných specifikátorů formátu, což jsou jednotlivé znaky nebo skupiny znaků, které definují, `ToString` jak má metoda formátovat svůj výstup. Formátovací řetězec je pak předán jako parametr `ToString` metodě objektu a určuje, jak by se měla zobrazit řetězcová reprezentace hodnoty tohoto objektu.

Všechny číselné typy, typy dat a času a typy výčtů v rozhraní .NET podporují předdefinovanou sadu specifikátorů formátu. Formátovací řetězce můžete také použít k definování více řetězcových reprezentací datových typů definovaných aplikací.

### <a name="standard-format-strings"></a>Standardní formátovací řetězce

Standardní formátovací řetězec obsahuje specifikátor jednoho formátu, což je abecední znak, který definuje řetězcovou reprezentaci objektu, na který je použit, spolu s volitelným specifikátorem přesnosti, který ovlivňuje počet číslic zobrazených v výsledek řetězce. Pokud je specifikátor přesnosti vynechán nebo není podporován, standardní specifikátor formátu je ekvivalentní standardnímu formátovacímu řetězci.

Rozhraní .NET definuje sadu specifikátorů standardního formátu pro všechny číselné typy, všechny typy dat a času a všechny typy výčtu. Například každá z těchto kategorií podporuje specifikátor standardního formátu "G", který definuje obecnou řetězcovou reprezentaci hodnoty tohoto typu.

Standardní formátovací řetězce pro typy výčtu přímo řídí řetězcovou reprezentaci hodnoty. Formátovací řetězce předané `ToString` metodě hodnoty výčtu určují, zda je hodnota zobrazena pomocí názvu řetězce (specifikátory formátu "G" a "F"), základní integrální hodnota (specifikátor formátu D) nebo jeho šestnáctková hodnota (specifikátor formátu "X"). Následující příklad ilustruje použití standardních formátovacích <xref:System.DayOfWeek> řetězců pro formátování hodnoty výčtu.

[!code-csharp[Conceptual.Formatting.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/standard1.cs#4)]
[!code-vb[Conceptual.Formatting.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/standard1.vb#4)]

Informace o formátovacích řetězcích výčtu naleznete v [tématu Formátových řetězců výčtu](../../../docs/standard/base-types/enumeration-format-strings.md).

Standardní formátovací řetězce pro číselné typy obvykle definují výsledný řetězec, jehož přesný vzhled je řízen jednou nebo více hodnotami vlastností. For example, the "C" format specifier formats a number as a currency value. Při volání `ToString` metody s specifikátorem formátu "C" jako jediným parametrem se k <xref:System.Globalization.NumberFormatInfo> definování řetězcové reprezentace číselné hodnoty používají následující hodnoty vlastností z objektu aktuální jazykové verze:

- Vlastnost, <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A> která určuje symbol měny aktuální jazykové verze.

- Vlastnost <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> <xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A> or, která vrací celé číslo, které určuje následující:

  - Umístění symbolu měny.

  - Určuje, zda jsou záporné hodnoty označeny úvodním záporným znaménkem, koncovým záporným znaménkem nebo závorky.

  - Určuje, zda se mezi číselnou hodnotou a symbolem měny zobrazí mezera.

- Vlastnost, <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A> která definuje počet desetinných míst ve výsledném řetězci.

- Vlastnost, <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A> která definuje symbol oddělovače desetinných míst ve výsledném řetězci.

- Vlastnost, <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A> která definuje symbol oddělovače skupiny.

- Vlastnost, <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A> která definuje počet číslic v každé skupině nalevo od desetinného místa.

- Vlastnost, <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> která určuje záporné znaménko použité ve výsledném řetězci, pokud závorky nejsou použity k označení záporných hodnot.

Kromě toho číselné formátovací řetězce mohou obsahovat specifikátor přesnosti. Význam tohoto specifikátoru závisí na formátovacím řetězci, se kterým se používá, ale obvykle označuje celkový počet číslic nebo počet desetinných číslic, které by se měly objevit ve výsledném řetězci. Například následující příklad používá standardní číselný řetězec "X4" a specifikátor přesnosti k vytvoření řetězcové hodnoty, která má čtyři šestnáctkové číslice.

[!code-csharp[Conceptual.Formatting.Overview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/precisionspecifier1.cs#6)]
[!code-vb[Conceptual.Formatting.Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/precisionspecifier1.vb#6)]

Další informace o standardních číselných formátovacích řetězcích naleznete [v tématu Standardní číselné formátovací řetězce](../../../docs/standard/base-types/standard-numeric-format-strings.md).

Standardní formátovací řetězce pro hodnoty data a času jsou aliasy <xref:System.Globalization.DateTimeFormatInfo> pro vlastní formátovací řetězce uložené určitou vlastností. Například volání `ToString` metody hodnoty data a času s specifikátorem formátu "D" zobrazí datum a čas pomocí vlastního <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> formátovacího řetězce uloženého ve vlastnosti aktuální jazykové verze. (Další informace o vlastních formátovacích řetězcích naleznete v [další části](#custom-format-strings).) Následující příklad ilustruje tento vztah.

[!code-csharp[Conceptual.Formatting.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/alias1.cs#5)]
[!code-vb[Conceptual.Formatting.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/alias1.vb#5)]

Další informace o standardních formátovacích řetězcích data a času naleznete [v tématu Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md).

Standardní formátovací řetězce můžete také použít k definování řetězcové reprezentace objektu definovaného aplikací, který je vytvořen `ToString(String)` metodou objektu. Můžete definovat konkrétní specifikátory standardního formátu, které objekt podporuje, a můžete určit, zda se jedná o malá a velká písmena nebo malá a velká písmena. Implementace `ToString(String)` metody by měla podporovat následující:

- Specifikátor formátu "G", který představuje obvyklý nebo běžný formát objektu. Parametrless přetížení `ToString` metody objektu by měl `ToString(String)` volat jeho přetížení a předat jej "G" standardní formát ovací řetězec.

- Podpora specifikátoru formátu, který se rovná`Nothing` nulovému odkazu (v jazyce Visual Basic). Specifikátor formátu, který se rovná nulovému odkazu, by měl být považován za ekvivalentní specifikátoru formátu "G".

Třída může `Temperature` například interně ukládat teplotu ve stupních Celsia a `Temperature` používat specifikátory formátu k reprezentaci hodnoty objektu ve stupních Celsia, stupních Fahrenheita a kelvinech. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.Formatting.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/appstandard1.cs#7)]
[!code-vb[Conceptual.Formatting.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/appstandard1.vb#7)]

### <a name="custom-format-strings"></a>Vlastní řetězce formátování

Kromě standardních formátovacích řetězců definuje rozhraní .NET vlastní formátovací řetězce pro číselné hodnoty i hodnoty data a času. Vlastní formátovací řetězec se skládá z jednoho nebo více vlastních specifikátorů formátu, které definují řetězcovou reprezentaci hodnoty. Například vlastní řetězec formátu data a času "yyyy/mm/dd hh:mm:ss.ffff t zzz" převede datum na jeho řetězcovou reprezentaci ve tvaru "2008/11/15 07:45:00.000P -08:00" pro jazykovou verzi en US. Podobně vlastní formátovací řetězec "0000" převede celá hodnota 12 na "0012". Úplný seznam vlastních formátovacích řetězců naleznete [v tématu Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) a Vlastní [číselné formátovací řetězce](../../../docs/standard/base-types/custom-numeric-format-strings.md).

Pokud se formátovací řetězec skládá z jednoho vlastního specifikátoru formátu, měl by specifikátor formátu předcházet procento (%) aby nedošlo k záměně se standardním specifikátorem formátu. Následující příklad používá vlastní specifikátor formátu "M" k zobrazení jednomístného nebo dvoumístného čísla měsíce určitého data.

[!code-csharp[Conceptual.Formatting.Overview#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/singlecustom1.cs#8)]
[!code-vb[Conceptual.Formatting.Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/singlecustom1.vb#8)]

Mnoho standardních formátovacích řetězců pro hodnoty data a času jsou aliasy <xref:System.Globalization.DateTimeFormatInfo> pro vlastní formátovací řetězce, které jsou definovány vlastnostmi objektu. Vlastní formátovací řetězce také nabízejí značnou flexibilitu při poskytování formátování definovaného aplikací pro číselné hodnoty nebo hodnoty data a času. Vlastní řetězce výsledků můžete definovat pro číselné hodnoty i hodnoty data a času kombinací více vlastních specifikátorů formátu do jednoho vlastního formátovacího řetězce. Následující příklad definuje vlastní formátovací řetězec, který zobrazuje den v týdnu v závorce za názvem měsíce, den a rok.

[!code-csharp[Conceptual.Formatting.Overview#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/custom1.cs#9)]
[!code-vb[Conceptual.Formatting.Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/custom1.vb#9)]

Následující příklad definuje vlastní formátovací řetězec, který zobrazuje hodnotu <xref:System.Int64> jako standardní sedmimístné telefonní číslo USA spolu s kódem oblasti.

[!code-csharp[Conceptual.Formatting.Overview#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/telnumber1.cs#21)]
[!code-vb[Conceptual.Formatting.Overview#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/telnumber1.vb#21)]

Přestože standardní formátovací řetězce obecně zvládnou většinu potřeb formátování pro typy definované aplikací, můžete také definovat vlastní specifikátory formátu pro formátování typů.

### <a name="format-strings-and-net-types"></a>Formátování řetězců a typů rozhraní .NET

Formát formátování formátovacími <xref:System.Byte>řetězci <xref:System.Double> <xref:System.Int16>podporují <xref:System.Int32> <xref:System.Int64>také <xref:System.SByte> <xref:System.Single> <xref:System.UInt16> <xref:System.UInt32> <xref:System.UInt64> <xref:System.Numerics.BigInteger> <xref:System.DateTime> <xref:System.DateTimeOffset> <xref:System.TimeSpan> <xref:System.Decimal> <xref:System.Guid>všechny číselné typy (tj. , , , , , , , , a typy), a také typy výčtů , podporují formátování pomocí formátovacích řetězců. Informace o konkrétních formátovacích řetězcích podporovaných jednotlivými typy naleznete v následujících tématech:

|Nadpis|Definice|
|-----------|----------------|
|[Standardní řetězce číselného formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Popisuje standardní formátovací řetězce, které vytvářejí běžně používané řetězcové reprezentace číselných hodnot.|
|[Vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Popisuje vlastní formátovací řetězce, které vytvářejí formáty specifické pro aplikaci pro číselné hodnoty.|
|[Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Popisuje standardní formátovací řetězce, které vytvářejí běžně <xref:System.DateTime> <xref:System.DateTimeOffset> používané řetězcové reprezentace a hodnoty.|
|[Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Popisuje vlastní formátovací řetězce, které vytvářejí <xref:System.DateTime> formáty specifické pro aplikaci a <xref:System.DateTimeOffset> hodnoty.|
|[Standardní řetězce formátu TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Popisuje standardní formátovací řetězce, které vytvářejí běžně používané řetězcové reprezentace časových intervalů.|
|[Vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Popisuje vlastní formátovací řetězce, které vytvářejí formáty specifické pro aplikaci pro časové intervaly.|
|[Výčet řetězců formátu](../../../docs/standard/base-types/enumeration-format-strings.md)|Popisuje standardní formátovací řetězce, které se používají k vytvoření řetězcových reprezentací hodnot výčtu.|
|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|Popisuje standardní formátovací <xref:System.Guid> řetězce pro hodnoty.|

## <a name="culture-sensitive-formatting-with-format-providers"></a>Formátování citlivé na jazykovou verzi s poskytovateli formátů

Přestože specifikátory formátu umožňují přizpůsobit formátování objektů, vytvoření smysluplné řetězcové reprezentace objektů často vyžaduje další informace o formátování. Například formátování čísla jako hodnoty měny pomocí standardního formátovacího řetězce "C" nebo vlastního formátovacího řetězce, například "$ #,#.00", vyžaduje minimálně informace o správném symbolu měny, oddělovači skupin a oddělovači desetinných míst, které mají být k dispozici pro zahrnutí do formátovaného řetězce. V rozhraní .NET jsou tyto další informace <xref:System.IFormatProvider> o formátování zpřístupněny prostřednictvím rozhraní, které je `ToString` k dispozici jako parametr pro jedno nebo více přetížení metody číselných typů a typů data a času. <xref:System.IFormatProvider>implementace se používají v rozhraní .NET pro podporu formátování specifické pro jazykovou verzi. Následující příklad ukazuje, jak se změní řetězcová reprezentace objektu, když je formátován třemi <xref:System.IFormatProvider> objekty, které představují různé jazykové verze.

[!code-csharp[Conceptual.Formatting.Overview#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformatprovider1.cs#11)]
[!code-vb[Conceptual.Formatting.Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformatprovider1.vb#11)]

Rozhraní <xref:System.IFormatProvider> obsahuje jednu <xref:System.IFormatProvider.GetFormat%28System.Type%29>metodu , která má jeden parametr, který určuje typ objektu, který poskytuje informace o formátování. Pokud metoda může poskytnout objekt tohoto typu, vrátí jej. V opačném případě vrátí`Nothing` odkaz null (v jazyce Visual Basic).

<xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType>je metoda zpětného volání. Při volání `ToString` přetížení metody, <xref:System.IFormatProvider> která obsahuje parametr, <xref:System.IFormatProvider.GetFormat%2A> volá <xref:System.IFormatProvider> metodu tohoto objektu. Metoda <xref:System.IFormatProvider.GetFormat%2A> je zodpovědná za vrácení objektu, který poskytuje potřebné informace `formatType` o formátování, `ToString` jak je určeno jeho parametrem, metodě.

Počet metod formátování nebo převodu řetězce zahrnuje <xref:System.IFormatProvider>parametr typu , ale v mnoha případech je hodnota parametru ignorována při volání metody. V následující tabulce jsou uvedeny některé metody formátování, které <xref:System.Type> používají parametr a <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> typ objektu, který předávají metodě.

|Metoda|Typ `formatType` parametru|
|------------|------------------------------------|
|`ToString`metoda číselných typů|<xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>|
|`ToString`způsob data a času|<xref:System.Globalization.DateTimeFormatInfo?displayProperty=nameWithType>|
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|

> [!NOTE]
> Metody `ToString` číselné typy a typy data a času jsou přetíženy a <xref:System.IFormatProvider> pouze některé z přetížení obsahují parametr. Pokud metoda nemá parametr typu <xref:System.IFormatProvider>, je místo toho <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> předán objekt, který je vrácen vlastností. Například volání výchozí <xref:System.Int32.ToString?displayProperty=nameWithType> metody nakonec vede k volání metody, například následující: `Int32.ToString("G", System.Globalization.CultureInfo.CurrentCulture)`.

.NET poskytuje tři <xref:System.IFormatProvider>třídy, které implementují :

- <xref:System.Globalization.DateTimeFormatInfo>, což je třída, která poskytuje informace o formátování pro hodnoty data a času pro konkrétní jazykovou verzi. Jeho <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementace vrátí samotnou instanci.

- <xref:System.Globalization.NumberFormatInfo>, třída, která poskytuje informace o číselném formátování pro určitou jazykovou verzi. Jeho <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementace vrátí samotnou instanci.

- <xref:System.Globalization.CultureInfo>. Jeho <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementace může <xref:System.Globalization.NumberFormatInfo> vrátit buď objekt poskytnout informace <xref:System.Globalization.DateTimeFormatInfo> o číselném formátování nebo objekt poskytnout informace o formátování pro hodnoty data a času.

Můžete také implementovat vlastní zprostředkovatele formátu nahradit některou z těchto tříd. <xref:System.IFormatProvider.GetFormat%2A> Metoda implementace však musí vrátit objekt typu uvedeného v předchozí tabulce, pokud má poskytnout `ToString` informace o formátování metody.

### <a name="culture-sensitive-formatting-of-numeric-values"></a>Formátování číselných hodnot zkoumaného z důvodu kultury

Ve výchozím nastavení je formátování číselných hodnot citlivé na jazykovou verzi. Pokud nezadáte jazykovou verzi při volání metody formátování, budou použity konvence formátování aktuální jazykové verze vlákna. To je znázorněno v následujícím příkladu, který změní aktuální <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> jazykovou verzi vlákna čtyřikrát a potom volá metodu. V každém případě výsledek řetězec odráží formátování konvence aktuální jazykové verze. Důvodem je, že `ToString` metody a `ToString(String)` zalamovat volání metody každého číselného typu. `ToString(String, IFormatProvider)`

[!code-csharp[Conceptual.Formatting.Overview#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific3.cs#19)]
[!code-vb[Conceptual.Formatting.Overview#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific3.vb#19)]

Můžete také formátovat číselnou hodnotu pro `ToString` konkrétní jazykovou verzi voláním přetížení, které má `provider` parametr a předáním buď následující:

- Objekt, <xref:System.Globalization.CultureInfo> který představuje jazykovou verzi, jejíž formátování konvence mají být použity. Jeho <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> metoda vrátí hodnotu <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> vlastnosti, <xref:System.Globalization.NumberFormatInfo> což je objekt, který poskytuje informace o formátování specifické pro jazykovou verzi pro číselné hodnoty.

- Objekt, <xref:System.Globalization.NumberFormatInfo> který definuje konvence formátování specifické pro jazykovou verzi, které mají být použity. Jeho <xref:System.Globalization.NumberFormatInfo.GetFormat%2A> metoda vrátí samotnou instanci.

Následující příklad <xref:System.Globalization.NumberFormatInfo> používá objekty, které představují jazykové verze angličtiny (Spojené státy) a angličtiny (Velká Británie) a francouzské a ruské neutrální jazykové verze k formátování čísla s plovoucí desetinnou tištěnou.

[!code-csharp[Conceptual.Formatting.Overview#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific4.cs#20)]
[!code-vb[Conceptual.Formatting.Overview#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific4.vb#20)]

### <a name="culture-sensitive-formatting-of-date-and-time-values"></a>Formátování hodnot data a času citlivé na jazykovou verzi

Ve výchozím nastavení je formátování hodnot data a času citlivé na jazykovou verzi. Pokud nezadáte jazykovou verzi při volání metody formátování, budou použity konvence formátování aktuální jazykové verze vlákna. To je znázorněno v následujícím příkladu, který změní aktuální <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> jazykovou verzi vlákna čtyřikrát a potom volá metodu. V každém případě výsledek řetězec odráží formátování konvence aktuální jazykové verze. Důvodem je, <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType>že <xref:System.DateTime.ToString?displayProperty=nameWithType> <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> , , , <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> a metody obtékání volání a metody.

[!code-csharp[Conceptual.Formatting.Overview#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific1.cs#17)]
[!code-vb[Conceptual.Formatting.Overview#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific1.vb#17)]

Můžete také formátovat hodnotu data a času <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> pro <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> konkrétní jazykovou verzi voláním nebo přetížení, který má `provider` parametr a předáním buď následující:

- Objekt, <xref:System.Globalization.CultureInfo> který představuje jazykovou verzi, jejíž formátování konvence mají být použity. Jeho <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> metoda vrátí hodnotu <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vlastnosti, <xref:System.Globalization.DateTimeFormatInfo> což je objekt, který poskytuje informace o formátování specifické pro jazykovou verzi pro hodnoty data a času.

- Objekt, <xref:System.Globalization.DateTimeFormatInfo> který definuje konvence formátování specifické pro jazykovou verzi, které mají být použity. Jeho <xref:System.Globalization.DateTimeFormatInfo.GetFormat%2A> metoda vrátí samotnou instanci.

Následující příklad <xref:System.Globalization.DateTimeFormatInfo> používá objekty, které představují angličtina (Spojené státy) a angličtina (Velká Británie) jazykové verze a francouzské a ruské neutrální jazykové verze formátovat datum.

[!code-csharp[Conceptual.Formatting.Overview#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific2.cs#18)]
[!code-vb[Conceptual.Formatting.Overview#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific2.vb#18)]

## <a name="the-iformattable-interface"></a>Rozhraní IFormattable

Obvykle typy, které `ToString` přetížení metody s formátovací řetězec a <xref:System.IFormatProvider> parametr také implementovat <xref:System.IFormattable> rozhraní. Toto rozhraní má <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>jeden člen , který obsahuje formátovací řetězec a zprostředkovatele formátu jako parametry.

Implementace rozhraní <xref:System.IFormattable> pro třídu definovanou aplikací nabízí dvě výhody:

- Podpora pro převod <xref:System.Convert> řetězce podle třídy. Volání <xref:System.Convert.ToString%28System.Object%29?displayProperty=nameWithType> metody <xref:System.Convert.ToString%28System.Object%2CSystem.IFormatProvider%29?displayProperty=nameWithType> a volání <xref:System.IFormattable> implementace automaticky.

- Podpora složeného formátování. Pokud se k formátování vlastního typu používá položka formátu, počítač COMMON Language <xref:System.IFormattable> runtime automaticky zavolá implementaci a předá jí formátovací řetězec. Další informace o složeném formátování pomocí <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>metod, jako jsou nebo , naleznete v části [Složené formátování.](#composite-formatting)

Následující příklad definuje `Temperature` třídu, která <xref:System.IFormattable> implementuje rozhraní. Podporuje specifikátory formátu "C" nebo "G" pro zobrazení teploty ve stupních Celsia, specifikátor formátu "F" pro zobrazení teploty ve Fahrenheitu a specifikátor formátu "K" pro zobrazení teploty v Kelvinu.

[!code-csharp[Conceptual.Formatting.Overview#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#12)]
[!code-vb[Conceptual.Formatting.Overview#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#12)]

Následující příklad vytvoří instance `Temperature` objektu. Potom volá <xref:System.Convert.ToString%2A> metodu a používá několik řetězců složené formát získat `Temperature` různé řetězce reprezentace objektu. Každý z těchto volání metody, <xref:System.IFormattable> podle pořadí `Temperature` volá implementaci třídy.

[!code-csharp[Conceptual.Formatting.Overview#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#13)]
[!code-vb[Conceptual.Formatting.Overview#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#13)]

## <a name="composite-formatting"></a>Složené formátování

Některé metody, <xref:System.String.Format%2A?displayProperty=nameWithType> například a <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, podporují složené formátování. Složený formátovací řetězec je druh šablony, která vrací jeden řetězec, který zahrnuje řetězcovou reprezentaci nula, jednoho nebo více objektů. Každý objekt je reprezentován ve složeném formátovacím řetězci položkou indexovaného formátu. Index položky formátu odpovídá pozici objektu, který představuje v seznamu parametrů metody. Indexy jsou od nuly. Například v následujícím volání <xref:System.String.Format%2A?displayProperty=nameWithType> metody je první položka `{0:D}`formátu , nahrazena řetězcovou reprezentací `thatDate`; druhá položka formátu `{1}`, se nahrazuje řetězcovou `item1`reprezentací písmene ; a třetí položka `{2:C2}`formátu , je nahrazena `item1.Value`řetězcovou reprezentací .

[!code-csharp[Conceptual.Formatting.Overview#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite1.cs#14)]
[!code-vb[Conceptual.Formatting.Overview#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite1.vb#14)]

Kromě nahrazení položky formátu řetězcovou reprezentací odpovídajícího objektu umožňují položky formátu také řídit následující:

- Konkrétní způsob, ve kterém je objekt reprezentován jako řetězec, pokud objekt implementuje <xref:System.IFormattable> rozhraní a podporuje formátovací řetězce. To lze provést podle indexu položky `:` formátu s (dvojtečka) následovaný platný formátovací řetězec. V předchozím příkladu bylo formátování hodnoty data pomocí řetězce formátu "d" (krátký vzor `{0:d}`data) (např. ) a formátováním číselné hodnoty pomocí formátovacího řetězce "C2" (např. `{2:C2}` představující číslo jako hodnota měny se dvěma zlomkovými desetinnými místy.

- Šířka pole, které obsahuje řetězcovou reprezentaci objektu, a zarovnání řetězcové reprezentace v tomto poli. To provést podle indexu položky formátu `,` s (čárka) za šířkou pole. Řetězec je v poli zarovnán doprava, pokud je šířka pole kladná hodnota, a je zarovnán doleva, pokud je šířka pole záporná. Následující příklad vlevo zarovná hodnoty kalendářních dat v poli o 20 znacích a vpravo zarovná desetinné hodnoty jednou zlomkovou číslicí v poli s 11 znaky.

     [!code-csharp[Conceptual.Formatting.Overview#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite2.cs#22)]
     [!code-vb[Conceptual.Formatting.Overview#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite2.vb#22)]

     Všimněte si, že pokud jsou k dispozici součást řetězce zarovnání i komponenta řetězce formátu, předchází první komponenta (například `{0,-20:g}`.

Další informace o složeném formátování naleznete v [tématu Složené formátování](../../../docs/standard/base-types/composite-formatting.md).

## <a name="custom-formatting-with-icustomformatter"></a>Vlastní formátování pomocí iCustomFormatter

Dvě metody složeného <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> formátování <xref:System.Text.StringBuilder.AppendFormat%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>a aplikace zahrnují parametr zprostředkovatele formátu, který podporuje vlastní formátování. Pokud je volána některá z těchto <xref:System.Type> metod formátování, <xref:System.ICustomFormatter> předá objekt, <xref:System.IFormatProvider.GetFormat%2A> který představuje rozhraní metody zprostředkovatele formátu. Metoda <xref:System.IFormatProvider.GetFormat%2A> je pak zodpovědný za <xref:System.ICustomFormatter> vrácení implementace, která poskytuje vlastní formátování.

Rozhraní <xref:System.ICustomFormatter> má jednu <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29>metodu , která je volána automaticky metodou složeného formátování, jednou pro každou položku formátu ve složeném formátovacím řetězci. Metoda <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29> má tři parametry: formátovací řetězec, který představuje `formatString` argument v položce <xref:System.IFormatProvider> formátu, objekt pro formátování a objekt, který poskytuje služby formátování. Obvykle třída, která implementuje <xref:System.ICustomFormatter> <xref:System.IFormatProvider>také implementuje , takže tento poslední parametr je odkaz na vlastní formátování třídy samotné. Metoda vrátí vlastní formátovaný řetězec reprezentace objektu, který má být formátován. Pokud metoda nemůže formátovat objekt, by měla`Nothing` vrátit nulový odkaz (v jazyce Visual Basic).

Následující příklad obsahuje <xref:System.ICustomFormatter> implementaci `ByteByByteFormatter` s názvem, která zobrazuje celočíselné hodnoty jako posloupnost dvoumístných šestnáctkových hodnot následovaných mezerou.

[!code-csharp[Conceptual.Formatting.Overview#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#15)]
[!code-vb[Conceptual.Formatting.Overview#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#15)]

Následující příklad používá `ByteByByteFormatter` třídu k formátování hodnot celého čísla. Všimněte <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> si, že metoda je <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> volána více než <xref:System.Globalization.NumberFormatInfo> jednou v druhé volání metody a že výchozí zprostředkovatel se používá ve třetí volání metody, protože .`ByteByByteFormatter.Format` metoda nerozpozná formátovací řetězec "N0" a`Nothing` vrátí nulový odkaz (v jazyce Visual Basic).

[!code-csharp[Conceptual.Formatting.Overview#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#16)]
[!code-vb[Conceptual.Formatting.Overview#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#16)]

## <a name="related-topics"></a>Související témata

|Nadpis|Definice|
|-----------|----------------|
|[Standardní řetězce číselného formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Popisuje standardní formátovací řetězce, které vytvářejí běžně používané řetězcové reprezentace číselných hodnot.|
|[Vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Popisuje vlastní formátovací řetězce, které vytvářejí formáty specifické pro aplikaci pro číselné hodnoty.|
|[Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Popisuje standardní formátovací řetězce, které vytvářejí běžně <xref:System.DateTime> používané řetězcové reprezentace hodnot.|
|[Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Popisuje vlastní formátovací řetězce, které vytvářejí <xref:System.DateTime> formáty pro hodnoty specifické pro aplikaci.|
|[Standardní řetězce formátu TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Popisuje standardní formátovací řetězce, které vytvářejí běžně používané řetězcové reprezentace časových intervalů.|
|[Vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Popisuje vlastní formátovací řetězce, které vytvářejí formáty specifické pro aplikaci pro časové intervaly.|
|[Výčet řetězců formátu](../../../docs/standard/base-types/enumeration-format-strings.md)|Popisuje standardní formátovací řetězce, které se používají k vytvoření řetězcových reprezentací hodnot výčtu.|
|[Složené formátování](../../../docs/standard/base-types/composite-formatting.md)|Popisuje, jak vložit jednu nebo více formátovaných hodnot do řetězce. Řetězec lze následně zobrazit na konzole nebo zapsány do datového proudu.|
|[Provádění operací formátování](../../../docs/standard/base-types/performing-formatting-operations.md)|Uvádí témata, která poskytují podrobné pokyny pro provádění konkrétních operací formátování.|
|[Analýza řetězců](../../../docs/standard/base-types/parsing-strings.md)|Popisuje, jak inicializovat objekty na hodnoty popsané řetězcovými reprezentacemi těchto objektů. Analýza je inverzní operace formátování.|

## <a name="reference"></a>Referenční informace

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- <xref:System.ICustomFormatter?displayProperty=nameWithType>
