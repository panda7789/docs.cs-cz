---
title: Vyrovnávací paměti pevné velikosti – Průvodce programováním v C#
ms.date: 04/23/2020
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 5920dd125ded34969d60feb299568b56402056ab
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140542"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="ee157-102">Vyrovnávací paměti pevné velikosti (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="ee157-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="ee157-103">V jazyce C# můžete použít příkaz [fixed](../../language-reference/keywords/fixed-statement.md) pro vytvoření vyrovnávací paměti s pevnou velikostí pole v datové struktuře.</span><span class="sxs-lookup"><span data-stu-id="ee157-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="ee157-104">Vyrovnávací paměti pevné velikosti jsou užitečné, když píšete metody, které podporují spolupráci se zdroji dat z jiných jazyků nebo platforem.</span><span class="sxs-lookup"><span data-stu-id="ee157-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="ee157-105">Pevné pole může mít libovolné atributy nebo modifikátory, které jsou povoleny pro běžné členy struktury.</span><span class="sxs-lookup"><span data-stu-id="ee157-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="ee157-106">Jediným omezením je, že typ pole musí být `bool`, `byte`, `char` `short`,, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, nebo `double`.</span><span class="sxs-lookup"><span data-stu-id="ee157-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="ee157-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ee157-107">Remarks</span></span>

<span data-ttu-id="ee157-108">V bezpečném kódu struktura C#, která obsahuje pole, neobsahuje prvky pole.</span><span class="sxs-lookup"><span data-stu-id="ee157-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="ee157-109">Místo toho struktura obsahuje odkaz na prvky.</span><span class="sxs-lookup"><span data-stu-id="ee157-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="ee157-110">Pole s pevnou velikostí můžete vložit do [struktury](../../language-reference/builtin-types/struct.md) , pokud se používá v [nebezpečném](../../language-reference/keywords/unsafe.md) bloku kódu.</span><span class="sxs-lookup"><span data-stu-id="ee157-110">You can embed an array of fixed size in a [struct](../../language-reference/builtin-types/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="ee157-111">Velikost následujícího `struct` není závislá na počtu prvků v poli, protože `pathName` je to odkaz:</span><span class="sxs-lookup"><span data-stu-id="ee157-111">Size of the following `struct` doesn't depend on the number of elements in the array, since `pathName` is a reference:</span></span>

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

<span data-ttu-id="ee157-112">`struct` Může obsahovat vložené pole v nebezpečném kódu.</span><span class="sxs-lookup"><span data-stu-id="ee157-112">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="ee157-113">V následujícím příkladu má `fixedBuffer` pole pevnou velikost.</span><span class="sxs-lookup"><span data-stu-id="ee157-113">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="ee157-114">Pomocí `fixed` příkazu vytvoříte ukazatel na první prvek.</span><span class="sxs-lookup"><span data-stu-id="ee157-114">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="ee157-115">K prvkům pole přistupujete prostřednictvím tohoto ukazatele.</span><span class="sxs-lookup"><span data-stu-id="ee157-115">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="ee157-116">`fixed` Příkaz připnete pole `fixedBuffer` instance do konkrétního umístění v paměti.</span><span class="sxs-lookup"><span data-stu-id="ee157-116">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

