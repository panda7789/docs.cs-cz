---
title: "Postupy: převedení řetězce na typ DateTime"
description: "Další techniky k analýze řetězců, které představují data a časy, chcete-li vytvořit hodnotu DateTime z řetězce data a času."
ms.date: 02/15/2018
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
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
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a17c96a03a35fcc4eb12e188dbc79d8d48153fb7
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2018
---
# <a name="parsing-date-and-time-strings-in-net"></a>Analýza řetězců data a času v rozhraní .NET

Analýza řetězců na převést tak, aby <xref:System.DateTime> objekty vyžaduje, abyste zadejte informace o tom, jak data a časy jsou reprezentovány jako text. Různé jazykové verze pomocí různých objednávky pro den, měsíc a rok. Některé reprezentace dobu 24 hodin, ostatní zadejte "AM" a "Odp." Některé aplikace potřebují jenom datum. Ostatní potřebují jenom na čas. Ostatní stále nutné zadat datum a čas. Metody, které převod řetězců na <xref:System.DateTime> objekty umožňují poskytují podrobné informace o formátech očekáváte a elementy datum a čas potřebám vaší aplikace. Existují tři dílčí úkoly k správně převod textu na <xref:System.DateTime>:

1. Musíte zadat očekávaný formát textu představující datum a čas.
1. Můžete určit jazykovou verzi pro formát Datum a čas.
1. Můžete určit způsob chybí komponenty v textu reprezentace jsou nastavené datum a čas.

<xref:System.DateTime.Parse%2A> a <xref:System.DateTime.TryParse%2A> převádí mnoho běžných vyjádření data a času. <xref:System.DateTime.ParseExact%2A> a <xref:System.DateTime.TryParseExact%2A> metody převést řetězcové vyjádření, která vyhovuje vzoru určeného řetězce formátu data a času. (Naleznete v článcích na [řetězce formátu standardní hodnoty data a času](standard-date-and-time-format-strings.md) a [řetězce formátu vlastní hodnota data a času](custom-date-and-time-format-strings.md) podrobnosti.)


Aktuální <xref:System.Globalization.DateTimeFormatInfo> objekt poskytuje větší kontrolu nad jak text by měl být interpretován jako datum a čas. Vlastnosti <xref:System.Globalization.DateTimeFormatInfo> popisují názvy měsíců, dnů a období a formát pro označení "AM" a "Odp.", datum a čas oddělovačů. Poskytuje jazykové verze aktuálního vlákna <xref:System.Globalization.DateTimeFormatInfo> představující aktuální jazykovou verzi. Pokud chcete konkrétní jazykové verze nebo vlastní nastavení, zadejte <xref:System.IFormatProvider> parametr metody analýzy. Pro <xref:System.IFormatProvider> parametr, zadejte <xref:System.Globalization.CultureInfo> objekt, který představuje jazykovou verzi, nebo <xref:System.Globalization.DateTimeFormatInfo> objektu.

Některé informace mohou chybět text představující datum nebo čas. Většina lidí by Předpokládejme třeba, data "12 března" představuje do aktuálního roku. Podobně "Března 2018" představuje měsíc dne v roce 2018. Text, který nemá představující čas často jenom zahrnuje hodiny, minuty a označení dop. / odp.  Analýza metody zpracovávat tyto chybějící informace pomocí přiměřené výchozí nastavení:

- Pokud je k dispozici jenom na čas, datum část, používá aktuální datum.
- Když se nachází pouze datum, čas část je půlnoc.
- Když v roce není zadané v datum, použije se do aktuálního roku.
- Když není zadaný den v měsíci, použije se první den v měsíci.

Pokud se data nachází v řetězci, musí obsahovat měsíc a den nebo rok. Pokud se nachází čas, musí obsahovat hodinu a dobu, po které nebo označení dop. / odp.

