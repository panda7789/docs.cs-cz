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
ms.locfileid: "33339050"
---
# <a name="enumeration-types-c-programming-guide"></a><span data-ttu-id="83ee8-102">Výčtové typy (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="83ee8-102">Enumeration types (C# Programming Guide)</span></span>

<span data-ttu-id="83ee8-103">Typ výčtu (i s názvem, výčet nebo výčtového) poskytuje účinný způsob, jak definovat sadu s názvem celočíselné konstanty, které může být přiřazený k proměnné.</span><span class="sxs-lookup"><span data-stu-id="83ee8-103">An enumeration type (also named an enumeration or an enum) provides an efficient way to define a set of named integral constants that may be assigned to a variable.</span></span> <span data-ttu-id="83ee8-104">Předpokládejme například, že máte k definování proměnné, jehož hodnota bude reprezentovat den v týdnu.</span><span class="sxs-lookup"><span data-stu-id="83ee8-104">For example, assume that you have to define a variable whose value will represent a day of the week.</span></span> <span data-ttu-id="83ee8-105">Nejsou k dispozici pouze sedm smysluplný hodnoty, které někdy uloží tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="83ee8-105">There are only seven meaningful values which that variable will ever store.</span></span> <span data-ttu-id="83ee8-106">Pokud chcete definovat tyto hodnoty, můžete použít typ výčtu, který je deklarovaný s použitím [výčtu](../../csharp/language-reference/keywords/enum.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="83ee8-106">To define those values, you can use an enumeration type, which is declared by using the [enum](../../csharp/language-reference/keywords/enum.md) keyword.</span></span>

[!code-csharp[csProgGuideEnums#1](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#1)]

<span data-ttu-id="83ee8-107">Ve výchozím nastavení je základní typ každý prvek v je výčet [int](../../csharp/language-reference/keywords/int.md). Můžete zadat jiný integrální číselný typ pomocí dvojtečky, jak je znázorněno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="83ee8-107">By default the underlying type of each element in the enum is [int](../../csharp/language-reference/keywords/int.md). You can specify another integral numeric type by using a colon, as shown in the previous example.</span></span> <span data-ttu-id="83ee8-108">Úplný seznam možných typů najdete v tématu [enum (referenční dokumentace jazyka C#)](../../csharp/language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="83ee8-108">For a full list of possible types, see [enum (C# Reference)](../../csharp/language-reference/keywords/enum.md).</span></span>

<span data-ttu-id="83ee8-109">Přetypování na základní typ, jak ukazuje následující příklad můžete ověřit základní číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="83ee8-109">You can verify the underlying numeric values by casting  to the underlying type, as the following example shows.</span></span>

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

<span data-ttu-id="83ee8-110">Následují výhody používání výčet místo číselného typu:</span><span class="sxs-lookup"><span data-stu-id="83ee8-110">The following are advantages of using an enum instead of a numeric type:</span></span>

- <span data-ttu-id="83ee8-111">Jasně zadejte hodnoty, které jsou platné pro proměnné kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="83ee8-111">You clearly specify for client code which values are valid for the variable.</span></span>

- <span data-ttu-id="83ee8-112">V sadě Visual Studio IntelliSense zobrazí seznam definovaných hodnot.</span><span class="sxs-lookup"><span data-stu-id="83ee8-112">In Visual Studio, IntelliSense lists the defined values.</span></span>

<span data-ttu-id="83ee8-113">Pokud nezadáte hodnoty pro elementy v seznamu výčtu, hodnoty jsou automaticky zvýší o 1.</span><span class="sxs-lookup"><span data-stu-id="83ee8-113">When you do not specify values for the elements in the enumerator list, the values are automatically incremented by 1.</span></span> <span data-ttu-id="83ee8-114">V předchozím příkladu `Day.Sunday` má hodnotu 0, `Day.Monday` má hodnotu 1 a tak dále.</span><span class="sxs-lookup"><span data-stu-id="83ee8-114">In the previous example, `Day.Sunday` has a value of 0, `Day.Monday` has a value of 1, and so on.</span></span> <span data-ttu-id="83ee8-115">Když vytvoříte novou `Day` objektu, bude mít výchozí hodnotu `Day.Sunday` (0), pokud nepřiřadíte explicitně jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="83ee8-115">When you create a new `Day` object, it will have a default value of `Day.Sunday` (0) if you do not explicitly assign it a value.</span></span> <span data-ttu-id="83ee8-116">Při vytváření výčtu vyberte nejvíce logickou hodnotu výchozí a dejte mu hodnota nula.</span><span class="sxs-lookup"><span data-stu-id="83ee8-116">When you create an enum, select the most logical default value and give it a value of zero.</span></span> <span data-ttu-id="83ee8-117">Které způsobí, že všechny výčty tak, aby měl tuto výchozí hodnotu, pokud jejich nejsou explicitně přiřazovat hodnota při jejich vytváření.</span><span class="sxs-lookup"><span data-stu-id="83ee8-117">That will cause all enums to have that default value if they are not explicitly assigned a value when they are created.</span></span>

<span data-ttu-id="83ee8-118">Pokud proměnná `meetingDay` je typu `Day`, pak (bez explicitní přetypování) můžete přiřadit jenom je jedna z hodnot definované `Day`.</span><span class="sxs-lookup"><span data-stu-id="83ee8-118">If the variable `meetingDay` is of type `Day`, then (without an explicit cast) you can only assign it one of the values defined by `Day`.</span></span> <span data-ttu-id="83ee8-119">A pokud se změní den schůzky, můžete přiřadit nové hodnoty z `Day` k `meetingDay`:</span><span class="sxs-lookup"><span data-stu-id="83ee8-119">And if the meeting day changes, you can assign a new value from `Day` to `meetingDay`:</span></span>

[!code-csharp[csProgGuideEnums#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#4)]

> [!NOTE]
> <span data-ttu-id="83ee8-120">Je možné přiřadit všechny libovolný celočíselnou hodnotu a `meetingDay`.</span><span class="sxs-lookup"><span data-stu-id="83ee8-120">It's possible to assign any arbitrary integer value to `meetingDay`.</span></span> <span data-ttu-id="83ee8-121">Například tento řádek kódu nevytváří chybu: `meetingDay = (Day) 42`.</span><span class="sxs-lookup"><span data-stu-id="83ee8-121">For example, this line of code does not produce an error: `meetingDay = (Day) 42`.</span></span> <span data-ttu-id="83ee8-122">Nesmí to však provést, protože implicitní očekává se, že proměnná výčtu bude obsahovat pouze jednu z hodnot výčtu definované.</span><span class="sxs-lookup"><span data-stu-id="83ee8-122">However, you should not do this because the implicit expectation is that an enum variable will only hold one of the values defined by the enum.</span></span> <span data-ttu-id="83ee8-123">Přiřadit libovolná hodnota proměnné typ výčtu je zavedení vysoce rizikové chyby.</span><span class="sxs-lookup"><span data-stu-id="83ee8-123">To assign an arbitrary value to a variable of an enumeration type is to introduce a high risk for errors.</span></span>

<span data-ttu-id="83ee8-124">Můžete přiřadit hodnoty elementů v seznamu výčtu výčtového typu, a můžete také použít počítaný hodnoty:</span><span class="sxs-lookup"><span data-stu-id="83ee8-124">You can assign any values to the elements in the enumerator list of an enumeration type, and you can also use computed values:</span></span>

[!code-csharp[csProgGuideEnums#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#3)]

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="83ee8-125">Výčtové typy jako bitové příznaky</span><span class="sxs-lookup"><span data-stu-id="83ee8-125">Enumeration types as bit flags</span></span>

<span data-ttu-id="83ee8-126">Můžete typ výčtu k definování bitové příznaky, které umožňuje instanci typu výčtu ukládat libovolné kombinace hodnot, které jsou definované v seznamu enumerátor.</span><span class="sxs-lookup"><span data-stu-id="83ee8-126">You can use an enumeration type to define bit flags, which enables an instance of the enumeration type to store any combination of the values that are defined in the enumerator list.</span></span> <span data-ttu-id="83ee8-127">(Samozřejmě některé kombinace nemusí být smysluplný nebo povolených v programovém kódu.)</span><span class="sxs-lookup"><span data-stu-id="83ee8-127">(Of course, some combinations may not be meaningful or allowed in your program code.)</span></span>

<span data-ttu-id="83ee8-128">Vytvořte trochu příznaky výčtu použitím <xref:System.FlagsAttribute?displayProperty=nameWithType> atribut a odpovídajícím způsobem definování hodnoty tak, aby `AND`, `OR`, `NOT` a `XOR` bitové operace můžete provádět s nimi.</span><span class="sxs-lookup"><span data-stu-id="83ee8-128">You create a bit flags enum by applying the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute and defining the values appropriately so that `AND`, `OR`, `NOT` and `XOR` bitwise operations can be performed on them.</span></span> <span data-ttu-id="83ee8-129">V trochu příznaky výčtu zahrnují pojmenované konstanta s hodnotou nula, tzn. "žádné příznaky se nastavují."</span><span class="sxs-lookup"><span data-stu-id="83ee8-129">In a bit flags enum, include a named constant with a value of zero that means "no flags are set."</span></span> <span data-ttu-id="83ee8-130">Neudělujte příznak hodnotu nula. Pokud neznamená "žádné příznaky se nastavují".</span><span class="sxs-lookup"><span data-stu-id="83ee8-130">Do not give a flag a value of zero if it does not mean "no flags are set".</span></span>

<span data-ttu-id="83ee8-131">V následujícím příkladu, jinou verzi aplikace `Day` výčtu, která se nazývá `Days`, je definovaný.</span><span class="sxs-lookup"><span data-stu-id="83ee8-131">In the following example, another version of the `Day` enum, which is named `Days`, is defined.</span></span> <span data-ttu-id="83ee8-132">`Days` má `Flags` další dosažení vyššího výkonu 2 je přiřazené atribut a každé hodnotě.</span><span class="sxs-lookup"><span data-stu-id="83ee8-132">`Days` has the `Flags` attribute, and each value is assigned the next greater power of 2.</span></span> <span data-ttu-id="83ee8-133">To umožňuje vytvářet `Days` proměnné, jehož hodnota je `Days.Tuesday | Days.Thursday`.</span><span class="sxs-lookup"><span data-stu-id="83ee8-133">This enables you to create a `Days` variable whose value is `Days.Tuesday | Days.Thursday`.</span></span>

[!code-csharp[csProgGuideEnums#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#2)]

<span data-ttu-id="83ee8-134">Pokud chcete nastavit příznak na výčet, použijte bitové hodnotě `OR` operátor, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="83ee8-134">To set a flag on an enum, use the bitwise `OR` operator as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#6)]

<span data-ttu-id="83ee8-135">Pokud chcete zjistit, zda je nastaven příznak konkrétní, použijte bitové `AND` operace, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="83ee8-135">To determine whether a specific flag is set, use a bitwise `AND` operation, as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#7)]

<span data-ttu-id="83ee8-136">Další informace o tom, co když definujete výčtové typy s <xref:System.FlagsAttribute?displayProperty=nameWithType> atributů najdete v tématu <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="83ee8-136">For more information about what to consider when you define enumeration types with the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a><span data-ttu-id="83ee8-137">Pomocí metod System.Enum ke zjištění a zpracování hodnot výčtu</span><span class="sxs-lookup"><span data-stu-id="83ee8-137">Using the System.Enum methods to discover and manipulate enum values</span></span>

<span data-ttu-id="83ee8-138">Všechny výčty jsou instancemi třídy <xref:System.Enum?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="83ee8-138">All enums are instances of the <xref:System.Enum?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="83ee8-139">Nelze odvodit nové třídy z <xref:System.Enum?displayProperty=nameWithType>, ale můžete použít její metody a zjistit informace o manipulaci s hodnotami v instanci výčtu.</span><span class="sxs-lookup"><span data-stu-id="83ee8-139">You cannot derive new classes from <xref:System.Enum?displayProperty=nameWithType>, but you can use its methods to discover information about and manipulate values in an enum instance.</span></span>

[!code-csharp[csProgGuideEnums#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#5)]

<span data-ttu-id="83ee8-140">Další informace naleznete v tématu <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="83ee8-140">For more information, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="83ee8-141">Můžete také vytvoření nové metody pro výčet pomocí metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="83ee8-141">You can also create a new method for an enum by using an extension method.</span></span> <span data-ttu-id="83ee8-142">Další informace najdete v tématu [postupy: vytvoření nové metody pro výčet](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="83ee8-142">For more information, see [How to: Create a New Method for an Enumeration](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="83ee8-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="83ee8-143">See also</span></span>
 <xref:System.Enum?displayProperty=nameWithType>  
 [<span data-ttu-id="83ee8-144">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="83ee8-144">C# Programming Guide</span></span>](../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="83ee8-145">enum</span><span class="sxs-lookup"><span data-stu-id="83ee8-145">enum</span></span>](../../csharp/language-reference/keywords/enum.md)
