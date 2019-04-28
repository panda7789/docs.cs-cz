---
title: enum – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: 768d8da320022a686f2ecfe5222880eccacee7dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661799"
---
# <a name="enum-c-reference"></a><span data-ttu-id="1ab29-102">enum (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="1ab29-102">enum (C# Reference)</span></span>

<span data-ttu-id="1ab29-103">`enum` – Klíčové slovo se používá k deklaraci výčtu, odlišný typ, který se skládá ze sady pojmenovaných konstant označovaného jako seznam výčtu.</span><span class="sxs-lookup"><span data-stu-id="1ab29-103">The `enum` keyword is used to declare an enumeration, a distinct type that consists of a set of named constants called the enumerator list.</span></span>  

<span data-ttu-id="1ab29-104">Obvykle je vhodné definovat výčet přímo v rámci oboru názvů tak, aby všechny třídy v oboru názvů můžete přistupovat pomocí stejné usnadnění.</span><span class="sxs-lookup"><span data-stu-id="1ab29-104">Usually it is best to define an enum directly within a namespace so that all classes in the namespace can access it with equal convenience.</span></span> <span data-ttu-id="1ab29-105">Výčet však také může být vnořena v rámci třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="1ab29-105">However, an enum can also be nested within a class or struct.</span></span>

<span data-ttu-id="1ab29-106">Ve výchozím nastavení první čítače mají hodnotu 0 a hodnotu každé po sobě jdoucích enumerátoru se zvýší o 1.</span><span class="sxs-lookup"><span data-stu-id="1ab29-106">By default, the first enumerator has the value 0, and the value of each successive enumerator is increased by 1.</span></span> <span data-ttu-id="1ab29-107">Například v následujícím výčet `Sat` je `0`, `Sun` je `1`, `Mon` je `2`a tak dále.</span><span class="sxs-lookup"><span data-stu-id="1ab29-107">For example, in the following enumeration, `Sat` is `0`, `Sun` is `1`, `Mon` is `2`, and so forth.</span></span>

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="1ab29-108">Enumerátory lze inicializátory přepsat výchozí hodnoty, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1ab29-108">Enumerators can use initializers to override the default values, as shown in the following example.</span></span>

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="1ab29-109">V tomto výčtu řadu prvků, musí spustit z `1` místo `0`.</span><span class="sxs-lookup"><span data-stu-id="1ab29-109">In this enumeration, the sequence of elements is forced to start from `1` instead of `0`.</span></span> <span data-ttu-id="1ab29-110">Nicméně se doporučuje včetně konstantu, která má hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="1ab29-110">However, including a constant that has the value of 0 is recommended.</span></span> <span data-ttu-id="1ab29-111">Další informace najdete v tématu [výčtové typy](../../programming-guide/enumeration-types.md).</span><span class="sxs-lookup"><span data-stu-id="1ab29-111">For more information, see [Enumeration Types](../../programming-guide/enumeration-types.md).</span></span>

<span data-ttu-id="1ab29-112">Každý typ výčtu se základní typ, který může být libovolný integrální typ kromě [char](char.md).</span><span class="sxs-lookup"><span data-stu-id="1ab29-112">Every enumeration type has an underlying type, which can be any integral type except [char](char.md).</span></span> <span data-ttu-id="1ab29-113">Výchozí základní typ výčtu prvků je [int](int.md). Chcete-li deklarovat výčet jiného celočíselného typu, například [bajtů](byte.md), použijte dvojtečku za identifikátorem a potom podle typu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1ab29-113">The default underlying type of enumeration elements is [int](int.md). To declare an enum of another integral type, such as [byte](byte.md), use a colon after the identifier followed by the type, as shown in the following example.</span></span>

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="1ab29-114">Seznam schválených typy výčtu [byte](byte.md), [sbyte](sbyte.md), [short](short.md), [ushort](ushort.md), [int](int.md), [uint](uint.md), [long](long.md), nebo [ulong](ulong.md).</span><span class="sxs-lookup"><span data-stu-id="1ab29-114">The approved types for an enum are [byte](byte.md), [sbyte](sbyte.md), [short](short.md), [ushort](ushort.md), [int](int.md), [uint](uint.md), [long](long.md), or [ulong](ulong.md).</span></span>

