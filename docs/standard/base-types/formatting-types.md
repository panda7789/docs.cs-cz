---
title: "Typy formátování v rozhraní .NET"
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
caps.latest.revision: "43"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 816337ead810be405339a0616798a06689b97315
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="formatting-types-in-net"></a>Typy formátování v rozhraní .NET
<a name="Introduction"></a>Formátování je proces převodu instance třídy, struktury nebo výčtové hodnoty na řetězcovou reprezentaci, často tak, aby výsledný řetězec, můžete se uživatelům zobrazí nebo deserializovat k obnovení původního datového typu. Tento převod může představovat určité problémy:  
  
-   Způsob hodnoty se uloží interně nutně neodráží způsob, uživatelé mají k jejich zobrazení. Například telefonní číslo pravděpodobně uloží do formuláře 8009999999, která není srozumitelná. Má být místo toho zobrazen jako 800-999-9999. Najdete v článku [vlastní řetězce formátu](#customStrings) části pro příklad, který zformátuje číslo tímto způsobem.  
  
-   Převod objektu na řetězcovou reprezentaci někdy není intuitivní. Například není jasné, jak zobrazit řetězcovou reprezentaci objektu teplota nebo objekt osoba. Příklad, který zformátuje objekt teploty v mnoha různými způsoby, najdete v článku [standardní řetězce formátu](#standardStrings) části.  
  
-   Hodnoty často vyžadují formátování jazykové verzi. V aplikaci, která používá čísla tak, aby odrážela peněžní hodnoty, například číselných řetězců by měla obsahovat symbolu měny aktuální jazykové verze, oddělovač skupin (což, u většiny verzí je tisíců oddělovače) a oddělovač tisíců. Příklad, naleznete v části [jazykovou formátování s zprostředkovatelé formátu a rozhraní IFormatProvider](#FormatProviders) části.  
  
-   Aplikace může být nutné zobrazit stejnou hodnotu různými způsoby. Aplikace může například představovat člena výčtu zobrazením řetězcovou reprezentaci jeho názvu nebo zobrazením její základní hodnoty. Pro příklad, který zformátuje členem <xref:System.DayOfWeek> výčtu různými způsoby, najdete v článku [standardní řetězce formátu](#standardStrings) části.  
  
> [!NOTE]
>  Hodnota typu formátování převede řetězcovou reprezentaci. Analýza je inverzní formátování. Operaci analýzy vytvoří instance datového typu z jeho řetězcová reprezentace. Informace o převádění řetězců na jiné datové typy najdete v tématu [Analýza řetězců](../../../docs/standard/base-types/parsing-strings.md).  
  
 Rozhraní .NET poskytuje rozsáhlou podporu formátování, které umožňuje vývojářům tyto požadavky.  
  
 Tento přehled obsahuje následující části:  
  
-   [Formátování v rozhraní .NET](#NetFormatting)  
  
-   [Výchozí formátování pomocí metody ToString](#DefaultToString)  
  
-   [Přetížení metody ToString](#OverrideToString)  
  
-   [Řetězce formátu a ToString – metoda](#FormatStrings)  
  
    -   [Standardní řetězce formátu](#standardStrings)  
  
    -   [Vlastní řetězce formátu](#customStrings)  
  
    -   [Formátování řetězců a typy knihovna tříd rozhraní .NET](#stringRef)  
  
-   [Formátování jazykové verzi s zprostředkovatelé formátu a rozhraní IFormatProvider](#FormatProviders)  
  
    -   [Jazykovou formátování číselných hodnot](#numericCulture)  
  
    -   [Jazykovou formátování hodnoty data a času](#dateCulture)  
  
-   [Rozhraní IFormattable](#IFormattable)  
  
-   [Složené formátování](#CompositeFormatting)  
  
-   [Vlastní formátování pomocí ICustomFormatter](#Custom)  
  
-   [Související témata](#RelatedTopics)  
  
-   [Referenční dokumentace](#Reference)  
  
<a name="NetFormatting"></a>   
## <a name="formatting-in-net"></a>Formátování v rozhraní .NET  
 Základní mechanismus pro formátování je výchozí implementaci <xref:System.Object.ToString%2A?displayProperty=nameWithType> metody, která je popsána v [výchozí formátování s použitím metody ToString](#DefaultToString) později v tomto tématu. Ale .NET poskytuje několik způsobů, jak upravit a rozšířit jeho výchozí formátování podpory. Patří mezi ně například:  
  
-   Přepsání <xref:System.Object.ToString%2A?displayProperty=nameWithType> metoda definovat vlastní řetězcová reprezentace hodnoty objektu. Další informace najdete v tématu [přetížení metody ToString](#OverrideToString) později v tomto tématu.  
  
-   Definování specifikátorů formátu, které umožňují řetězcová reprezentace hodnoty objektu provést více formulářů. Například specifikátor formátu "X" v následujícím příkazu převede celé řetězcová reprezentace šestnáctkové hodnoty.  
  
     [!code-csharp[Conceptual.Formatting.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#3)]
     [!code-vb[Conceptual.Formatting.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#3)]  
  
     Další informace o specifikátory formátu v tématu [metody ToString a řetězce formátu](#FormatStrings) části.  
  
-   Pomocí poskytovatelů formátu využívat výhod konvencí formátování konkrétní jazykové verze. Následující příkaz například zobrazí hodnotu měny pomocí konvencí formátování jazykové verze en US.  
  
     [!code-csharp[Conceptual.Formatting.Overview#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#10)]
     [!code-vb[Conceptual.Formatting.Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#10)]  
  
     Další informace o formátování pomocí formátu poskytovatelů najdete v tématu [zprostředkovatelé formátu a rozhraní IFormatProvider](#FormatProviders) části.  
  
-   Implementace <xref:System.IFormattable> rozhraní pro podporu obou převod řetězce s <xref:System.Convert> třídy a složené formátování. Další informace najdete v tématu [rozhraní IFormattable](#IFormattable) části.  
  
-   Použití složené formátování pro vložení řetězcovou reprezentaci hodnoty řetězců. Další informace najdete v tématu [složené formátování](#CompositeFormatting) části.  
  
-   Implementace <xref:System.ICustomFormatter> a <xref:System.IFormatProvider> zajistit kompletního řešení vlastní formátování. Další informace najdete v tématu [vlastní formátování pomocí ICustomFormatter](#Custom) části.  
  
 V následujících částech Zkontrolujte tyto metody pro převod na řetězcovou reprezentaci objektu.  
  
 [Zpět na začátek](#Introduction)  
  
<a name="DefaultToString"></a>   
## <a name="default-formatting-using-the-tostring-method"></a>Výchozí formátování pomocí metody ToString  
 Každý typ, který je odvozený od <xref:System.Object?displayProperty=nameWithType> automaticky zdědí bez parametrů `ToString` metoda, která vrátí název typu ve výchozím nastavení. Následující příklad ilustruje výchozí `ToString` metoda. Definuje třídu s názvem `Automobile` , nemá žádnou implementaci. Když je vytvořena instance třídy a jeho `ToString` metoda je volána, zobrazí se jeho název typu. Všimněte si, že `ToString` metoda není volána explicitně v příkladu. <xref:System.Console.WriteLine%28System.Object%29?displayProperty=nameWithType> Metoda implicitně volá `ToString` metodu objektu do ní předán jako argument.  
  
 [!code-csharp[Conceptual.Formatting.Overview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/default1.cs#1)]
 [!code-vb[Conceptual.Formatting.Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/default1.vb#1)]  
  
> [!WARNING]
>  Od verze [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[wrt](../../../includes/wrt-md.md)] zahrnuje [IStringable](http://msdn.microsoft.com/library/windows/apps/windows.foundation.istringable.aspx) rozhraní s jedinou metodu [IStringable.ToString](http://msdn.microsoft.com/library/windows/apps/windows.foundation.istringable.tostring.aspx), který poskytuje výchozí formátování podpory. Doporučujeme však, že spravované typy neimplementují `IStringable` rozhraní. Další informace najdete v tématu " [!INCLUDE[wrt](../../../includes/wrt-md.md)] a `IStringable` rozhraní" části na <xref:System.Object.ToString%2A?displayProperty=nameWithType> stránka s referencemi k.  
  
 Protože všechny typy než rozhraní jsou odvozeny od <xref:System.Object>, tato funkce je automaticky poskytované vaše vlastní třídy nebo struktury. Však funkce nabízené výchozí `ToString` metoda, je omezený: i když identifikuje typ, se nepodaří zadejte informace o instanci typu. Pokud chcete zadat řetězcovou reprezentaci objektu, který obsahuje informace o tomto objektu, je nutné přepsat `ToString` metoda.  
  
> [!NOTE]
>  Struktury dědí z <xref:System.ValueType>, který je zase odvozen z <xref:System.Object>. I když <xref:System.ValueType> přepsání <xref:System.Object.ToString%2A?displayProperty=nameWithType>, jejich implementace jsou totožné.  
  
 [Zpět na začátek](#Introduction)  
  
<a name="OverrideToString"></a>   
## <a name="overriding-the-tostring-method"></a>Přetížení metody ToString  
 Zobrazení názvu typu je často omezené použití a neumožňuje odběratelům vašich typů rozlišit jednu instanci z jiné. Však můžete přepsat `ToString` metodu za účelem poskytnutí užitečnější reprezentace hodnoty objektu. V následujícím příkladu definuje `Temperature` objekt a přepsání jeho `ToString` metodu pro zobrazení teploty ve stupních c.  
  
 [!code-csharp[Conceptual.Formatting.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/overrides1.cs#2)]
 [!code-vb[Conceptual.Formatting.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/overrides1.vb#2)]  
  
 V rozhraní .NET `ToString` metoda každého typu primitivní hodnota bylo přepsáno zobrazíte hodnota objektu místo jeho názvu. V následující tabulce jsou přepsání pro jednotlivé primitivní typy. Všimněte si, že většina přepsaného metod volá jiné přetížení `ToString` metoda a předejte ji specifikátor formátu "G", který definuje obecnou strukturu pro tento typ, a <xref:System.IFormatProvider> objekt, který představuje aktuální jazykovou verzi.  
  
|Typ|ToString – přepsat|  
|----------|-----------------------|  
|<xref:System.Boolean>|Vrací buď <xref:System.Boolean.TrueString?displayProperty=nameWithType> nebo <xref:System.Boolean.FalseString?displayProperty=nameWithType>.|  
|<xref:System.Byte>|Volání `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` k formátování <xref:System.Byte> hodnotu pro aktuální jazykovou verzi.|  
|<xref:System.Char>|Vrátí znak jako řetězec.|  
|<xref:System.DateTime>|Volání `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` k formátování hodnota data a času pro aktuální jazykovou verzi.|  
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
## <a name="the-tostring-method-and-format-strings"></a>Řetězce formátu a ToString – metoda  
 Spoléhat na výchozí `ToString` metoda nebo přepsání `ToString` je vhodné, pokud objekt má jednu řetězcovou reprezentaci. Hodnota objektu má však často více reprezentace. Například může být vyjádřena teplotě ve stupních Fahrenheita, stupňů c nebo kelvinech. Podobně, může být reprezentován celočíselnou hodnotu 10 mnoha způsoby, včetně 10, 10.0, 1.0e01 nebo 10,00 USD.  
  
 Chcete-li jednu hodnotu tak, aby měl více řetězcové vyjádření, používá rozhraní .NET řetězce formátu. Formátovací řetězec je řetězec, který obsahuje jeden nebo více předdefinovaných specifikátorů formátu, které jsou jednotlivé znaky nebo skupiny znaků, které definují, jak `ToString` metoda by měla formátu její výstup. Řetězec formátu jsou předána jako parametr do objektu `ToString` metoda a určuje, jak zobrazit řetězcovou reprezentaci hodnoty tohoto objektu.  
  
 Všechny číselné typy, datum a čas, typy výčet a v rozhraní .NET podporují předdefinovanou sadu specifikátorů formátu. Formát řetězce můžete také použít k definování více řetězcové vyjádření vaší aplikace definované datové typy.  
  
<a name="standardStrings"></a>   
### <a name="standard-format-strings"></a>Standardní řetězce formátu  
 Standardní formátovací řetězec obsahuje jeden specifikátor formátu, který je znak abecedy, která definuje řetězcovou reprezentaci objektu, ke které se použije, společně s volitelným specifikátorem přesnosti ovlivňující, kolik číslic se zobrazují v výsledný řetězec. Pokud specifikátor přesnosti je vynechán nebo není podporovaná, je standardní formát specifikátor ekvivalentní standardní formátovací řetězec.  
  
 Rozhraní .NET definuje sadu standardních specifikátorů formátu pro všechny číselné typy, všechny datum a čas, všechny typy výčet a. Například každá z těchto kategorií podporuje standardní formát specifikátor "G", který definuje obecné řetězcovou reprezentaci hodnoty tohoto typu.  
  
 Standardní řetězce formátu pro výčtové typy přímo řídit řetězcovou reprezentaci hodnoty. Řetězce formátu předaný hodnotou výčtu `ToString` metoda určit, zda je hodnota zobrazena pomocí názvu řetězce ("G" a "F" specifikátory formátu), její základní celočíselné hodnoty (specifikátor formátu "D") nebo jeho šestnáctkové hodnoty ("X "Formát specifikátor). Následující příklad ukazuje použití standardní řetězce formátu k formátování <xref:System.DayOfWeek> hodnota výčtu.  
  
 [!code-csharp[Conceptual.Formatting.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/standard1.cs#4)]
 [!code-vb[Conceptual.Formatting.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/standard1.vb#4)]  
  
 Informace o výčet řetězců formátu najdete v tématu [výčet řetězců formátu](../../../docs/standard/base-types/enumeration-format-strings.md).  
  
 Standardní řetězce formátu pro číselné typy obvykle definují výsledný řetězec, jehož přesný vzhled řídí jeden nebo více hodnot vlastností. Například specifikátor formátu "C" formátuje číslo jako hodnotu měny. Při volání `ToString` metoda s specifikátor formátu "C" jako jediný parametr, následující hodnoty vlastností z aktuální jazykovou verzi <xref:System.Globalization.NumberFormatInfo> objekt se používá k definování řetězcová reprezentace číselné hodnoty:  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A> Vlastnost, která určuje symbol měny aktuální jazykovou verzi.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> Nebo <xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A> vlastnost, která vrací celé číslo, které určuje následující:  
  
    -   Umístění symbolu měny.  
  
    -   Jestli záporné hodnoty jsou vypsány se záporným znaménkem, koncové záporné znaménko nebo závorky.  
  
    -   Určuje, zda zobrazí mezeru mezi číselnou hodnotu a symbolu měny.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A> Vlastnosti, která definuje počet míst za desetinnou čárkou ve výsledném řetězci.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A> Vlastnost, která definuje symbol oddělovač desetinných míst ve výsledném řetězci.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A> Vlastnost, která definuje symbol oddělovače skupiny.  
  
-   <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A> Vlastnosti, která definuje počet číslic v každé skupině směrem doleva od desetinné čárky.  
  
-   <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> Vlastnosti, která určuje záporné znaménko použité ve výsledném řetězci, pokud nejsou použity závorky k označení záporné hodnoty.  
  
 Řetězce číselných formátů kromě toho může zahrnovat specifikátorem přesnosti. Význam tento specifikátor závisí na řetězci formátu, pomocí kterého se používá, ale obvykle označuje buď celkový počet číslic nebo počet míst za desetinnou čárkou, které se mají zobrazit ve výsledném řetězci. Například v následujícím příkladu používá "X 4" standardní číselného řetězce a specifikátorem přesnosti vytvořit hodnotu řetězce, který má čtyři hexadecimální číslice.  
  
 [!code-csharp[Conceptual.Formatting.Overview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/precisionspecifier1.cs#6)]
 [!code-vb[Conceptual.Formatting.Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/precisionspecifier1.vb#6)]  
  
 Další informace o standardních číselných formátovacích řetězců najdete v tématu [standardní číselných řetězců formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md).  
  
 Standardní řetězce formátu pro hodnoty data a času jsou aliasy pro vlastní řetězce formátu uložených určitou <xref:System.Globalization.DateTimeFormatInfo> vlastnost. Například volání `ToString` metoda hodnotu data a času s specifikátor formátu "D" zobrazí datum a čas pomocí vlastní řetězec formátu uložené v aktuální jazykovou verzi <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> vlastnost. (Další informace o vlastní řetězce formátu najdete v tématu [další části](#customStrings).) Následující příklad znázorňuje tento vztah.  
  
 [!code-csharp[Conceptual.Formatting.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/alias1.cs#5)]
 [!code-vb[Conceptual.Formatting.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/alias1.vb#5)]  
  
 Další informace o standardní hodnoty data a řetězce formátu časových najdete v tématu [standardní hodnoty data a řetězce formátu časových](../../../docs/standard/base-types/standard-date-and-time-format-strings.md).  
  
 Standardní řetězce formátu můžete také použít k definování řetězcovou reprezentaci objektu definované aplikací, který je vytvořen pomocí objektu `ToString(String)` metoda. Můžete definovat určité standardní formát specifikátory, které podporuje vaše objektu, a můžete určit, jestli jsou malá a velká písmena nebo velká a malá písmena. Vaši implementaci `ToString(String)` metoda by měla podporovat následující:  
  
-   Specifikátor formátu "G", který představuje obvyklý nebo obecný formát objektu. Bez parametrů přetížení tohoto objektu `ToString` by měly volat metoda jeho `ToString(String)` přetížení a předat standardní formátovací řetězec "G".  
  
-   Podpora pro specifikátor formátu, který se rovná odkaz s hodnotou null (`Nothing` v jazyce Visual Basic). Specifikátor formátu, který se rovná odkaz s hodnotou null by měl být považován za ekvivalent specifikátor formátu "G".  
  
 Například `Temperature` třída interně uchovávat teplotu ve stupních c a využívá specifikátory formátu, který představuje hodnotu `Temperature` objekt ve stupních c, stupňů Fahrenheita a kelvinech. V následujícím příkladu je uvedena ukázka.  
  
 [!code-csharp[Conceptual.Formatting.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/appstandard1.cs#7)]
 [!code-vb[Conceptual.Formatting.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/appstandard1.vb#7)]  
  
 [Zpět na začátek](#Introduction)  
  
<a name="customStrings"></a>   
### <a name="custom-format-strings"></a>Vlastní řetězce formátu  
 Kromě standardní formát řetězce .NET definuje vlastní řetězce formátu pro číselné hodnoty a hodnoty data a času. Vlastní řetězec formátu se skládá z jedné nebo více vlastních specifikátorů formátu definující řetězcovou reprezentaci hodnoty. Například vlastní datum a čas naformátovat řetězec "rrrr/mm/dd hh:mm:ss.ffff t zzz" převede datum na řetězcovou reprezentaci ve tvaru "2008/11/15 07:45:00.0000 P-08: 00" pro jazykovou verzi en US. Podobně vlastní formátovací řetězec "0000" převede celočíselnou hodnotu 12 "0012". Úplný seznam řetězců vlastního formátu, najdete v části [vlastní řetězců data a času formát](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) a [vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md).  
  
 Pokud řetězec formátu obsahuje jeden vlastní specifikátor formátu, formátu specifikátor musí předcházet nedocházelo k záměně se standardní formát specifikátor na symbol procent (%). Následující příklad používá vlastní formát specifikátor "M" zobrazte jednociferné nebo dvouciferné číslo v měsíci určitého data.  
  
 [!code-csharp[Conceptual.Formatting.Overview#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/singlecustom1.cs#8)]
 [!code-vb[Conceptual.Formatting.Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/singlecustom1.vb#8)]  
  
 Mnoho standardní řetězce formátu pro hodnoty data a času jsou aliasy pro vlastní formát řetězce, které jsou definovány vlastnosti <xref:System.Globalization.DateTimeFormatInfo> objektu. Vlastní řetězce formátu nabízí také značnou flexibilitu při poskytování definované aplikací formátování číselných hodnot nebo hodnoty data a času. Můžete definovat vlastní vlastní výsledný řetězec pro číselné hodnoty a hodnoty data a času kombinováním více vlastních specifikátorů formátu do jednoho vlastní formátovací řetězec. V následujícím příkladu definuje řetězec vlastní formát, který zobrazuje den v týdnu v závorkách za název měsíc, den a rok.  
  
 [!code-csharp[Conceptual.Formatting.Overview#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/custom1.cs#9)]
 [!code-vb[Conceptual.Formatting.Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/custom1.vb#9)]  
  
 V následujícím příkladu definuje řetězec vlastní formát, který zobrazuje <xref:System.Int64> hodnotu jako standardní, 7 číslic USA telefonní číslo společně s jeho směrové číslo oblasti.  
  
 [!code-csharp[Conceptual.Formatting.Overview#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/telnumber1.cs#21)]
 [!code-vb[Conceptual.Formatting.Overview#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/telnumber1.vb#21)]  
  
 I když standardní řetězce formátu obecně zpracovat většinu formátování potřeby vaší aplikace definované typy, můžete také definovat vlastní specifikátory formátu pro formátování těchto typů.  
  
 [Zpět na začátek](#Introduction)  
  
<a name="stringRef"></a>   
### <a name="format-strings-and-net-class-library-types"></a>Formátování řetězců a typy knihovna tříd rozhraní .NET  
 Všechny číselnými typy (který je <xref:System.Byte>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>a <xref:System.Numerics.BigInteger>typy)  
  
 , a taky <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, <xref:System.Guid>, a podporují všechny typy výčet formátování s řetězce formátu. Informace o řetězce konkrétní formátu podporované jednotlivými typy naleznete v následujících tématech  
  
|Název|Definice|  
|-----------|----------------|  
|[Standardní řetězce formátu čísla](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Popisuje standardní formát řetězce, které vytvářejí běžně používané řetězcové reprezentace číselné hodnoty.|  
|[Vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Popisuje řetězců vlastního formátu, které vytvářejí formáty specifické pro aplikaci pro číselné hodnoty.|  
|[Řetězce formátu standardní hodnoty data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Popisuje standardní formát řetězce, které vytvářejí běžně používané řetězcové vyjádření <xref:System.DateTime> hodnoty.|  
|[Řetězce formátu vlastní hodnota data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Popisuje řetězců vlastního formátu, které vytvářejí formáty specifické pro aplikaci pro <xref:System.DateTime> hodnoty.|  
|[Standardní řetězce formátu TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Popisuje standardní formát řetězce, které vytvářejí běžně používané řetězcové vyjádření časové intervaly.|  
|[Vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Popisuje řetězců vlastního formátu, které vytvářejí formáty specifické pro aplikaci pro časové intervaly.|  
|[Výčet řetězců formátu](../../../docs/standard/base-types/enumeration-format-strings.md)|Popisuje standardní formát řetězce, které se používají k vytvoření řetězcové vyjádření hodnot výčtu.|  
|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|Popisuje standardní řetězce formátu pro <xref:System.Guid> hodnoty.|  
  
<a name="FormatProviders"></a>   
## <a name="culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface"></a>Formátování zohledňující jazykovou verzi s použitím poskytovatelů formátu a rozhraní IFormatProvider  
 I když specifikátory formátu umožňují přizpůsobit formátování objektů, vytváření smysluplný řetězcovou reprezentaci objektů často vyžaduje další informace o formátování. Například formátování číslo jako hodnotu měny pomocí standardní formátovací řetězec "C" nebo vlastní řetězec formátu, jako "$ #, č. 00" vyžaduje minimálně informace o správného symbolu měny, oddělovač skupin a oddělovač desetinných míst na k dispozici pro zahrnutí do formátovaný řetězec. V rozhraní .NET, je k dispozici prostřednictvím tyto další formátování informace <xref:System.IFormatProvider> rozhraní, který je poskytnut jako parametr pro jeden nebo více přetížení `ToString` metoda číselnými typy a typy data a času. <xref:System.IFormatProvider>implementace se používají v rozhraní .NET pro podporu formátování specifické pro jazykovou verzi. Následující příklad ukazuje, jak řetězcovou reprezentaci objektu změní, když je formátován pomocí tří <xref:System.IFormatProvider> objekty, které představují různé jazykové verze.  
  
 [!code-csharp[Conceptual.Formatting.Overview#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformatprovider1.cs#11)]
 [!code-vb[Conceptual.Formatting.Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformatprovider1.vb#11)]  
  
 <xref:System.IFormatProvider> Rozhraní zahrnuje jednu metodu <xref:System.IFormatProvider.GetFormat%28System.Type%29>, který má jeden parametr, který určuje typ objektu, který poskytuje informace o formátování. Pokud metoda poskytnout objekt daného typu, vrátí se. Jinak vrátí hodnotu Null (`Nothing` v jazyce Visual Basic).  
  
 <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType>je metoda zpětného volání. Při volání `ToString` přetížení metody, která zahrnuje <xref:System.IFormatProvider> parametr, zavolá <xref:System.IFormatProvider.GetFormat%2A> metoda této <xref:System.IFormatProvider> objektu. <xref:System.IFormatProvider.GetFormat%2A> Metoda odpovídá za vrátí objekt, který zajišťuje informace nezbytné k formátování, podle specifikace jeho `formatType` parametr, do `ToString` metoda.  
  
 Několik metod pro převod formátování nebo řetězec zahrnout parametr typu <xref:System.IFormatProvider>, ale hodnota parametru v mnoha případech se ignoruje při volání metody. Následující tabulka uvádí některé metody formátování, které používají parametr a typ <xref:System.Type> objekt, který se předat <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> metoda.  
  
|Metoda|Typ `formatType` parametr|  
|------------|------------------------------------|  
|`ToString`Metoda číselnými typy|<xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>|  
|`ToString`Metoda typu datum a čas|<xref:System.Globalization.DateTimeFormatInfo?displayProperty=nameWithType>|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|  
  
> [!NOTE]
>  `ToString` Jsou přetížené metody číselnými typy a typy data a času a jenom některé z přetížení obsahují <xref:System.IFormatProvider> parametr. Pokud metoda nemá parametr typu <xref:System.IFormatProvider>, objekt, který je vrácený <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnost předaný místo. Například volání výchozí <xref:System.Int32.ToString?displayProperty=nameWithType> metoda ve výsledku volání metody, jako jsou následující: `Int32.ToString("G", System.Globalization.CultureInfo.CurrentCulture)`.  
  
 Rozhraní .NET poskytuje tři třídy, které implementují <xref:System.IFormatProvider>:  
  
-   <xref:System.Globalization.DateTimeFormatInfo>, třídu, která poskytuje informace o formátování pro hodnoty data a času pro konkrétní jazykové verze. Jeho <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementace vrátí instance sám sebe.  
  
-   <xref:System.Globalization.NumberFormatInfo>, třídu, která poskytuje informace o formátování čísel pro konkrétní jazykové verze. Jeho <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementace vrátí instance sám sebe.  
  
-   <xref:System.Globalization.CultureInfo>. Jeho <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementace může vrátit buď <xref:System.Globalization.NumberFormatInfo> objekt, který chcete zadat informace o formátování čísel nebo <xref:System.Globalization.DateTimeFormatInfo> objekt, který chcete zadat informace o formátování pro hodnoty data a času.  
  
 Můžete také implementovat vlastní zprostředkovatel formátu nahradit některého z těchto tříd. Ale vaší implementace <xref:System.IFormatProvider.GetFormat%2A> metoda musí vrátit objekt typu uvedené v předchozí tabulce, pokud je poskytovat informace o formátování `ToString` metoda.  
  
 [Zpět na začátek](#Introduction)  
  
<a name="numericCulture"></a>   
### <a name="culture-sensitive-formatting-of-numeric-values"></a>Formátování číselných hodnot zohledňující jazykovou verzi  
 Ve výchozím nastavení je formátování číselných hodnot zohledňující jazykovou verzi. Pokud nezadáte jazykovou verzi při volání metody pro formátování, použijí se konvencí formátování jazykové verze aktuálního vlákna. To je znázorněno v následujícím příkladu, který změní jazykové verze aktuálního vlákna čtyřikrát a pak zavolá <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> metoda. V každém případě odráží výsledný řetězec formátování konvence aktuální jazykové verze. Důvodem je, že `ToString` a `ToString(String)` metody zabalení volání každý číselného typu `ToString(String, IFormatProvider)` metoda.  
  
 [!code-csharp[Conceptual.Formatting.Overview#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific3.cs#19)]
 [!code-vb[Conceptual.Formatting.Overview#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific3.vb#19)]  
  
 Můžete také formátovat číselnou hodnotu pro konkrétní jazykové verze voláním `ToString` přetížení, které má `provider` parametr a předání z následujících:  
  
-   A <xref:System.Globalization.CultureInfo> objekt, který reprezentuje jazykovou verzi, jejíž formátování konvence mají být použita. Jeho <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> metoda vrátí hodnotu <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> vlastnost, která je <xref:System.Globalization.NumberFormatInfo> objekt, který poskytuje informace o formátování specifické pro jazykovou verzi pro číselné hodnoty.  
  
-   A <xref:System.Globalization.NumberFormatInfo> objekt, který definuje se specifické pro jazykovou verzi formátování názvů, který se má použít. Jeho <xref:System.Globalization.NumberFormatInfo.GetFormat%2A> metoda vrátí instanci sebe sama.  
  
 Následující příklad používá <xref:System.Globalization.NumberFormatInfo> objekty, které představují Czech (Czech Republic) a jazykové verze Angličtina (Velká Británie) a neutrální jazykové verze francouzštině a ruština formátuje číslo s plovoucí desetinnou čárkou.  
  
 [!code-csharp[Conceptual.Formatting.Overview#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific4.cs#20)]
 [!code-vb[Conceptual.Formatting.Overview#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific4.vb#20)]  
  
<a name="dateCulture"></a>   
### <a name="culture-sensitive-formatting-of-date-and-time-values"></a>Formátování hodnot data a času zohledňující jazykovou verzi  
 Ve výchozím nastavení je formátování hodnoty data a času zohledňující jazykovou verzi. Pokud nezadáte jazykovou verzi při volání metody pro formátování, použijí se konvencí formátování jazykové verze aktuálního vlákna. To je znázorněno v následujícím příkladu, který změní jazykové verze aktuálního vlákna čtyřikrát a pak zavolá <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> metoda. V každém případě odráží výsledný řetězec formátování konvence aktuální jazykové verze. Důvodem je, že <xref:System.DateTime.ToString?displayProperty=nameWithType>, <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType>, a <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metody zabalení volání <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> a <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody.  
  
 [!code-csharp[Conceptual.Formatting.Overview#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific1.cs#17)]
 [!code-vb[Conceptual.Formatting.Overview#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific1.vb#17)]  
  
 Můžete také formátovat hodnotu Datum a čas pro konkrétní jazykové verze voláním <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> přetížení, které má `provider` parametr a předání z následujících:  
  
-   A <xref:System.Globalization.CultureInfo> objekt, který reprezentuje jazykovou verzi, jejíž formátování konvence mají být použita. Jeho <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> metoda vrátí hodnotu <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vlastnost, která je <xref:System.Globalization.DateTimeFormatInfo> objekt, který poskytuje informace o formátování specifické pro jazykovou verzi pro hodnoty data a času.  
  
-   A <xref:System.Globalization.DateTimeFormatInfo> objekt, který definuje se specifické pro jazykovou verzi formátování názvů, který se má použít. Jeho <xref:System.Globalization.DateTimeFormatInfo.GetFormat%2A> metoda vrátí instanci sebe sama.  
  
 Následující příklad používá <xref:System.Globalization.DateTimeFormatInfo> objekty, které představují Czech (Czech Republic) a jazykové verze Angličtina (Velká Británie) a neutrální jazykové verze francouzštině a ruština formátování data.  
  
 [!code-csharp[Conceptual.Formatting.Overview#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific2.cs#18)]
 [!code-vb[Conceptual.Formatting.Overview#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific2.vb#18)]  
  
<a name="IFormattable"></a>   
## <a name="the-iformattable-interface"></a>Rozhraní IFormattable  
 Obvykle typy této přetížení `ToString` metoda s řetězec formátu a <xref:System.IFormatProvider> parametr taky implementovat <xref:System.IFormattable> rozhraní. Toto rozhraní má jednoho člena, <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, který obsahuje řetězec formátu i poskytovatele formátu jako parametry.  
  
 Implementace <xref:System.IFormattable> rozhraní pro vaše aplikace definované třídy, nabízí dvě výhody:  
  
-   Podpora pro převod řetězce podle <xref:System.Convert> třídy. Volání <xref:System.Convert.ToString%28System.Object%29?displayProperty=nameWithType> a <xref:System.Convert.ToString%28System.Object%2CSystem.IFormatProvider%29?displayProperty=nameWithType> volání metody vaší <xref:System.IFormattable> implementace automaticky.  
  
-   Podpora pro složené formátování. Pokud položku formátu, který obsahuje řetězec formátu slouží k formátování vašeho vlastního typu, modul common language runtime automaticky vyvolá vaší <xref:System.IFormattable> implementace a předává je řetězec formátu. Další informace o složené formátování pomocí metod, jako například <xref:System.String.Format%2A?displayProperty=nameWithType> nebo <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, najdete v článku [složené formátování](#CompositeFormatting) části.  
  
 V následujícím příkladu definuje `Temperature` třídu, která implementuje <xref:System.IFormattable> rozhraní. Podporuje "C" nebo "G" specifikátory formátu pro zobrazení teploty v c, specifikátor formátu "F" pro zobrazení teploty v Fahrenheita a specifikátor formátu "K" pro zobrazení teploty v Kelvin.  
  
 [!code-csharp[Conceptual.Formatting.Overview#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#12)]
 [!code-vb[Conceptual.Formatting.Overview#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#12)]  
  
 Následující příklad vytvoří `Temperature` objektu. Potom zavolá <xref:System.Convert.ToString%2A> metoda a používá několik složených formátovacích řetězců pro získání různých řetězec reprezentace `Temperature` objektu. Každý z těchto volání metod, volá <xref:System.IFormattable> implementace `Temperature` třídy.  
  
 [!code-csharp[Conceptual.Formatting.Overview#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#13)]
 [!code-vb[Conceptual.Formatting.Overview#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#13)]  
  
 [Zpět na začátek](#Introduction)  
  
<a name="CompositeFormatting"></a>   
## <a name="composite-formatting"></a>Složené formátování  
 Některé metody, jako například <xref:System.String.Format%2A?displayProperty=nameWithType> a <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, podporují složené formátování. Složený formátovací řetězec je druh šablony, která vrátí jeden řetězec, který zahrnuje řetězcovou reprezentaci nula, jednu nebo více objektů. Každý objekt je v složený formátovací řetězec reprezentována položku indexované formátu. Index položky formátu odpovídá pozici objektu, který reprezentuje v seznamu parametrů metody. Indexy jsou od nuly. Například následující volání do <xref:System.String.Format%2A?displayProperty=nameWithType> metoda, je první položka formátu `{0:D}`, je nahrazena řetězcovou reprezentaci `thatDate`; druhá položka formátu `{1}`, je nahrazena řetězcovou reprezentaci `item1`; a třetí položku formátu `{2:C2}`, je nahrazena řetězcovou reprezentaci `item1.Value`.  
  
 [!code-csharp[Conceptual.Formatting.Overview#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite1.cs#14)]
 [!code-vb[Conceptual.Formatting.Overview#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite1.vb#14)]  
  
 Kromě nahrazení řetězcovou reprezentaci objektu jeho odpovídající položku formátu, formátu položek vám také umožní řídit následující:  
  
-   Způsobem v konkrétním, který objekt je reprezentována jako řetězec, pokud objekt implementuje <xref:System.IFormattable> rozhraní a podporuje řetězce formátu. To provedete pomocí následujícího formátu položka indexu s `:` (středníkem), za nímž následuje řetězec platný formát. Předchozí příklad to nebyla ve formátování hodnotu date s řetězec "d" (vzoru krátkého data) formátu (například `{0:d}`) a že formát číselnou hodnotu s "C2" řetězec formátu (například `{2:C2}` představují číslo jako hodnotu měny se dvěma zlomkové desetinných míst.  
  
-   Šířka pole obsahující řetězcovou reprezentaci objektu a zarovnání řetězcovou reprezentaci v tomto poli. To provedete pomocí následujícího formátu položka indexu s `,` (čárkou) a potom šířka pole. Řetězec má zarovnaný doprava v poli Pokud je šířka pole kladnou hodnotu a jeho je zarovnaný doleva-li pole zápornou hodnotu. Následující příklad vlevo zarovná hodnot data v poli 20 znaků, a ho vpravo – desetinná čísla s jednu číslici zlomkové v poli 11 znaků.  
  
     [!code-csharp[Conceptual.Formatting.Overview#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite2.cs#22)]
     [!code-vb[Conceptual.Formatting.Overview#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite2.vb#22)]  
  
     Všimněte si, že pokud je přítomen komponentu řetězec zarovnání i komponentu řetězec formátu, Bývalé předchází k tomu (například `{0,-20:g}`.  
  
 Další informace o složené formátování najdete v tématu [složené formátování](../../../docs/standard/base-types/composite-formatting.md).  
  
 [Zpět na začátek](#Introduction)  
  
<a name="Custom"></a>   
## <a name="custom-formatting-with-icustomformatter"></a>Vlastní formátování pomocí ICustomFormatter  
 Složené formátování způsobů, <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> a <xref:System.Text.StringBuilder.AppendFormat%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, zahrnout parametr poskytovatele formátu, který podporuje vlastní formátování. Jedna z těchto metod formátování nazývá předá <xref:System.Type> objekt, který reprezentuje <xref:System.ICustomFormatter> rozhraní ke zprostředkovateli formátu <xref:System.IFormatProvider.GetFormat%2A> metoda. <xref:System.IFormatProvider.GetFormat%2A> Metoda je poté zodpovědný za vrácení <xref:System.ICustomFormatter> implementace, která poskytuje vlastní formátování.  
  
 <xref:System.ICustomFormatter> Rozhraní obsahuje jedinou metodu, <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29>, která je volána automaticky složeného formátování metoda pro každou položku formátu v složený formátovací řetězec. <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29> Metoda má tři parametry: řetězec formátu, který představuje `formatString` argument v položce formátu objekt do formátu a <xref:System.IFormatProvider> objekt, který poskytuje formátování služeb. Obvykle třídu, která implementuje <xref:System.ICustomFormatter> také implementuje <xref:System.IFormatProvider>, takže tento poslední parametr je odkaz na vlastní formátování třídy sám sebe. Metoda vrátí vlastní formátovaný řetězcovou reprezentaci objekt, který má být ve formátu. Pokud objekt nelze zformátovat metodu, má být vrácen odkaz s hodnotou null (`Nothing` v jazyce Visual Basic).  
  
 Následující příklad uvádí <xref:System.ICustomFormatter> implementace s názvem `ByteByByteFormatter` zobrazující celočíselné hodnoty jako posloupnost letopočty šestnáctkové hodnoty následované mezerou.  
  
 [!code-csharp[Conceptual.Formatting.Overview#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#15)]
 [!code-vb[Conceptual.Formatting.Overview#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#15)]  
  
 Následující příklad používá `ByteByByteFormatter` třídy pro formátování celočíselné hodnoty. Všimněte si, že <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> metoda je volána více než jednou za sekundu <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> volání metody a že výchozí <xref:System.Globalization.NumberFormatInfo> zprostředkovatele se používá v třetím volání metody, protože.`ByteByByteFormatter.Format` Metoda nebyl rozpoznán řetězec formátu "N0" a vrátí odkaz s hodnotou null (`Nothing` v jazyce Visual Basic).  
  
 [!code-csharp[Conceptual.Formatting.Overview#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#16)]
 [!code-vb[Conceptual.Formatting.Overview#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#16)]  
  
 [Zpět na začátek](#Introduction)  
  
<a name="RelatedTopics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Definice|  
|-----------|----------------|  
|[Standardní řetězce formátu čísla](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Popisuje standardní formát řetězce, které vytvářejí běžně používané řetězcové reprezentace číselné hodnoty.|  
|[Vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Popisuje řetězců vlastního formátu, které vytvářejí formáty specifické pro aplikaci pro číselné hodnoty.|  
|[Řetězce formátu standardní hodnoty data a času](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Popisuje standardní formát řetězce, které vytvářejí běžně používané řetězcové vyjádření <xref:System.DateTime> hodnoty.|  
|[Řetězce formátu vlastní hodnota data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Popisuje řetězců vlastního formátu, které vytvářejí formáty specifické pro aplikaci pro <xref:System.DateTime> hodnoty.|  
|[Standardní řetězce formátu TimeSpan](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Popisuje standardní formát řetězce, které vytvářejí běžně používané řetězcové vyjádření časové intervaly.|  
|[Vlastní řetězce formátu TimeSpan](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Popisuje řetězců vlastního formátu, které vytvářejí formáty specifické pro aplikaci pro časové intervaly.|  
|[Výčet řetězců formátu](../../../docs/standard/base-types/enumeration-format-strings.md)|Popisuje standardní formát řetězce, které se používají k vytvoření řetězcové vyjádření hodnot výčtu.|  
|[Složené formátování](../../../docs/standard/base-types/composite-formatting.md)|Popisuje postup vložit jeden nebo více formátovaný hodnot v řetězci. Řetězec můžete následně zobrazit v konzole nebo zapisovat do datového proudu.|  
|[Provádění operací formátování](../../../docs/standard/base-types/performing-formatting-operations.md)|Obsahuje seznam témat, které poskytují podrobné pokyny k provedení určitých operací formátování.|  
|[Analýza řetězců](../../../docs/standard/base-types/parsing-strings.md)|Popisuje, jak inicializovat objekty s hodnotami popsanými řetězcové vyjádření těchto objektů. Analýza je inverzní operace formátování.|  
  
 [Zpět na začátek](#Introduction)  
  
<a name="Reference"></a>   
## <a name="reference"></a>Odkaz  
 <xref:System.IFormattable?displayProperty=nameWithType>  
  
 <xref:System.IFormatProvider?displayProperty=nameWithType>  
  
 <xref:System.ICustomFormatter?displayProperty=nameWithType>
