---
title: Převést řetězce na DateTime
description: Naučte se techniky analyzovat řetězce, které reprezentují data a časy pro vytvoření hodnoty DateTime z řetězce data a času.
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
ms.openlocfilehash: 9fba80e4dbe1e4950ed24e7489ac48ea1b6ff20b
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662898"
---
# <a name="parse-date-and-time-strings-in-net"></a>Analyzovat řetězce data a času v .NET

Analýza řetězců pro jejich převod na <xref:System.DateTime> objekty vyžaduje, abyste určili informace o tom, jak jsou data a časy reprezentované jako text. Různé jazykové verze používají různé objednávky pro den, měsíc a rok. Některá časová vyjádření používají 24hodinové hodiny, ostatní určují "AM" a "PM". Některé aplikace potřebují pouze datum. Ostatní potřebují jenom čas. Dál je potřeba zadat jak datum, tak i čas. Metody, které převádějí řetězce na <xref:System.DateTime> objekty, umožňují zadat podrobné informace o formátech, které očekáváte, a o prvcích data a času, které vaše aplikace potřebuje. Existují tři dílčí úkoly, které správně převádějí text na <xref:System.DateTime> :

1. Je nutné zadat očekávaný formát textu, který představuje datum a čas.
1. Lze zadat jazykovou verzi pro formát data a času.
1. Můžete určit, jak mají být chybějící komponenty v textové reprezentace nastaveny v poli Datum a čas.

<xref:System.DateTime.Parse%2A>Metody a <xref:System.DateTime.TryParse%2A> převádějí mnoho běžných reprezentace data a času. <xref:System.DateTime.ParseExact%2A>Metody a <xref:System.DateTime.TryParseExact%2A> převádějí řetězcovou reprezentaci, která odpovídá vzoru určenému řetězcem formátu data a času. (Podrobnosti najdete v článcích o [standardních formátovacích řetězcích data a času](standard-date-and-time-format-strings.md) a [vlastních formátovacích řetězcích data a času](custom-date-and-time-format-strings.md) .)

Aktuální <xref:System.Globalization.DateTimeFormatInfo> objekt poskytuje větší kontrolu nad tím, jak by měl být text interpretován jako datum a čas. Vlastnosti <xref:System.Globalization.DateTimeFormatInfo> popište oddělovače data a času a názvy měsíců, dnů a mazání a formát pro označení am a PM. Aktuální jazyková verze vlákna poskytuje hodnotu <xref:System.Globalization.DateTimeFormatInfo> , která představuje aktuální jazykovou verzi. Chcete-li určit konkrétní jazykovou verzi nebo vlastní nastavení, zadejte <xref:System.IFormatProvider> parametr metody analýzy. Pro <xref:System.IFormatProvider> parametr zadejte <xref:System.Globalization.CultureInfo> objekt, který představuje jazykovou verzi nebo <xref:System.Globalization.DateTimeFormatInfo> objekt.

Text, který představuje datum nebo čas, může chybět některé informace. Většina lidí například předpokládá, že datum "Březen 12" představuje aktuální rok. Podobně "březen 2018" představuje měsíc v březnu v roce 2018. Text, který představuje častou dobu, zahrnuje jenom hodiny, minuty a označení dopoledne/odpoledne.  Metody analýzy zpracovávají tyto chybějící informace pomocí přiměřených výchozích hodnot:

- Pokud je k dispozici pouze čas, část data použije aktuální datum.
- Pokud je k dispozici pouze datum, je časová část půlnoc.
- Pokud rok není zadaný v datu, použije se aktuální rok.
- Když není zadaný den v měsíci, použije se první měsíc v měsíci.

Pokud se datum nachází v řetězci, musí obsahovat měsíc a jeden z dnů nebo roků. Pokud je k dispozici čas, musí zahrnovat hodinu a buď minuty, nebo označení dopoledne/odpoledne.

