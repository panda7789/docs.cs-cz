---
title: Výčty
description: Další informace o použití F# výčty místo literály, aby byl kód čitelnější a udržovatelný.
ms.date: 05/16/2016
ms.openlocfilehash: a8839b73de074f62606b70ffe969a53b3db753bf
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611728"
---
# <a name="enumerations"></a><span data-ttu-id="68b6b-103">Výčty</span><span class="sxs-lookup"><span data-stu-id="68b6b-103">Enumerations</span></span>

<span data-ttu-id="68b6b-104">*Výčty*, označované také jako *výčty*,, jsou celočíselných typů, kde popisky jsou přiřazeny k podmnožině hodnoty.</span><span class="sxs-lookup"><span data-stu-id="68b6b-104">*Enumerations*, also known as *enums*, , are integral types where labels are assigned to a subset of the values.</span></span> <span data-ttu-id="68b6b-105">Můžete je použít místo literály aby byl kód čitelnější a udržovatelný.</span><span class="sxs-lookup"><span data-stu-id="68b6b-105">You can use them in place of literals to make code more readable and maintainable.</span></span>

## <a name="syntax"></a><span data-ttu-id="68b6b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68b6b-106">Syntax</span></span>

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a><span data-ttu-id="68b6b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="68b6b-107">Remarks</span></span>

<span data-ttu-id="68b6b-108">Výčet vypadá podobně jako diskriminované sjednocení, který má jednoduché hodnoty, s tím rozdílem, že můžete zadat hodnoty.</span><span class="sxs-lookup"><span data-stu-id="68b6b-108">An enumeration looks much like a discriminated union that has simple values, except that the values can be specified.</span></span> <span data-ttu-id="68b6b-109">Hodnoty jsou obvykle celých čísel, které začínají 0 nebo 1 nebo celých čísel představujících bitové pozice.</span><span class="sxs-lookup"><span data-stu-id="68b6b-109">The values are typically integers that start at 0 or 1, or integers that represent bit positions.</span></span> <span data-ttu-id="68b6b-110">Pokud výčet slouží k reprezentaci bitové pozice, měli byste také použít [příznaky](xref:System.FlagsAttribute) atribut.</span><span class="sxs-lookup"><span data-stu-id="68b6b-110">If an enumeration is intended to represent bit positions, you should also use the [Flags](xref:System.FlagsAttribute) attribute.</span></span>

<span data-ttu-id="68b6b-111">Základní typ výčtu je určen z literál, který se používá, takže například můžete použít literály s příponou, jako například `1u`, `2u`, a tak dále pro celé číslo bez znaménka (`uint32`) typu.</span><span class="sxs-lookup"><span data-stu-id="68b6b-111">The underlying type of the enumeration is determined from the literal that is used, so that, for example, you can use literals with a suffix, such as `1u`, `2u`, and so on, for an unsigned integer (`uint32`) type.</span></span>

<span data-ttu-id="68b6b-112">Při odkazování na pojmenované hodnoty, musíte použít název samotného typu výčtu jako kvalifikátoru, tedy `enum-name.value1`, nejen `value1`.</span><span class="sxs-lookup"><span data-stu-id="68b6b-112">When you refer to the named values, you must use the name of the enumeration type itself as a qualifier, that is, `enum-name.value1`, not just `value1`.</span></span> <span data-ttu-id="68b6b-113">Toto chování se liší od rozlišovaná sjednocení.</span><span class="sxs-lookup"><span data-stu-id="68b6b-113">This behavior differs from that of discriminated unions.</span></span> <span data-ttu-id="68b6b-114">Důvodem je, že výčty mají vždy [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) atribut.</span><span class="sxs-lookup"><span data-stu-id="68b6b-114">This is because enumerations always have the [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) attribute.</span></span>

<span data-ttu-id="68b6b-115">Následující kód ukazuje deklaraci a užívání výčet.</span><span class="sxs-lookup"><span data-stu-id="68b6b-115">The following code shows the declaration and use of an enumeration.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

