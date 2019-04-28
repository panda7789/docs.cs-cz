---
title: Výčtové typy - C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 09/10/2017
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
ms.openlocfilehash: e34350e8f431b6ece95186147762d1954b5dd10f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61711171"
---
# <a name="enumeration-types-c-programming-guide"></a><span data-ttu-id="27c02-102">Výčtové typy (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="27c02-102">Enumeration types (C# Programming Guide)</span></span>

<span data-ttu-id="27c02-103">Typ výčtu (také s názvem, výčet nebo výčet) poskytuje efektivní způsob, jak definovat sadu pojmenovaných integrálních konstant, které může být přiřazen proměnné.</span><span class="sxs-lookup"><span data-stu-id="27c02-103">An enumeration type (also named an enumeration or an enum) provides an efficient way to define a set of named integral constants that may be assigned to a variable.</span></span> <span data-ttu-id="27c02-104">Předpokládejme například, že máte k definování proměnné, jejíž hodnota bude představovat den v týdnu.</span><span class="sxs-lookup"><span data-stu-id="27c02-104">For example, assume that you have to define a variable whose value will represent a day of the week.</span></span> <span data-ttu-id="27c02-105">Existují pouze sedm smysluplné hodnoty, které někdy uloží danou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="27c02-105">There are only seven meaningful values which that variable will ever store.</span></span> <span data-ttu-id="27c02-106">Pokud chcete definovat tyto hodnoty, můžete použít typ výčtu, která je deklarována pomocí [výčtu](../../csharp/language-reference/keywords/enum.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="27c02-106">To define those values, you can use an enumeration type, which is declared by using the [enum](../../csharp/language-reference/keywords/enum.md) keyword.</span></span>

[!code-csharp[csProgGuideEnums#1](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#1)]

<span data-ttu-id="27c02-107">Ve výchozím nastavení je základní typ každý prvek ve výčtovém typu [int](../../csharp/language-reference/keywords/int.md). Můžete zadat jiný integrální číselný typ pomocí dvojtečky, jak je znázorněno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="27c02-107">By default the underlying type of each element in the enum is [int](../../csharp/language-reference/keywords/int.md). You can specify another integral numeric type by using a colon, as shown in the previous example.</span></span> <span data-ttu-id="27c02-108">Úplný seznam možných typů najdete v tématu [enum (referenční dokumentace jazyka C#)](../../csharp/language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="27c02-108">For a full list of possible types, see [enum (C# Reference)](../../csharp/language-reference/keywords/enum.md).</span></span>

<span data-ttu-id="27c02-109">Základní číselné hodnoty můžete ověřit tak přetypování na základní typ, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="27c02-109">You can verify the underlying numeric values by casting  to the underlying type, as the following example shows.</span></span>

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

<span data-ttu-id="27c02-110">Následují výhody místo číselného typu výčtu:</span><span class="sxs-lookup"><span data-stu-id="27c02-110">The following are advantages of using an enum instead of a numeric type:</span></span>

- <span data-ttu-id="27c02-111">Jasně určili klientský kód, který hodnoty jsou platné pro proměnné.</span><span class="sxs-lookup"><span data-stu-id="27c02-111">You clearly specify for client code which values are valid for the variable.</span></span>

- <span data-ttu-id="27c02-112">V sadě Visual Studio IntelliSense vypíše definovanými hodnotami.</span><span class="sxs-lookup"><span data-stu-id="27c02-112">In Visual Studio, IntelliSense lists the defined values.</span></span>

<span data-ttu-id="27c02-113">Pokud nezadáte hodnoty pro elementy v seznam výčtu, hodnoty jsou automaticky zvýší o 1.</span><span class="sxs-lookup"><span data-stu-id="27c02-113">When you do not specify values for the elements in the enumerator list, the values are automatically incremented by 1.</span></span> <span data-ttu-id="27c02-114">V předchozím příkladu `Day.Sunday` má hodnotu 0, `Day.Monday` má hodnotu 1 a tak dále.</span><span class="sxs-lookup"><span data-stu-id="27c02-114">In the previous example, `Day.Sunday` has a value of 0, `Day.Monday` has a value of 1, and so on.</span></span> <span data-ttu-id="27c02-115">Když vytvoříte nový `Day` objektu, bude mít výchozí hodnotu `Day.Sunday` (0) Pokud není explicitně ji přiřadíte hodnotu.</span><span class="sxs-lookup"><span data-stu-id="27c02-115">When you create a new `Day` object, it will have a default value of `Day.Sunday` (0) if you do not explicitly assign it a value.</span></span> <span data-ttu-id="27c02-116">Při vytváření výčtu, vyberte největší smysl výchozí hodnotu a přiřaďte jí hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="27c02-116">When you create an enum, select the most logical default value and give it a value of zero.</span></span> <span data-ttu-id="27c02-117">Který způsobí, že všechny výčty mít tuto výchozí hodnotu, pokud jsou nejsou explicitně přiřazovat hodnota při jejich vytváření.</span><span class="sxs-lookup"><span data-stu-id="27c02-117">That will cause all enums to have that default value if they are not explicitly assigned a value when they are created.</span></span>

<span data-ttu-id="27c02-118">Pokud proměnná `meetingDay` je typu `Day`, pak (bez explicitního přetypování) pouze ji můžete přiřadit jednu z hodnot fronty definovaných podle `Day`.</span><span class="sxs-lookup"><span data-stu-id="27c02-118">If the variable `meetingDay` is of type `Day`, then (without an explicit cast) you can only assign it one of the values defined by `Day`.</span></span> <span data-ttu-id="27c02-119">A pokud se změní denní schůzku můžete přiřadit nové hodnoty z `Day` k `meetingDay`:</span><span class="sxs-lookup"><span data-stu-id="27c02-119">And if the meeting day changes, you can assign a new value from `Day` to `meetingDay`:</span></span>

[!code-csharp[csProgGuideEnums#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#4)]

> [!NOTE]
> <span data-ttu-id="27c02-120">Je možné přiřadit libovolné libovolné celé číslo k `meetingDay`.</span><span class="sxs-lookup"><span data-stu-id="27c02-120">It's possible to assign any arbitrary integer value to `meetingDay`.</span></span> <span data-ttu-id="27c02-121">Například tento řádek kódu nevytvoří chybu: `meetingDay = (Day) 42`.</span><span class="sxs-lookup"><span data-stu-id="27c02-121">For example, this line of code does not produce an error: `meetingDay = (Day) 42`.</span></span> <span data-ttu-id="27c02-122">By neměl to však provést, protože implicitní očekává se, že proměnná výčtu bude obsahovat pouze jednu z hodnot fronty definovaných ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="27c02-122">However, you should not do this because the implicit expectation is that an enum variable will only hold one of the values defined by the enum.</span></span> <span data-ttu-id="27c02-123">Přiřazení je libovolná hodnota proměnné typu výčtu je vám představit vysokým rizikem pro chyby.</span><span class="sxs-lookup"><span data-stu-id="27c02-123">To assign an arbitrary value to a variable of an enumeration type is to introduce a high risk for errors.</span></span>

<span data-ttu-id="27c02-124">Můžete přiřadit libovolné hodnoty prvků v seznamu výčtu výčtového typu, a můžete také použít počítané hodnoty:</span><span class="sxs-lookup"><span data-stu-id="27c02-124">You can assign any values to the elements in the enumerator list of an enumeration type, and you can also use computed values:</span></span>

[!code-csharp[csProgGuideEnums#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#3)]

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="27c02-125">Výčtové typy jako bitové příznaky</span><span class="sxs-lookup"><span data-stu-id="27c02-125">Enumeration types as bit flags</span></span>

<span data-ttu-id="27c02-126">Můžete použít typ výčtu pro definování bitových příznaků, umožňující instance typu výčtu pro uložení libovolnou kombinací hodnot, které jsou definovány v seznam výčtu.</span><span class="sxs-lookup"><span data-stu-id="27c02-126">You can use an enumeration type to define bit flags, which enables an instance of the enumeration type to store any combination of the values that are defined in the enumerator list.</span></span> <span data-ttu-id="27c02-127">(Samozřejmě některé kombinace nemusí být smysluplné nebo povolených ve svém kódu programu.)</span><span class="sxs-lookup"><span data-stu-id="27c02-127">(Of course, some combinations may not be meaningful or allowed in your program code.)</span></span>

<span data-ttu-id="27c02-128">Vytvořit trochu výčet příznaků s použitím <xref:System.FlagsAttribute?displayProperty=nameWithType> atribut a odpovídajícím způsobem definování hodnoty tak, aby `AND`, `OR`, `NOT` a `XOR` bitové operace lze provádět s nimi.</span><span class="sxs-lookup"><span data-stu-id="27c02-128">You create a bit flags enum by applying the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute and defining the values appropriately so that `AND`, `OR`, `NOT` and `XOR` bitwise operations can be performed on them.</span></span> <span data-ttu-id="27c02-129">V trochu příznaků výčtu zahrnují pojmenované konstanty s hodnotou nula, která znamená, že "se nastavit žádné příznaky."</span><span class="sxs-lookup"><span data-stu-id="27c02-129">In a bit flags enum, include a named constant with a value of zero that means "no flags are set."</span></span> <span data-ttu-id="27c02-130">Neudělujte příznak nulovou hodnotu Pokud neznamená "žádné příznaky se nastavují".</span><span class="sxs-lookup"><span data-stu-id="27c02-130">Do not give a flag a value of zero if it does not mean "no flags are set".</span></span>

<span data-ttu-id="27c02-131">V následujícím příkladu, jinou verzi aplikace `Day` výčet, který se nazývá `Days`, je definován.</span><span class="sxs-lookup"><span data-stu-id="27c02-131">In the following example, another version of the `Day` enum, which is named `Days`, is defined.</span></span> <span data-ttu-id="27c02-132">`Days` má `Flags` atribut a každá hodnota se přiřadí další větší mocninu 2.</span><span class="sxs-lookup"><span data-stu-id="27c02-132">`Days` has the `Flags` attribute, and each value is assigned the next greater power of 2.</span></span> <span data-ttu-id="27c02-133">To vám umožní vytvořit `Days` proměnnou, jejíž hodnota je `Days.Tuesday | Days.Thursday`.</span><span class="sxs-lookup"><span data-stu-id="27c02-133">This enables you to create a `Days` variable whose value is `Days.Tuesday | Days.Thursday`.</span></span>

[!code-csharp[csProgGuideEnums#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#2)]

<span data-ttu-id="27c02-134">Chcete-li nastavit příznak pro výčet, použijte bitový `OR` operátor, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="27c02-134">To set a flag on an enum, use the bitwise `OR` operator as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#6)]

<span data-ttu-id="27c02-135">Pokud chcete zjistit, zda je konkrétní příznak nastaven, pomocí logické bitové `AND` operace, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="27c02-135">To determine whether a specific flag is set, use a bitwise `AND` operation, as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#7)]

<span data-ttu-id="27c02-136">Další informace o tom, co vzít v úvahu při definování typů výčtu s <xref:System.FlagsAttribute?displayProperty=nameWithType> atributu naleznete v tématu <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="27c02-136">For more information about what to consider when you define enumeration types with the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a><span data-ttu-id="27c02-137">Pomocí metod System.Enum ke zjištění a manipulaci s hodnotami výčtu.</span><span class="sxs-lookup"><span data-stu-id="27c02-137">Using the System.Enum methods to discover and manipulate enum values</span></span>

<span data-ttu-id="27c02-138">Všechny výčty jsou instance <xref:System.Enum?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="27c02-138">All enums are instances of the <xref:System.Enum?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="27c02-139">Nelze odvozovat nové třídy z <xref:System.Enum?displayProperty=nameWithType>, ale můžete použít metody a projděte si informace o manipulaci s hodnotami v instanci výčtu.</span><span class="sxs-lookup"><span data-stu-id="27c02-139">You cannot derive new classes from <xref:System.Enum?displayProperty=nameWithType>, but you can use its methods to discover information about and manipulate values in an enum instance.</span></span>

[!code-csharp[csProgGuideEnums#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#5)]

<span data-ttu-id="27c02-140">Další informace naleznete v tématu <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="27c02-140">For more information, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="27c02-141">Můžete také vytvořit nové metody pro výčet pomocí metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="27c02-141">You can also create a new method for an enum by using an extension method.</span></span> <span data-ttu-id="27c02-142">Další informace najdete v tématu [jak: Vytvoření nové metody pro výčet](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="27c02-142">For more information, see [How to: Create a New Method for an Enumeration](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="27c02-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27c02-143">See also</span></span>

- <xref:System.Enum?displayProperty=nameWithType>
- [<span data-ttu-id="27c02-144">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="27c02-144">C# Programming Guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="27c02-145">enum</span><span class="sxs-lookup"><span data-stu-id="27c02-145">enum</span></span>](../../csharp/language-reference/keywords/enum.md)
