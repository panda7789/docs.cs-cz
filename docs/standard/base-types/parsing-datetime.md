---
title: 'Postupy: převod řetězce na datum a čas'
description: Další techniky k parsování řetězců, které představují data a časy, chcete-li vytvořit hodnotu DateTime z řetězce data a času.
ms.date: 02/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parsing strings, date and time strings
- date and time strings
- ParseExact method
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
- DateTime object
- time strings
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 413a04d6ccdfff4b9cbf937821683ab7f7b37361
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208121"
---
# <a name="parsing-date-and-time-strings-in-net"></a>Analýza řetězců data a času v .NET

Analýza řetězců převést tak, aby <xref:System.DateTime> objekty je potřeba zadat informace o tom, jak jsou data a časy jsou reprezentovány jako text. Různé jazykové verze používají různé objednávek pro den, měsíc a rok. Reprezentace nějakou dobu 24 hodin, ostatní zadejte "Dop." a "Odp." Některé aplikace potřebují pouze datum. Ostatní potřebují jenom při spuštění. Ostatní stále potřebují zadejte datum a čas. Metody, které převod řetězců na <xref:System.DateTime> objekty umožňují poskytují podrobné informace o formátech očekáváte, že a prvky datum a čas potřeby vaší aplikace. Existují tři dílčí úkoly správně převádění textu do <xref:System.DateTime>:

1. Je nutné zadat očekávanému formátu textu představující datum a čas.
1. Můžete zadat jazykovou verzi pro formát Datum čas.
1. Můžete zadat jak chybějící součásti v textu reprezentace nastavené datum a čas.

<xref:System.DateTime.Parse%2A> a <xref:System.DateTime.TryParse%2A> převádí mnoho běžných vyjádření data a času. <xref:System.DateTime.ParseExact%2A> a <xref:System.DateTime.TryParseExact%2A> metody převést řetězcovou reprezentaci, která odpovídají vzoru určenému řetězcem formátu data a času. (Naleznete v článcích na [řetězce formátu data a času](standard-date-and-time-format-strings.md) a [řetězce formátu vlastní data a času](custom-date-and-time-format-strings.md) podrobnosti.)

Aktuální <xref:System.Globalization.DateTimeFormatInfo> objekt poskytuje větší kontrolu nad jak text by měl být interpretován jako datum a čas. Vlastnosti <xref:System.Globalization.DateTimeFormatInfo> popisují datum a čas oddělovače a názvy měsíců, dnů a větší počet období a formát pro označení "Dop." a "Odp.". Poskytuje aktuální jazykové verzi vlákna <xref:System.Globalization.DateTimeFormatInfo> , který představuje aktuální jazykovou verzi. Pokud chcete konkrétní jazykovou verzi nebo vlastní nastavení, zadejte <xref:System.IFormatProvider> parametr metody analýzy. Pro <xref:System.IFormatProvider> parametr, zadejte <xref:System.Globalization.CultureInfo> objektu, který představuje jazykovou verzi, nebo <xref:System.Globalization.DateTimeFormatInfo> objektu.

Text představující data nebo času můžou chybět některé informace. Data "12. březen" představuje do aktuálního roku Předpokládejme například, většina lidí. Podobně ". března 2018" představuje měsíc dne v roce 2018. Text, který často reprezentující čas provádí pouze zahrnují hodiny, minuty a označení dop. / odp.  Parsování metody zpracovávají chybějící informace s použitím rozumné výchozí hodnoty:

- Když je k dispozici jenom čas, datum část použije aktuální datum.
- Pokud je k dispozici pouze data, čas se předpokládá půlnoc.
- Když rok není zadané v datum, použije se do aktuálního roku.
- Když není zadaný den v měsíci, použije se první den v měsíci.

Pokud se data nachází v řetězci, musí zahrnovat měsíc a den nebo rok. Pokud se nachází čas, musí zahrnovat do hodiny a minuty nebo označení dopoledne/odpoledne.

