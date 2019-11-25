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
# <a name="enumeration-types-c-programming-guide"></a><span data-ttu-id="58458-102">Výčtové typyC# (Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="58458-102">Enumeration types (C# Programming Guide)</span></span>

<span data-ttu-id="58458-103">Výčtový typ (také nazvaný výčet nebo Enum) poskytuje efektivní způsob, jak definovat sadu pojmenovaných integrálních konstant, které mohou být přiřazeny proměnné.</span><span class="sxs-lookup"><span data-stu-id="58458-103">An enumeration type (also named an enumeration or an enum) provides an efficient way to define a set of named integral constants that may be assigned to a variable.</span></span> <span data-ttu-id="58458-104">Předpokládejme například, že je nutné definovat proměnnou, jejíž hodnota bude představovat den v týdnu.</span><span class="sxs-lookup"><span data-stu-id="58458-104">For example, assume that you have to define a variable whose value will represent a day of the week.</span></span> <span data-ttu-id="58458-105">K dispozici je pouze sedm smysluplných hodnot, které tato proměnná bude nikdy ukládat.</span><span class="sxs-lookup"><span data-stu-id="58458-105">There are only seven meaningful values which that variable will ever store.</span></span> <span data-ttu-id="58458-106">Pro definování těchto hodnot můžete použít typ výčtu, který je deklarován pomocí klíčového slova [Enum](../language-reference/keywords/enum.md) .</span><span class="sxs-lookup"><span data-stu-id="58458-106">To define those values, you can use an enumeration type, which is declared by using the [enum](../language-reference/keywords/enum.md) keyword.</span></span>

