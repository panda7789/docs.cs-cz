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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50cc71b62581e1fb9302fe241abf6349afd33f8d
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106632"
---
# <a name="instantiating-a-datetimeoffset-object"></a>Vytvoření instance objektu DateTimeOffset

Struktura nabízí několik způsobů, jak vytvořit nové <xref:System.DateTimeOffset> hodnoty. <xref:System.DateTimeOffset> Mnohé z nich odpovídají přímo metodám, které jsou k dispozici pro <xref:System.DateTime> vytváření instancí nových hodnot, s vylepšeními, která umožňují zadat posun hodnoty data a času od koordinovaného světového času (UTC). Konkrétně lze vytvořit instanci <xref:System.DateTimeOffset> hodnoty následujícími způsoby:

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

<xref:System.DateTimeOffset> Typ definuje šest konstruktorů. Čtyři z nich odpovídají přímo <xref:System.DateTime> konstruktorům, s dalším parametrem typu <xref:System.TimeSpan> , který definuje posun data a času od času UTC. Ty vám umožní definovat <xref:System.DateTimeOffset> hodnotu na základě hodnoty jejich jednotlivých komponent data a času. Například následující kód používá tyto čtyři konstruktory k vytvoření instance <xref:System.DateTimeOffset> objektů se stejnými hodnotami 7/1/2008 12:05 am + 01:00.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

Všimněte si, že pokud se hodnota <xref:System.DateTimeOffset> objektu, jehož instance je vytvořena <xref:System.Globalization.PersianCalendar> pomocí objektu jako jeden z argumentů jeho konstruktoru, zobrazuje v konzole, je vyjádřena jako datum v gregoriánském, nikoli v Perském kalendáři. Chcete-li vytvořit výstup data pomocí perského kalendáře, přečtěte si <xref:System.Globalization.PersianCalendar> příklad v tématu.

Další dva konstruktory vytvoří <xref:System.DateTimeOffset> objekt <xref:System.DateTime> z hodnoty. První z nich má jeden parametr, <xref:System.DateTime> hodnota, která má být převedena <xref:System.DateTimeOffset> na hodnotu. Posun výsledné <xref:System.DateTimeOffset> hodnoty závisí <xref:System.DateTime.Kind%2A> na vlastnosti jediného parametru konstruktoru. Pokud je <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>jeho hodnota, posun je nastaven na hodnotu <xref:System.TimeSpan.Zero?displayProperty=nameWithType>EQUAL. V opačném případě je jeho posun nastavený na stejný jako místní časové pásmo. Následující příklad ilustruje použití tohoto konstruktoru pro vytvoření instance <xref:System.DateTimeOffset> objektů reprezentujících UTC a místní časové pásmo:

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> Volání přetížení <xref:System.DateTimeOffset> konstruktoru, který má jeden <xref:System.DateTime> parametr, je ekvivalentní k provádění implicitního převodu <xref:System.DateTime> hodnoty na <xref:System.DateTimeOffset> hodnotu.

Druhý konstruktor, který <xref:System.DateTimeOffset> vytváří objekt z hodnoty, <xref:System.DateTime> <xref:System.DateTime> má dva parametry: hodnotu pro převod a <xref:System.TimeSpan> hodnotu představující posun data a času od času UTC. Tato hodnota posunu musí odpovídat <xref:System.DateTime.Kind%2A> vlastnosti prvního parametru konstruktoru <xref:System.ArgumentException> nebo vyvolání. Pokud je <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>vlastnost prvního parametru hodnota, musí být <xref:System.TimeSpan.Zero?displayProperty=nameWithType>druhý parametr. Pokud je <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Local?displayProperty=nameWithType>vlastnost prvního parametru, hodnota druhého parametru musí být posunem časového pásma místního systému. Pokud je <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>vlastnost prvního parametru nastavená na, posun může být libovolná platná hodnota. <xref:System.DateTime.Kind%2A> Následující kód ilustruje volání tohoto konstruktoru pro převod <xref:System.DateTime> na <xref:System.DateTimeOffset> hodnoty.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>Implicitní převod typu

Typ podporuje jeden implicitní převod typu: <xref:System.DateTime> z hodnoty na <xref:System.DateTimeOffset> hodnotu. <xref:System.DateTimeOffset> (Implicitní převod typu je převod z jednoho typu na jiný, který nevyžaduje explicitní přetypování (in C#) nebo převod (v Visual Basic) a který neztratí informace. Díky tomu může vypadat jako následující kód.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

Posun výsledné <xref:System.DateTimeOffset> hodnoty závisí <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> na hodnotě vlastnosti. Pokud je <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>jeho hodnota, posun je nastaven na hodnotu <xref:System.TimeSpan.Zero?displayProperty=nameWithType>EQUAL. Je-li jeho hodnota <xref:System.DateTimeKind.Local?displayProperty=nameWithType> buď <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>nebo, posun je nastaven na hodnotu rovnou místnímu časovému pásmu.

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>Analýza řetězcové reprezentace data a času

Typ podporuje čtyři metody, které umožňují převést řetězcové vyjádření data a času <xref:System.DateTimeOffset> na hodnotu: <xref:System.DateTimeOffset>

- <xref:System.DateTimeOffset.Parse%2A>, který se pokusí převést řetězcové vyjádření data a času na <xref:System.DateTimeOffset> hodnotu a vyvolá výjimku, pokud převod není úspěšný.

- <xref:System.DateTimeOffset.TryParse%2A>, který se pokusí převést řetězcové vyjádření data a času na <xref:System.DateTimeOffset> hodnotu a vrátí `false` , pokud převod není úspěšný.

- <xref:System.DateTimeOffset.ParseExact%2A>, který se pokusí převést řetězcové vyjádření data a času v zadaném formátu na <xref:System.DateTimeOffset> hodnotu. Metoda vyvolá výjimku, pokud se převod nezdařil.

- <xref:System.DateTimeOffset.TryParseExact%2A>, který se pokusí převést řetězcové vyjádření data a času v zadaném formátu na <xref:System.DateTimeOffset> hodnotu. Metoda vrátí `false` , pokud převod není úspěšný.

Následující příklad znázorňuje volání každé z těchto čtyř metod převodu řetězce pro vytvoření instance <xref:System.DateTimeOffset> hodnoty.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
