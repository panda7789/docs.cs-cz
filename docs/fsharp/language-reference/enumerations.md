---
title: Výčty
description: Naučte se používat F# výčty namísto literálů, aby bylo možné čitelnější a udržovatelnější kód.
ms.date: 05/16/2016
ms.openlocfilehash: 784cd9612b199e4648bb64432d3b4422ad35f649
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630347"
---
# <a name="enumerations"></a><span data-ttu-id="14e81-103">Výčty</span><span class="sxs-lookup"><span data-stu-id="14e81-103">Enumerations</span></span>

<span data-ttu-id="14e81-104">*Výčty*, označované takéjako výčty, představují celočíselné typy, kde jsou popisky přiřazeny podmnožině hodnot.</span><span class="sxs-lookup"><span data-stu-id="14e81-104">*Enumerations*, also known as *enums*, , are integral types where labels are assigned to a subset of the values.</span></span> <span data-ttu-id="14e81-105">Můžete je použít místo literálů, aby bylo možné čitelnější a udržovatelnější kód.</span><span class="sxs-lookup"><span data-stu-id="14e81-105">You can use them in place of literals to make code more readable and maintainable.</span></span>

## <a name="syntax"></a><span data-ttu-id="14e81-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14e81-106">Syntax</span></span>

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a><span data-ttu-id="14e81-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14e81-107">Remarks</span></span>

<span data-ttu-id="14e81-108">Výčet vypadá podobně jako rozlišené sjednocení, které má jednoduché hodnoty, s výjimkou toho, že je možné zadat hodnoty.</span><span class="sxs-lookup"><span data-stu-id="14e81-108">An enumeration looks much like a discriminated union that has simple values, except that the values can be specified.</span></span> <span data-ttu-id="14e81-109">Hodnoty jsou obvykle celá čísla, která začínají na 0 nebo 1 nebo celá čísla, která představují bitové pozice.</span><span class="sxs-lookup"><span data-stu-id="14e81-109">The values are typically integers that start at 0 or 1, or integers that represent bit positions.</span></span> <span data-ttu-id="14e81-110">Pokud je výčet určen pro reprezentace bitových pozic, měli byste také použít atribut [Flags](xref:System.FlagsAttribute) .</span><span class="sxs-lookup"><span data-stu-id="14e81-110">If an enumeration is intended to represent bit positions, you should also use the [Flags](xref:System.FlagsAttribute) attribute.</span></span>

<span data-ttu-id="14e81-111">Podkladový typ výčtu je určen z literálu, který je použit, takže lze například použít literály s příponou, například `1u`, `2u`a tak dále, pro typ unsigned integer (`uint32`).</span><span class="sxs-lookup"><span data-stu-id="14e81-111">The underlying type of the enumeration is determined from the literal that is used, so that, for example, you can use literals with a suffix, such as `1u`, `2u`, and so on, for an unsigned integer (`uint32`) type.</span></span>

<span data-ttu-id="14e81-112">Když odkazujete na pojmenované hodnoty, je nutné použít název vlastního typu výčtu jako kvalifikátor, to znamená `enum-name.value1`, ne pouze. `value1`</span><span class="sxs-lookup"><span data-stu-id="14e81-112">When you refer to the named values, you must use the name of the enumeration type itself as a qualifier, that is, `enum-name.value1`, not just `value1`.</span></span> <span data-ttu-id="14e81-113">Toto chování se liší od v případě rozlišených sjednocení.</span><span class="sxs-lookup"><span data-stu-id="14e81-113">This behavior differs from that of discriminated unions.</span></span> <span data-ttu-id="14e81-114">Je to proto, že výčty mají vždy atribut [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) .</span><span class="sxs-lookup"><span data-stu-id="14e81-114">This is because enumerations always have the [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) attribute.</span></span>

<span data-ttu-id="14e81-115">Následující kód ukazuje deklaraci a použití výčtu.</span><span class="sxs-lookup"><span data-stu-id="14e81-115">The following code shows the declaration and use of an enumeration.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

<span data-ttu-id="14e81-116">Výčty lze snadno převést na podkladový typ pomocí příslušného operátoru, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="14e81-116">You can easily convert enumerations to the underlying type by using the appropriate operator, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

<span data-ttu-id="14e81-117">`sbyte`Výčtové typy mohou mít jeden z následujících základních typů:, `uint16` `uint32` `int64` `uint16` `int16` `byte`, `int32` ,,`uint64`,,,, a. `char`</span><span class="sxs-lookup"><span data-stu-id="14e81-117">Enumerated types can have one of the following underlying types: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, and `char`.</span></span> <span data-ttu-id="14e81-118">Výčtové typy jsou reprezentovány v .NET Framework jako typy, které `System.Enum`jsou zděděny z, který je `System.ValueType`zase zděděn z.</span><span class="sxs-lookup"><span data-stu-id="14e81-118">Enumeration types are represented in the .NET Framework as types that are inherited from `System.Enum`, which in turn is inherited from `System.ValueType`.</span></span> <span data-ttu-id="14e81-119">Proto jsou typy hodnot, které jsou umístěny v zásobníku nebo vloženy do obsahujícího objektu, a libovolná hodnota základního typu je platná hodnota výčtu.</span><span class="sxs-lookup"><span data-stu-id="14e81-119">Thus, they are value types that are located on the stack or inline in the containing object, and any value of the underlying type is a valid value of the enumeration.</span></span> <span data-ttu-id="14e81-120">To je důležité v případě porovnávání vzorů s hodnotami výčtu, protože je nutné zadat vzor, který zachytává nepojmenované hodnoty.</span><span class="sxs-lookup"><span data-stu-id="14e81-120">This is significant when pattern matching on enumeration values, because you have to provide a pattern that catches the unnamed values.</span></span>

<span data-ttu-id="14e81-121">Funkce v F# knihovně může být použita k vygenerování hodnoty výčtu, dokonce i jiné hodnoty než jedné z předdefinovaných pojmenovaných hodnot. `enum`</span><span class="sxs-lookup"><span data-stu-id="14e81-121">The `enum` function in the F# library can be used to generate an enumeration value, even a value other than one of the predefined, named values.</span></span> <span data-ttu-id="14e81-122">`enum` Funkci použijete následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="14e81-122">You use the `enum` function as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

<span data-ttu-id="14e81-123">Výchozí `enum` funkce funguje s typem `int32`.</span><span class="sxs-lookup"><span data-stu-id="14e81-123">The default `enum` function works with type `int32`.</span></span> <span data-ttu-id="14e81-124">Proto jej nelze použít s výčtovým typem, které mají jiné základní typy.</span><span class="sxs-lookup"><span data-stu-id="14e81-124">Therefore, it cannot be used with enumeration types that have other underlying types.</span></span> <span data-ttu-id="14e81-125">Místo toho použijte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="14e81-125">Instead, use the following.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

<span data-ttu-id="14e81-126">Kromě toho jsou případy vydaných výčty vždy `public`generovány jako.</span><span class="sxs-lookup"><span data-stu-id="14e81-126">Additionally, cases for enums are always emitted as `public`.</span></span> <span data-ttu-id="14e81-127">To je tak, že se zarovnají s C# a zbytkem platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="14e81-127">This is so that they align with C# and the rest of the .NET platform.</span></span>

## <a name="see-also"></a><span data-ttu-id="14e81-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14e81-128">See also</span></span>

- [<span data-ttu-id="14e81-129">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="14e81-129">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="14e81-130">Přetypování a převody</span><span class="sxs-lookup"><span data-stu-id="14e81-130">Casting and Conversions</span></span>](casting-and-conversions.md)