Můžete zadat <xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault> – konstanta přepsat toto výchozí nastavení. Při použití této konstanty, všechny chybějící rok, měsíc nebo jsou nastavena na hodnotu vlastnosti den `1`. [Poslední příklad](#styles-example) pomocí <xref:System.DateTime.Parse%2A> ukazuje toto chování.

Kromě data a času může obsahovat řetězcovou reprezentaci data a času posun, která určuje, kolik času se liší od koordinovaného světového času (UTC). Například řetězec "2/14/2007 5:32:00 -7:00" definuje čas, který je sedm hodin dříve než čas UTC. Posun je z řetězcové reprezentace čas vynechán, analýza kódu vrátí <xref:System.DateTime> objekt s jeho <xref:System.DateTime.Kind%2A> nastavenou na <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>. Pokud je zadaný posun, analýze vrátí <xref:System.DateTime> objekt s jeho <xref:System.DateTime.Kind%2A> nastavenou na <xref:System.DateTimeKind.Local?displayProperty=nameWithType> a upravit její hodnotu na místní časové pásmo vašeho počítače. Toto chování lze upravit pomocí <xref:System.Globalization.DateTimeStyles> hodnotu s metoda analýzy.
  
Poskytovatele formátu se používá také k interpretaci nejednoznačný číselná data. To není jasné, které součásti data reprezentovaná tímto řetězcem "02/03/04" jsou měsíc, den a rok. Komponenty se interpretují podle pořadí podobné formáty kalendářního data v poskytovatele formátu.

## <a name="parse"></a>Analýzy

Následující příklad ukazuje použití <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> způsobů, jak převést `string` do <xref:System.DateTime>. Tento příklad používá jazykové verze přidružené k aktuální vlákno. Pokud <xref:System.Globalization.CultureInfo> přidružené k aktuální jazykové verze nelze parsovat vstupní řetězec <xref:System.FormatException> je vyvolána výjimka.

> [!TIP]
> Spustit všechny jazyka C# ukázky v tomto článku v prohlížeči. Stisknutím klávesy **spustit** tlačítko, abyste viděli výstup. Můžete také upravit, aby sami experimentovat.

> [!NOTE]
> Tyto příklady jsou k dispozici v úložišti Githubu dokumentace pro obě [jazyka C#](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/conversions) a [VB](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/how-to/conversions). Nebo si můžete stáhnout jako zipfile pro projekt [jazyka C#](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/conversions.zip) nebo [VB](https://github.com/dotnet/samples/raw/master/snippets/visualbasic/how-to/conversions.zip).

[!code-csharp-interactive[Parsing.DateAndTime#1](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#1)]
[!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#1)]

Můžete také explicitně definovat jazykovou verzi, jejíž úmluvy formátování se používají při analýze řetězce. Můžete určit jeden ze standardních <xref:System.Globalization.DateTimeFormatInfo> objektů vrácených podle <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vlastnost. Následující příklad používá k analýze německé řetězce do poskytovatele formátu <xref:System.DateTime>. Vytvoří <xref:System.Globalization.CultureInfo> představující `de-DE` jazykovou verzi. Že `CultureInfo` objekt zajistí úspěšné analýzy tento konkrétní řetězec. To vylučuje jakékoli nastavení <xref:System.Threading.Thread.CurrentCulture> z <xref:System.Threading.Thread.CurrentThread>.  
  
[!code-csharp-interactive[Parsing.DateAndTime#2](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#2)]
[!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#2)]

Nicméně i když můžete použít přetížení <xref:System.DateTime.Parse%2A> metodu pro určení vlastních poskytovatelů formátu, metoda nepodporuje analýzu nestandardní formáty. Chcete-li analyzovat datum a čas vyjádřený nestandardní formát, použijte <xref:System.DateTime.ParseExact%2A> metoda místo.  

<a name="styles-example"></a>V následujícím příkladu <xref:System.Globalization.DateTimeStyles> výčet k určení, že aktuální informace o datu a času nepřidávat <xref:System.DateTime> pro Nespecifikovaná pole.  

[!code-csharp-interactive[Parsing.DateAndTime#3](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#3)]
[!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#3)]
 
## <a name="parseexact"></a>ParseExact

<xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> Metoda převede řetězec <xref:System.DateTime> objektu, pokud odpovídá jednomu ze vzorů zadaného řetězce. Když tato metoda předána řetězec, který není jedním z formuláře zadaný <xref:System.FormatException> je vyvolána výjimka. Můžete zadat jednu standardní datum a čas specifikátory formátu nebo kombinace specifikátorů vlastního formátu. Pomocí specifikátoru vlastního formátu, je možné, můžete vytvořit vlastní rozpoznávání řetězec. Informace o specifikátorech, najdete v tématech na [řetězce formátu data a času](standard-date-and-time-format-strings.md) a [řetězce formátu vlastní data a času](custom-date-and-time-format-strings.md).  

V následujícím příkladu <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> metodě se předává objekt string analyzovat, za nímž následuje specifikátoru formátu, za nímž následuje <xref:System.Globalization.CultureInfo> objektu. To <xref:System.DateTime.ParseExact%2A> metoda analyzovat pouze řetězce, které mají tvar dlouhého data v `en-US` jazykovou verzi.  

[!code-csharp-interactive[Parsing.DateAndTime#4](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#4)]
[!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#4)]

Každé přetížení <xref:System.DateTime.Parse%2A> a <xref:System.DateTime.ParseExact%2A> metod má také <xref:System.IFormatProvider> parametr, který poskytuje informace specifické jazykové verze o formátování řetězce. To <xref:System.IFormatProvider> je objekt <xref:System.Globalization.CultureInfo> objekt, který reprezentuje standardní jazykové verze nebo <xref:System.Globalization.DateTimeFormatInfo> objekt, který je vrácený <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vlastnost.  <xref:System.DateTime.ParseExact%2A> také používá další řetězec nebo pole argument řetězce, který definuje jeden nebo více vlastní datum a čas formátů.  

## <a name="see-also"></a>Viz také:

- [Analýza řetězců](parsing-strings.md)
- [Typy formátování](formatting-types.md)
- [Převod typů v rozhraní .NET](type-conversion.md)
- [Formáty data a času](standard-date-and-time-format-strings.md)
- [Řetězce formátu vlastní data a času](custom-date-and-time-format-strings.md)
