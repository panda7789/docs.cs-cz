---
title: Výčtové typy C# – Průvodce programováním
ms.custom: seodec18
ms.date: 09/10/2017
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
ms.openlocfilehash: 3573959a1e10b475a9867631767de5d10a08b9ea
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969763"
---
# <a name="enumeration-types-c-programming-guide"></a>Výčtové typyC# (Průvodce programováním)

Výčtový typ (také nazvaný výčet nebo Enum) poskytuje efektivní způsob, jak definovat sadu pojmenovaných integrálních konstant, které mohou být přiřazeny proměnné. Předpokládejme například, že je nutné definovat proměnnou, jejíž hodnota bude představovat den v týdnu. K dispozici je pouze sedm smysluplných hodnot, které tato proměnná bude nikdy ukládat. Pro definování těchto hodnot můžete použít typ výčtu, který je deklarován pomocí klíčového slova [Enum](../language-reference/keywords/enum.md) .

[!code-csharp[csProgGuideEnums#1](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#1)]

Ve výchozím nastavení je podkladový typ každého prvku ve výčtu [int](../language-reference/builtin-types/integral-numeric-types.md). Můžete zadat jiný integrální číselný typ pomocí dvojtečky, jak je znázorněno v předchozím příkladu. Úplný seznam možných typů naleznete v tématu [Enum (C# reference)](../language-reference/keywords/enum.md).

Můžete ověřit základní číselné hodnoty přetypováním na podkladový typ, jak ukazuje následující příklad.

```csharp
Day today = Day.Monday;
int dayNumber =(int)today;
Console.WriteLine("{0} is day number #{1}.", today, dayNumber);

Month thisMonth = Month.Dec;
byte monthNumber = (byte)thisMonth;
Console.WriteLine("{0} is month number #{1}.", thisMonth, monthNumber);

// Output:
// Monday is day number #1.
// Dec is month number #11.
```

Níže jsou uvedené výhody použití výčtu místo číselného typu:

- Pro kód klienta jasně určíte, které hodnoty jsou pro proměnnou platné.

- V aplikaci Visual Studio IntelliSense zobrazí seznam definovaných hodnot.

Pokud nezadáte hodnoty prvků v seznamu enumerátorů, hodnoty se automaticky zvýší o 1. V předchozím příkladu má `Day.Sunday` hodnotu 0, `Day.Monday` má hodnotu 1 a tak dále. Když vytvoříte nový objekt `Day`, bude mít výchozí hodnotu `Day.Sunday` (0), pokud explicitně nepřiřadíte hodnotu. Při vytváření výčtu vyberte nejvíce logické výchozí hodnoty a udělte jí hodnotu nula. Tím dojde k tomu, že všechny výčty mají tuto výchozí hodnotu, pokud při jejich vytváření explicitně nepřiřazuje hodnotu.

Pokud je proměnná `meetingDay` typu `Day`a pak (bez explicitního přetypování), můžete ji přiřadit pouze jedné z hodnot definovaných `Day`. A pokud se změní den schůzky, můžete přiřadit novou hodnotu z `Day` `meetingDay`:

[!code-csharp[csProgGuideEnums#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#4)]

> [!NOTE]
> K `meetingDay`je možné přiřadit libovolný celočíselnou hodnotu. Například tento řádek kódu nevytvoří chybu: `meetingDay = (Day) 42`. Nicméně to byste neměli dělat, protože implicitní očekáváme, že proměnná výčtu bude uchovávat jenom jednu z hodnot definovaných výčtem. Chcete-li přiřadit libovolnou hodnotu proměnné výčtového typu, je nutné zavést vysoké riziko pro chyby.

K prvkům v seznamu enumerátoru typu výčtu můžete přiřadit libovolné hodnoty a můžete také použít počítané hodnoty:

[!code-csharp[csProgGuideEnums#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#3)]

## <a name="enumeration-types-as-bit-flags"></a>Výčtové typy jako bitové příznaky

Můžete použít typ výčtu k definování bitových příznaků, které umožňují instanci výčtového typu ukládat libovolnou kombinaci hodnot, které jsou definovány v seznamu enumerátorů. (Samozřejmě některé kombinace nemusí být v kódu programu smysluplné nebo povolené.)

Vytvoříte výčet bitových příznaků použitím atributu <xref:System.FlagsAttribute?displayProperty=nameWithType> a patřičným definováním hodnot tak, aby bylo možné provést `AND`, `OR`, `NOT` a `XOR` bitové operace. V výčtu bitových příznaků zahrňte pojmenovanou konstantu s nulovou hodnotou, která znamená, že nejsou nastavené žádné příznaky. Neposkytněte příznak hodnotu nula, pokud to neznamená, že nejsou nastavené žádné příznaky.

V následujícím příkladu je definována jiná verze `Day` výčtu, která je pojmenována `Days`. `Days` má atribut `Flags` a každá hodnota je přiřazena dalších větší mocniny 2. To umožňuje vytvořit `Days` proměnnou, jejíž hodnota je `Days.Tuesday | Days.Thursday`.

[!code-csharp[csProgGuideEnums#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#2)]

Chcete-li nastavit příznak u výčtu, použijte operátor bitového `OR`, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideEnums#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#6)]

Chcete-li zjistit, zda je nastaven konkrétní příznak, použijte bitovou operaci `AND`, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideEnums#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#7)]

Další informace o tom, co je potřeba vzít v úvahu při definování výčtových typů s atributem <xref:System.FlagsAttribute?displayProperty=nameWithType>, naleznete v tématu <xref:System.Enum?displayProperty=nameWithType>.

## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a>Použití metod System. Enum ke zjišťování a manipulaci s hodnotami výčtu

Všechny výčty jsou instancemi <xref:System.Enum?displayProperty=nameWithType>ho typu. Nemůžete odvodit nové třídy z <xref:System.Enum?displayProperty=nameWithType>, ale můžete použít její metody ke zjištění informací o a manipulaci s hodnotami v instanci výčtu.

[!code-csharp[csProgGuideEnums#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#5)]

Další informace najdete v tématu <xref:System.Enum?displayProperty=nameWithType>.

Můžete také vytvořit novou metodu pro výčet pomocí metody rozšíření. Další informace najdete v tématu [Postup vytvoření nové metody pro výčet](./classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Enum?displayProperty=nameWithType>
- [Průvodce programováním v jazyce C#](./index.md)
- [enum](../language-reference/keywords/enum.md)