[!code-csharp[csProgGuideEnums#1](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#1)]

<span data-ttu-id="58458-107">Ve výchozím nastavení je podkladový typ každého prvku ve výčtu [int](../language-reference/builtin-types/integral-numeric-types.md). Můžete zadat jiný integrální číselný typ pomocí dvojtečky, jak je znázorněno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="58458-107">By default the underlying type of each element in the enum is [int](../language-reference/builtin-types/integral-numeric-types.md). You can specify another integral numeric type by using a colon, as shown in the previous example.</span></span> <span data-ttu-id="58458-108">Úplný seznam možných typů naleznete v tématu [Enum (C# reference)](../language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="58458-108">For a full list of possible types, see [enum (C# Reference)](../language-reference/keywords/enum.md).</span></span>

<span data-ttu-id="58458-109">Můžete ověřit základní číselné hodnoty přetypováním na podkladový typ, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="58458-109">You can verify the underlying numeric values by casting  to the underlying type, as the following example shows.</span></span>

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

<span data-ttu-id="58458-110">Níže jsou uvedené výhody použití výčtu místo číselného typu:</span><span class="sxs-lookup"><span data-stu-id="58458-110">The following are advantages of using an enum instead of a numeric type:</span></span>

- <span data-ttu-id="58458-111">Pro kód klienta jasně určíte, které hodnoty jsou pro proměnnou platné.</span><span class="sxs-lookup"><span data-stu-id="58458-111">You clearly specify for client code which values are valid for the variable.</span></span>

- <span data-ttu-id="58458-112">V aplikaci Visual Studio IntelliSense zobrazí seznam definovaných hodnot.</span><span class="sxs-lookup"><span data-stu-id="58458-112">In Visual Studio, IntelliSense lists the defined values.</span></span>

<span data-ttu-id="58458-113">Pokud nezadáte hodnoty prvků v seznamu enumerátorů, hodnoty se automaticky zvýší o 1.</span><span class="sxs-lookup"><span data-stu-id="58458-113">When you do not specify values for the elements in the enumerator list, the values are automatically incremented by 1.</span></span> <span data-ttu-id="58458-114">V předchozím příkladu má `Day.Sunday` hodnotu 0, `Day.Monday` má hodnotu 1 a tak dále.</span><span class="sxs-lookup"><span data-stu-id="58458-114">In the previous example, `Day.Sunday` has a value of 0, `Day.Monday` has a value of 1, and so on.</span></span> <span data-ttu-id="58458-115">Když vytvoříte nový objekt `Day`, bude mít výchozí hodnotu `Day.Sunday` (0), pokud explicitně nepřiřadíte hodnotu.</span><span class="sxs-lookup"><span data-stu-id="58458-115">When you create a new `Day` object, it will have a default value of `Day.Sunday` (0) if you do not explicitly assign it a value.</span></span> <span data-ttu-id="58458-116">Při vytváření výčtu vyberte nejvíce logické výchozí hodnoty a udělte jí hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="58458-116">When you create an enum, select the most logical default value and give it a value of zero.</span></span> <span data-ttu-id="58458-117">Tím dojde k tomu, že všechny výčty mají tuto výchozí hodnotu, pokud při jejich vytváření explicitně nepřiřazuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="58458-117">That will cause all enums to have that default value if they are not explicitly assigned a value when they are created.</span></span>

<span data-ttu-id="58458-118">Pokud je proměnná `meetingDay` typu `Day`a pak (bez explicitního přetypování), můžete ji přiřadit pouze jedné z hodnot definovaných `Day`.</span><span class="sxs-lookup"><span data-stu-id="58458-118">If the variable `meetingDay` is of type `Day`, then (without an explicit cast) you can only assign it one of the values defined by `Day`.</span></span> <span data-ttu-id="58458-119">A pokud se změní den schůzky, můžete přiřadit novou hodnotu z `Day` `meetingDay`:</span><span class="sxs-lookup"><span data-stu-id="58458-119">And if the meeting day changes, you can assign a new value from `Day` to `meetingDay`:</span></span>

[!code-csharp[csProgGuideEnums#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#4)]

> [!NOTE]
> <span data-ttu-id="58458-120">K `meetingDay`je možné přiřadit libovolný celočíselnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="58458-120">It's possible to assign any arbitrary integer value to `meetingDay`.</span></span> <span data-ttu-id="58458-121">Například tento řádek kódu nevytvoří chybu: `meetingDay = (Day) 42`.</span><span class="sxs-lookup"><span data-stu-id="58458-121">For example, this line of code does not produce an error: `meetingDay = (Day) 42`.</span></span> <span data-ttu-id="58458-122">Nicméně to byste neměli dělat, protože implicitní očekáváme, že proměnná výčtu bude uchovávat jenom jednu z hodnot definovaných výčtem.</span><span class="sxs-lookup"><span data-stu-id="58458-122">However, you should not do this because the implicit expectation is that an enum variable will only hold one of the values defined by the enum.</span></span> <span data-ttu-id="58458-123">Chcete-li přiřadit libovolnou hodnotu proměnné výčtového typu, je nutné zavést vysoké riziko pro chyby.</span><span class="sxs-lookup"><span data-stu-id="58458-123">To assign an arbitrary value to a variable of an enumeration type is to introduce a high risk for errors.</span></span>

<span data-ttu-id="58458-124">K prvkům v seznamu enumerátoru typu výčtu můžete přiřadit libovolné hodnoty a můžete také použít počítané hodnoty:</span><span class="sxs-lookup"><span data-stu-id="58458-124">You can assign any values to the elements in the enumerator list of an enumeration type, and you can also use computed values:</span></span>

[!code-csharp[csProgGuideEnums#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#3)]

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="58458-125">Výčtové typy jako bitové příznaky</span><span class="sxs-lookup"><span data-stu-id="58458-125">Enumeration types as bit flags</span></span>

<span data-ttu-id="58458-126">Můžete použít typ výčtu k definování bitových příznaků, které umožňují instanci výčtového typu ukládat libovolnou kombinaci hodnot, které jsou definovány v seznamu enumerátorů.</span><span class="sxs-lookup"><span data-stu-id="58458-126">You can use an enumeration type to define bit flags, which enables an instance of the enumeration type to store any combination of the values that are defined in the enumerator list.</span></span> <span data-ttu-id="58458-127">(Samozřejmě některé kombinace nemusí být v kódu programu smysluplné nebo povolené.)</span><span class="sxs-lookup"><span data-stu-id="58458-127">(Of course, some combinations may not be meaningful or allowed in your program code.)</span></span>

<span data-ttu-id="58458-128">Vytvoříte výčet bitových příznaků použitím atributu <xref:System.FlagsAttribute?displayProperty=nameWithType> a patřičným definováním hodnot tak, aby bylo možné provést `AND`, `OR`, `NOT` a `XOR` bitové operace.</span><span class="sxs-lookup"><span data-stu-id="58458-128">You create a bit flags enum by applying the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute and defining the values appropriately so that `AND`, `OR`, `NOT` and `XOR` bitwise operations can be performed on them.</span></span> <span data-ttu-id="58458-129">V výčtu bitových příznaků zahrňte pojmenovanou konstantu s nulovou hodnotou, která znamená, že nejsou nastavené žádné příznaky.</span><span class="sxs-lookup"><span data-stu-id="58458-129">In a bit flags enum, include a named constant with a value of zero that means "no flags are set."</span></span> <span data-ttu-id="58458-130">Neposkytněte příznak hodnotu nula, pokud to neznamená, že nejsou nastavené žádné příznaky.</span><span class="sxs-lookup"><span data-stu-id="58458-130">Do not give a flag a value of zero if it does not mean "no flags are set".</span></span>

<span data-ttu-id="58458-131">V následujícím příkladu je definována jiná verze `Day` výčtu, která je pojmenována `Days`.</span><span class="sxs-lookup"><span data-stu-id="58458-131">In the following example, another version of the `Day` enum, which is named `Days`, is defined.</span></span> <span data-ttu-id="58458-132">`Days` má atribut `Flags` a každá hodnota je přiřazena dalších větší mocniny 2.</span><span class="sxs-lookup"><span data-stu-id="58458-132">`Days` has the `Flags` attribute, and each value is assigned the next greater power of 2.</span></span> <span data-ttu-id="58458-133">To umožňuje vytvořit `Days` proměnnou, jejíž hodnota je `Days.Tuesday | Days.Thursday`.</span><span class="sxs-lookup"><span data-stu-id="58458-133">This enables you to create a `Days` variable whose value is `Days.Tuesday | Days.Thursday`.</span></span>

[!code-csharp[csProgGuideEnums#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#2)]

<span data-ttu-id="58458-134">Chcete-li nastavit příznak u výčtu, použijte operátor bitového `OR`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="58458-134">To set a flag on an enum, use the bitwise `OR` operator as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#6)]

<span data-ttu-id="58458-135">Chcete-li zjistit, zda je nastaven konkrétní příznak, použijte bitovou operaci `AND`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="58458-135">To determine whether a specific flag is set, use a bitwise `AND` operation, as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#7)]

<span data-ttu-id="58458-136">Další informace o tom, co je potřeba vzít v úvahu při definování výčtových typů s atributem <xref:System.FlagsAttribute?displayProperty=nameWithType>, naleznete v tématu <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="58458-136">For more information about what to consider when you define enumeration types with the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a><span data-ttu-id="58458-137">Použití metod System. Enum ke zjišťování a manipulaci s hodnotami výčtu</span><span class="sxs-lookup"><span data-stu-id="58458-137">Using the System.Enum methods to discover and manipulate enum values</span></span>

<span data-ttu-id="58458-138">Všechny výčty jsou instancemi <xref:System.Enum?displayProperty=nameWithType>ho typu.</span><span class="sxs-lookup"><span data-stu-id="58458-138">All enums are instances of the <xref:System.Enum?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="58458-139">Nemůžete odvodit nové třídy z <xref:System.Enum?displayProperty=nameWithType>, ale můžete použít její metody ke zjištění informací o a manipulaci s hodnotami v instanci výčtu.</span><span class="sxs-lookup"><span data-stu-id="58458-139">You cannot derive new classes from <xref:System.Enum?displayProperty=nameWithType>, but you can use its methods to discover information about and manipulate values in an enum instance.</span></span>

[!code-csharp[csProgGuideEnums#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#5)]

<span data-ttu-id="58458-140">Další informace najdete v tématu <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="58458-140">For more information, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="58458-141">Můžete také vytvořit novou metodu pro výčet pomocí metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="58458-141">You can also create a new method for an enum by using an extension method.</span></span> <span data-ttu-id="58458-142">Další informace najdete v tématu [Postup vytvoření nové metody pro výčet](./classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="58458-142">For more information, see [How to create a new method for an enumeration](./classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="58458-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58458-143">See also</span></span>

- <xref:System.Enum?displayProperty=nameWithType>
- [<span data-ttu-id="58458-144">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="58458-144">C# Programming Guide</span></span>](./index.md)
- [<span data-ttu-id="58458-145">enum</span><span class="sxs-lookup"><span data-stu-id="58458-145">enum</span></span>](../language-reference/keywords/enum.md)