Můžete zadat <xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault> konstantu pro přepsání těchto výchozích hodnot. Při použití této konstanty se všechny vlastnosti chybějícího roku, měsíce nebo dne nastaví na hodnotu `1` . [Poslední příklad](#styles-example) s <xref:System.DateTime.Parse%2A> tímto chováním demonstruje.

Kromě data a času může řetězcová reprezentace data a času zahrnovat posun, který indikuje, kolik času se liší od koordinovaného světového času (UTC). Například řetězec "2/14/2007 5:32:00 -7:00" definuje čas, který je sedm hodin starší než UTC. Pokud je posun vynechán z řetězcové reprezentace času, analýza vrátí <xref:System.DateTime> objekt s <xref:System.DateTime.Kind%2A> vlastností nastavenou na <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> . Je-li zadán posun, při analýze se vrátí <xref:System.DateTime> objekt s <xref:System.DateTime.Kind%2A> vlastností nastavenou na <xref:System.DateTimeKind.Local?displayProperty=nameWithType> hodnotu a jeho hodnota se upraví na místní časové pásmo počítače. Toto chování můžete upravit pomocí <xref:System.Globalization.DateTimeStyles> hodnoty s metodou analýzy.

Zprostředkovatel formátu slouží také k interpretaci nejednoznačného číselného data. Není jasné, které součásti data reprezentované řetězcem "02/03/04" jsou měsíc, den a rok. Komponenty jsou interpretovány podle pořadí podobných formátů data ve zprostředkovateli formátu.

## <a name="parse"></a>Analyzovat

Následující příklad ukazuje použití <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> metody pro převod typu na `string` <xref:System.DateTime> . V tomto příkladu se používá jazyková verze přidružená k aktuálnímu vláknu. Pokud <xref:System.Globalization.CultureInfo> přidružená k aktuální jazykové verzi nemůže analyzovat vstupní řetězec, <xref:System.FormatException> je vyvolána.

> [!TIP]
> Všechny ukázky C# v tomto článku se spouštějí v prohlížeči. Kliknutím na tlačítko **Spustit** zobrazíte výstup. Můžete je také upravit a experimentovat.

> [!NOTE]
> Tyto příklady jsou k dispozici v úložišti Docs na GitHubu pro [C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/conversions) i [Visual Basic](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/how-to/conversions).

[!code-csharp-interactive[Parsing.DateAndTime#1](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#1)]
[!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#1)]

Můžete také explicitně definovat jazykovou verzi, jejíž konvence formátování jsou používány při analýze řetězce. Zadáte jeden ze standardních <xref:System.Globalization.DateTimeFormatInfo> objektů vrácených <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vlastností. Následující příklad používá poskytovatele formátu k analýze německého řetězce do <xref:System.DateTime> . Vytvoří <xref:System.Globalization.CultureInfo> reprezentující `de-DE` jazykovou verzi. Tento `CultureInfo` objekt zajišťuje úspěšnou analýzu tohoto konkrétního řetězce. To vylučuje jakékoli nastavení v <xref:System.Threading.Thread.CurrentCulture> <xref:System.Threading.Thread.CurrentThread> .

[!code-csharp-interactive[Parsing.DateAndTime#2](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#2)]
[!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#2)]

I když však můžete použít přetížení <xref:System.DateTime.Parse%2A> metody k určení vlastních poskytovatelů formátu, metoda nepodporuje analýzu nestandardních formátů. Chcete-li analyzovat datum a čas vyjádřený v nestandardním formátu, použijte <xref:System.DateTime.ParseExact%2A> místo toho metodu.

<a name="styles-example"></a>Následující příklad používá <xref:System.Globalization.DateTimeStyles> výčet k určení, že informace o aktuálním datu a čase by neměly být přidány do pole <xref:System.DateTime> pro nespecifikovaná pole.

[!code-csharp-interactive[Parsing.DateAndTime#3](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#3)]
[!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#3)]

## <a name="parseexact"></a>ParseExact

<xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>Metoda převede řetězec na <xref:System.DateTime> objekt, pokud odpovídá jednomu ze zadaných vzorů řetězce. Pokud je řetězec, který není jedním z určených formulářů, předán této metodě, <xref:System.FormatException> je vyvolána. Můžete zadat jeden ze specifikátorů standardního formátu data a času nebo kombinaci vlastního specifikátoru formátu. Pomocí specifikátorů vlastního formátu je možné vytvořit vlastní řetězec pro rozpoznávání. Vysvětlení specifikátorů naleznete v tématech o standardních formátovacích [řetězcích data a času](standard-date-and-time-format-strings.md) a [vlastních formátovacích řetězcích data a času](custom-date-and-time-format-strings.md).

V následujícím příkladu <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> je metoda předána objektu řetězce pro analýzu následovaný specifikátorem formátu následovaným <xref:System.Globalization.CultureInfo> objektem. Tato <xref:System.DateTime.ParseExact%2A> metoda může analyzovat pouze řetězce, které následují po dlouhém vzoru data v `en-US` jazykové verzi.

[!code-csharp-interactive[Parsing.DateAndTime#4](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#4)]
[!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#4)]

Každé přetížení <xref:System.DateTime.Parse%2A> <xref:System.DateTime.ParseExact%2A> metod a má také <xref:System.IFormatProvider> parametr, který poskytuje informace specifické pro jazykovou verzi o formátování řetězce. Tento <xref:System.IFormatProvider> objekt je <xref:System.Globalization.CultureInfo> objekt, který představuje standardní jazykovou verzi nebo <xref:System.Globalization.DateTimeFormatInfo> objekt, který je vrácen <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vlastností.  <xref:System.DateTime.ParseExact%2A>používá také další argument řetězce nebo pole řetězců, který definuje jeden nebo více vlastních formátů data a času.

## <a name="see-also"></a>Viz také

- [Analýza řetězců](parsing-strings.md)
- [Typy formátování](formatting-types.md)
- [Převod typů v rozhraní .NET](type-conversion.md)
- [Standardní formáty data a času](standard-date-and-time-format-strings.md)
- [Vlastní řetězce formátu data a času](custom-date-and-time-format-strings.md)