<span data-ttu-id="ee157-117">Velikost pole elementu `char` 128 je 256 bajtů.</span><span class="sxs-lookup"><span data-stu-id="ee157-117">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="ee157-118">Pevná velikost [znaková](../../language-reference/builtin-types/char.md) vyrovnávací paměť vždy bere dva bajty na znak bez ohledu na kódování.</span><span class="sxs-lookup"><span data-stu-id="ee157-118">Fixed size [char](../../language-reference/builtin-types/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="ee157-119">To platí i v případě, že jsou vyrovnávací paměti pro znaky zařazeny do metod nebo struktur `CharSet = CharSet.Auto` rozhraní `CharSet = CharSet.Ansi`API pomocí nebo.</span><span class="sxs-lookup"><span data-stu-id="ee157-119">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="ee157-120">Další informace naleznete v tématu <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="ee157-120">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="ee157-121">Předchozí příklad ukazuje přístup k `fixed` polím bez připnutí, která je k dispozici počínaje jazykem C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="ee157-121">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="ee157-122">Další společné pole s pevnou velikostí je pole [bool](../../language-reference/builtin-types/bool.md) .</span><span class="sxs-lookup"><span data-stu-id="ee157-122">Another common fixed-size array is the [bool](../../language-reference/builtin-types/bool.md) array.</span></span> <span data-ttu-id="ee157-123">Prvky v `bool` poli mají velikost vždy jeden bajt.</span><span class="sxs-lookup"><span data-stu-id="ee157-123">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="ee157-124">`bool`pole nejsou vhodná pro vytváření bitových polí nebo vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="ee157-124">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

<span data-ttu-id="ee157-125">Vyrovnávací paměti pevné velikosti jsou kompilovány s <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType>, který instruuje modul CLR (Common Language Runtime), který typ obsahuje nespravované pole, které může potenciálně přetečení.</span><span class="sxs-lookup"><span data-stu-id="ee157-125">Fixed size buffers are compiled with the <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType>, which instructs the common language runtime (CLR) that a type contains an unmanaged array that can potentially overflow.</span></span> <span data-ttu-id="ee157-126">To se podobá paměti vytvořené pomocí [stackalloc](../../language-reference/operators/stackalloc.md), která v modulu CLR automaticky povoluje funkce detekce přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ee157-126">This is similar to memory created using [stackalloc](../../language-reference/operators/stackalloc.md), which automatically enables buffer overrun detection features in the CLR.</span></span> <span data-ttu-id="ee157-127">Předchozí příklad ukazuje, jak může vyrovnávací paměť s pevnou velikostí existovat v `unsafe struct`.</span><span class="sxs-lookup"><span data-stu-id="ee157-127">The previous example shows how a fixed size buffer could exist in an `unsafe struct`.</span></span>

```csharp
internal unsafe struct Buffer
{
    public fixed char fixedBuffer[128];
}
```

<span data-ttu-id="ee157-128">Kompilátorem generovaný C# pro `Buffer`je následující atribut:</span><span class="sxs-lookup"><span data-stu-id="ee157-128">The compiler generated C# for `Buffer`, is attributed as follows:</span></span>

```csharp
internal struct Buffer
{
    [StructLayout(LayoutKind.Sequential, Size = 256)]
    [CompilerGenerated]
    [UnsafeValueType]
    public struct <fixedBuffer>e__FixedBuffer
    {
        public char FixedElementField;
    }

    [FixedBuffer(typeof(char), 128)]
    public <fixedBuffer>e__FixedBuffer fixedBuffer;
}
```

<span data-ttu-id="ee157-129">Vyrovnávací paměti pevné velikosti se od standardních polí liší následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="ee157-129">Fixed size buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="ee157-130">Dá se použít jenom v [nezabezpečeném](../../language-reference/keywords/unsafe.md) kontextu.</span><span class="sxs-lookup"><span data-stu-id="ee157-130">May only be used in an [unsafe](../../language-reference/keywords/unsafe.md) context.</span></span>
- <span data-ttu-id="ee157-131">Mohou být pouze poli instancí struktur.</span><span class="sxs-lookup"><span data-stu-id="ee157-131">May only be instance fields of structs.</span></span>
- <span data-ttu-id="ee157-132">Jsou to vždycky vektory nebo jednorozměrná pole.</span><span class="sxs-lookup"><span data-stu-id="ee157-132">They're always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="ee157-133">Deklarace by měla obsahovat délku, například `fixed char id[8]`.</span><span class="sxs-lookup"><span data-stu-id="ee157-133">The declaration should include the length, such as `fixed char id[8]`.</span></span> <span data-ttu-id="ee157-134">Nemůžete `fixed char id[]`použít.</span><span class="sxs-lookup"><span data-stu-id="ee157-134">You cannot use `fixed char id[]`.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee157-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee157-135">See also</span></span>

- [<span data-ttu-id="ee157-136">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="ee157-136">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ee157-137">Nezabezpečený kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="ee157-137">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="ee157-138">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="ee157-138">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="ee157-139">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="ee157-139">Interoperability</span></span>](../interop/index.md)
