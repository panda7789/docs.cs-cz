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
ms.openlocfilehash: a48ea87bb5eb1e302ae6a1169c22ea30bd4bc7ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="instantiating-a-datetimeoffset-object"></a>Vytvoření instance objektu DateTimeOffset

<xref:System.DateTimeOffset> Struktura nabízí několik způsobů, jak vytvořit nový <xref:System.DateTimeOffset> hodnoty. Mnohé z nich odpovídají přímo dostupné metody pro vytvoření nové instance <xref:System.DateTime> hodnoty, s vylepšeními, které vám umožní zadat hodnoty data a času posun od koordinovaného světového času (UTC). Konkrétně můžete vytvořit instanci <xref:System.DateTimeOffset> hodnotu následujícími způsoby:

* Pomocí datum a čas literálu.

* Při volání <xref:System.DateTimeOffset> konstruktor.

* Podle implicitně převodu hodnoty na <xref:System.DateTimeOffset> hodnotu.

* Analýzou řetězcovou reprezentaci data a času.

Toto téma obsahuje větší podrobnosti a kód příklady, které ilustrují tyto metody pro vytváření nových instancí <xref:System.DateTimeOffset> hodnoty.

## <a name="date-and-time-literals"></a>Datum a čas literály

Pro jazyky, které to podporují, nejběžnější způsoby k vytváření instancí <xref:System.DateTime> hodnota je poskytnout datum a čas, jako je pevně Literálová hodnota. Například následující kód jazyka Visual Basic vytvoří <xref:System.DateTime> objekt, jehož hodnota je 1. ledna 2008 na 10:00.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

<xref:System.DateTimeOffset> hodnoty mohou být navíc inicializované pomocí literály datum a čas, při použití jazyky, které podporují <xref:System.DateTime> literály. Například následující kód jazyka Visual Basic vytvoří <xref:System.DateTimeOffset> objektu.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

Jak ukazuje výstup konzoly, <xref:System.DateTimeOffset> hodnota vytvořené v tomto případě je přiřazena posun místního časového pásma. To znamená, že <xref:System.DateTimeOffset> hodnotu přiřazenou pomocí znakového literálu neidentifikuje jediný bod čas, pokud kód běží na různých počítačích.

## <a name="datetimeoffset-constructors"></a>Konstruktory DateTimeOffset

<xref:System.DateTimeOffset> Typ definuje šest konstruktorů. Čtyři z nich odpovídají přímo na <xref:System.DateTime> konstruktory s dalším parametrem typu <xref:System.TimeSpan> , který definuje datum a čas posun od času UTC. Ty umožňují definovat <xref:System.DateTimeOffset> hodnota založená na hodnotě jeho jednotlivých komponent data a času. Například následující kód používá tyto čtyři konstruktory k vytvoření instance <xref:System.DateTimeOffset> objekty s identické hodnoty 7/1/2008 12:05:00 + 01:00.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

Všimněte si, že, když hodnota <xref:System.DateTimeOffset> instance objektu pomocí <xref:System.Globalization.PersianCalendar> objekt jako jednoho z argumentů jeho konstruktoru je zobrazen na konzole, je vyjádřena jako datum ve Gregoriánském místo perského kalendáře. Výstupu data Perském kalendáři, podívejte se na příklad v <xref:System.Globalization.PersianCalendar> tématu.

Vytvořte další dva konstruktory <xref:System.DateTimeOffset> objektu z <xref:System.DateTime> hodnotu. První z nich má jeden parametr, <xref:System.DateTime> hodnotu převést <xref:System.DateTimeOffset> hodnotu. Posun výsledná <xref:System.DateTimeOffset> hodnota závisí na <xref:System.DateTime.Kind%2A> vlastnost jednoho parametru konstruktoru. Pokud je jeho hodnota <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, posun nastavena na hodnotu <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Její posun je nastaven, jinak hodnota stejně z místního časového pásma. Následující příklad ukazuje použití tento konstruktor pro vytvoření instance <xref:System.DateTimeOffset> objekty, které představují UTC a místní časové pásmo:

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> Volání přetížení <xref:System.DateTimeOffset> konstruktor, který má jeden <xref:System.DateTime> parametr je ekvivalentní k provádění implicitní převod <xref:System.DateTime> hodnotu <xref:System.DateTimeOffset> hodnotu.

Druhý konstruktor, který vytvoří <xref:System.DateTimeOffset> objektu z <xref:System.DateTime> hodnota má dva parametry: <xref:System.DateTime> hodnotu převést a <xref:System.TimeSpan> hodnotu představující datum a čas posun od času UTC. Tato hodnota posunu musí odpovídat <xref:System.DateTime.Kind%2A> vlastnost první parametr v konstruktoru nebo <xref:System.ArgumentException> je vyvolána výjimka. Pokud <xref:System.DateTime.Kind%2A> vlastnost první parametr je <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, musí být hodnota druhého parametru <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Pokud <xref:System.DateTime.Kind%2A> vlastnost první parametr je <xref:System.DateTimeKind.Local?displayProperty=nameWithType>, hodnota druhého parametru musí být posun časového pásma místního systému. Pokud <xref:System.DateTime.Kind%2A> vlastnost první parametr je <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, posun může být libovolná hodnota platná. Následující kód ukazuje volání do tohoto konstruktoru převést <xref:System.DateTime> k <xref:System.DateTimeOffset> hodnoty.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>Typ implicitní převod

<xref:System.DateTimeOffset> Typu podporuje jeden typ implicitní převod: z <xref:System.DateTime> hodnotu <xref:System.DateTimeOffset> hodnotu. (Typu implicitní převod je převod z jednoho typu do jiného, nevyžaduje explicitní přetypování (v jazyku C#) nebo převod (v jazyce Visual Basic) a který není dojít ke ztrátě informací. Umožňuje kód jako následující možné.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

Posun výsledná <xref:System.DateTimeOffset> hodnota závisí na <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> hodnotu vlastnosti. Pokud je jeho hodnota <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, posun nastavena na hodnotu <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Pokud je jeho hodnota může být buď <xref:System.DateTimeKind.Local?displayProperty=nameWithType> nebo <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, posun je nastavena na s místním časovém pásmu.

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>Analýza řetězcovou reprezentaci data a času

<xref:System.DateTimeOffset> Typ podporuje čtyři metody, které vám umožní převést řetězcovou reprezentaci datum a čas do <xref:System.DateTimeOffset> hodnotu:

* <xref:System.DateTimeOffset.Parse%2A>, která se pokusí převést řetězec představující datum a čas <xref:System.DateTimeOffset> hodnotu a vyvolá výjimku, pokud převod selže.

* <xref:System.DateTimeOffset.TryParse%2A>, která se pokusí převést řetězec představující datum a čas <xref:System.DateTimeOffset> hodnotu a vrátí `false` Pokud převod selže.

* <xref:System.DateTimeOffset.ParseExact%2A>, která se pokusí převést řetězcové vyjádření data a času v zadaném formátu do <xref:System.DateTimeOffset> hodnotu. Pokud převod selže, vyvolá metoda výjimku.

* <xref:System.DateTimeOffset.TryParseExact%2A>, která se pokusí převést řetězcové vyjádření data a času v zadaném formátu do <xref:System.DateTimeOffset> hodnotu. Vrátí metoda `false` Pokud převod selže.

Následující příklad ukazuje volání pro každé z těchto metod pro převod čtyři řetězec k vytváření instancí <xref:System.DateTimeOffset> hodnotu.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>Viz také

[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