<span data-ttu-id="1ab29-115">Proměnná typu výčtu lze přiřadit jakoukoli hodnotu v rozsahu podkladový typ; hodnoty nejsou omezené na pojmenované konstanty.</span><span class="sxs-lookup"><span data-stu-id="1ab29-115">A variable of an enumeration type can be assigned any value in the range of the underlying type; the values are not limited to the named constants.</span></span>

<span data-ttu-id="1ab29-116">Výchozí hodnota `enum E` je hodnotu vytvořenou testovaným výraz `(E)0`.</span><span class="sxs-lookup"><span data-stu-id="1ab29-116">The default value of an `enum E` is the value produced by the expression `(E)0`.</span></span>

> [!NOTE]
> <span data-ttu-id="1ab29-117">Enumerátor nemůže obsahovat prázdné znaky v názvu.</span><span class="sxs-lookup"><span data-stu-id="1ab29-117">An enumerator cannot contain white space in its name.</span></span>

<span data-ttu-id="1ab29-118">Základní typ Určuje, kolik úložiště je alokováno pro každý čítač.</span><span class="sxs-lookup"><span data-stu-id="1ab29-118">The underlying type specifies how much storage is allocated for each enumerator.</span></span> <span data-ttu-id="1ab29-119">Explicitní přetypování je však potřeba převést z `enum` typ celočíselného typu.</span><span class="sxs-lookup"><span data-stu-id="1ab29-119">However, an explicit cast is necessary to convert from `enum` type to an integral type.</span></span> <span data-ttu-id="1ab29-120">Například následující příkaz přiřadí enumerátor `Sun` na proměnnou typu [int](int.md) pomocí přetypování pro převod z `enum` k `int`.</span><span class="sxs-lookup"><span data-stu-id="1ab29-120">For example, the following statement assigns the enumerator `Sun` to a variable of the type [int](int.md) by using a cast to convert from `enum` to `int`.</span></span>

```csharp
int x = (int)Day.Sun;
```

<span data-ttu-id="1ab29-121">Pokud použijete <xref:System.FlagsAttribute?displayProperty=nameWithType> na výčet, který obsahuje prvky, které můžete kombinovat pomocí logické bitové `OR` operaci, atribut má vliv na chování `enum` při jeho použití s některé nástroje.</span><span class="sxs-lookup"><span data-stu-id="1ab29-121">When you apply <xref:System.FlagsAttribute?displayProperty=nameWithType> to an enumeration that contains elements that can be combined with a bitwise `OR` operation, the attribute affects the behavior of the `enum` when it is used with some tools.</span></span> <span data-ttu-id="1ab29-122">Můžete si tyto změny při použití nástroje, jako <xref:System.Console> třídy, metody a vyhodnocovací filtr výrazů.</span><span class="sxs-lookup"><span data-stu-id="1ab29-122">You can notice these changes when you use tools such as the <xref:System.Console> class methods and the Expression Evaluator.</span></span> <span data-ttu-id="1ab29-123">(Viz třetí příklad).</span><span class="sxs-lookup"><span data-stu-id="1ab29-123">(See the third example.)</span></span>

## <a name="robust-programming"></a><span data-ttu-id="1ab29-124">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="1ab29-124">Robust programming</span></span>

<span data-ttu-id="1ab29-125">Stejně jako u libovolná konstanta se všechny odkazy na jednotlivé hodnoty výčtu převedou na číselné literály v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="1ab29-125">Just as with any constant, all references to the individual values of an enum are converted to numeric literals at compile time.</span></span> <span data-ttu-id="1ab29-126">To může způsobit potenciální problémy s verzí, jak je popsáno v [konstanty](../../programming-guide/classes-and-structs/constants.md).</span><span class="sxs-lookup"><span data-stu-id="1ab29-126">This can create potential versioning issues as described in [Constants](../../programming-guide/classes-and-structs/constants.md).</span></span>