Můžete zadat <xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault> konstanta přepsat toto výchozí nastavení. Pokud použijete tento konstanta, všechny chybějící rok, měsíc a den vlastnosti jsou nastaveny na hodnotu `1`. [Poslední příklad](#styles-example) pomocí <xref:System.DateTime.Parse%2A> ukazuje toto chování.

Kromě data a času může zahrnovat řetězcovou reprezentaci datum a čas posunem, která určuje, kolik čas se liší od koordinovaný světový čas (UTC). Například řetězec "2/14/2007 5:32:00 -7:00" definuje čas, který je sedm hodin dříve než čas UTC. Pokud je vynechaný posun řetězcovou reprezentaci čas, analýze vrátí <xref:System.DateTime> objektu s jeho <xref:System.DateTime.Kind%2A> vlastnost nastavena na hodnotu <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>. Pokud je zadaný posun, analýze vrátí <xref:System.DateTime> objektu s jeho <xref:System.DateTime.Kind%2A> vlastnost nastavena na hodnotu <xref:System.DateTimeKind.Local?displayProperty=nameWithType> a jeho hodnota upravena na místní časové pásmo počítače. Toto chování můžete upravit pomocí <xref:System.Globalization.DateTimeStyles> hodnotu s metodou analýzy.
  
Zprostředkovatel formátu slouží také k interpretaci dvojznačného číselného data. Není jasné součástí, které data reprezentována řetězec "02/03/04" jsou měsíc, den a rok. Komponenty se interpretují podle pořadí podobné dat. formáty dat v rámci zprostředkovatele formátu.

## <a name="parse"></a>analyzovat

Následující příklad ukazuje použití <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> způsobů, jak převést `string` do <xref:System.DateTime>. Tento příklad používá jazykovou verzi spojenou s aktuálním vláknem. Pokud <xref:System.Globalization.CultureInfo> přidružené k aktuální jazykovou verzi nelze analyzovat vstupní řetězec <xref:System.FormatException> je vyvolána výjimka.

> [!TIP]
> Všechny C# ukázky v tomto článku spustit v prohlížeči. Stiskněte **spustit** tlačítko Zobrazit výstup. Můžete taky upravit je a experimentovat sami.

> [!NOTE]
> Tyto příklady jsou k dispozici v úložišti GitHub dokumentace pro obě [C#](https://github.com/dotnet/docs/samples/tree/master/snippets/csharp/how-to/conversions) a [VB](https://github.com/dotnet/docs/samples/tree/master/snippets/visualbasic/how-to/conversions). Nebo si můžete stáhnout projektu jako zipfile pro [C#] ((https://github.com/dotnet/docs/samples/tree/master/snippets/csharp/how-to/conversions.zip) nebo [VB](https://github.com/dotnet/docs/samples/tree/master/snippets/visualbasic/how-to/conversions.zip).

[!code-csharp-interactive[Parsing.DateAndTime#1](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#1)]
[!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#1)]

Můžete také explicitně definovat jazykovou verzi, jejíž formátování konvence se používají při analyzovat řetězec. Zadejte jednu z standardní <xref:System.Globalization.DateTimeFormatInfo> objektů vrácený <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vlastnost. Následující příklad používá zprostředkovatel formátu analyzovat řetězec němčině do <xref:System.DateTime>. Vytvoří <xref:System.Globalization.CultureInfo> představující `de-DE` jazykovou verzi. Aby `CultureInfo` objekt zajišťuje úspěšné analýzy tento konkrétní řetězec. To vylučuje jakékoli nastavení <xref:System.Threading.Thread.CurrentCulture> z <xref:System.Threading.Thread.CurrentThread>.  
  
[!code-csharp-interactive[Parsing.DateAndTime#2](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#2)]
[!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#2)]

Ale i když můžete použít přetížení metody <xref:System.DateTime.Parse%2A> metodu za účelem určení vlastních poskytovatelů formátu, metodu nepodporuje analýzy nestandardní formáty. Chcete-li analyzovat data a času vyjádřené v nestandardním formátu, použijte <xref:System.DateTime.ParseExact%2A> metoda místo.  

<a name="styles-example"></a>Následující příklad používá <xref:System.Globalization.DateTimeStyles> výčtu k určení, že aktuální informace o datu a času nepřidávat <xref:System.DateTime> pro neurčené pole.  

[!code-csharp-interactive[Parsing.DateAndTime#3](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#3)]
[!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#3)]
 
## <a name="parseexact"></a>ParseExact –

<xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> Metoda převede řetězec na <xref:System.DateTime> objektu, pokud odpovídá jednomu z vzory zadaný řetězec. Když tato metoda předána řetězec, který není jedním z formuláře zadat <xref:System.FormatException> je vyvolána výjimka. Můžete určit jednu standardní datum a čas specifikátory formátu nebo jejich kombinaci specifikátory vlastní formát. Použití specifikátorů vlastní formátu, je možné sestavit vlastní rozpoznávání řetězec. Informace o specifikátorech, najdete v tématech na [řetězce formátu standardní hodnoty data a času](standard-date-and-time-format-strings.md) a [vlastní datum a čas řetězce formátu](custom-date-and-time-format-strings.md).  

V následujícím příkladu <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> metodě se předává objekt string analyzovat, za nímž následuje specifikátorem formátu, za nímž následuje <xref:System.Globalization.CultureInfo> objektu. To <xref:System.DateTime.ParseExact%2A> metoda analyzovat pouze řetězce, které podle vzoru dlouhého data v `en-US` jazykovou verzi.  

[!code-csharp-interactive[Parsing.DateAndTime#4](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#4)]
[!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#4)]

Každé přetížení <xref:System.DateTime.Parse%2A> a <xref:System.DateTime.ParseExact%2A> metody má také <xref:System.IFormatProvider> parametr, který poskytuje informace specifické pro jazykovou verzi o formátování řetězce. To <xref:System.IFormatProvider> objekt <xref:System.Globalization.CultureInfo> objekt, který reprezentuje standardní jazykovou verzi nebo <xref:System.Globalization.DateTimeFormatInfo> objekt, který je vrácený <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vlastnost.  <xref:System.DateTime.ParseExact%2A> také používá další řetězec nebo pole argument řetězce, který definuje jeden nebo více vlastních datum a čas formáty.  

## <a name="see-also"></a>Viz také  
 [Analýza řetězců](parsing-strings.md)  
 [Typy formátování](formatting-types.md)  
 [Převod typů v rozhraní .NET](type-conversion.md)  
 [Standardní datum a čas formáty](standard-date-and-time-format-strings.md)  
 [Řetězce formátu vlastní hodnota data a času](custom-date-and-time-format-strings.md)
