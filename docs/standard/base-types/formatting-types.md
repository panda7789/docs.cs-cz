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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82dc1e36ae5a0eede7099c8e13ac9a2393bbb904
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253981"
---
# <a name="formatting-types-in-net"></a>Formátování typů v .NET

Formátování je proces převodu instance třídy, struktury nebo výčtové hodnoty na její řetězcové vyjádření, často tak aby výsledný řetězec mohl být zobrazen uživatelům nebo deserializovat, aby obnovil původní datový typ. Tento převod může představovat množství problémů:

- Způsob, jakým se hodnoty ukládají interně, nemusí nutně odrážet způsob, jakým uživatelé chtějí zobrazit. Například telefonní číslo může být uloženo ve formě 8009999999, což není uživatelsky přívětivé. Místo toho by se mělo zobrazit jako 800-999-9999. V části [Vlastní řetězce formátu](#customStrings) najdete příklad, který tímto způsobem formátuje číslo.

- V některých případech není převod objektu na jeho řetězcovou reprezentaci intuitivní. Například není jasné, jak by se měla zobrazit řetězcová reprezentace objektu teploty nebo objektu Person. Příklad, který formátuje objekt teploty v různých způsobech, naleznete v oddílu [standardní formátovací řetězce](#standardStrings) .

- Hodnoty často vyžadují formátování zohledňující jazykovou verzi. Například v aplikaci, která používá čísla k zohlednění peněžních hodnot, musí číselné řetězce zahrnovat symbol měny aktuální jazykové verze, oddělovač skupin (ve většině kultur je oddělovač tisíců) a symbol desetinné čárky. Příklad naleznete v části formátování zohledňující [jazykovou verzi s použitím poskytovatelů formátu a rozhraní IFormatProvider](#FormatProviders) .

- Aplikace může být muset zobrazit stejnou hodnotu různými způsoby. Například aplikace může představovat člen výčtu zobrazením řetězcové reprezentace jeho názvu nebo zobrazením jeho základní hodnoty. Příklad, který formátuje člen <xref:System.DayOfWeek> výčtu různými způsoby, naleznete v oddílu [standardní formátovací řetězce](#standardStrings) .

> [!NOTE]
> Formátování převede hodnotu typu na řetězcovou reprezentaci. Analýza je inverzní k formátování. Operace analýzy vytvoří instanci datového typu z jeho řetězcové reprezentace. Informace o převodu řetězců na jiné datové typy naleznete v tématu [Analýza řetězců](../../../docs/standard/base-types/parsing-strings.md).

Rozhraní .NET poskytuje bohatou podporu formátování, která vývojářům umožňuje řešit tyto požadavky.

Tento přehled obsahuje následující oddíly:

- [Formátování v .NET](#NetFormatting)

- [Výchozí formátování pomocí metody ToString](#DefaultToString)

- [Přepsání metody ToString](#OverrideToString)

- [Metoda ToString a formátovací řetězce](#FormatStrings)

  - [Standardní formátovací řetězce](#standardStrings)

  - [Vlastní řetězce formátu](#customStrings)

  - [Typy řetězců formátu a typy knihoven tříd .NET](#stringRef)

- [Formátování zohledňující jazykovou verzi s poskytovateli formátu a rozhraním IFormatProvider](#FormatProviders)

  - [Formátování číselných hodnot zohledňující jazykovou verzi](#numericCulture)

  - [Formátování hodnot data a času zohledňující jazykovou verzi](#dateCulture)

- [Rozhraní IFormattable](#IFormattable)

- [Složené formátování](#CompositeFormatting)

- [Vlastní formátování pomocí ICustomFormatter](#Custom)

- [Příbuzná témata](#RelatedTopics)

- [Referenční informace](#Reference)

<a name="NetFormatting"></a>

## <a name="formatting-in-net"></a>Formátování v .NET

Základní mechanismus pro formátování je výchozí implementace <xref:System.Object.ToString%2A?displayProperty=nameWithType> metody, která je popsána v části [výchozí formátování pomocí metody ToString](#DefaultToString) dále v tomto tématu. Rozhraní .NET však nabízí několik způsobů, jak upravit a zvětšit výchozí podporu formátování. Patří mezi ně například:

- <xref:System.Object.ToString%2A?displayProperty=nameWithType> Přepsání metody pro definování vlastní řetězcové reprezentace hodnoty objektu. Další informace naleznete v části [přepsání metody ToString](#OverrideToString) dále v tomto tématu.

- Definování specifikátorů formátu, které umožňují řetězcové vyjádření hodnoty objektu, aby bylo možné převzít více formulářů. Například specifikátor formátu "X" v následujícím příkazu převede celé číslo na řetězcovou reprezentaci hexadecimální hodnoty.

     [!code-csharp[Conceptual.Formatting.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#3)]
     [!code-vb[Conceptual.Formatting.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#3)]

     Další informace o specifikátorech formátu naleznete v části [metoda ToString a formátovací řetězce](#FormatStrings) .

- Použití poskytovatelů formátu k využití konvencí formátování konkrétní jazykové verze. Například následující příkaz zobrazí hodnotu měny pomocí konvencí formátování jazykové verze en-US.

     [!code-csharp[Conceptual.Formatting.Overview#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#10)]
     [!code-vb[Conceptual.Formatting.Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#10)]

     Další informace o formátování s poskytovateli formátu naleznete v části [poskytovatelé formátu a rozhraní IFormatProvider](#FormatProviders) .

- Implementace rozhraní pro podporu převodu řetězce <xref:System.Convert> s použitím třídy i složeného formátování. <xref:System.IFormattable> Další informace najdete v části [rozhraní IFormattable](#IFormattable) .

- Použití složeného formátování pro vložení řetězcové reprezentace hodnoty do většího řetězce. Další informace najdete v oddílu [složené formátování](#CompositeFormatting) .

- Implementace <xref:System.ICustomFormatter> a<xref:System.IFormatProvider> k poskytnutí kompletního řešení vlastního formátování. Další informace najdete v části [vlastní formátování pomocí ICustomFormatter](#Custom) .

Následující části prozkoumají tyto metody pro převod objektu na jeho řetězcovou reprezentaci.

<a name="DefaultToString"></a>

## <a name="default-formatting-using-the-tostring-method"></a>Výchozí formátování pomocí metody ToString

Každý typ, který je odvozen <xref:System.Object?displayProperty=nameWithType> z automaticky dědí `ToString` metodu bez parametrů, která ve výchozím nastavení vrací název typu. Následující příklad ilustruje výchozí `ToString` metodu. Definuje třídu s názvem `Automobile` , která nemá žádnou implementaci. Když je vytvořena instance třídy a je volána `ToString` její metoda, zobrazí se její název typu. Všimněte si, `ToString` že metoda není explicitně volána v příkladu. Metoda implicitně volá metodu objektu předanou do něj jako argument. `ToString` <xref:System.Console.WriteLine%28System.Object%29?displayProperty=nameWithType>

[!code-csharp[Conceptual.Formatting.Overview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/default1.cs#1)]
[!code-vb[Conceptual.Formatting.Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/default1.vb#1)]

> [!WARNING]
> Počínaje verzí prostředí Windows Runtime <xref:Windows.Foundation.IStringable> obsahuje rozhraní s jedinou metodou, [IStringable. ToString](xref:Windows.Foundation.IStringable.ToString%2A), která poskytuje výchozí podporu formátování. [!INCLUDE[win81](../../../includes/win81-md.md)] Nicméně doporučujeme, aby spravované typy neimplementovaly `IStringable` rozhraní. Další informace naleznete v části prostředí Windows Runtime a `IStringable` rozhraní <xref:System.Object.ToString%2A?displayProperty=nameWithType> na referenční stránce.

Vzhledem k tomu, že všechny typy kromě rozhraní <xref:System.Object>jsou odvozeny z, tato funkce je automaticky poskytována vašim vlastním třídám nebo strukturám. Funkce nabízené výchozí `ToString` metodou je však omezená: I když identifikuje typ, nemůže poskytnout žádné informace o instanci typu. Chcete-li poskytnout řetězcovou reprezentaci objektu, který poskytuje informace o tomto objektu, je nutné `ToString` přepsat metodu.

> [!NOTE]
> Struktury dědí z <xref:System.ValueType>, který je zase odvozen z. <xref:System.Object> I <xref:System.ValueType> když <xref:System.Object.ToString%2A?displayProperty=nameWithType>Přepisuje, je jeho implementace identická.

<a name="OverrideToString"></a>

## <a name="overriding-the-tostring-method"></a>Přepsání metody ToString

Zobrazení názvu typu je často omezeného použití a neumožňuje příjemcům vašich typů odlišit jednu instanci od druhé. Můžete však přepsat `ToString` metodu a poskytnout tak užitečnější reprezentace hodnoty objektu. Následující příklad definuje `Temperature` objekt a Přepisuje jeho `ToString` metodu pro zobrazení teploty ve stupních Celsia.

[!code-csharp[Conceptual.Formatting.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/overrides1.cs#2)]
[!code-vb[Conceptual.Formatting.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/overrides1.vb#2)]

V rozhraní .NET `ToString` byla metoda každého primitivního typu hodnoty přepsána tak, aby zobrazila hodnotu objektu namísto názvu. Následující tabulka ukazuje přepsání pro každý primitivní typ. Všimněte si, že většina přepsaných metod volá jiné přetížení `ToString` metody a předá jí specifikátor formátu "G", který definuje obecný formát pro svůj typ <xref:System.IFormatProvider> a objekt, který představuje aktuální jazykovou verzi.

|type|Přepsání ToString|
|----------|-----------------------|
|<xref:System.Boolean>|Vrátí buď <xref:System.Boolean.TrueString?displayProperty=nameWithType> nebo <xref:System.Boolean.FalseString?displayProperty=nameWithType>.|
|<xref:System.Byte>|Volá `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` k<xref:System.Byte> formátování hodnoty pro aktuální jazykovou verzi.|
|<xref:System.Char>|Vrátí znak jako řetězec.|
|<xref:System.DateTime>|Volá `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` k formátování hodnoty data a času pro aktuální jazykovou verzi.|
|<xref:System.Decimal>|Volá `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` k<xref:System.Decimal> formátování hodnoty pro aktuální jazykovou verzi.|
|<xref:System.Double>|Volá `Double.ToString("G", NumberFormatInfo.CurrentInfo)` k<xref:System.Double> formátování hodnoty pro aktuální jazykovou verzi.|
|<xref:System.Int16>|Volá `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` k<xref:System.Int16> formátování hodnoty pro aktuální jazykovou verzi.|
|<xref:System.Int32>|Volá `Int32.ToString("G", NumberFormatInfo.CurrentInfo)` k<xref:System.Int32> formátování hodnoty pro aktuální jazykovou verzi.|
|<xref:System.Int64>|Volá `Int64.ToString("G", NumberFormatInfo.CurrentInfo)` k<xref:System.Int64> formátování hodnoty pro aktuální jazykovou verzi.|
|<xref:System.SByte>|Volá `SByte.ToString("G", NumberFormatInfo.CurrentInfo)` k<xref:System.SByte> formátování hodnoty pro aktuální jazykovou verzi.|
|<xref:System.Single>|Volá `Single.ToString("G", NumberFormatInfo.CurrentInfo)` k<xref:System.Single> formátování hodnoty pro aktuální jazykovou verzi.|
|<xref:System.UInt16>|Volá `UInt16.ToString("G", NumberFormatInfo.CurrentInfo)` k<xref:System.UInt16> formátování hodnoty pro aktuální jazykovou verzi.|
|<xref:System.UInt32>|Volá `UInt32.ToString("G", NumberFormatInfo.CurrentInfo)` k<xref:System.UInt32> formátování hodnoty pro aktuální jazykovou verzi.|
|<xref:System.UInt64>|Volá `UInt64.ToString("G", NumberFormatInfo.CurrentInfo)` k<xref:System.UInt64> formátování hodnoty pro aktuální jazykovou verzi.|

<a name="FormatStrings"></a>

## <a name="the-tostring-method-and-format-strings"></a>Metoda ToString a formátovací řetězce

Spoléhání se na výchozí `ToString` metodu nebo přepsání `ToString` je vhodné, pokud objekt obsahuje jedinou řetězcovou reprezentaci. Hodnota objektu má však často více reprezentace. Například je možné vyjádřit teplotu ve stupních Fahrenheita, stupních Celsia nebo kelvinech. Podobně může být celočíselná hodnota 10 reprezentovaná mnoha způsoby, včetně 10, 10,0, 1.0 E01 nebo $10,00.

Pokud chcete povolit, aby jedna hodnota měla více řetězcových reprezentací, používá rozhraní .NET řetězce formátu. Formátovací řetězec je řetězec, který obsahuje jeden nebo více předdefinovaných specifikátorů formátu, což jsou jednotlivé znaky nebo skupiny znaků, které definují, jak `ToString` má metoda formátovat svůj výstup. Formátovací řetězec je pak předán jako parametr `ToString` metodě objektu a určuje, jak se má zobrazit řetězcová reprezentace hodnoty daného objektu.

Všechny číselné typy, typy data a času a výčtové typy v rozhraní .NET podporují předdefinovanou sadu specifikátorů formátu. Můžete také použít formátovací řetězce k definování více řetězcových reprezentace datových typů definovaných aplikací.

<a name="standardStrings"></a>

### <a name="standard-format-strings"></a>Standardní formátovací řetězce

Řetězec standardního formátu obsahuje specifikátor jednoho formátu, což je abecední znak definující řetězcovou reprezentaci objektu, na který je použit, spolu s volitelným specifikátorem přesnosti, který ovlivňuje, kolik číslic se zobrazí v Výsledný řetězec Pokud je specifikátor přesnosti vynechán nebo není podporován, standardní specifikátor formátu je ekvivalentní standardnímu formátovacímu řetězci.

Rozhraní .NET definuje sadu standardních specifikátorů formátu pro všechny číselné typy, všechny typy data a času a všechny typy výčtu. Například každá z těchto kategorií podporuje standardní specifikátor formátu "G", který definuje obecnou řetězcovou reprezentaci hodnoty tohoto typu.

Standardní formátovací řetězce pro typy výčtu přímo ovládají řetězcovou reprezentaci hodnoty. Formátovací řetězce předané `ToString` metodě hodnoty výčtu určují, zda se hodnota zobrazuje pomocí názvu řetězce (specifikátory formátu "G" a "F"), její základní celočíselné hodnoty (specifikátor formátu "D") nebo její hexadecimální hodnota ("X specifikátor formátu). Následující příklad ilustruje použití standardního formátovacího řetězce k formátování <xref:System.DayOfWeek> hodnoty výčtu.

[!code-csharp[Conceptual.Formatting.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/standard1.cs#4)]
[!code-vb[Conceptual.Formatting.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/standard1.vb#4)]

Informace o formátovacích řetězcích výčtů naleznete v tématu [výčty formátu výčtu](../../../docs/standard/base-types/enumeration-format-strings.md).

Standardní formátovací řetězce pro číselné typy obvykle definují výsledný řetězec, jehož přesný vzhled je řízen jednou nebo více hodnotami vlastností. Například specifikátor formátu "C" formátuje číslo jako hodnotu měny. Při volání `ToString` metody se specifikátorem formátu "C" jako jediným parametrem, jsou pro definování řetězcové reprezentace číselné hodnoty použity následující hodnoty <xref:System.Globalization.NumberFormatInfo> vlastností z objektu aktuální jazykové verze:

- <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A> Vlastnost, která určuje symbol měny aktuální jazykové verze.

- Vlastnost <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> nebo<xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A> , která vrací celé číslo, které určuje následující:

  - Umístění symbolu měny.

  - Určuje, zda jsou záporné hodnoty označeny počátečním záporným znaménkem, koncovým záporným znaménkem nebo závorkami.

  - Určuje, zda se mezi číselnou hodnotou a symbolem měny zobrazí mezera.

- <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A> Vlastnost, která definuje počet zlomkových číslic ve výsledném řetězci.

- <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A> Vlastnost, která definuje symbol oddělovače desetinných míst ve výsledném řetězci.

- <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A> Vlastnost, která definuje symbol oddělovače skupiny.

- <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A> Vlastnost, která definuje počet číslic v každé skupině nalevo od desetinné čárky.

- <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> Vlastnost, která určuje záporné znaménko použité ve výsledném řetězci, pokud nejsou použity závorky k označení záporných hodnot.

Kromě toho číselné formátovací řetězce můžou obsahovat specifikátor přesnosti. Význam tohoto specifikátoru závisí na formátovacím řetězci, se kterým je použit, ale obvykle označuje buď celkový počet číslic, nebo počet zlomkových číslic, které se mají zobrazit ve výsledném řetězci. Například následující příklad používá standardní číselný řetězec "X4" a specifikátor přesnosti pro vytvoření řetězcové hodnoty se čtyřmi šestnáctkovými číslicemi.

[!code-csharp[Conceptual.Formatting.Overview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/precisionspecifier1.cs#6)]
[!code-vb[Conceptual.Formatting.Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/precisionspecifier1.vb#6)]

Další informace o standardních formátovacích řetězcích čísel naleznete v tématu [Standardní číselné formátovací řetězce](../../../docs/standard/base-types/standard-numeric-format-strings.md).

Standardní formátovací řetězce pro hodnoty data a času jsou aliasy pro vlastní formátovací řetězce uložené určitou <xref:System.Globalization.DateTimeFormatInfo> vlastností. Například volání `ToString` metody hodnoty data a času s specifikátorem formátu "D" zobrazí datum a čas pomocí vlastního formátovacího řetězce uloženého ve <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> vlastnosti aktuální jazykové verze. (Další informace o vlastních formátovacích řetězcích naleznete v [Další části](#customStrings).) Následující příklad znázorňuje tuto relaci.

[!code-csharp[Conceptual.Formatting.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/alias1.cs#5)]
[!code-vb[Conceptual.Formatting.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/alias1.vb#5)]

Další informace o standardních formátovacích řetězcích data a času naleznete v tématu [Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md).

Můžete také použít standardní formátovací řetězce k definování řetězcové reprezentace objektu definovaného aplikací, který je vytvořen `ToString(String)` metodou objektu. Můžete definovat konkrétní standardní specifikátory formátu, které váš objekt podporuje, a můžete určit, zda rozlišují velká a malá písmena. Vaše implementace `ToString(String)` metody by měla podporovat následující:

- Specifikátor formátu "G", který představuje vlastní nebo běžný formát objektu. Přetížení `ToString` metody vašeho objektu bez parametrů by mělo `ToString(String)` volat přetížení a předat standardní formátovací řetězec "G".

- Podpora specifikátoru formátu, který je roven nulovému odkazu (`Nothing` v Visual Basic). Specifikátor formátu, který je roven nulovému odkazu, by měl být považován za ekvivalent specifikátoru formátu "G".

`Temperature` Třída například může interně uchovávat teplotu ve stupních Celsia a používat specifikátory formátu k vyjádření hodnoty `Temperature` objektu ve stupních Celsia, stupních Fahrenheita a kelvinech. V následujícím příkladu je uvedena ukázka.

[!code-csharp[Conceptual.Formatting.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/appstandard1.cs#7)]
[!code-vb[Conceptual.Formatting.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/appstandard1.vb#7)]

<a name="customStrings"></a>

### <a name="custom-format-strings"></a>Vlastní řetězce formátu

Kromě standardních formátovacích řetězců definuje rozhraní .NET řetězce vlastního formátu pro číselné hodnoty a hodnoty data a času. Vlastní formátovací řetězec se skládá z jednoho nebo více vlastních specifikátorů formátu, které definují řetězcovou reprezentaci hodnoty. Například vlastní řetězec formátu data a času "rrrr/MM/DD hh: mm: ss. FFFF t ZZZ" převede datum na jeho řetězcovou reprezentaci ve formátu "2008/11/15 07:45:00.0000 P-08:00" pro jazykovou verzi en-US. Podobně řetězec vlastního formátu "0000" Převede celočíselnou hodnotu 12 na "0012". Úplný seznam vlastních formátovacích řetězců naleznete v tématu [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) a [vlastní číselné formátovací řetězce](../../../docs/standard/base-types/custom-numeric-format-strings.md).

Pokud formátovací řetězec se skládá z jednoho vlastního specifikátoru formátu, před specifikátorem formátu by měl předcházet procentuální hodnota (%) symbol, aby nedocházelo k záměně se standardním specifikátorem formátu. V následujícím příkladu je použit Specifikátor vlastního formátu "M" k zobrazení jednociferného nebo dvoumístného čísla měsíce určitého data.

[!code-csharp[Conceptual.Formatting.Overview#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/singlecustom1.cs#8)]
[!code-vb[Conceptual.Formatting.Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/singlecustom1.vb#8)]

Mnoho standardních formátovacích řetězců pro hodnoty data a času jsou aliasy pro vlastní formátovací řetězce, které jsou definovány vlastnostmi <xref:System.Globalization.DateTimeFormatInfo> objektu. Vlastní řetězce formátu také nabízejí značnou flexibilitu při poskytování formátování definovaného aplikací pro číselné hodnoty nebo hodnoty data a času. Můžete definovat vlastní výsledné řetězce pro číselné hodnoty a hodnoty data a času kombinací více specifikátorů vlastního formátu do jednoho vlastního formátovacího řetězce. Následující příklad definuje vlastní formátovací řetězec, který zobrazuje den v týdnu v závorkách po názvu měsíce, den a rok.

[!code-csharp[Conceptual.Formatting.Overview#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/custom1.cs#9)]
[!code-vb[Conceptual.Formatting.Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/custom1.vb#9)]

Následující příklad definuje vlastní formátovací řetězec, který zobrazí <xref:System.Int64> hodnotu jako standardní, sedmé číslo telefonního čísla USA spolu s jeho kódem oblasti.

[!code-csharp[Conceptual.Formatting.Overview#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/telnumber1.cs#21)]
[!code-vb[Conceptual.Formatting.Overview#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/telnumber1.vb#21)]

I když standardní formátovací řetězce mohou obecně zpracovat většinu formátovacích potřeb pro aplikace definované uživatelem, můžete také definovat vlastní specifikátory formátu pro formátování typů.

<a name="stringRef"></a>

### <a name="format-strings-and-net-types"></a>Řetězce formátu a typy .NET

Všechny číselné typy <xref:System.Byte>(tj <xref:System.Int64> <xref:System.SByte> .,<xref:System.Single>, <xref:System.Int32>, ,,<xref:System.UInt16>,,, ,<xref:System.UInt32>, ,<xref:System.UInt64>a <xref:System.Int16> <xref:System.Decimal> <xref:System.Double> <xref:System.Numerics.BigInteger>typy) a <xref:System.DateTime>také, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, <xref:System.Guid>a všechny typy výčtu, podporují formátování pomocí formátovacích řetězců. Informace o konkrétních formátovacích řetězcích podporovaných jednotlivými typy naleznete v následujících tématech:

|Název|Definice|
|-----------|----------------|
|[Standardní řetězce číselného formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Popisuje standardní formátovací řetězce, které vytvářejí běžně používané řetězcové reprezentace číselných hodnot.|
|[Vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Popisuje vlastní formátovací řetězce, které vytvářejí formáty číselných hodnot specifické pro danou aplikaci.|
|[Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Popisuje standardní formátovací řetězce, které vytvářejí běžně používané řetězcové reprezentace <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty.|
|[Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Popisuje vlastní formátovací řetězce, které vytvářejí formáty a <xref:System.DateTime> <xref:System.DateTimeOffset> hodnoty specifické pro aplikaci.|
|[Standardní řetězce formátu TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Popisuje standardní formátovací řetězce, které vytvářejí běžně používané řetězcové reprezentace časových intervalů.|
|[Vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Popisuje vlastní formátovací řetězce, které vytvářejí formáty časových intervalů specifické pro danou aplikaci.|
|[Výčet řetězců formátu](../../../docs/standard/base-types/enumeration-format-strings.md)|Popisuje standardní formátovací řetězce, které slouží k vytvoření řetězcové reprezentace hodnot výčtu.|
|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|Popisuje standardní formátovací řetězce pro <xref:System.Guid> hodnoty.|

<a name="FormatProviders"></a>

## <a name="culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface"></a>Formátování zohledňující jazykovou verzi s použitím poskytovatelů formátu a rozhraní IFormatProvider

I když specifikátory formátu umožňují přizpůsobit formátování objektů a vytváření smysluplných řetězcové reprezentace objektů, často vyžadují další informace o formátování. Například formátování čísla jako hodnoty měny buď pomocí standardního formátovacího řetězce "C" nebo vlastního formátovacího řetězce, jako je "$ #, #. 00", vyžaduje minimálně informace o správném symbolu měny, oddělovači skupin a oddělovači desetinných míst. k dispozici pro zahrnutí do formátovaného řetězce. V rozhraní .NET jsou tyto dodatečné informace o formátování k dispozici <xref:System.IFormatProvider> prostřednictvím rozhraní, které je poskytováno jako parametr jednomu nebo více přetížením `ToString` metody číselných typů a typů data a času. <xref:System.IFormatProvider>implementace jsou používány v rozhraní .NET pro podporu formátování specifického pro jazykovou verzi. Následující příklad ukazuje, jak se řetězcové reprezentace objektu mění při formátování třemi <xref:System.IFormatProvider> objekty, které reprezentují různé jazykové verze.

[!code-csharp[Conceptual.Formatting.Overview#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformatprovider1.cs#11)]
[!code-vb[Conceptual.Formatting.Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformatprovider1.vb#11)]

Rozhraní zahrnuje jednu metodu, <xref:System.IFormatProvider.GetFormat%28System.Type%29>, která má jeden parametr, který určuje typ objektu, který poskytuje informace o formátování. <xref:System.IFormatProvider> Pokud metoda může poskytnout objekt daného typu, vrátí jej. V opačném případě vrátí odkaz s hodnotou`Nothing` null (v Visual Basic).

<xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType>je metoda zpětného volání. Při volání `ToString` přetížení metody, která <xref:System.IFormatProvider> obsahuje <xref:System.IFormatProvider.GetFormat%2A> parametr, <xref:System.IFormatProvider> volá metodu tohoto objektu. Metoda zodpovídá za vrácení objektu, který poskytuje nezbytné informace o formátování, jak je `ToString` určeno jeho `formatType` parametrem, metodě. <xref:System.IFormatProvider.GetFormat%2A>

Několik metod formátování nebo převodu řetězce obsahuje parametr typu <xref:System.IFormatProvider>, ale v mnoha případech je hodnota parametru při volání metody ignorována. V následující tabulce jsou uvedeny některé metody formátování, které používají parametr a typ <xref:System.Type> objektu, který předávají <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metodě.

|Metoda|`formatType` Typ parametru|
|------------|------------------------------------|
|`ToString`Metoda číselných typů|<xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>|
|`ToString`Metoda typů data a času|<xref:System.Globalization.DateTimeFormatInfo?displayProperty=nameWithType>|
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|

> [!NOTE]
> Metody číselných typů a typů data a času jsou přetíženy a pouze některá z přetížení <xref:System.IFormatProvider> obsahují parametr. `ToString` Pokud metoda nemá parametr typu <xref:System.IFormatProvider>, je místo toho předán objekt vrácený <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastností. Například volání výchozí <xref:System.Int32.ToString?displayProperty=nameWithType> metody nakonec má za následek volání metody, jako je následující: `Int32.ToString("G", System.Globalization.CultureInfo.CurrentCulture)`.

Rozhraní .NET poskytuje tři třídy, <xref:System.IFormatProvider>které implementují:

- <xref:System.Globalization.DateTimeFormatInfo>Třída, která poskytuje informace o formátování pro hodnoty data a času pro konkrétní jazykovou verzi. Jeho <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementace vrátí instanci sebe sama.

- <xref:System.Globalization.NumberFormatInfo>Třída, která poskytuje informace o formátování čísel pro konkrétní jazykovou verzi. Jeho <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementace vrátí instanci sebe sama.

- <xref:System.Globalization.CultureInfo>. Jeho <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementace může vracet <xref:System.Globalization.NumberFormatInfo> buď objekt, který poskytuje informace o formátování <xref:System.Globalization.DateTimeFormatInfo> čísel, nebo objekt, který poskytuje informace o formátování hodnot data a času.

Můžete také implementovat vlastního poskytovatele formátu a nahradit jednu z těchto tříd. Nicméně <xref:System.IFormatProvider.GetFormat%2A> metoda vaší implementace musí vracet objekt typu, který je uveden v předchozí tabulce, pokud má poskytnout informace o `ToString` formátování metodě.

<a name="numericCulture"></a>

### <a name="culture-sensitive-formatting-of-numeric-values"></a>Formátování číselných hodnot zohledňující jazykovou verzi

Ve výchozím nastavení je formátování číselných hodnot závislé na jazykové verzi. Pokud nezadáte jazykovou verzi při volání metody formátování, jsou použity konvence formátování aktuální jazykové verze vlákna. To je znázorněno v následujícím příkladu, který čtyřikrát změní aktuální jazykovou verzi vlákna a poté volá <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> metodu. V každém případě výsledný řetězec odráží konvence formátování aktuální jazykové verze. Důvodem je, že `ToString` metody `ToString(String)` a zabalí volání `ToString(String, IFormatProvider)` do jednotlivých metod číselného typu.

[!code-csharp[Conceptual.Formatting.Overview#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific3.cs#19)]
[!code-vb[Conceptual.Formatting.Overview#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific3.vb#19)]

Můžete také formátovat číselnou hodnotu pro konkrétní jazykovou verzi voláním `ToString` přetížení obsahujícího `provider` parametr a předáním některého z následujících:

- <xref:System.Globalization.CultureInfo> Objekt, který představuje jazykovou verzi, jejíž konvence formátování se mají použít. Jeho <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> metoda vrátí <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> hodnotu<xref:System.Globalization.NumberFormatInfo> vlastnosti, což je objekt, který poskytuje informace o formátování specifické pro jazykovou verzi pro číselné hodnoty.

- <xref:System.Globalization.NumberFormatInfo> Objekt definující konvence formátování specifické pro jazykovou verzi, které mají být použity. Jeho <xref:System.Globalization.NumberFormatInfo.GetFormat%2A> metoda vrátí instanci sebe sama.

V následujícím příkladu jsou <xref:System.Globalization.NumberFormatInfo> použity objekty, které reprezentují jazykové verze English (USA) a angličtina (Velká Británie) a francouzské a ruské neutrální kultury pro formátování čísla s plovoucí desetinnou čárkou.

[!code-csharp[Conceptual.Formatting.Overview#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific4.cs#20)]
[!code-vb[Conceptual.Formatting.Overview#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific4.vb#20)]

<a name="dateCulture"></a>

### <a name="culture-sensitive-formatting-of-date-and-time-values"></a>Formátování hodnot data a času zohledňující jazykovou verzi

Ve výchozím nastavení je formátování hodnot data a času závislé na jazykové verzi. Pokud nezadáte jazykovou verzi při volání metody formátování, jsou použity konvence formátování aktuální jazykové verze vlákna. To je znázorněno v následujícím příkladu, který čtyřikrát změní aktuální jazykovou verzi vlákna a poté volá <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> metodu. V každém případě výsledný řetězec odráží konvence formátování aktuální jazykové verze. To je způsobeno <xref:System.DateTime.ToString?displayProperty=nameWithType>tím <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType>, že metody <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> ,, a balí volání <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metod <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> a.

[!code-csharp[Conceptual.Formatting.Overview#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific1.cs#17)]
[!code-vb[Conceptual.Formatting.Overview#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific1.vb#17)]

Můžete také naformátovat hodnotu data a času pro konkrétní jazykovou verzi voláním <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> metody <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> nebo přetížení s `provider` parametrem a předáním některého z následujících:

- <xref:System.Globalization.CultureInfo> Objekt, který představuje jazykovou verzi, jejíž konvence formátování se mají použít. Jeho <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> metoda vrátí <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> hodnotu<xref:System.Globalization.DateTimeFormatInfo> vlastnosti, což je objekt, který poskytuje informace o formátování specifické pro jazykovou verzi pro hodnoty data a času.

- <xref:System.Globalization.DateTimeFormatInfo> Objekt definující konvence formátování specifické pro jazykovou verzi, které mají být použity. Jeho <xref:System.Globalization.DateTimeFormatInfo.GetFormat%2A> metoda vrátí instanci sebe sama.

V následujícím příkladu jsou <xref:System.Globalization.DateTimeFormatInfo> použity objekty, které reprezentují jazykové verze English (USA) a angličtina (Velká Británie), a francouzská a ruština neutrální kultury k formátování data.

[!code-csharp[Conceptual.Formatting.Overview#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific2.cs#18)]
[!code-vb[Conceptual.Formatting.Overview#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific2.vb#18)]

<a name="IFormattable"></a>

## <a name="the-iformattable-interface"></a>Rozhraní IFormattable

Obvykle typy, které přetěžují `ToString` metodu s formátovacím řetězcem <xref:System.IFormatProvider> a parametr také implementují <xref:System.IFormattable> rozhraní. Toto rozhraní má jediný člen, <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, který zahrnuje formátovací řetězec i poskytovatele formátu jako parametry.

<xref:System.IFormattable> Implementace rozhraní pro třídu definovanou aplikací nabízí dvě výhody:

- Podpora převodu <xref:System.Convert> řetězců třídou. Volání metod <xref:System.Convert.ToString%28System.Object%2CSystem.IFormatProvider%29?displayProperty=nameWithType> <xref:System.IFormattable> a volají vaši implementaci automaticky. <xref:System.Convert.ToString%28System.Object%29?displayProperty=nameWithType>

- Podpora složeného formátování. Pokud je k formátování vlastního typu použita položka formátu, která obsahuje formátovací řetězec, modul CLR (Common Language Runtime) automaticky zavolá vaši <xref:System.IFormattable> implementaci a předá ho formátovacím řetězcem. Další informace o složeném formátování pomocí metod <xref:System.String.Format%2A?displayProperty=nameWithType> , jako je například nebo <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, naleznete v oddílu [složené formátování](#CompositeFormatting) .

Následující příklad definuje `Temperature` třídu, která <xref:System.IFormattable> implementuje rozhraní. Podporuje specifikátory formátu "C" nebo "G" k zobrazení teploty ve stupních Celsia, specifikátor formátu "F" pro zobrazení teploty ve stupních Fahrenheita a specifikátor formátu "K" pro zobrazení teploty v kelvinech.

[!code-csharp[Conceptual.Formatting.Overview#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#12)]
[!code-vb[Conceptual.Formatting.Overview#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#12)]

Následující příklad vytvoří instanci `Temperature` objektu. Pak zavolá <xref:System.Convert.ToString%2A> metodu a použije několik složených formátovacích řetězců k získání různých řetězcových reprezentace `Temperature` objektu. Každé z těchto volání metod zase volá <xref:System.IFormattable> implementaci `Temperature` třídy.

[!code-csharp[Conceptual.Formatting.Overview#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#13)]
[!code-vb[Conceptual.Formatting.Overview#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#13)]

<a name="CompositeFormatting"></a>

## <a name="composite-formatting"></a>Složené formátování

Některé metody, například <xref:System.String.Format%2A?displayProperty=nameWithType> a <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, podporují složené formátování. Složený formátovací řetězec je druh šablony, která vrací jeden řetězec, který zahrnuje řetězcovou reprezentaci nuly, jednoho nebo více objektů. Jednotlivé objekty jsou reprezentovány ve složeném formátovacím řetězci pomocí položky indexovaného formátu. Index položky formátu odpovídá pozici objektu, který představuje v seznamu parametrů metody. Indexy jsou počítány od nuly. <xref:System.String.Format%2A?displayProperty=nameWithType> Například v následujícím volání metody je první `{0:D}`položka formátu nahrazena řetězcovou reprezentací `thatDate`; druhá položka `{1}`formátu je nahrazena řetězcovou reprezentací `item1`; a třetí položka `{2:C2}`formátu je nahrazena řetězcovou `item1.Value`reprezentací.

[!code-csharp[Conceptual.Formatting.Overview#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite1.cs#14)]
[!code-vb[Conceptual.Formatting.Overview#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite1.vb#14)]

Kromě nahrazení položky formátu řetězcovou reprezentací odpovídajícího objektu je také možné řídit následující:

- Konkrétní způsob, jakým je objekt reprezentován jako řetězec, pokud objekt implementuje <xref:System.IFormattable> rozhraní a podporuje řetězce formátu. To provedete tak, že použijete index položky formátu `:` s (dvojtečkou) následovaný platným formátovacím řetězcem. Předchozí příklad vystupoval pomocí formátovací hodnoty data s formátovacím řetězcem "d" (vzor krátkého formátu data) (například `{0:d}`) a formátováním číselné hodnoty s formátovacím řetězcem "C2" (např `{2:C2}` . aby představovalo číslo jako hodnotu měny se dvěma zlomky desítkových číslic.

- Šířka pole obsahujícího řetězcovou reprezentaci objektu a zarovnání řetězcové reprezentace v tomto poli. Provedete to tak, že použijete index položky formátu `,` s (čárka) následovaný šířkou pole. Řetězec je zarovnán vpravo v poli, pokud je šířka pole kladná hodnota a je zarovnána doleva, pokud je šířka pole záporná. Následující příklad Zarovná hodnoty data do pole o 20 znacích a v poli se 11 znaky Zarovná desítkové číslo s jednou zlomkovou hodnotou.

     [!code-csharp[Conceptual.Formatting.Overview#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite2.cs#22)]
     [!code-vb[Conceptual.Formatting.Overview#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite2.vb#22)]

     Všimněte si, že pokud jsou přítomny buď komponenty řetězce zarovnání, a formátovací řetězec komponenty, předchozí předchází druhý (například `{0,-20:g}`.

Další informace o složeném formátování najdete v tématu [složené formátování](../../../docs/standard/base-types/composite-formatting.md).

<a name="Custom"></a>

## <a name="custom-formatting-with-icustomformatter"></a>Vlastní formátování pomocí ICustomFormatter

Dvě metody <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> složeného formátování a <xref:System.Text.StringBuilder.AppendFormat%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>zahrnují parametr poskytovatele formátu, který podporuje vlastní formátování. Když je volána kterákoli z těchto metod formátování, předá <xref:System.Type> objekt, který <xref:System.ICustomFormatter> představuje rozhraní <xref:System.IFormatProvider.GetFormat%2A> pro metodu poskytovatele formátu. Metoda je pak zodpovědná za <xref:System.ICustomFormatter> vrácení implementace, která poskytuje vlastní formátování. <xref:System.IFormatProvider.GetFormat%2A>

Rozhraní má jedinou <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29>metodu, která je volána automaticky metodou složeného formátování, jednou pro každou položku formátu ve složeném formátovacím řetězci. <xref:System.ICustomFormatter> Metoda má tři parametry: formátovací řetězec, který `formatString` představuje argument v položce formátu, objekt <xref:System.IFormatProvider> pro formátování a objekt, který poskytuje služby formátování. <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29> Obvykle třída, která implementuje <xref:System.ICustomFormatter> také implementuje <xref:System.IFormatProvider>, takže tento poslední parametr je odkazem na vlastní třídu vlastního formátování. Metoda vrátí vlastní formátovanou řetězcovou reprezentaci objektu, který má být formátován. Pokud metoda nemůže objekt naformátovat, měl by vrátit odkaz s hodnotou null`Nothing` (v Visual Basic).

Následující příklad poskytuje <xref:System.ICustomFormatter> implementaci s názvem `ByteByByteFormatter` , která zobrazuje celočíselné hodnoty jako posloupnost hexadecimálních hodnot se dvěma číslicemi následovaných mezerou.

[!code-csharp[Conceptual.Formatting.Overview#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#15)]
[!code-vb[Conceptual.Formatting.Overview#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#15)]

Následující příklad používá `ByteByByteFormatter` třídu pro formátování celočíselných hodnot. Všimněte si, <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> že metoda je volána více než jednou ve druhém <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> volání metody a že výchozí <xref:System.Globalization.NumberFormatInfo> zprostředkovatel je použit ve třetí volání metody, protože.`ByteByByteFormatter.Format` Metoda nerozpozná formátovací řetězec "N0" a vrátí odkaz s hodnotou null (`Nothing` v Visual Basic).

[!code-csharp[Conceptual.Formatting.Overview#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#16)]
[!code-vb[Conceptual.Formatting.Overview#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#16)]

<a name="RelatedTopics"></a>

## <a name="related-topics"></a>Související témata

|Název|Definice|
|-----------|----------------|
|[Standardní řetězce číselného formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Popisuje standardní formátovací řetězce, které vytvářejí běžně používané řetězcové reprezentace číselných hodnot.|
|[Vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Popisuje vlastní formátovací řetězce, které vytvářejí formáty číselných hodnot specifické pro danou aplikaci.|
|[Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Popisuje standardní formátovací řetězce, které vytvářejí běžně používané řetězcové reprezentace <xref:System.DateTime> hodnot.|
|[Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Popisuje vlastní formátovací řetězce, které vytvářejí formáty pro hodnoty specifické <xref:System.DateTime> pro aplikaci.|
|[Standardní řetězce formátu TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Popisuje standardní formátovací řetězce, které vytvářejí běžně používané řetězcové reprezentace časových intervalů.|
|[Vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Popisuje vlastní formátovací řetězce, které vytvářejí formáty časových intervalů specifické pro danou aplikaci.|
|[Výčet řetězců formátu](../../../docs/standard/base-types/enumeration-format-strings.md)|Popisuje standardní formátovací řetězce, které slouží k vytvoření řetězcové reprezentace hodnot výčtu.|
|[Složené formátování](../../../docs/standard/base-types/composite-formatting.md)|Popisuje, jak vložit jednu nebo více formátovaných hodnot do řetězce. Řetězec lze následně zobrazit v konzole nebo zapsat do datového proudu.|
|[Provádění operací formátování](../../../docs/standard/base-types/performing-formatting-operations.md)|Obsahuje seznam témat, která poskytují podrobné pokyny pro provádění konkrétních operací formátování.|
|[Analýza řetězců](../../../docs/standard/base-types/parsing-strings.md)|Popisuje, jak inicializovat objekty pro hodnoty, které jsou popsány řetězcovými reprezentacemi těchto objektů. Analýza je inverzní operace formátování.|

<a name="Reference"></a>

## <a name="reference"></a>Reference

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- <xref:System.ICustomFormatter?displayProperty=nameWithType>
