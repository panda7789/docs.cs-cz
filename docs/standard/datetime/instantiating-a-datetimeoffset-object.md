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
ms.openlocfilehash: 6d8f4254da256bf2814f66aa62d43204fb302701
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44494054"
---
# <a name="instantiating-a-datetimeoffset-object"></a>Vytvoření instance objektu DateTimeOffset

<xref:System.DateTimeOffset> Struktura nabízí celou řadu způsobů, jak vytvořit nový <xref:System.DateTimeOffset> hodnoty. Řada z nich odpovídá přímo dostupné metody pro vytvoření nové instance <xref:System.DateTime> hodnoty, s vylepšeními, které vám umožňují určit posun od koordinovaného světového času (UTC) hodnoty data a času. Konkrétně můžete vytvořit instanci <xref:System.DateTimeOffset> hodnotu následujícími způsoby:

* Pomocí data a času literálu.

* Při volání <xref:System.DateTimeOffset> konstruktoru.

* Implicitním převodem hodnotu <xref:System.DateTimeOffset> hodnotu.

* Pomocí analýzy řetězcové vyjádření data a času.

Toto téma obsahuje větší podrobnosti a příklady kódu, které ilustrují tyto metody pro vytvoření nové instance <xref:System.DateTimeOffset> hodnoty.

## <a name="date-and-time-literals"></a>Literály data a času

Pro jazyky, které jej podporují, jeden z nejběžnějších způsobů, jak vytvořit instanci <xref:System.DateTime> hodnota je datum a čas jako hodnotu literálu pevně zakódované. Například následující kód jazyka Visual Basic vytvoří <xref:System.DateTime> objekt, jehož hodnota je 1. ledna 2008 v 10:00.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

<xref:System.DateTimeOffset> hodnoty mohou také být inicializovány pomocí literály data a času při použití jazyky, které podporují <xref:System.DateTime> literály. Například následující kód jazyka Visual Basic vytvoří <xref:System.DateTimeOffset> objektu.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

Jak ukazuje výstup konzoly <xref:System.DateTimeOffset> hodnotu tímto způsobem je přiřazen posun místního časového pásma. To znamená, že <xref:System.DateTimeOffset> hodnotu přiřazenou pomocí znakového literálu neidentifikuje jediný bod času, pokud je kód spuštěn na různých počítačích.

## <a name="datetimeoffset-constructors"></a>Konstruktory DateTimeOffset

<xref:System.DateTimeOffset> Typ definuje šest konstruktory. Čtyři z nich přímo na odpovídají <xref:System.DateTime> konstruktory s dalším parametrem typu <xref:System.TimeSpan> , který definuje datum a časový posun od času UTC. Ty umožňují definovat <xref:System.DateTimeOffset> hodnota založená na hodnotě jeho jednotlivých komponent data a času. Například následující kód používá tyto čtyři konstruktory pro vytvoření instance <xref:System.DateTimeOffset> objekty pomocí stejných hodnot 7/1/2008 00:05:00 + 01:00.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

Všimněte si, že při hodnotu <xref:System.DateTimeOffset> instance pomocí objektu <xref:System.Globalization.PersianCalendar> objektu jako jeden z argumentů konstruktoru se zobrazí v konzole, je vyjádřeno jako datum v gregoriánském spíše než perský kalendář. Výstup data v Perském kalendáři, podívejte se na příklad v <xref:System.Globalization.PersianCalendar> tématu.

Vytvořit dva konstruktory <xref:System.DateTimeOffset> objektu z <xref:System.DateTime> hodnotu. První z nich má jeden parametr, <xref:System.DateTime> hodnota převedená na <xref:System.DateTimeOffset> hodnotu. Posun výsledné <xref:System.DateTimeOffset> hodnota závisí na <xref:System.DateTime.Kind%2A> vlastnost jeden parametr konstruktoru. Pokud je jeho hodnota <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, posun nastavena na hodnotu <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Posun je nastavena v opačném případě rovná místní časové pásmo. Následující příklad ukazuje použití tento konstruktor k vytvoření instance <xref:System.DateTimeOffset> objektů představujících UTC a místním časovém pásmu:

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> Volání přetížení <xref:System.DateTimeOffset> konstruktoru, který obsahuje jeden <xref:System.DateTime> parametr je ekvivalentní k provádění implicitní převod <xref:System.DateTime> hodnota, která se <xref:System.DateTimeOffset> hodnotu.

Druhý konstruktor, který vytvoří <xref:System.DateTimeOffset> objektu z <xref:System.DateTime> hodnota má dva parametry: <xref:System.DateTime> hodnotu chcete převést a <xref:System.TimeSpan> posun hodnoty představující datum a čas od času UTC. Tato hodnota posunu musí odpovídat <xref:System.DateTime.Kind%2A> vlastnost první parametr konstruktoru nebo <xref:System.ArgumentException> je vyvolána výjimka. Pokud <xref:System.DateTime.Kind%2A> vlastnost první parametr je <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, musí být hodnota druhého parametru <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Pokud <xref:System.DateTime.Kind%2A> vlastnost první parametr je <xref:System.DateTimeKind.Local?displayProperty=nameWithType>, hodnotu druhého parametru musí být posun místního časového pásma. Pokud <xref:System.DateTime.Kind%2A> vlastnost první parametr je <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, posun může být jakákoli platná hodnota. Následující kód znázorňuje volání tohoto konstruktoru převést <xref:System.DateTime> k <xref:System.DateTimeOffset> hodnoty.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>Implicitní převod typu

<xref:System.DateTimeOffset> Typ podporuje jednu implicitní převod typu: z <xref:System.DateTime> hodnota, která se <xref:System.DateTimeOffset> hodnotu. (Implicitní převod typu je převod z jednoho typu na jiný, který nevyžaduje převod (v jazyce Visual Basic) nebo explicitní přetypování (v jazyce C#), aplikace a, který není dojít ke ztrátě informací. Díky kód jako následující.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

Posun výsledné <xref:System.DateTimeOffset> hodnota závisí <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> hodnotu vlastnosti. Pokud je jeho hodnota <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, posun nastavena na hodnotu <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Pokud je jeho hodnota <xref:System.DateTimeKind.Local?displayProperty=nameWithType> nebo <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, posun je nastavena na tento místní časové pásmo.

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>Analýza kódu řetězcové vyjádření data a času

<xref:System.DateTimeOffset> Typů podporuje čtyři metody, které umožňují převést řetězcové vyjádření data a času do <xref:System.DateTimeOffset> hodnotu:

* <xref:System.DateTimeOffset.Parse%2A>, která se pokusí převést řetězcové vyjádření data a času na <xref:System.DateTimeOffset> hodnotu a vyvolá výjimku, pokud převod selže.

* <xref:System.DateTimeOffset.TryParse%2A>, která se pokusí převést řetězcové vyjádření data a času na <xref:System.DateTimeOffset> hodnotu a vrátí `false` Pokud převod selže.

* <xref:System.DateTimeOffset.ParseExact%2A>, který se snaží převést řetězcové vyjádření data a času v zadaném formátu do <xref:System.DateTimeOffset> hodnotu. Metoda vyvolá výjimku, pokud převod selže.

* <xref:System.DateTimeOffset.TryParseExact%2A>, který se snaží převést řetězcové vyjádření data a času v zadaném formátu do <xref:System.DateTimeOffset> hodnotu. Metoda vrátí `false` Pokud převod selže.

Následující příklad ukazuje volání na každý z těchto metod pro převod řetězce pro vytvoření instance <xref:System.DateTimeOffset> hodnotu.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>Viz také:

* [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
