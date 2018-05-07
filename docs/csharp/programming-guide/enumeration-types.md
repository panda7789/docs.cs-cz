---
title: Výčtové typy (C# Průvodce programováním)
ms.date: 09/10/2017
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
ms.openlocfilehash: a97c3569899e7cf99dd522024de8373c60076571
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="enumeration-types-c-programming-guide"></a>Výčtové typy (C# Průvodce programováním)

Typ výčtu (i s názvem, výčet nebo výčtového) poskytuje účinný způsob, jak definovat sadu s názvem celočíselné konstanty, které může být přiřazený k proměnné. Předpokládejme například, že máte k definování proměnné, jehož hodnota bude reprezentovat den v týdnu. Nejsou k dispozici pouze sedm smysluplný hodnoty, které někdy uloží tuto proměnnou. Pokud chcete definovat tyto hodnoty, můžete použít typ výčtu, který je deklarovaný s použitím [výčtu](../../csharp/language-reference/keywords/enum.md) – klíčové slovo.

[!code-csharp[csProgGuideEnums#1](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#1)]

Ve výchozím nastavení je základní typ každý prvek v je výčet [int](../../csharp/language-reference/keywords/int.md). Můžete zadat jiný integrální číselný typ pomocí dvojtečky, jak je znázorněno v předchozím příkladu. Úplný seznam možných typů najdete v tématu [enum (referenční dokumentace jazyka C#)](../../csharp/language-reference/keywords/enum.md).

Přetypování na základní typ, jak ukazuje následující příklad můžete ověřit základní číselné hodnoty.

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

Následují výhody používání výčet místo číselného typu:

- Jasně zadejte hodnoty, které jsou platné pro proměnné kódu klienta.

- V sadě Visual Studio IntelliSense zobrazí seznam definovaných hodnot.

Pokud nezadáte hodnoty pro elementy v seznamu výčtu, hodnoty jsou automaticky zvýší o 1. V předchozím příkladu `Day.Sunday` má hodnotu 0, `Day.Monday` má hodnotu 1 a tak dále. Když vytvoříte novou `Day` objektu, bude mít výchozí hodnotu `Day.Sunday` (0), pokud nepřiřadíte explicitně jeho hodnotu. Při vytváření výčtu vyberte nejvíce logickou hodnotu výchozí a dejte mu hodnota nula. Které způsobí, že všechny výčty tak, aby měl tuto výchozí hodnotu, pokud jejich nejsou explicitně přiřazovat hodnota při jejich vytváření.

Pokud proměnná `meetingDay` je typu `Day`, pak (bez explicitní přetypování) můžete přiřadit jenom je jedna z hodnot definované `Day`. A pokud se změní den schůzky, můžete přiřadit nové hodnoty z `Day` k `meetingDay`:

[!code-csharp[csProgGuideEnums#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#4)]

> [!NOTE]
> Je možné přiřadit všechny libovolný celočíselnou hodnotu a `meetingDay`. Například tento řádek kódu nevytváří chybu: `meetingDay = (Day) 42`. Nesmí to však provést, protože implicitní očekává se, že proměnná výčtu bude obsahovat pouze jednu z hodnot výčtu definované. Přiřadit libovolná hodnota proměnné typ výčtu je zavedení vysoce rizikové chyby.

Můžete přiřadit hodnoty elementů v seznamu výčtu výčtového typu, a můžete také použít počítaný hodnoty:

[!code-csharp[csProgGuideEnums#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#3)]

## <a name="enumeration-types-as-bit-flags"></a>Výčtové typy jako bitové příznaky

Můžete typ výčtu k definování bitové příznaky, které umožňuje instanci typu výčtu ukládat libovolné kombinace hodnot, které jsou definované v seznamu enumerátor. (Samozřejmě některé kombinace nemusí být smysluplný nebo povolených v programovém kódu.)

Vytvořte trochu příznaky výčtu použitím <xref:System.FlagsAttribute?displayProperty=nameWithType> atribut a odpovídajícím způsobem definování hodnoty tak, aby `AND`, `OR`, `NOT` a `XOR` bitové operace můžete provádět s nimi. V trochu příznaky výčtu zahrnují pojmenované konstanta s hodnotou nula, tzn. "žádné příznaky se nastavují." Neudělujte příznak hodnotu nula. Pokud neznamená "žádné příznaky se nastavují".

V následujícím příkladu, jinou verzi aplikace `Day` výčtu, která se nazývá `Days`, je definovaný. `Days` má `Flags` další dosažení vyššího výkonu 2 je přiřazené atribut a každé hodnotě. To umožňuje vytvářet `Days` proměnné, jehož hodnota je `Days.Tuesday | Days.Thursday`.

[!code-csharp[csProgGuideEnums#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#2)]

Pokud chcete nastavit příznak na výčet, použijte bitové hodnotě `OR` operátor, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideEnums#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#6)]

Pokud chcete zjistit, zda je nastaven příznak konkrétní, použijte bitové `AND` operace, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideEnums#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#7)]

Další informace o tom, co když definujete výčtové typy s <xref:System.FlagsAttribute?displayProperty=nameWithType> atributů najdete v tématu <xref:System.Enum?displayProperty=nameWithType>.

## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a>Pomocí metod System.Enum ke zjištění a zpracování hodnot výčtu

Všechny výčty jsou instancemi třídy <xref:System.Enum?displayProperty=nameWithType> typu. Nelze odvodit nové třídy z <xref:System.Enum?displayProperty=nameWithType>, ale můžete použít její metody a zjistit informace o manipulaci s hodnotami v instanci výčtu.

[!code-csharp[csProgGuideEnums#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#5)]

Další informace naleznete v tématu <xref:System.Enum?displayProperty=nameWithType>.

Můžete také vytvoření nové metody pro výčet pomocí metody rozšíření. Další informace najdete v tématu [postupy: vytvoření nové metody pro výčet](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).

## <a name="see-also"></a>Viz také
 <xref:System.Enum?displayProperty=nameWithType>  
 [Průvodce programováním v jazyce C#](../../csharp/programming-guide/index.md)  
 [enum](../../csharp/language-reference/keywords/enum.md)