<span data-ttu-id="68b6b-116">Jak je znázorněno v následujícím kódu, můžete snadno převést výčty pro základní typ pomocí příslušného operátoru.</span><span class="sxs-lookup"><span data-stu-id="68b6b-116">You can easily convert enumerations to the underlying type by using the appropriate operator, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

<span data-ttu-id="68b6b-117">Výčtové typy může mít jednu z následujících typů základní: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, a `char`.</span><span class="sxs-lookup"><span data-stu-id="68b6b-117">Enumerated types can have one of the following underlying types: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, and `char`.</span></span> <span data-ttu-id="68b6b-118">Typy výčtu jsou reprezentovány v rozhraní .NET Framework jako typy, které jsou zděděny z `System.Enum`, pak dědí se ze `System.ValueType`.</span><span class="sxs-lookup"><span data-stu-id="68b6b-118">Enumeration types are represented in the .NET Framework as types that are inherited from `System.Enum`, which in turn is inherited from `System.ValueType`.</span></span> <span data-ttu-id="68b6b-119">Proto jsou typy hodnot, které jsou umístěny na zásobník nebo vloženého do nadřazeného objektu a platná hodnota výčtu je libovolná hodnota základního typu.</span><span class="sxs-lookup"><span data-stu-id="68b6b-119">Thus, they are value types that are located on the stack or inline in the containing object, and any value of the underlying type is a valid value of the enumeration.</span></span> <span data-ttu-id="68b6b-120">To je důležité, když vzorec pro porovnávání na výčet hodnot, protože je nutné zadat vzor, který zachytává nepojmenovaných hodnot.</span><span class="sxs-lookup"><span data-stu-id="68b6b-120">This is significant when pattern matching on enumeration values, because you have to provide a pattern that catches the unnamed values.</span></span>

<span data-ttu-id="68b6b-121">`enum` Fungovat v F# knihovny lze použít ke generování hodnoty výčtu, dokonce i jiná hodnota než jeden z předdefinovaných, s názvem hodnoty.</span><span class="sxs-lookup"><span data-stu-id="68b6b-121">The `enum` function in the F# library can be used to generate an enumeration value, even a value other than one of the predefined, named values.</span></span> <span data-ttu-id="68b6b-122">Můžete použít `enum` funkce následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="68b6b-122">You use the `enum` function as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

<span data-ttu-id="68b6b-123">Výchozí hodnota `enum` funkce pracuje s typem `int32`.</span><span class="sxs-lookup"><span data-stu-id="68b6b-123">The default `enum` function works with type `int32`.</span></span> <span data-ttu-id="68b6b-124">Proto jej nelze použít s výčtové typy, které mají jiné základní typy.</span><span class="sxs-lookup"><span data-stu-id="68b6b-124">Therefore, it cannot be used with enumeration types that have other underlying types.</span></span> <span data-ttu-id="68b6b-125">Místo toho použijte následující.</span><span class="sxs-lookup"><span data-stu-id="68b6b-125">Instead, use the following.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

<span data-ttu-id="68b6b-126">Kromě toho případech pro výčty jsou vždy generované jako `public`.</span><span class="sxs-lookup"><span data-stu-id="68b6b-126">Additionally, cases for enums are always emitted as `public`.</span></span> <span data-ttu-id="68b6b-127">Je to tak, aby jejich zarovnání bylo pomocí C# a zbytek na platformě .NET.</span><span class="sxs-lookup"><span data-stu-id="68b6b-127">This is so that they align with C# and the rest of the .NET platform.</span></span>

## <a name="see-also"></a><span data-ttu-id="68b6b-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68b6b-128">See also</span></span>

- [<span data-ttu-id="68b6b-129">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="68b6b-129">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="68b6b-130">Přetypování a převody</span><span class="sxs-lookup"><span data-stu-id="68b6b-130">Casting and Conversions</span></span>](casting-and-conversions.md)