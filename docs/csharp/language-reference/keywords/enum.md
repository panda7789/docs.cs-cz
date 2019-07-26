---
title: Enum – klíčové C# slovo – Reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: e33877d2a5e79866bbef12cd9fec5cb11b044240
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433873"
---
# <a name="enum-c-reference"></a><span data-ttu-id="eed2b-102">enum (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="eed2b-102">enum (C# Reference)</span></span>

<span data-ttu-id="eed2b-103">`enum` Klíčové slovo se používá k deklaraci výčtu, odlišného typu, který se skládá ze sady pojmenovaných konstant označované jako seznam enumerátorů.</span><span class="sxs-lookup"><span data-stu-id="eed2b-103">The `enum` keyword is used to declare an enumeration, a distinct type that consists of a set of named constants called the enumerator list.</span></span>

<span data-ttu-id="eed2b-104">Obvykle je vhodné definovat výčet přímo v rámci oboru názvů tak, aby všechny třídy v oboru názvů měly přístup k tomuto rozhraní s rovností pohodlí.</span><span class="sxs-lookup"><span data-stu-id="eed2b-104">Usually it is best to define an enum directly within a namespace so that all classes in the namespace can access it with equal convenience.</span></span> <span data-ttu-id="eed2b-105">Výčty ale mohou být také vnořené v rámci třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="eed2b-105">However, an enum can also be nested within a class or struct.</span></span>

<span data-ttu-id="eed2b-106">Ve výchozím nastavení má první enumerátor hodnotu 0 a hodnota každého úspěšného enumerátoru se zvýší o 1.</span><span class="sxs-lookup"><span data-stu-id="eed2b-106">By default, the first enumerator has the value 0, and the value of each successive enumerator is increased by 1.</span></span> <span data-ttu-id="eed2b-107">Například v následujícím výčtu `Sat` je `0`, `Sun` `1`je ,atakdále.`Mon` `2`</span><span class="sxs-lookup"><span data-stu-id="eed2b-107">For example, in the following enumeration, `Sat` is `0`, `Sun` is `1`, `Mon` is `2`, and so forth.</span></span>

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="eed2b-108">Enumerátory mohou použít inicializátory k přepsání výchozích hodnot, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="eed2b-108">Enumerators can use initializers to override the default values, as shown in the following example.</span></span>

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="eed2b-109">V tomto výčtu je sekvence prvků nucená začít od `1` `0`místo.</span><span class="sxs-lookup"><span data-stu-id="eed2b-109">In this enumeration, the sequence of elements is forced to start from `1` instead of `0`.</span></span> <span data-ttu-id="eed2b-110">Nicméně, včetně konstanty, která má hodnotu 0, je doporučeno.</span><span class="sxs-lookup"><span data-stu-id="eed2b-110">However, including a constant that has the value of 0 is recommended.</span></span> <span data-ttu-id="eed2b-111">Další informace naleznete v tématu [výčtové typy](../../programming-guide/enumeration-types.md).</span><span class="sxs-lookup"><span data-stu-id="eed2b-111">For more information, see [Enumeration Types](../../programming-guide/enumeration-types.md).</span></span>

