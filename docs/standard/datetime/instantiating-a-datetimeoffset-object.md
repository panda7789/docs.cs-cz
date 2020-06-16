---
title: Vytvoření instance objektu DateTimeOffset
description: Přečtěte si, jak vytvářet instance (vytvořit instanci) objektu DateTimeOffset v rozhraní .NET. Seznamte se s datovými literály, &mi časovými literály, konstruktory, implicitním převodem typu & další.
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
- DateTimeOffset structure, converting to DateTime
- DateTimeOffset structure, instantiating
ms.assetid: 9648375f-d368-4373-a976-3332ece00c0a
ms.openlocfilehash: c2b71a2a98353a4ec9ed249acf18939dd4740e99
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768895"
---
# <a name="instantiating-a-datetimeoffset-object"></a>Vytvoření instance objektu DateTimeOffset

<xref:System.DateTimeOffset>Struktura nabízí několik způsobů, jak vytvořit nové <xref:System.DateTimeOffset> hodnoty. Mnohé z nich odpovídají přímo metodám, které jsou k dispozici pro vytváření instancí nových <xref:System.DateTime> hodnot, s vylepšeními, která umožňují zadat posun hodnoty data a času od koordinovaného světového času (UTC). Konkrétně lze vytvořit instanci <xref:System.DateTimeOffset> hodnoty následujícími způsoby:

- Pomocí literálu data a času.

- Voláním <xref:System.DateTimeOffset> konstruktoru.

- Implicitním převodem hodnoty na <xref:System.DateTimeOffset> hodnotu.

- Pomocí analýzy řetězcové reprezentace data a času.

Toto téma poskytuje více podrobností a příklady kódu, které ilustrují tyto metody vytváření instancí nových <xref:System.DateTimeOffset> hodnot.

## <a name="date-and-time-literals"></a>Literály data a času

U jazyků, které to podporují, je jedním z nejběžnějších způsobů vytvoření instance <xref:System.DateTime> hodnoty zadání data a času jako pevně zakódované hodnoty literálu. Například následující kód Visual Basic vytvoří <xref:System.DateTime> objekt, jehož hodnota je 1. ledna 2008, v 10:00 dop.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

<xref:System.DateTimeOffset>hodnoty lze také inicializovat pomocí literálů data a času při použití jazyků, které podporují <xref:System.DateTime> literály. Například následující kód Visual Basic vytvoří <xref:System.DateTimeOffset> objekt.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

Jak ukazuje výstup konzoly, <xref:System.DateTimeOffset> hodnota vytvořená tímto způsobem je přiřazena posunu místního časového pásma. To znamená, že <xref:System.DateTimeOffset> hodnota přiřazená pomocí literálu znaků neidentifikuje jediný bod času, pokud je kód spuštěn na různých počítačích.

## <a name="datetimeoffset-constructors"></a>Konstruktory DateTimeOffset

<xref:System.DateTimeOffset>Typ definuje šest konstruktorů. Čtyři z nich odpovídají přímo <xref:System.DateTime> konstruktorům, s dalším parametrem typu <xref:System.TimeSpan> , který definuje posun data a času od času UTC. Ty vám umožní definovat hodnotu na <xref:System.DateTimeOffset> základě hodnoty jejich jednotlivých komponent data a času. Například následující kód používá tyto čtyři konstruktory k vytvoření instance <xref:System.DateTimeOffset> objektů se stejnými hodnotami 7/1/2008 12:05 am + 01:00.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

Všimněte si, že pokud se hodnota objektu, jehož <xref:System.DateTimeOffset> instance je vytvořena pomocí <xref:System.Globalization.PersianCalendar> objektu jako jeden z argumentů jeho konstruktoru, zobrazuje v konzole, je vyjádřena jako datum v gregoriánském, nikoli v Perském kalendáři. Chcete-li vytvořit výstup data pomocí perského kalendáře, přečtěte si příklad v <xref:System.Globalization.PersianCalendar> tématu.

