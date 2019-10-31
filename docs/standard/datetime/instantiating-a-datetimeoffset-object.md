---
title: Vytvoření instance objektu DateTimeOffset
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
ms.openlocfilehash: 1b1178623258393eab28a7087eb04c47b55a9176
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122313"
---
# <a name="instantiating-a-datetimeoffset-object"></a>Vytvoření instance objektu DateTimeOffset

Struktura <xref:System.DateTimeOffset> nabízí několik způsobů, jak vytvořit nové <xref:System.DateTimeOffset> hodnoty. Mnohé z nich odpovídají přímo metodám, které jsou k dispozici pro vytvoření instance nových <xref:System.DateTime>ch hodnot, s vylepšeními, která umožňují zadat posun hodnoty data a času od koordinovaného světového času (UTC). Konkrétně lze vytvořit instanci <xref:System.DateTimeOffset> hodnoty následujícími způsoby:

- Pomocí literálu data a času.

- Voláním konstruktoru <xref:System.DateTimeOffset>.

- Implicitním převodem hodnoty na <xref:System.DateTimeOffset> Value.

- Pomocí analýzy řetězcové reprezentace data a času.

Toto téma poskytuje více podrobností a příklady kódu, které ilustrují tyto metody vytváření instancí nových <xref:System.DateTimeOffset> hodnot.

## <a name="date-and-time-literals"></a>Literály data a času

Pro jazyky, které to podporují, je jedním z nejběžnějších způsobů vytvoření instance <xref:System.DateTime> hodnoty zadání hodnoty data a času jako pevně zakódovaného literálu. Například následující kód Visual Basic vytvoří objekt <xref:System.DateTime>, jehož hodnota je 1. ledna 2008, v 10:00 dop.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

<xref:System.DateTimeOffset> hodnoty lze také inicializovat pomocí literálů data a času při použití jazyků, které podporují <xref:System.DateTime> literály. Například následující kód Visual Basic vytvoří objekt <xref:System.DateTimeOffset>.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

Jak ukazuje výstup konzoly, hodnota <xref:System.DateTimeOffset> vytvořená tímto způsobem je přiřazen posun místního časového pásma. To znamená, že hodnota <xref:System.DateTimeOffset> přiřazená pomocí literálu znaků neidentifikuje jediný bod času, pokud je kód spuštěn v různých počítačích.

## <a name="datetimeoffset-constructors"></a>Konstruktory DateTimeOffset

Typ <xref:System.DateTimeOffset> definuje šest konstruktorů. Čtyři z nich odpovídají přímo <xref:System.DateTime> konstruktory, s dalším parametrem typu <xref:System.TimeSpan>, který definuje posun data a času od času UTC. Ty vám umožní definovat <xref:System.DateTimeOffset> hodnotu na základě hodnoty jejich jednotlivých komponent data a času. Například následující kód používá tyto čtyři konstruktory k vytvoření instance <xref:System.DateTimeOffset> objektů se stejnými hodnotami 7/1/2008 12:05 AM + 01:00.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

Všimněte si, že pokud se hodnota objektu <xref:System.DateTimeOffset> instance s použitím objektu <xref:System.Globalization.PersianCalendar> jako jeden z argumentů jeho konstruktoru zobrazuje v konzole, je vyjádřena jako datum v gregoriánskému místo v Perském kalendáři. Chcete-li vytvořit výstup data pomocí perského kalendáře, přečtěte si příklad v tématu <xref:System.Globalization.PersianCalendar>.

