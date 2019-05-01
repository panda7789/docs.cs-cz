---
title: Typy formátování v .NET
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
ms.openlocfilehash: b0185d79d8663d552378248f0e021a7fee8f0522
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956101"
---
# <a name="formatting-types-in-net"></a>Typy formátování v .NET
<a name="Introduction"></a> Formátování je proces převodu instance třídy, struktury nebo výčtové hodnoty na řetězcové vyjádření často tak, aby výsledný řetězec, můžete zobrazovaný uživatelům nebo rekonstruován pro obnovení původního datového typu. Tento převod může představovat určité problémy:  
  
-   Způsob interního uložení hodnoty nutně neodráží způsob, uživatelé mají k jejich zobrazení. Například telefonní číslo může být uložena ve formě 8009999999, která není srozumitelná. Místo toho má být zobrazen jako 800-999-9999. Zobrazit [vlastní formátovací řetězce](#customStrings) oddílu příklad, který formátuje číslo tímto způsobem.  
  
-   Někdy není převod objektu na jeho řetězcovou reprezentaci intuitivní. Například není jasné, jak by se měla objevit řetězcová reprezentace objektu teplota nebo osoba. Příklad, který formátuje objekt teplota v mnoha různými způsoby, najdete v článku [standardní formátovací řetězce](#standardStrings) oddílu.  
  
-   Hodnoty často vyžadují specifické formátování zohledňující jazykovou verzi. Například v aplikaci, která používá čísla pro zobrazení peněžních hodnot, by měly číselné řetězce obsahovat symbol měny aktuální jazykové verze, oddělovač skupin (který, ve většině kultur, je tisíců oddělovač) a symbol desetinné čárky. Příklad najdete v tématu [formátování zohledňující jazykovou verzi pomocí poskytovatelů formátů a rozhraní IFormatProvider](#FormatProviders) oddílu.  
  
-   Aplikace může mít k zobrazení stejné hodnoty různými způsoby. Například může aplikace vyjadřovat člen výčtového typu zobrazením řetězcové reprezentace jeho názvu nebo zobrazením jeho zadané hodnoty. Příklad, který se formátování člena <xref:System.DayOfWeek> výčet různými způsoby, najdete v článku [standardní formátovací řetězce](#standardStrings) oddílu.  
  
> [!NOTE]
>  Formátování převede hodnotu typu na řetězcovou reprezentaci. Analýza je opakem formátování. Operace analýzy vytváří instanci datového typu z jeho řetězcové reprezentace. Informace o převedení řetězce na jiné datové typy najdete v tématu [Parsování řetězců](../../../docs/standard/base-types/parsing-strings.md).  
  
 .NET poskytuje bohatou podporu formátování, který umožňuje vývojářům tyto požadavky splnit.  
  
 Tento přehled obsahuje následující části:  
  
-   [Formátování v rozhraní .NET](#NetFormatting)  
  
-   [Výchozí formátování pomocí metody ToString](#DefaultToString)  
  
-   [Přepsání metody ToString](#OverrideToString)  
  
-   [Metoda ToString a formátovací řetězce](#FormatStrings)  
  
    -   [Standardní řetězce formátu](#standardStrings)  
  
    -   [Vlastní formátovací řetězce](#customStrings)  
  
    -   [Formátování řetězců a typy v knihovně tříd rozhraní .NET](#stringRef)  
  
-   [Formátování zohledňující jazykovou verzi pomocí poskytovatelů formátů a rozhraní IFormatProvider](#FormatProviders)  
  
    -   [Formátování číselných hodnot zohledňující jazykovou verzi](#numericCulture)  
  
    -   [Formátování zohledňující jazykovou verzi z hodnoty data a času](#dateCulture)  
  
-   [Rozhraní IFormattable](#IFormattable)  
  
-   [Složené formátování](#CompositeFormatting)  
  
-   [Vlastní formátování pomocí ICustomFormatter](#Custom)  
  
-   [Související témata](#RelatedTopics)  
  
-   [Referenční informace](#Reference)  
  
<a name="NetFormatting"></a>   
## <a name="formatting-in-net"></a>Formátování v rozhraní .NET  
 Základní mechanismus pro formátování je výchozí implementace <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodu, která je podrobněji popsána [výchozí formátování pomocí metody ToString](#DefaultToString) později v tomto tématu. Ale .NET nabízí několik způsobů, jak upravit a rozšířit její výchozí podporu formátování. Patří mezi ně například:  
  
-   Přepsání <xref:System.Object.ToString%2A?displayProperty=nameWithType> metoda k definování vlastní řetězcové reprezentace hodnoty objektu. Další informace najdete v tématu [přetížení metody ToString](#OverrideToString) později v tomto tématu.  
  
-   Definování specifikátorů formátu pro umožnění řetězcová reprezentace hodnoty objektu mohla mít více tvarů. Například specifikátor formátu "X" v následujícím příkazu převede celé číslo na řetězcovou reprezentaci šestnáctkové hodnoty.  
  
     [!code-csharp[Conceptual.Formatting.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#3)]
     [!code-vb[Conceptual.Formatting.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#3)]  
  
     Další informace o specifikátorech formátu naleznete v tématu [Metoda ToString a formátovací řetězce](#FormatStrings) oddílu.  
  
-   Použití poskytovatelů formátu výhod konvencí formátování specifické jazykové verze. Následující příkaz například zobrazí hodnotu měny pomocí konvencí formátování jazykové verze en US.  
  
     [!code-csharp[Conceptual.Formatting.Overview#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#10)]
     [!code-vb[Conceptual.Formatting.Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#10)]  
  
     Další informace o formátování pomocí poskytovatelů formátu naleznete v tématu [poskytovatelů formátu a rozhraní IFormatProvider](#FormatProviders) oddílu.  
  
-   Implementace <xref:System.IFormattable> rozhraní pro podporu převodu řetězce pomocí <xref:System.Convert> třídy a složené formátování. Další informace najdete v tématu [rozhraní IFormattable](#IFormattable) oddílu.  
  
-   Použití složeného formátování pro vložení řetězcové reprezentace hodnoty do většího řetězce. Další informace najdete v tématu [složené formátování](#CompositeFormatting) oddílu.  
  
-   Implementace <xref:System.ICustomFormatter> a <xref:System.IFormatProvider> zajištění kompletního vlastního řešení formátování. Další informace najdete v tématu [vlastní formátování pomocí ICustomFormatter](#Custom) oddílu.  
  
 V následujících částech Zkontrolujte tyto metody pro převod objektu na jeho řetězcovou reprezentaci.  
  
 [Zpět na začátek](#Introduction)  
  
<a name="DefaultToString"></a>   
## <a name="default-formatting-using-the-tostring-method"></a>Výchozí formátování pomocí metody ToString  
 Každý typ, který je odvozen z <xref:System.Object?displayProperty=nameWithType> automaticky dědí metodu `ToString` metodu, která ve výchozím nastavení vrátí název typu. Následující příklad ukazuje takovouto výchozí `ToString` metody. Definuje třídu s názvem `Automobile` , který nemá žádnou implementaci. Když je vytvořena instance třídy a jeho `ToString` metoda je volána, zobrazí se název jejího typu. Všimněte si, `ToString` metoda není explicitně volána v příkladu. <xref:System.Console.WriteLine%28System.Object%29?displayProperty=nameWithType> Implicitně volá metodu `ToString` metodu objektu je předán jako argument.  
  
 [!code-csharp[Conceptual.Formatting.Overview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/default1.cs#1)]
 [!code-vb[Conceptual.Formatting.Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/default1.vb#1)]  
  
> [!WARNING]
>  Od verze [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[wrt](../../../includes/wrt-md.md)] zahrnuje <xref:Windows.Foundation.IStringable> rozhraní s jedinou metodu [IStringable.ToString](xref:Windows.Foundation.IStringable.ToString%2A), která poskytuje výchozí podporu formátování. Doporučujeme však, že se spravovanými typy neimplementují `IStringable` rozhraní. Další informace najdete v tématu " [!INCLUDE[wrt](../../../includes/wrt-md.md)] a `IStringable` rozhraní" v části <xref:System.Object.ToString%2A?displayProperty=nameWithType> referenční stránce.  
  
 Protože všechny typy jiné než rozhraní jsou odvozeny z <xref:System.Object>, tato funkce je automaticky poskytnuta vlastním třídám nebo strukturám. Však nabízí funkce ve výchozím nastavení `ToString` metoda, je omezený: I když se identifikuje typ, není schopna poskytnout žádné informace o instanci typu. Chcete-li poskytnout řetězcovou reprezentaci objektu, který obsahuje informace o tomto objektu, je nutné přepsat `ToString` metody.  
  
> [!NOTE]
>  Struktury dědí z <xref:System.ValueType>, který je zase odvozen z <xref:System.Object>. I když <xref:System.ValueType> přepíše <xref:System.Object.ToString%2A?displayProperty=nameWithType>, jejich implementace jsou totožné.  
  
 [Zpět na začátek](#Introduction)  
  
<a name="OverrideToString"></a>   
## <a name="overriding-the-tostring-method"></a>Přepsání metody ToString  
 Zobrazení názvu typu má často omezené použití a neumožňuje odběratelům vašich typů rozlišit jednu instanci od druhé. Však můžete přepsat `ToString` metodu pro poskytnutí užitečnější reprezentace hodnoty objektu. Následující příklad definuje `Temperature` objektu a přepsání jeho `ToString` metodu pro zobrazení teploty ve stupních Celsia.  
  
 [!code-csharp[Conceptual.Formatting.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/overrides1.cs#2)]
 [!code-vb[Conceptual.Formatting.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/overrides1.vb#2)]  
  
 V rozhraní .NET `ToString` metoda každého primitivního hodnotového typu bylo přepsáno pro zobrazení hodnotu objektu namísto jeho názvu. V následující tabulce jsou uvedeny přepsání pro každý primitivní typ. Všimněte si, že většina přepsaných metod volá jiné přetížení `ToString` metoda a předejte jí specifikátor formátu "G", který definuje obecný formát pro daný typ, a <xref:System.IFormatProvider> objekt, který představuje aktuální jazykovou verzi.  
  
|Type|Přetížení metody ToString|  
|----------|-----------------------|  
|<xref:System.Boolean>|Vrátí buď <xref:System.Boolean.TrueString?displayProperty=nameWithType> nebo <xref:System.Boolean.FalseString?displayProperty=nameWithType>.|  
|<xref:System.Byte>|Volání `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` k formátování <xref:System.Byte> hodnotu pro aktuální jazykovou verzi.|  
|<xref:System.Char>|Vrátí znak jako řetězec.|  
|<xref:System.DateTime>|Volání `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` pro formátování hodnoty data a času pro aktuální jazykovou verzi.|  
|<xref:System.Decimal>|Volání `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` k formátování <xref:System.Decimal> hodnotu pro aktuální jazykovou verzi.|  
|<xref:System.Double>|Volání `Double.ToString("G", NumberFormatInfo.CurrentInfo)` k formátování <xref:System.Double> hodnotu pro aktuální jazykovou verzi.|  
|<xref:System.Int16>|Volání `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` k formátování <xref:System.Int16> hodnotu pro aktuální jazykovou verzi.|  
|<xref:System.Int32>|Volání `Int32.ToString("G", NumberFormatInfo.CurrentInfo)` k formátování <xref:System.Int32> hodnotu pro aktuální jazykovou verzi.|  
|<xref:System.Int64>|Volání `Int64.ToString("G", NumberFormatInfo.CurrentInfo)` k formátování <xref:System.Int64> hodnotu pro aktuální jazykovou verzi.|  
|<xref:System.SByte>|Volání `SByte.ToString("G", NumberFormatInfo.CurrentInfo)` k formátování <xref:System.SByte> hodnotu pro aktuální jazykovou verzi.|  
|<xref:System.Single>|Volání `Single.ToString("G", NumberFormatInfo.CurrentInfo)` k formátování <xref:System.Single> hodnotu pro aktuální jazykovou verzi.|  
|<xref:System.UInt16>|Volání `UInt16.ToString("G", NumberFormatInfo.CurrentInfo)` k formátování <xref:System.UInt16> hodnotu pro aktuální jazykovou verzi.|  
|<xref:System.UInt32>|Volání `UInt32.ToString("G", NumberFormatInfo.CurrentInfo)` k formátování <xref:System.UInt32> hodnotu pro aktuální jazykovou verzi.|  
|<xref:System.UInt64>|Volání `UInt64.ToString("G", NumberFormatInfo.CurrentInfo)` k formátování <xref:System.UInt64> hodnotu pro aktuální jazykovou verzi.|  
  
 [Zpět na začátek](#Introduction)  
  
<a name="FormatStrings"></a>   
## <a name="the-tostring-method-and-format-strings"></a>Metoda ToString a formátovací řetězce  
 Spoléhání se na výchozí `ToString` metoda nebo přepsání `ToString` je vhodné, pokud má objekt jedinou řetězcovou reprezentaci. Hodnota objektu má však často více reprezentací. Například může být vyjádřena teplotu ve stupních Fahrenheita, stupních Celsia nebo kelvinech. Obdobně celočíselná hodnota 10 může být reprezentován mnoha způsoby, včetně 10, 10.0, 1.0e01 nebo 10,00 USD.  
  
 Pokud chcete povolit více řetězcových reprezentací pro jednu hodnotu, používá .NET formátovací řetězce. Formátovací řetězec je řetězec, který obsahuje jeden nebo více předdefinovaných specifikátorů formátu, což jsou jednotlivé znaky nebo skupiny znaků, které definují způsob, jakým `ToString` metoda formátovat svůj výstup. Formátovací řetězec je pak předán jako parametr objektu `ToString` metody a určuje, jak by se měla zobrazit řetězcové reprezentace hodnoty tohoto objektu.  
  
 Všechny číselné typy, datum a čas typy a výčtové typy v .NET podporují předdefinovanou sadu specifikátorů formátu. Formátovací řetězce můžete také použít k definování více řetězcových reprezentací definovaného aplikací datových typů.  
  
<a name="standardStrings"></a>   
### <a name="standard-format-strings"></a>Standardní řetězce formátu  
 Standardní formátovací řetězec obsahuje jeden specifikátor formátu, který je abecední znak, který definuje řetězcovou reprezentaci objektu, ke kterému je uplatněna, spolu s volitelným specifikátorem přesnosti, která ovlivňuje počet číslic zobrazovaných ve výsledný řetězec. Pokud specifikátor přesnosti je vynechán nebo není podporován, standardní specifikátor formátu je stejná jako řetězec standardního formátu.  
  
 .NET definuje sadu standardních specifikátorů formátu pro všechny číselné typy, všechna data a času typy a všechny typy výčtu. Každá z těchto kategorií například podporuje specifikátor standardního formátu "G", který definuje obecnou řetězcovou reprezentaci hodnoty daného typu.  
  
 Standardní formátovací řetězce pro výčtové typy přímo ovládají řetězcovou reprezentaci hodnoty. Formátovací řetězce předané hodnoty výčtu `ToString` metoda určit, zda je hodnota zobrazena pomocí jejího řetězcového názvu ("G" a "F" specifikátory formátu), její základní celočíselné hodnoty (specifikátor formátu "D") nebo její šestnáctkové hodnoty ("X "specifikátor formátu). Následující příklad ukazuje použití standardního formátovacího řetězce pro formátování <xref:System.DayOfWeek> hodnota výčtu.  
  
 [!code-csharp[Conceptual.Formatting.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/standard1.cs#4)]
 [!code-vb[Conceptual.Formatting.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/standard1.vb#4)]  
  
 Informace o formátovacích řetězcích výčtů naleznete v tématu [výčet řetězců formátu](../../../docs/standard/base-types/enumeration-format-strings.md).  
  
 Standardní formátovací řetězce pro číselné typy obvykle definují výsledný řetězec, jehož přesný vzhled je řízen jeden nebo více hodnot vlastností. Specifikátor formátu "C" například zformátuje číslo jako hodnotu měny. Při volání `ToString` metoda se specifikátorem formátu "C" jako jediným parametrem, následující hodnoty vlastností z aktuální jazykové verze <xref:System.Globalization.NumberFormatInfo> objektů se používají k definování řetězcové reprezentace číselné hodnoty:  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A> Vlastnost, která určuje symbol měny aktuální jazykové verze.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> Nebo <xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A> vlastnost, která vrátí celé číslo, které určuje následující:  
  
    -   Umístění symbolu měny.  
  
    -   Určuje, zda jsou označeny se záporným znaménkem, koncové záporného znaménka nebo závorky záporné hodnoty.  
  
    -   Určuje, zda se mezi číselnou hodnotou a symbolem měny zobrazí mezera.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A> Vlastnost, která definuje počet zlomkových číslic ve výsledném řetězci.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A> Vlastnost, která definuje symbol desetinného oddělovače ve výsledném řetězci.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A> Vlastnost, která definuje symbol oddělovače skupiny.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A> Vlastnost, která definuje počet číslic v každé skupině nalevo od desetinné čárky.  
  
-   <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> Vlastnost, která určuje záporné znaménko použité ve výsledném řetězci, pokud nejsou použity závorky k označení záporné hodnoty.  
  
 Kromě toho řetězce číselného formátu mohou obsahovat specifikátor přesnosti. Význam tohoto specifikátoru závisí na řetězci formátu, pomocí kterého se používá, ale obvykle označuje buď celkový počet číslic nebo počet zlomkových číslic, které se mají zobrazit ve výsledném řetězci. Například v následujícím příkladu "X 4" standardní číselný řetězec a specifikátor přesnosti vytvořit hodnotu řetězce, která má čtyři šestnáctkové číslice.  
  
 [!code-csharp[Conceptual.Formatting.Overview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/precisionspecifier1.cs#6)]
 [!code-vb[Conceptual.Formatting.Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/precisionspecifier1.vb#6)]  
  
 Další informace o standardních číselných formátovacích řetězcích naleznete v tématu [Standard Numeric Format Strings](../../../docs/standard/base-types/standard-numeric-format-strings.md).  
  
 Standardní formátovací řetězce pro hodnoty data a času jsou zástupci pro vlastní formátovací řetězce uložené určitou <xref:System.Globalization.DateTimeFormatInfo> vlastnost. Například volání `ToString` metoda hodnoty data a času se specifikátorem formátu "D" zobrazí datum a čas pomocí vlastního formátovacího řetězce uložené v aktuální jazykové verze <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> vlastnost. (Další informace o vlastních formátovacích řetězcích naleznete v tématu [další části](#customStrings).) Následující příklad ukazuje tuto vazbu.  
  
 [!code-csharp[Conceptual.Formatting.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/alias1.cs#5)]
 [!code-vb[Conceptual.Formatting.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/alias1.vb#5)]  
  
 Další informace o standardní hodnoty data a času formátovací řetězce najdete v tématu [standardní hodnoty data a řetězce formátu časových](../../../docs/standard/base-types/standard-date-and-time-format-strings.md).  
  
 Standardní formátovací řetězce můžete také použít pro definování řetězcové reprezentace objektu definovaného aplikací, který je vytvořen v objektu `ToString(String)` metody. Můžete definovat určité standardní specifikátory formátu, které podporovány vašim objektem, a můžete určit, jestli jsou malá a velká písmena nebo velká a malá písmena. Implementace `ToString(String)` metoda by měla podporovat následující:  
  
-   Specifikátor formátu "G" představující obvyklý nebo obecný formát objektu. Konstruktor bez parametrů přetížení váš objekt `ToString` metoda by měla volat jeho `ToString(String)` přetížení a předat standardní formátovací řetězec "G".  
  
-   Podporu specifikátoru formátu, který je roven nulovému odkazu (`Nothing` v jazyce Visual Basic). Specifikátor formátu, který je roven nulovému odkazu by měl být považován za ekvivalent specifikátoru formátu "G".  
  
 Například `Temperature` třída může interně uchovávat teplotu ve stupních Celsia a použít specifikátory formátu k reprezentaci hodnoty `Temperature` objektu ve stupních Celsia, stupních Fahrenheita a kelvinech. V následujícím příkladu je uvedena ukázka.  
  
 [!code-csharp[Conceptual.Formatting.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/appstandard1.cs#7)]
 [!code-vb[Conceptual.Formatting.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/appstandard1.vb#7)]  
  
 [Zpět na začátek](#Introduction)  
  
<a name="customStrings"></a>   
### <a name="custom-format-strings"></a>Vlastní formátovací řetězce  
 Kromě standardních formátovacích řetězců definuje rozhraní .NET vlastní formátovací řetězce pro číselné hodnoty a hodnoty data a času. Řetězec vlastního formátu se skládá z jednoho nebo více vlastního specifikátoru formátu definujících řetězcovou reprezentaci hodnoty. Například vlastní data a času naformátovat řetězec "rrrr/mm/dd hh:mm:ss.ffff t zzz" převede datum na řetězcovou reprezentaci ve tvaru "2008/11/15 07:45:00.0000 P-08: 00" pro jazykovou verzi en US. Podobně vlastní formátovací řetězec "0000" převede celočíselnou hodnotu 12 na "0012". Úplný seznam vlastních formátovacích řetězců naleznete v tématu [vlastní data a řetězce formátu časových](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) a [Custom Numeric Format Strings](../../../docs/standard/base-types/custom-numeric-format-strings.md).  
  
 Pokud řetězec formátu obsahuje jeden vlastní specifikátor formátu, by měl párový příkaz specifikátor formátu procent (%) symbol, který má nedocházelo k záměně se standardním specifikátorem formátu. Následující příklad používá specifikátor vlastního formátu "M" k zobrazení jednociferného nebo dvojciferného čísla měsíce konkrétního data.  
  
 [!code-csharp[Conceptual.Formatting.Overview#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/singlecustom1.cs#8)]
 [!code-vb[Conceptual.Formatting.Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/singlecustom1.vb#8)]  
  
 Mnoho standardních formátovacích řetězců pro hodnoty data a času jsou zástupci pro vlastní formátovací řetězce, které jsou definovány vlastnostmi objektu <xref:System.Globalization.DateTimeFormatInfo> objektu. Vlastní formátovací řetězce také nabízejí značnou flexibilitu při poskytování formátování definovaného aplikací pro číselné hodnoty nebo hodnoty data a času. Můžete definovat vlastní vlastní výsledný řetězec pro číselné hodnoty a hodnoty data a času kombinováním více vlastních specifikátorů formátu do jediného vlastního formátovacího řetězce. Následující příklad definuje vlastní formátovací řetězec, který zobrazuje den v týdnu v závorkách za názvem měsíce, dne a roku.  
  
 [!code-csharp[Conceptual.Formatting.Overview#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/custom1.cs#9)]
 [!code-vb[Conceptual.Formatting.Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/custom1.vb#9)]  
  
 Následující příklad definuje vlastní formátovací řetězec, který se zobrazí <xref:System.Int64> hodnotu jako standardní, sedmičíselné americké telefonní číslo spolu s jeho směrové číslo oblasti.  
  
 [!code-csharp[Conceptual.Formatting.Overview#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/telnumber1.cs#21)]
 [!code-vb[Conceptual.Formatting.Overview#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/telnumber1.vb#21)]  
  
 Ačkoli standardní formátovací řetězce mohou zpracovat většinu požadavků na formátování pro vaše typy definované aplikací, můžete také definovat vlastní specifikátory formátu pro formátování těchto typů.  
  
 [Zpět na začátek](#Introduction)  
  
<a name="stringRef"></a>   
### <a name="format-strings-and-net-types"></a>Formátování řetězců a typy .NET  
 Všechny číselné typy (to znamená, <xref:System.Byte>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>a <xref:System.Numerics.BigInteger>typy), stejně jako <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, <xref:System.Guid>, a podporují všechny typy výčtu, formátování s řetězci formátu. Informace o podporované jednotlivými typy konkrétního formátovací řetězce naleznete v následujících tématech:  
  
|Název|Definice|  
|-----------|----------------|  
|[Standardní řetězce číselného formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Popisuje standardní formátovací řetězce, které vytvářejí běžně používané řetězcové reprezentace číselných hodnot.|  
|[Vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Popisuje vlastní formátovací řetězce, které vytvářejí formáty číselných hodnot specifické pro aplikaci.|  
|[Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Popisuje standardní formátovací řetězce, které vytvářejí běžně používané řetězcové reprezentace <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty.|  
|[Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Popisuje vlastní formátovací řetězce, které vytvářejí formáty specifické pro aplikaci pro <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty.|  
|[Standardní řetězce formátu TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Popisuje standardní formátovací řetězce, které vytvářejí běžně používané řetězcové reprezentace časových intervalů.|  
|[Vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Popisuje vlastní formátovací řetězce, které vytvářejí formáty specifické pro aplikaci pro časové intervaly.|  
|[Výčet řetězců formátu](../../../docs/standard/base-types/enumeration-format-strings.md)|Popisuje standardní formátovací řetězce, které se používají k vytvoření řetězcové reprezentace hodnot výčtu.|  
|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|Popisuje standardní formátovací řetězce pro <xref:System.Guid> hodnoty.|  
  
<a name="FormatProviders"></a>   
## <a name="culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface"></a>Formátování zohledňující jazykovou verzi s použitím poskytovatelů formátu a rozhraní IFormatProvider  
 I když specifikátory formátu umožňují přizpůsobit formátování objektů, vytváření smysluplné řetězcové reprezentace objektů často vyžaduje další informace o formátování. Například formátování čísla jako hodnota měny pomocí standardního formátovacího řetězce "C" nebo vlastního formátovacího řetězce, jako "$ #, #. 00", vyžaduje minimálně informace o správném symbolu měny, oddělovači skupin a oddělovač desetinných míst, třeba k dispozici pro vložení formátovaný řetězec. V rozhraní .NET, je k dispozici prostřednictvím tohoto Další informace o formátování <xref:System.IFormatProvider> rozhraní, která se poskytuje jako parametr pro jeden nebo více přetížení `ToString` metoda číselné typy a typy data a času. <xref:System.IFormatProvider> implementace se používá v rozhraní .NET pro podporu formátování specifické pro jazykovou verzi. Následující příklad ukazuje, jak se řetězcová reprezentace objektu mění při je formátována pomocí tří <xref:System.IFormatProvider> objektů představujících různé jazykové verze.  
  
 [!code-csharp[Conceptual.Formatting.Overview#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformatprovider1.cs#11)]
 [!code-vb[Conceptual.Formatting.Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformatprovider1.vb#11)]  
  
 <xref:System.IFormatProvider> Rozhraní zahrnuje jednu metodu <xref:System.IFormatProvider.GetFormat%28System.Type%29>, která má jeden parametr, který určuje typ objektu, který poskytuje informace o formátování. Pokud může metoda poskytnout objekt tohoto typu, vrátí jej. V opačném případě vrátí nulový odkaz (`Nothing` v jazyce Visual Basic).  
  
 <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> je metoda zpětného volání. Při volání `ToString` přetížení metody, která zahrnuje <xref:System.IFormatProvider> parametr, volá <xref:System.IFormatProvider.GetFormat%2A> metodu, která <xref:System.IFormatProvider> objektu. <xref:System.IFormatProvider.GetFormat%2A> Metoda je zodpovědný za vrácení objektu, který obsahuje nezbytné informace o formátování specifikované parametrem jeho `formatType` parametr do `ToString` metoda.  
  
 Několik metod formátování nebo řetězec převod obsahují parametr typu <xref:System.IFormatProvider>, ale v mnoha případech je hodnota parametru ignorována, pokud je volána metoda. V následující tabulce jsou uvedeny některé metody formátování, které používají tento parametr a typ <xref:System.Type> objekt, který předávají <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metoda.  
  
|Metoda|Typ `formatType` parametr|  
|------------|------------------------------------|  
|`ToString` Metoda číselné typy|<xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>|  
|`ToString` Metoda typy data a času|<xref:System.Globalization.DateTimeFormatInfo?displayProperty=nameWithType>|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|  
  
> [!NOTE]
>  `ToString` Metody číselné typy a typy data a času jsou přetížené a pouze některá přetížení obsahují <xref:System.IFormatProvider> parametru. Pokud metoda nemá parametr typu <xref:System.IFormatProvider>, objekt, který je vrácený <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnost je místo něho předán. Například volání výchozí <xref:System.Int32.ToString?displayProperty=nameWithType> metoda nakonec vyústí ve volání metody, jako je následující: `Int32.ToString("G", System.Globalization.CultureInfo.CurrentCulture)`.  
  
 .NET poskytuje tři třídy, které implementují <xref:System.IFormatProvider>:  
  
-   <xref:System.Globalization.DateTimeFormatInfo>, třídu, která poskytuje informace o formátování hodnot data a času pro konkrétní jazykovou verzi. Jeho <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementace vrátí instanci sebe sama.  
  
-   <xref:System.Globalization.NumberFormatInfo>, třídu, která poskytuje informace o formátování čísel pro konkrétní jazykovou verzi. Jeho <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementace vrátí instanci sebe sama.  
  
-   <xref:System.Globalization.CultureInfo>. Jeho <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> může vrátit implementaci <xref:System.Globalization.NumberFormatInfo> který poskytuje informace o formátování čísel nebo <xref:System.Globalization.DateTimeFormatInfo> který poskytuje informace o formátování hodnot data a času.  
  
 Můžete také implementovat vlastní poskytovatele formátu pro nahrazení kterékoli z těchto tříd. Však vaší implementace <xref:System.IFormatProvider.GetFormat%2A> metoda musí vracet objekt typu uvedené v předchozí tabulce, pokud má poskytovat informace o formátování `ToString` metody.  
  
 [Zpět na začátek](#Introduction)  
  
<a name="numericCulture"></a>   
### <a name="culture-sensitive-formatting-of-numeric-values"></a>Formátování číselných hodnot zohledňující jazykovou verzi  
 Ve výchozím nastavení je formátování číselných hodnot zohledňující jazykovou verzi. Pokud při volání metody pro formátování nezadáte jazykovou verzi, použijí se formátovacích úmluv aktuální jazykové verzi vlákna. To je znázorněno v následujícím příkladu, který čtyřikrát změní aktuální jazykovou verzi vlákna a zavolá <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> metody. V každém případě odráží výsledný řetězec formátovacích úmluv aktuální jazykové verze. Je to proto, `ToString` a `ToString(String)` metody zabalte volání do každého číselného typu `ToString(String, IFormatProvider)` metoda.  
  
 [!code-csharp[Conceptual.Formatting.Overview#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific3.cs#19)]
 [!code-vb[Conceptual.Formatting.Overview#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific3.vb#19)]  
  
 Číselná hodnota pro konkrétní jazykovou verzi může formátovat také voláním `ToString` přetížení, která má `provider` parametr a předáním některého z následujících akcí:  
  
-   A <xref:System.Globalization.CultureInfo> objekt, který představuje jazykovou verzi, jejíž úmluvy formátování se mají použít. Jeho <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> metoda vrátí hodnotu <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> vlastnost, která je <xref:System.Globalization.NumberFormatInfo> objekt, který poskytuje informace o formátování specifické pro jazykovou verzi pro číselné hodnoty.  
  
-   A <xref:System.Globalization.NumberFormatInfo> objekt, který definuje konvence formátování specifické pro jazykovou verzi pro. Jeho <xref:System.Globalization.NumberFormatInfo.GetFormat%2A> metoda vrátí instanci sebe sama.  
  
 Následující příklad používá <xref:System.Globalization.NumberFormatInfo> objekty, které představují jazykových verzí Angličtina (Velká Británie) a angličtina (Spojené státy) a neutrální jazykové verze a ruskými formátování čísla s plovoucí desetinnou čárkou.  
  
 [!code-csharp[Conceptual.Formatting.Overview#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific4.cs#20)]
 [!code-vb[Conceptual.Formatting.Overview#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific4.vb#20)]  
  
<a name="dateCulture"></a>   
### <a name="culture-sensitive-formatting-of-date-and-time-values"></a>Formátování hodnot data a času zohledňující jazykovou verzi  
 Ve výchozím nastavení je formátování hodnot data a času zohledňující jazykovou verzi. Pokud při volání metody pro formátování nezadáte jazykovou verzi, použijí se formátovacích úmluv aktuální jazykové verzi vlákna. To je znázorněno v následujícím příkladu, který čtyřikrát změní aktuální jazykovou verzi vlákna a zavolá <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> metody. V každém případě odráží výsledný řetězec formátovacích úmluv aktuální jazykové verze. Je to proto, <xref:System.DateTime.ToString?displayProperty=nameWithType>, <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType>, a <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> obalují volání metod <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> a <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody.  
  
 [!code-csharp[Conceptual.Formatting.Overview#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific1.cs#17)]
 [!code-vb[Conceptual.Formatting.Overview#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific1.vb#17)]  
  
 Hodnoty data a času pro konkrétní jazykovou verzi může formátovat také voláním <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> přetížení, která má `provider` parametr a předáním některého z následujících akcí:  
  
-   A <xref:System.Globalization.CultureInfo> objekt, který představuje jazykovou verzi, jejíž úmluvy formátování se mají použít. Jeho <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> metoda vrátí hodnotu <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vlastnost, která je <xref:System.Globalization.DateTimeFormatInfo> objekt, který poskytuje informace o formátování specifické pro jazykovou verzi pro hodnoty data a času.  
  
-   A <xref:System.Globalization.DateTimeFormatInfo> objekt, který definuje konvence formátování specifické pro jazykovou verzi pro. Jeho <xref:System.Globalization.DateTimeFormatInfo.GetFormat%2A> metoda vrátí instanci sebe sama.  
  
 Následující příklad používá <xref:System.Globalization.DateTimeFormatInfo> objekty, které představují Angličtina (Spojené státy) a jazykové verze Angličtina (Velká Británie) a neutrální jazykové verze a formátování data.  
  
 [!code-csharp[Conceptual.Formatting.Overview#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific2.cs#18)]
 [!code-vb[Conceptual.Formatting.Overview#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific2.vb#18)]  
  
<a name="IFormattable"></a>   
## <a name="the-iformattable-interface"></a>Rozhraní IFormattable  
 Obvykle typy, které přetěžují `ToString` metoda pomocí formátovacího řetězce a <xref:System.IFormatProvider> parametr implementovat taky <xref:System.IFormattable> rozhraní. Toto rozhraní má jediný člen <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, který obsahuje řetězec formátu i poskytovatele formátu jako parametry.  
  
 Implementace <xref:System.IFormattable> rozhraní pro třídu definované aplikací nabízí dvě výhody:  
  
-   Podpora převodu řetězce pomocí <xref:System.Convert> třídy. Volání <xref:System.Convert.ToString%28System.Object%29?displayProperty=nameWithType> a <xref:System.Convert.ToString%28System.Object%2CSystem.IFormatProvider%29?displayProperty=nameWithType> volání metody vaše <xref:System.IFormattable> implementace automaticky.  
  
-   Podpora pro složené formátování. Pokud položka formátu, která obsahuje formátovací řetězec se používá k formátování vašeho vlastního typu, modul common language runtime automaticky volá vaši <xref:System.IFormattable> implementace a předává jí formátovací řetězec. Další informace o složeném formátování pomocí metod, jako například <xref:System.String.Format%2A?displayProperty=nameWithType> nebo <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, najdete v článku [složené formátování](#CompositeFormatting) oddílu.  
  
 Následující příklad definuje `Temperature` třídu, která implementuje <xref:System.IFormattable> rozhraní. Podporuje "C" nebo "G" specifikátory formátu pro zobrazení teploty ve stupních Celsia, specifikátor formátu "F" pro zobrazení teploty ve stupních Fahrenheita a specifikátor formátu "K" pro zobrazení teploty ve stupních Kelvinů.  
  
 [!code-csharp[Conceptual.Formatting.Overview#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#12)]
 [!code-vb[Conceptual.Formatting.Overview#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#12)]  
  
 Následující příklad vytvoří instance `Temperature` objektu. Poté zavolá <xref:System.Convert.ToString%2A> metoda a používá několik složených formátovacích řetězců pro získání různých řetězcových reprezentací objektu `Temperature` objektu. Každá z těchto volání metod volá <xref:System.IFormattable> provádění `Temperature` třídy.  
  
 [!code-csharp[Conceptual.Formatting.Overview#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#13)]
 [!code-vb[Conceptual.Formatting.Overview#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#13)]  
  
 [Zpět na začátek](#Introduction)  
  
<a name="CompositeFormatting"></a>   
## <a name="composite-formatting"></a>Složené formátování  
 Některé metody, jako například <xref:System.String.Format%2A?displayProperty=nameWithType> a <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, podporují také složené formátování. Složený formátovací řetězec je druh šablony, která vrátí jediný řetězec, který zahrnuje řetězcové vyjádření žádného, jeden nebo více objektů. Každý objekt je reprezentován ve složeném formátovacím řetězci indexovanou položkou formátu. Index položky formátu odpovídá pozici objektu, který představuje seznam parametrů metody. Indexy jsou počítány od nuly. Například v následujícím volání <xref:System.String.Format%2A?displayProperty=nameWithType> metoda, je první položka formátu `{0:D}`, je nahrazena řetězcovou reprezentací `thatDate`; druhá položka formátu `{1}`, je nahrazena řetězcovou reprezentací `item1`; a třetí položka formátu `{2:C2}`, je nahrazena řetězcovou reprezentací `item1.Value`.  
  
 [!code-csharp[Conceptual.Formatting.Overview#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite1.cs#14)]
 [!code-vb[Conceptual.Formatting.Overview#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite1.vb#14)]  
  
 Kromě nahrazování položky formátu s řetězcovou reprezentací odpovídajícího objektu, formát položky také umožňují kontrolovat následující:  
  
-   Konkrétní způsob, který objekt je reprezentován jako řetězec, pokud objekt implementuje <xref:System.IFormattable> rozhraní a podporuje formát řetězce. To provedete pomocí následujícího index položky formátu `:` (dvojtečka), za nímž následuje platným formátovacím řetězcem. Předchozí příklad udělal to formátování hodnotu date s řetězec formátu "d" (vzor krátkého formátu data) (například `{0:d}`) a formátování numerickou hodnotu "C2" řetězec formátu (například `{2:C2}` představující číslo jako hodnotu měny se dvěma desetinné desítkových číslic.  
  
-   Šířka pole s údajem o řetězcovou reprezentaci objektu a zarovnání řetězcové vyjádření v daném poli. To provedete pomocí následujícího index položky formátu `,` (čárka) a potom jako šířku pole zadáte. Řetězec je zarovnaný vpravo v poli Pokud jako šířku pole zadáte kladnou hodnotu a vlevo – zarovná se pokud jako šířku pole zadáte záporné hodnoty. Následující příklad vlevo – zarovná hodnot data do 20 znaků pole a jeho vpravo – zarovná desetinné hodnoty s jeden zlomková číslice v poli 11 znaků.  
  
     [!code-csharp[Conceptual.Formatting.Overview#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite2.cs#22)]
     [!code-vb[Conceptual.Formatting.Overview#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite2.vb#22)]  
  
     Všimněte si, že pokud je součást řetězec zarovnání a součást řetězec formátu, nejprve předchází ten (například `{0,-20:g}`.  
  
 Další informace o složeném formátování naleznete v tématu [složené formátování](../../../docs/standard/base-types/composite-formatting.md).  
  
 [Zpět na začátek](#Introduction)  
  
<a name="Custom"></a>   
## <a name="custom-formatting-with-icustomformatter"></a>Vlastní formátování pomocí ICustomFormatter  
 Dvě metody pro složené formátování, <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> a <xref:System.Text.StringBuilder.AppendFormat%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, zahrnují parametr poskytovatele formátu, který podporuje vlastní formátování. Když je zavolána některá z těchto metod formátování, předá <xref:System.Type> objekt, který reprezentuje <xref:System.ICustomFormatter> rozhraní poskytovatele formátu <xref:System.IFormatProvider.GetFormat%2A> metoda. <xref:System.IFormatProvider.GetFormat%2A> Metoda je pak zodpovědná za navrácení <xref:System.ICustomFormatter> implementace, která poskytuje vlastní formátování.  
  
 <xref:System.ICustomFormatter> Rozhraní obsahuje jedinou metodu, <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29>, která je volána automaticky metodou složeného formátování pro každou položku formátu ve složeném formátovacím řetězci. <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29> Metoda má tři parametry: formátovací řetězec, který představuje `formatString` argument v položce formátu, objekt pro formátování a <xref:System.IFormatProvider> služby, který poskytuje formátování. Obvykle třída, která implementuje <xref:System.ICustomFormatter> také implementuje <xref:System.IFormatProvider>, takže tento poslední parametr je odkazem na vlastní formátování třídu. Metoda vrátí řetězcovou reprezentaci vlastního formátování objektu, který má být formátováno. Pokud metoda nemůže objekt zformátovat, měl by být vrácen nulový odkaz (`Nothing` v jazyce Visual Basic).  
  
 Následující příklad uvádí <xref:System.ICustomFormatter> implementace s názvem `ByteByByteFormatter` zobrazující celočíselné hodnoty jako sekvenci dvěma číslicemi šestnáctkových hodnot následovanou mezerou.  
  
 [!code-csharp[Conceptual.Formatting.Overview#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#15)]
 [!code-vb[Conceptual.Formatting.Overview#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#15)]  
  
 V následujícím příkladu `ByteByByteFormatter` třídy pro formátování celočíselné hodnoty. Všimněte si, že <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> metoda je volána více než jednou za sekundu <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> volání metody a že výchozí <xref:System.Globalization.NumberFormatInfo> zprostředkovatele je použit ve třetím volání metody, protože.`ByteByByteFormatter.Format` Metoda nerozpozná formátovací řetězec "N0" a vrátí nulový odkaz (`Nothing` v jazyce Visual Basic).  
  
 [!code-csharp[Conceptual.Formatting.Overview#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#16)]
 [!code-vb[Conceptual.Formatting.Overview#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#16)]  
  
 [Zpět na začátek](#Introduction)  
  
<a name="RelatedTopics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Definice|  
|-----------|----------------|  
|[Standardní řetězce číselného formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Popisuje standardní formátovací řetězce, které vytvářejí běžně používané řetězcové reprezentace číselných hodnot.|  
|[Vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Popisuje vlastní formátovací řetězce, které vytvářejí formáty číselných hodnot specifické pro aplikaci.|  
|[Standardní řetězce formátu data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Popisuje standardní formátovací řetězce, které vytvářejí běžně používané řetězcové reprezentace <xref:System.DateTime> hodnoty.|  
|[Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Popisuje vlastní formátovací řetězce, které vytvářejí formáty specifické pro aplikaci pro <xref:System.DateTime> hodnoty.|  
|[Standardní řetězce formátu TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Popisuje standardní formátovací řetězce, které vytvářejí běžně používané řetězcové reprezentace časových intervalů.|  
|[Vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Popisuje vlastní formátovací řetězce, které vytvářejí formáty specifické pro aplikaci pro časové intervaly.|  
|[Výčet řetězců formátu](../../../docs/standard/base-types/enumeration-format-strings.md)|Popisuje standardní formátovací řetězce, které se používají k vytvoření řetězcové reprezentace hodnot výčtu.|  
|[Složené formátování](../../../docs/standard/base-types/composite-formatting.md)|Popisuje postup vložení jedné nebo více formátovaných hodnot do řetězce. Řetězec lze následně zobrazit na konzole nebo zapisovat do datového proudu.|  
|[Provádění operací formátování](../../../docs/standard/base-types/performing-formatting-operations.md)|Seznam témat, která poskytují podrobné pokyny pro provádění určitých operací formátování.|  
|[Analýza řetězců](../../../docs/standard/base-types/parsing-strings.md)|Popisuje, jak inicializovat objekty s hodnotami popsanými řetězcovou interpretací těchto objektů. Analýza je inverzní operace k formátování.|  
  
 [Zpět na začátek](#Introduction)  
  
<a name="Reference"></a>   
## <a name="reference"></a>Odkaz  
 <xref:System.IFormattable?displayProperty=nameWithType>  
  
 <xref:System.IFormatProvider?displayProperty=nameWithType>  
  
 <xref:System.ICustomFormatter?displayProperty=nameWithType>
