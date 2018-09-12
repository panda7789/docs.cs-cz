---
title: Výčtové typy (C# Programming Guide)
ms.date: 09/10/2017
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
ms.openlocfilehash: 3efedd48303c79bafde3704b0fdd6fcdd465a0a7
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44705541"
---
# <a name="enumeration-types-c-programming-guide"></a>Výčtové typy (C# Programming Guide)

Typ výčtu (také s názvem, výčet nebo výčet) poskytuje efektivní způsob, jak definovat sadu pojmenovaných integrálních konstant, které může být přiřazen proměnné. Předpokládejme například, že máte k definování proměnné, jejíž hodnota bude představovat den v týdnu. Existují pouze sedm smysluplné hodnoty, které někdy uloží danou proměnnou. Pokud chcete definovat tyto hodnoty, můžete použít typ výčtu, která je deklarována pomocí [výčtu](../../csharp/language-reference/keywords/enum.md) – klíčové slovo.

[!code-csharp[csProgGuideEnums#1](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#1)]

Ve výchozím nastavení je základní typ každý prvek ve výčtovém typu [int](../../csharp/language-reference/keywords/int.md). Můžete zadat jiný integrální číselný typ pomocí dvojtečky, jak je znázorněno v předchozím příkladu. Úplný seznam možných typů najdete v tématu [enum (referenční dokumentace jazyka C#)](../../csharp/language-reference/keywords/enum.md).

Základní číselné hodnoty můžete ověřit tak přetypování na základní typ, jak ukazuje následující příklad.

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

Následují výhody místo číselného typu výčtu:

- Jasně určili klientský kód, který hodnoty jsou platné pro proměnné.

- V sadě Visual Studio IntelliSense vypíše definovanými hodnotami.

Pokud nezadáte hodnoty pro elementy v seznam výčtu, hodnoty jsou automaticky zvýší o 1. V předchozím příkladu `Day.Sunday` má hodnotu 0, `Day.Monday` má hodnotu 1 a tak dále. Když vytvoříte nový `Day` objektu, bude mít výchozí hodnotu `Day.Sunday` (0) Pokud není explicitně ji přiřadíte hodnotu. Při vytváření výčtu, vyberte největší smysl výchozí hodnotu a přiřaďte jí hodnotu nula. Který způsobí, že všechny výčty mít tuto výchozí hodnotu, pokud jsou nejsou explicitně přiřazovat hodnota při jejich vytváření.

Pokud proměnná `meetingDay` je typu `Day`, pak (bez explicitního přetypování) pouze ji můžete přiřadit jednu z hodnot fronty definovaných podle `Day`. A pokud se změní denní schůzku můžete přiřadit nové hodnoty z `Day` k `meetingDay`:

[!code-csharp[csProgGuideEnums#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#4)]

> [!NOTE]
> Je možné přiřadit libovolné libovolné celé číslo k `meetingDay`. Například tento řádek kódu nevytvoří chybu: `meetingDay = (Day) 42`. By neměl to však provést, protože implicitní očekává se, že proměnná výčtu bude obsahovat pouze jednu z hodnot fronty definovaných ve výčtu. Přiřazení je libovolná hodnota proměnné typu výčtu je vám představit vysokým rizikem pro chyby.

Můžete přiřadit libovolné hodnoty prvků v seznamu výčtu výčtového typu, a můžete také použít počítané hodnoty:

[!code-csharp[csProgGuideEnums#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#3)]

## <a name="enumeration-types-as-bit-flags"></a>Výčtové typy jako bitové příznaky

Můžete použít typ výčtu pro definování bitových příznaků, umožňující instance typu výčtu pro uložení libovolnou kombinací hodnot, které jsou definovány v seznam výčtu. (Samozřejmě některé kombinace nemusí být smysluplné nebo povolených ve svém kódu programu.)

Vytvořit trochu výčet příznaků s použitím <xref:System.FlagsAttribute?displayProperty=nameWithType> atribut a odpovídajícím způsobem definování hodnoty tak, aby `AND`, `OR`, `NOT` a `XOR` bitové operace lze provádět s nimi. V trochu příznaků výčtu zahrnují pojmenované konstanty s hodnotou nula, která znamená, že "se nastavit žádné příznaky." Neudělujte příznak nulovou hodnotu Pokud neznamená "žádné příznaky se nastavují".

V následujícím příkladu, jinou verzi aplikace `Day` výčet, který se nazývá `Days`, je definován. `Days` má `Flags` atribut a každá hodnota se přiřadí další větší mocninu 2. To vám umožní vytvořit `Days` proměnnou, jejíž hodnota je `Days.Tuesday | Days.Thursday`.

[!code-csharp[csProgGuideEnums#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#2)]

Chcete-li nastavit příznak pro výčet, použijte bitový `OR` operátor, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideEnums#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#6)]

Pokud chcete zjistit, zda je konkrétní příznak nastaven, pomocí logické bitové `AND` operace, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideEnums#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#7)]

Další informace o tom, co vzít v úvahu při definování typů výčtu s <xref:System.FlagsAttribute?displayProperty=nameWithType> atributu naleznete v tématu <xref:System.Enum?displayProperty=nameWithType>.

## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a>Pomocí metod System.Enum ke zjištění a manipulaci s hodnotami výčtu.

Všechny výčty jsou instance <xref:System.Enum?displayProperty=nameWithType> typu. Nelze odvozovat nové třídy z <xref:System.Enum?displayProperty=nameWithType>, ale můžete použít metody a projděte si informace o manipulaci s hodnotami v instanci výčtu.

[!code-csharp[csProgGuideEnums#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#5)]

Další informace naleznete v tématu <xref:System.Enum?displayProperty=nameWithType>.

Můžete také vytvořit nové metody pro výčet pomocí metody rozšíření. Další informace najdete v tématu [postupy: vytvoření nové metody pro výčet](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).

## <a name="see-also"></a>Viz také

- <xref:System.Enum?displayProperty=nameWithType>  
- [Průvodce programováním v jazyce C#](../../csharp/programming-guide/index.md)  
- [enum](../../csharp/language-reference/keywords/enum.md)