<span data-ttu-id="1ab29-127">Další hodnoty přiřadit nové verze výčtů nebo změna hodnoty výčtu členů v nové verzi může způsobovat problémy pro závislé zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="1ab29-127">Assigning additional values to new versions of enums, or changing the values of the enum members in a new version, can cause problems for dependent source code.</span></span> <span data-ttu-id="1ab29-128">Hodnoty výčtu jsou často používány v [přepnout](switch.md) příkazy.</span><span class="sxs-lookup"><span data-stu-id="1ab29-128">Enum values often are used in [switch](switch.md) statements.</span></span> <span data-ttu-id="1ab29-129">Pokud další prvky byly přidány do `enum` neočekávaně lze vybrat typ, výchozí část příkazu switch.</span><span class="sxs-lookup"><span data-stu-id="1ab29-129">If additional elements have been added to the `enum` type, the default section of the switch statement can be selected unexpectedly.</span></span>

<span data-ttu-id="1ab29-130">Pokud ostatní vývojáři používat váš kód, byste měli poskytnout pokyny o jak svůj kód by měl reagovat při přidání nové prvky k libovolnému `enum` typy.</span><span class="sxs-lookup"><span data-stu-id="1ab29-130">If other developers use your code, you should provide guidelines about how their code should react if new elements are added to any `enum` types.</span></span>

## <a name="example"></a><span data-ttu-id="1ab29-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ab29-131">Example</span></span>

<span data-ttu-id="1ab29-132">V následujícím příkladu, výčtu, `Day`, je deklarována.</span><span class="sxs-lookup"><span data-stu-id="1ab29-132">In the following example, an enumeration, `Day`, is declared.</span></span> <span data-ttu-id="1ab29-133">Dva enumerátory jsou explicitně převést na celé číslo a přiřazeny celočíselné proměnné.</span><span class="sxs-lookup"><span data-stu-id="1ab29-133">Two enumerators are explicitly converted to integer and assigned to integer variables.</span></span>

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a><span data-ttu-id="1ab29-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ab29-134">Example</span></span>

<span data-ttu-id="1ab29-135">V následujícím příkladu se používá možnost Základní typ pro deklaraci `enum` jejíž členové jsou typu `long`.</span><span class="sxs-lookup"><span data-stu-id="1ab29-135">In the following example, the base-type option is used to declare an `enum` whose members are of type `long`.</span></span> <span data-ttu-id="1ab29-136">Všimněte si, že i když je základní typ výčtu `long`, členy výčtu stále musí být explicitně převeden na typ `long` pomocí přetypování.</span><span class="sxs-lookup"><span data-stu-id="1ab29-136">Notice that even though the underlying type of the enumeration is `long`, the enumeration members still must be explicitly converted to type `long` by using a cast.</span></span>

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a><span data-ttu-id="1ab29-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ab29-137">Example</span></span>

<span data-ttu-id="1ab29-138">Následující příklad kódu ukazuje použití a účinku <xref:System.FlagsAttribute?displayProperty=nameWithType> atribut na `enum` deklarace.</span><span class="sxs-lookup"><span data-stu-id="1ab29-138">The following code example illustrates the use and effect of the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute on an `enum` declaration.</span></span>

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a><span data-ttu-id="1ab29-139">Komentáře</span><span class="sxs-lookup"><span data-stu-id="1ab29-139">Comments</span></span>

<span data-ttu-id="1ab29-140">Pokud odeberete `Flags`, v příkladu se zobrazí následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="1ab29-140">If you remove `Flags`, the example displays the following values:</span></span>

`5`

`5`

## <a name="c-language-specification"></a><span data-ttu-id="1ab29-141">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1ab29-141">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1ab29-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ab29-142">See also</span></span>

- [<span data-ttu-id="1ab29-143">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1ab29-143">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1ab29-144">Výčtové typy</span><span class="sxs-lookup"><span data-stu-id="1ab29-144">Enumeration Types</span></span>](../../programming-guide/enumeration-types.md)
- [<span data-ttu-id="1ab29-145">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1ab29-145">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1ab29-146">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="1ab29-146">Integral Types Table</span></span>](integral-types-table.md)
- [<span data-ttu-id="1ab29-147">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="1ab29-147">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="1ab29-148">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="1ab29-148">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="1ab29-149">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="1ab29-149">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="1ab29-150">Zásady vytváření názvů výčtu</span><span class="sxs-lookup"><span data-stu-id="1ab29-150">Enum Naming Conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