Další dva konstruktory vytvoří objekt <xref:System.DateTimeOffset> z hodnoty <xref:System.DateTime>. První z nich má jeden parametr, <xref:System.DateTime> hodnota, která se má převést na hodnotu <xref:System.DateTimeOffset>. Posun výsledné <xref:System.DateTimeOffset> hodnoty závisí na vlastnosti <xref:System.DateTime.Kind%2A> jednoho parametru konstruktoru. Je-li jeho hodnota <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, posun je nastaven na hodnotu <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. V opačném případě je jeho posun nastavený na stejný jako místní časové pásmo. Následující příklad ukazuje použití tohoto konstruktoru pro vytvoření instance <xref:System.DateTimeOffset> objektů reprezentujících UTC a místní časové pásmo:

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> Volání přetížení konstruktoru <xref:System.DateTimeOffset>, který má jeden <xref:System.DateTime> parametr je ekvivalentní k provádění implicitního převodu <xref:System.DateTime> hodnoty na <xref:System.DateTimeOffset>ou hodnotu.

Druhý konstruktor, který vytváří objekt <xref:System.DateTimeOffset> z <xref:System.DateTime> hodnoty má dva parametry: <xref:System.DateTime> hodnota pro převod a hodnota <xref:System.TimeSpan> představující posun data a času od času UTC. Hodnota posunu musí odpovídat vlastnosti <xref:System.DateTime.Kind%2A> prvního parametru konstruktoru nebo je vyvolána <xref:System.ArgumentException>. Je-li vlastnost <xref:System.DateTime.Kind%2A> prvního parametru <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, musí být hodnota druhého parametru <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Pokud je vlastnost <xref:System.DateTime.Kind%2A> prvního parametru <xref:System.DateTimeKind.Local?displayProperty=nameWithType>, hodnota druhého parametru musí být posunem časového pásma místního systému. Pokud je vlastnost <xref:System.DateTime.Kind%2A> prvního parametru <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, posun může být libovolná platná hodnota. Následující kód ilustruje volání tohoto konstruktoru pro převod <xref:System.DateTime> na <xref:System.DateTimeOffset> hodnoty.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>Implicitní převod typu

Typ <xref:System.DateTimeOffset> podporuje jeden implicitní převod typu: z hodnoty <xref:System.DateTime> na hodnotu <xref:System.DateTimeOffset>. (Implicitní převod typu je převod z jednoho typu na jiný, který nevyžaduje explicitní přetypování (in C#) nebo převod (v Visual Basic) a který neztratí informace. Díky tomu může vypadat jako následující kód.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

Posun výsledné <xref:System.DateTimeOffset> hodnoty závisí na hodnotě vlastnosti <xref:System.DateTime.Kind%2A?displayProperty=nameWithType>. Je-li jeho hodnota <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, posun je nastaven na hodnotu <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Je-li jeho hodnota buď <xref:System.DateTimeKind.Local?displayProperty=nameWithType>, nebo <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, posun je nastaven na hodnotu rovnající se místnímu časovému pásmu.

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>Analýza řetězcové reprezentace data a času

Typ <xref:System.DateTimeOffset> podporuje čtyři metody, které umožňují převést řetězcové vyjádření data a času na hodnotu <xref:System.DateTimeOffset>:

- <xref:System.DateTimeOffset.Parse%2A>, která se pokusí převést řetězcové vyjádření data a času na hodnotu <xref:System.DateTimeOffset> a vyvolá výjimku, pokud se převod nezdařil.

- <xref:System.DateTimeOffset.TryParse%2A>, která se pokusí převést řetězcové vyjádření data a času na hodnotu <xref:System.DateTimeOffset> a vrátí `false`, pokud převod není úspěšný.

- <xref:System.DateTimeOffset.ParseExact%2A>, která se pokusí převést řetězcové vyjádření data a času v zadaném formátu na hodnotu <xref:System.DateTimeOffset>. Metoda vyvolá výjimku, pokud se převod nezdařil.

- <xref:System.DateTimeOffset.TryParseExact%2A>, která se pokusí převést řetězcové vyjádření data a času v zadaném formátu na hodnotu <xref:System.DateTimeOffset>. Metoda vrátí `false`, pokud převod není úspěšný.

Následující příklad znázorňuje volání každé z těchto čtyř metod převodu řetězce pro vytvoření instance <xref:System.DateTimeOffset> hodnoty.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
