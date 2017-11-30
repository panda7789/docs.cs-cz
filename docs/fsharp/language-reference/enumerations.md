---
title: "Výčty (F#)"
description: "Další informace o použití výčty F # místo literály, aby váš kód více čitelný a udržovatelný."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9272bf5a-9a9f-4314-9e34-a3248e5244f5
ms.openlocfilehash: de0273900b707c99e6fb1bcc84e5c2b9ef2bc725
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="enumerations"></a><span data-ttu-id="60d7a-104">Výčty</span><span class="sxs-lookup"><span data-stu-id="60d7a-104">Enumerations</span></span>

<span data-ttu-id="60d7a-105">*Výčty*, také známé jako *výčty*,, jsou celočíselné typy, kde se popisky přiřazené k podmnožině hodnoty.</span><span class="sxs-lookup"><span data-stu-id="60d7a-105">*Enumerations*, also known as *enums*, , are integral types where labels are assigned to a subset of the values.</span></span> <span data-ttu-id="60d7a-106">Můžete je používat místo literály, aby kód víc čitelný a udržovatelný.</span><span class="sxs-lookup"><span data-stu-id="60d7a-106">You can use them in place of literals to make code more readable and maintainable.</span></span>


## <a name="syntax"></a><span data-ttu-id="60d7a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60d7a-107">Syntax</span></span>

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a><span data-ttu-id="60d7a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="60d7a-108">Remarks</span></span>
<span data-ttu-id="60d7a-109">Výčet vypadá podobně jako rozlišovaná sjednocení, která má jednoduché hodnoty, s tím rozdílem, že lze zadat hodnoty.</span><span class="sxs-lookup"><span data-stu-id="60d7a-109">An enumeration looks much like a discriminated union that has simple values, except that the values can be specified.</span></span> <span data-ttu-id="60d7a-110">Hodnoty jsou obvykle celá čísla, které začínají 0 nebo 1 nebo celá čísla, které představují bit pozic.</span><span class="sxs-lookup"><span data-stu-id="60d7a-110">The values are typically integers that start at 0 or 1, or integers that represent bit positions.</span></span> <span data-ttu-id="60d7a-111">Pokud výčet slouží k reprezentaci pozic bit, byste měli použít také [příznaky](xref:System.FlagsAttribute) atribut.</span><span class="sxs-lookup"><span data-stu-id="60d7a-111">If an enumeration is intended to represent bit positions, you should also use the [Flags](xref:System.FlagsAttribute) attribute.</span></span>

<span data-ttu-id="60d7a-112">Základní typ výčtu je určit literál, který se používá, takže například můžete použít literály s příponou, jako například `1u`, `2u`a tak dále pro celé číslo bez znaménka (`uint32`) typu.</span><span class="sxs-lookup"><span data-stu-id="60d7a-112">The underlying type of the enumeration is determined from the literal that is used, so that, for example, you can use literals with a suffix, such as `1u`, `2u`, and so on, for an unsigned integer (`uint32`) type.</span></span>

<span data-ttu-id="60d7a-113">Když odkazujete na pojmenovaných hodnot, musíte použít název typu výčtu sám sebe jako kvalifikátor, který je `enum-name.value1`, ne jenom `value1`.</span><span class="sxs-lookup"><span data-stu-id="60d7a-113">When you refer to the named values, you must use the name of the enumeration type itself as a qualifier, that is, `enum-name.value1`, not just `value1`.</span></span> <span data-ttu-id="60d7a-114">Toto chování se liší od rozlišovaná sjednocení.</span><span class="sxs-lookup"><span data-stu-id="60d7a-114">This behavior differs from that of discriminated unions.</span></span> <span data-ttu-id="60d7a-115">Důvodem je, že výčty vždy k dispozici [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) atribut.</span><span class="sxs-lookup"><span data-stu-id="60d7a-115">This is because enumerations always have the [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) attribute.</span></span>

<span data-ttu-id="60d7a-116">Následující kód ukazuje deklarace a používání výčtu.</span><span class="sxs-lookup"><span data-stu-id="60d7a-116">The following code shows the declaration and use of an enumeration.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

<span data-ttu-id="60d7a-117">Můžete snadno převést výčty základní typ pomocí příslušné operátor, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="60d7a-117">You can easily convert enumerations to the underlying type by using the appropriate operator, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

<span data-ttu-id="60d7a-118">Výčtové typy může mít jeden z následujících typů základní: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, a `char`.</span><span class="sxs-lookup"><span data-stu-id="60d7a-118">Enumerated types can have one of the following underlying types: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, and `char`.</span></span> <span data-ttu-id="60d7a-119">Výčtové typy jsou vyjádřené v rozhraní .NET Framework typy, které se dědí z `System.Enum`, který je pak zděděno od `System.ValueType`.</span><span class="sxs-lookup"><span data-stu-id="60d7a-119">Enumeration types are represented in the .NET Framework as types that are inherited from `System.Enum`, which in turn is inherited from `System.ValueType`.</span></span> <span data-ttu-id="60d7a-120">Proto jsou typy hodnot, které jsou umístěny v zásobníku nebo vložené v objekt obsahující a hodnotou základní typ není platná hodnota výčtu.</span><span class="sxs-lookup"><span data-stu-id="60d7a-120">Thus, they are value types that are located on the stack or inline in the containing object, and any value of the underlying type is a valid value of the enumeration.</span></span> <span data-ttu-id="60d7a-121">To je důležité při porovnávání se na výčet hodnot, protože je nutné zadat vzor, který zachytí nepojmenované hodnoty.</span><span class="sxs-lookup"><span data-stu-id="60d7a-121">This is significant when pattern matching on enumeration values, because you have to provide a pattern that catches the unnamed values.</span></span>

<span data-ttu-id="60d7a-122">`enum` Funkce knihovny F # lze použít ke generování hodnotou výčtu, i jiná hodnota než jeden z předdefinovaných, s názvem hodnoty.</span><span class="sxs-lookup"><span data-stu-id="60d7a-122">The `enum` function in the F# library can be used to generate an enumeration value, even a value other than one of the predefined, named values.</span></span> <span data-ttu-id="60d7a-123">Můžete použít `enum` funkce následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="60d7a-123">You use the `enum` function as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

<span data-ttu-id="60d7a-124">Výchozí hodnota `enum` funkce funguje s typem `int32`.</span><span class="sxs-lookup"><span data-stu-id="60d7a-124">The default `enum` function works with type `int32`.</span></span> <span data-ttu-id="60d7a-125">Proto jej nelze použít s výčtové typy, které mají jiné základní typy.</span><span class="sxs-lookup"><span data-stu-id="60d7a-125">Therefore, it cannot be used with enumeration types that have other underlying types.</span></span> <span data-ttu-id="60d7a-126">Místo toho použijte následující.</span><span class="sxs-lookup"><span data-stu-id="60d7a-126">Instead, use the following.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]
    
## <a name="see-also"></a><span data-ttu-id="60d7a-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="60d7a-127">See Also</span></span>
[<span data-ttu-id="60d7a-128">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="60d7a-128">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="60d7a-129">Přetypování a převody</span><span class="sxs-lookup"><span data-stu-id="60d7a-129">Casting and Conversions</span></span>](casting-and-conversions.md)
