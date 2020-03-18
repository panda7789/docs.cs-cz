---
title: 'Postup: převod řetězců na DateTime'
description: Naučte se techniky analyzovat řetězce, které představují data a časy k vytvoření DateTime z řetězce data a času.
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
ms.openlocfilehash: 9555304e570226b2ed3b040735cf099b5a018f93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156540"
---
# <a name="parsing-date-and-time-strings-in-net"></a>Analýza řetězců data a času v rozhraní .NET

Analýza řetězců pro jejich převod <xref:System.DateTime> na objekty vyžaduje zadání informací o tom, jak jsou kalendářní data a časy reprezentovány jako text. Různé jazykové verze používají různé objednávky pro den, měsíc a rok. Některé časové reprezentace používají 24hodinový čas, jiné určují "AM" a "PM". Některé aplikace potřebují pouze datum. Jiní potřebují jen čas. Ještě jiní musí specifikovat datum i čas. Metody, které převádějí řetězce na <xref:System.DateTime> objekty, umožňují poskytnout podrobné informace o očekávaných formátech a prvcích data a času, které vaše aplikace potřebuje. Existují tři dílčí úkoly pro správný <xref:System.DateTime>převod textu na :

1. Je nutné zadat očekávaný formát textu představujícího datum a čas.
1. Můžete určit jazykovou verzi pro formát data času.
1. Můžete určit, jak budou chybějící součásti v reprezentaci textu nastaveny v datu a čase.

Metody <xref:System.DateTime.Parse%2A> <xref:System.DateTime.TryParse%2A> a převést mnoho běžných reprezentací data a času. Metody <xref:System.DateTime.ParseExact%2A> <xref:System.DateTime.TryParseExact%2A> a převádějí řetězcovou reprezentaci, která odpovídá vzoru určenému řetězcem formátu data a času. (Podrobnosti naleznete v článcích [standardních formátovacích řetězců data a času](standard-date-and-time-format-strings.md) a [vlastních formátovacích řetězcích data a času.)](custom-date-and-time-format-strings.md)

Aktuální <xref:System.Globalization.DateTimeFormatInfo> objekt poskytuje větší kontrolu nad tím, jak by měl být text interpretován jako datum a čas. Vlastnosti <xref:System.Globalization.DateTimeFormatInfo> popisují oddělovače data a času a názvy měsíců, dnů a období a formát označení "AM" a "PM". Aktuální jazyková verze <xref:System.Globalization.DateTimeFormatInfo> vlákna poskytuje, který představuje aktuální jazykovou verzi. Pokud chcete konkrétní jazykovou verzi nebo <xref:System.IFormatProvider> vlastní nastavení, zadejte parametr metody analýzy. Pro <xref:System.IFormatProvider> parametr zadejte <xref:System.Globalization.CultureInfo> objekt, který představuje jazykovou verzi, nebo <xref:System.Globalization.DateTimeFormatInfo> objekt.

V textu představujícím datum nebo čas mohou chybět některé informace. Většina lidí by například předpokládala, že datum "12. března" představuje aktuální rok. Podobně "březen 2018" představuje měsíc březen v roce 2018. Text představující čas často obsahuje pouze hodiny, minuty a označení Dopoledne a odpoledne.  Metody analýzy zpracovávají tyto chybějící informace pomocí přiměřených výchozích hodnot:

- Pokud je k dispozici pouze čas, část data používá aktuální datum.
- Pokud je k dispozici pouze datum, je časová část půlnoc.
- Pokud není rok zadán v datu, použije se aktuální rok.
- Pokud není zadán den v měsíci, použije se první v měsíci.

Pokud je datum v řetězci, musí obsahovat měsíc a jeden den nebo rok. Pokud je přítomen čas, musí obsahovat hodinu a buď minuty nebo označení Do/pm.