<span data-ttu-id="eed2b-112">Každý typ výčtu má podkladový typ, který může být libovolný [celočíselný numerický typ](../builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="eed2b-112">Every enumeration type has an underlying type, which can be any [integral numeric type](../builtin-types/integral-numeric-types.md).</span></span> <span data-ttu-id="eed2b-113">Typ [znaku](char.md) nemůže být základní typ výčtu.</span><span class="sxs-lookup"><span data-stu-id="eed2b-113">The [char](char.md) type cannot be an underlying type of an enum.</span></span> <span data-ttu-id="eed2b-114">Výchozí podkladový typ prvků výčtu je [int](../builtin-types/integral-numeric-types.md). Chcete-li deklarovat výčet jiného integrálního typu, jako je například [Byte](../builtin-types/integral-numeric-types.md), použijte dvojtečku za identifikátor následovaný typem, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="eed2b-114">The default underlying type of enumeration elements is [int](../builtin-types/integral-numeric-types.md). To declare an enum of another integral type, such as [byte](../builtin-types/integral-numeric-types.md), use a colon after the identifier followed by the type, as shown in the following example.</span></span>

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="eed2b-115">Proměnné typu výčtu lze přiřadit libovolnou hodnotu v rozsahu základního typu; hodnoty nejsou omezeny na pojmenované konstanty.</span><span class="sxs-lookup"><span data-stu-id="eed2b-115">A variable of an enumeration type can be assigned any value in the range of the underlying type; the values are not limited to the named constants.</span></span>

<span data-ttu-id="eed2b-116">Výchozí hodnota `enum E` je hodnota vytvořená výrazem `(E)0`.</span><span class="sxs-lookup"><span data-stu-id="eed2b-116">The default value of an `enum E` is the value produced by the expression `(E)0`.</span></span>

> [!NOTE]
> <span data-ttu-id="eed2b-117">Enumerátor nemůže v názvu obsahovat prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="eed2b-117">An enumerator cannot contain white space in its name.</span></span>

<span data-ttu-id="eed2b-118">Nadřízený typ Určuje, kolik úložiště je přiděleno pro každý enumerátor.</span><span class="sxs-lookup"><span data-stu-id="eed2b-118">The underlying type specifies how much storage is allocated for each enumerator.</span></span> <span data-ttu-id="eed2b-119">Nicméně explicitní přetypování je nezbytné pro převod `enum` typu na celočíselný typ.</span><span class="sxs-lookup"><span data-stu-id="eed2b-119">However, an explicit cast is necessary to convert from `enum` type to an integral type.</span></span> <span data-ttu-id="eed2b-120">Například následující `Sun` příkaz přiřadí enumerátor proměnné typu [int](../builtin-types/integral-numeric-types.md) pomocí přetypování pro převod z `enum` na. `int`</span><span class="sxs-lookup"><span data-stu-id="eed2b-120">For example, the following statement assigns the enumerator `Sun` to a variable of the type [int](../builtin-types/integral-numeric-types.md) by using a cast to convert from `enum` to `int`.</span></span>

```csharp
int x = (int)Day.Sun;
```

<span data-ttu-id="eed2b-121">Když použijete <xref:System.FlagsAttribute?displayProperty=nameWithType> na výčet, který obsahuje prvky, které mohou být kombinovány s `OR` bitovou operací, atribut `enum` má vliv na chování při použití s některými nástroji.</span><span class="sxs-lookup"><span data-stu-id="eed2b-121">When you apply <xref:System.FlagsAttribute?displayProperty=nameWithType> to an enumeration that contains elements that can be combined with a bitwise `OR` operation, the attribute affects the behavior of the `enum` when it is used with some tools.</span></span> <span data-ttu-id="eed2b-122">Tyto změny si můžete všimnout, když použijete nástroje, jako <xref:System.Console> jsou metody třídy a vyhodnocovací filtr výrazů.</span><span class="sxs-lookup"><span data-stu-id="eed2b-122">You can notice these changes when you use tools such as the <xref:System.Console> class methods and the Expression Evaluator.</span></span> <span data-ttu-id="eed2b-123">(Viz třetí příklad.)</span><span class="sxs-lookup"><span data-stu-id="eed2b-123">(See the third example.)</span></span>

## <a name="robust-programming"></a><span data-ttu-id="eed2b-124">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="eed2b-124">Robust programming</span></span>

<span data-ttu-id="eed2b-125">Stejně jako u jakékoli konstanty jsou všechny odkazy na jednotlivé hodnoty výčtu převedeny na číselné literály v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="eed2b-125">Just as with any constant, all references to the individual values of an enum are converted to numeric literals at compile time.</span></span> <span data-ttu-id="eed2b-126">To může způsobit problémy se správou verzí, jak [](../../programming-guide/classes-and-structs/constants.md)je popsáno v konstantách.</span><span class="sxs-lookup"><span data-stu-id="eed2b-126">This can create potential versioning issues as described in [Constants](../../programming-guide/classes-and-structs/constants.md).</span></span>

<span data-ttu-id="eed2b-127">Přiřazení dalších hodnot novým verzím výčtů nebo změna hodnot členů výčtu v nové verzi může způsobit problémy závislého zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="eed2b-127">Assigning additional values to new versions of enums, or changing the values of the enum members in a new version, can cause problems for dependent source code.</span></span> <span data-ttu-id="eed2b-128">Hodnoty výčtu jsou často používány v příkazech [Switch](switch.md) .</span><span class="sxs-lookup"><span data-stu-id="eed2b-128">Enum values often are used in [switch](switch.md) statements.</span></span> <span data-ttu-id="eed2b-129">Pokud byly do `enum` typu přidány další prvky, lze výchozí oddíl příkazu switch vybrat neočekávaně.</span><span class="sxs-lookup"><span data-stu-id="eed2b-129">If additional elements have been added to the `enum` type, the default section of the switch statement can be selected unexpectedly.</span></span>

<span data-ttu-id="eed2b-130">Pokud jiný vývojář používá váš kód, měli byste poskytnout pokyny, jak by měl kód reagovat, pokud jsou přidány nové prvky do `enum` libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="eed2b-130">If other developers use your code, you should provide guidelines about how their code should react if new elements are added to any `enum` types.</span></span>

## <a name="example"></a><span data-ttu-id="eed2b-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="eed2b-131">Example</span></span>

<span data-ttu-id="eed2b-132">V následujícím příkladu je deklarován výčet `Day`,.</span><span class="sxs-lookup"><span data-stu-id="eed2b-132">In the following example, an enumeration, `Day`, is declared.</span></span> <span data-ttu-id="eed2b-133">Dva enumerátory jsou explicitně převedeny na celé číslo a přiřazeny celočíselným proměnným.</span><span class="sxs-lookup"><span data-stu-id="eed2b-133">Two enumerators are explicitly converted to integer and assigned to integer variables.</span></span>

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a><span data-ttu-id="eed2b-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="eed2b-134">Example</span></span>

<span data-ttu-id="eed2b-135">V následujícím příkladu je použita možnost základního typu k deklaraci `enum` , jejichž členové jsou typu. `long`</span><span class="sxs-lookup"><span data-stu-id="eed2b-135">In the following example, the base-type option is used to declare an `enum` whose members are of type `long`.</span></span> <span data-ttu-id="eed2b-136">Všimněte si, že i když je `long`podkladový typ výčtu, musí být členy výčtu stále explicitně převedeny na typ `long` pomocí přetypování.</span><span class="sxs-lookup"><span data-stu-id="eed2b-136">Notice that even though the underlying type of the enumeration is `long`, the enumeration members still must be explicitly converted to type `long` by using a cast.</span></span>

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a><span data-ttu-id="eed2b-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="eed2b-137">Example</span></span>

<span data-ttu-id="eed2b-138">Následující příklad kódu ukazuje použití a účinek <xref:System.FlagsAttribute?displayProperty=nameWithType> atributu `enum` deklarace.</span><span class="sxs-lookup"><span data-stu-id="eed2b-138">The following code example illustrates the use and effect of the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute on an `enum` declaration.</span></span>

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a><span data-ttu-id="eed2b-139">Komentáře</span><span class="sxs-lookup"><span data-stu-id="eed2b-139">Comments</span></span>

<span data-ttu-id="eed2b-140">Pokud odeberete `Flags`, v příkladu se zobrazí následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="eed2b-140">If you remove `Flags`, the example displays the following values:</span></span>

`5`

`5`

## <a name="c-language-specification"></a><span data-ttu-id="eed2b-141">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="eed2b-141">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="eed2b-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eed2b-142">See also</span></span>

- [<span data-ttu-id="eed2b-143">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="eed2b-143">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="eed2b-144">Výčtové typy</span><span class="sxs-lookup"><span data-stu-id="eed2b-144">Enumeration Types</span></span>](../../programming-guide/enumeration-types.md)
- [<span data-ttu-id="eed2b-145">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="eed2b-145">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="eed2b-146">Celočíselné typy</span><span class="sxs-lookup"><span data-stu-id="eed2b-146">Integral types</span></span>](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="eed2b-147">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="eed2b-147">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="eed2b-148">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="eed2b-148">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="eed2b-149">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="eed2b-149">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="eed2b-150">Zásady vytváření názvů výčtu</span><span class="sxs-lookup"><span data-stu-id="eed2b-150">Enum Naming Conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