Další dva konstruktory vytvoří <xref:System.DateTimeOffset> objekt z <xref:System.DateTime> hodnoty. První z nich má jeden parametr, hodnota, která má být <xref:System.DateTime> převedena na <xref:System.DateTimeOffset> hodnotu. Posun výsledné <xref:System.DateTimeOffset> hodnoty závisí na <xref:System.DateTime.Kind%2A> vlastnosti jediného parametru konstruktoru. Pokud je jeho hodnota <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> , posun je nastaven na hodnotu Equal <xref:System.TimeSpan.Zero?displayProperty=nameWithType> . V opačném případě je jeho posun nastavený na stejný jako místní časové pásmo. Následující příklad ilustruje použití tohoto konstruktoru pro vytvoření instance <xref:System.DateTimeOffset> objektů reprezentujících UTC a místní časové pásmo:

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> Volání přetížení <xref:System.DateTimeOffset> konstruktoru, který má jeden <xref:System.DateTime> parametr, je ekvivalentní k provádění implicitního převodu <xref:System.DateTime> hodnoty na <xref:System.DateTimeOffset> hodnotu.

Druhý konstruktor, který vytváří <xref:System.DateTimeOffset> objekt z hodnoty, <xref:System.DateTime> má dva parametry: <xref:System.DateTime> hodnotu pro převod a <xref:System.TimeSpan> hodnotu představující posun data a času od času UTC. Tato hodnota posunu musí odpovídat <xref:System.DateTime.Kind%2A> vlastnosti prvního parametru konstruktoru nebo <xref:System.ArgumentException> vyvolání. Pokud <xref:System.DateTime.Kind%2A> je vlastnost prvního parametru <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> hodnota, musí být druhý parametr <xref:System.TimeSpan.Zero?displayProperty=nameWithType> . Pokud <xref:System.DateTime.Kind%2A> je vlastnost prvního parametru <xref:System.DateTimeKind.Local?displayProperty=nameWithType> , hodnota druhého parametru musí být posunem časového pásma místního systému. Pokud <xref:System.DateTime.Kind%2A> je vlastnost prvního parametru nastavená na <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> , posun může být libovolná platná hodnota. Následující kód ilustruje volání tohoto konstruktoru pro převod <xref:System.DateTime> na <xref:System.DateTimeOffset> hodnoty.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>Implicitní převod typu

<xref:System.DateTimeOffset>Typ podporuje jeden implicitní převod typu: z <xref:System.DateTime> hodnoty na <xref:System.DateTimeOffset> hodnotu. (Implicitní převod typu je převod z jednoho typu na jiný, který nevyžaduje explicitní přetypování (v jazyce C#) nebo převod (v Visual Basic) a který neztratí informace. Díky tomu může vypadat jako následující kód.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

Posun výsledné <xref:System.DateTimeOffset> hodnoty závisí na <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> hodnotě vlastnosti. Pokud je jeho hodnota <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> , posun je nastaven na hodnotu Equal <xref:System.TimeSpan.Zero?displayProperty=nameWithType> . Je-li jeho hodnota buď <xref:System.DateTimeKind.Local?displayProperty=nameWithType> nebo <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> , posun je nastaven na hodnotu rovnou místnímu časovému pásmu.

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>Analýza řetězcové reprezentace data a času

<xref:System.DateTimeOffset>Typ podporuje čtyři metody, které umožňují převést řetězcové vyjádření data a času na <xref:System.DateTimeOffset> hodnotu:

- <xref:System.DateTimeOffset.Parse%2A>, který se pokusí převést řetězcové vyjádření data a času na <xref:System.DateTimeOffset> hodnotu a vyvolá výjimku, pokud převod není úspěšný.

- <xref:System.DateTimeOffset.TryParse%2A>, který se pokusí převést řetězcové vyjádření data a času na <xref:System.DateTimeOffset> hodnotu a vrátí, `false` Pokud převod není úspěšný.

- <xref:System.DateTimeOffset.ParseExact%2A>, který se pokusí převést řetězcové vyjádření data a času v zadaném formátu na <xref:System.DateTimeOffset> hodnotu. Metoda vyvolá výjimku, pokud se převod nezdařil.

- <xref:System.DateTimeOffset.TryParseExact%2A>, který se pokusí převést řetězcové vyjádření data a času v zadaném formátu na <xref:System.DateTimeOffset> hodnotu. Metoda vrátí, `false` Pokud převod není úspěšný.

Následující příklad znázorňuje volání každé z těchto čtyř metod převodu řetězce pro vytvoření instance <xref:System.DateTimeOffset> hodnoty.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>Viz také

- [Data, časy a časová pásma](index.md)