Můžete určit <xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault> konstantu, která má přepsat tyto výchozí hodnoty. Při použití této konstanty jsou všechny chybějící vlastnosti roku, `1`měsíce nebo dne nastaveny na hodnotu . [Poslední příklad](#styles-example) <xref:System.DateTime.Parse%2A> pomocí ukazuje toto chování.

Kromě komponenty data a času může řetězcová reprezentace data a času obsahovat posun, který označuje, jak moc se čas liší od koordinovaného světového času (UTC). Například řetězec "2/14/2007 5:32:00 -7:00" definuje čas, který je o sedm hodin dříve než UTC. Pokud je posun vynechán z řetězcové reprezentace času, <xref:System.DateTime> vrátí analýza <xref:System.DateTime.Kind%2A> objektu <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>s vlastností nastavenou na . Pokud je zadán posun, parsování <xref:System.DateTime> vrátí <xref:System.DateTime.Kind%2A> objekt <xref:System.DateTimeKind.Local?displayProperty=nameWithType> s jeho vlastnost nastavenou na a jeho hodnota upravena na místní časové pásmo počítače. Toto chování můžete upravit <xref:System.Globalization.DateTimeStyles> pomocí hodnoty s metodou analýzy.
  
Zprostředkovatel formátu se také používá k interpretaci nejednoznačného číselného data. Není jasné, které součásti data reprezentovaného řetězcem "02/03/04" jsou měsíc, den a rok. Komponenty jsou interpretovány podle pořadí podobných formátů data ve zprostředkovateli formátu.

## <a name="parse"></a>Analyzovat

Následující příklad ilustruje použití <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> metody převést `string` na <xref:System.DateTime>. Tento příklad používá jazykovou verzi přidruženou k aktuálnímu vláknu. Pokud <xref:System.Globalization.CultureInfo> přidružené k aktuální jazykové verzi nelze analyzovat <xref:System.FormatException> vstupní řetězec, je vyvolána.

> [!TIP]
> Všechny ukázky jazyka C# v tomto článku spustit v prohlížeči. Stisknutím tlačítka **Spustit** zobrazíte výstup. Můžete je také upravit a experimentovat sami.

> [!NOTE]
> Tyto příklady jsou k dispozici v úložišti dokumentů GitHub pro [C#](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/conversions) i [Visual Basic](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/how-to/conversions). Nebo můžete stáhnout projekt jako soubor zip pro [C#](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/conversions.zip) nebo [Visual Basic](https://github.com/dotnet/samples/raw/master/snippets/visualbasic/how-to/conversions.zip).

[!code-csharp-interactive[Parsing.DateAndTime#1](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#1)]
[!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#1)]

Můžete také explicitně definovat jazykovou verzi, jejíž konvencí formátování se používají při analýzě řetězce. Zadáte jeden ze <xref:System.Globalization.DateTimeFormatInfo> standardních objektů <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vrácených vlastností. Následující příklad používá zprostředkovatele formátu k analýzě <xref:System.DateTime>německého řetězce do . Vytvoří <xref:System.Globalization.CultureInfo> představující jazykovou `de-DE` verzi. Tento `CultureInfo` objekt zajišťuje úspěšnou analýzu tohoto konkrétního řetězce. To vylučuje jakékoli nastavení <xref:System.Threading.Thread.CurrentCulture> je <xref:System.Threading.Thread.CurrentThread>v .  
  
[!code-csharp[Parsing.DateAndTime#2](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#2)]
[!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#2)]

I když však můžete použít <xref:System.DateTime.Parse%2A> přetížení metody k určení zprostředkovatelů vlastního formátu, metoda nepodporuje analýzu nestandardních formátů. Chcete-li analyzovat datum a čas vyjádřený v nestandardním formátu, použijte místo toho metodu. <xref:System.DateTime.ParseExact%2A>  

<a name="styles-example"></a>Následující příklad používá <xref:System.Globalization.DateTimeStyles> výčet k určení, že aktuální informace o datu <xref:System.DateTime> a čase by neměly být přidány do polí pro nespecifikované.  

[!code-csharp[Parsing.DateAndTime#3](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#3)]
[!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#3)]

## <a name="parseexact"></a>Parseexact

Metoda <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> převede řetězec na <xref:System.DateTime> objekt, pokud odpovídá jednomu ze zadaných vzorů řetězce. Pokud řetězec, který není jedním z zadaných formulářů <xref:System.FormatException> je předán této metodě, je vyvolána. Můžete zadat jeden ze standardních specifikátorů formátu data a času nebo kombinaci vlastních specifikátorů formátu. Pomocí vlastních specifikátorů formátu je možné vytvořit vlastní řetězec rozpoznávání. Vysvětlení specifikátorů naleznete v tématech standardních [formátovacích řetězců kalendářních a časových formátů](standard-date-and-time-format-strings.md) a [vlastních formátovacích řetězců data a času](custom-date-and-time-format-strings.md).  

V následujícím příkladu <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> je metoda předána objektu řetězce k analýzě, následovaným specifikátorem formátu následovaným objektem. <xref:System.Globalization.CultureInfo> Tato <xref:System.DateTime.ParseExact%2A> metoda může analyzovat pouze řetězce, které následují `en-US` vzorek dlouhé datum v jazykové verzi.  

[!code-csharp[Parsing.DateAndTime#4](../../../samples/snippets/csharp/how-to/conversions/StringToDateTime.cs#4)]
[!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/how-to/conversions/Program.vb#4)]

Každé přetížení <xref:System.DateTime.Parse%2A> a <xref:System.DateTime.ParseExact%2A> metody má <xref:System.IFormatProvider> také parametr, který poskytuje informace specifické pro jazykovou verzi o formátování řetězce. Tento <xref:System.IFormatProvider> objekt <xref:System.Globalization.CultureInfo> je objekt, který představuje <xref:System.Globalization.DateTimeFormatInfo> standardní jazykovou <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> verzi nebo objekt, který je vrácen vlastností.  <xref:System.DateTime.ParseExact%2A>Používá také další argument řetězce nebo pole řetězce, který definuje jeden nebo více vlastních formátů data a času.  

## <a name="see-also"></a>Viz také

- [Analýza řetězců](parsing-strings.md)
- [Typy formátování](formatting-types.md)
- [Převod typů v rozhraní .NET](type-conversion.md)
- [Standardní formáty data a času](standard-date-and-time-format-strings.md)
- [Vlastní formátovací řetězce data a času](custom-date-and-time-format-strings.md)
