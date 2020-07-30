---
title: Vyrovnávací paměti pevné velikosti – Průvodce programováním v C#
description: Přečtěte si o vyrovnávacích pamětech pevné velikosti. Vyrovnávací paměti pevné velikosti se používají k zápisu metod, které spolupracují se zdroji dat z jiných jazyků.
ms.date: 04/23/2020
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 1d4f5068121cdc98976954f2d99f4ac020c3b2a8
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381239"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="72329-104">Vyrovnávací paměti pevné velikosti (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="72329-104">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="72329-105">V jazyce C# můžete použít příkaz [fixed](../../language-reference/keywords/fixed-statement.md) pro vytvoření vyrovnávací paměti s pevnou velikostí pole v datové struktuře.</span><span class="sxs-lookup"><span data-stu-id="72329-105">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="72329-106">Vyrovnávací paměti pevné velikosti jsou užitečné, když píšete metody, které podporují spolupráci se zdroji dat z jiných jazyků nebo platforem.</span><span class="sxs-lookup"><span data-stu-id="72329-106">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="72329-107">Pevné pole může mít libovolné atributy nebo modifikátory, které jsou povoleny pro běžné členy struktury.</span><span class="sxs-lookup"><span data-stu-id="72329-107">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="72329-108">Jediným omezením je, že typ pole musí být `bool` , `byte` ,,, `char` `short` `int` , `long` , `sbyte` , `ushort` , `uint` , `ulong` , `float` , nebo `double` .</span><span class="sxs-lookup"><span data-stu-id="72329-108">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="72329-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72329-109">Remarks</span></span>

<span data-ttu-id="72329-110">V bezpečném kódu struktura C#, která obsahuje pole, neobsahuje prvky pole.</span><span class="sxs-lookup"><span data-stu-id="72329-110">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="72329-111">Místo toho struktura obsahuje odkaz na prvky.</span><span class="sxs-lookup"><span data-stu-id="72329-111">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="72329-112">Pole s pevnou velikostí můžete vložit do [struktury](../../language-reference/builtin-types/struct.md) , pokud se používá v [nebezpečném](../../language-reference/keywords/unsafe.md) bloku kódu.</span><span class="sxs-lookup"><span data-stu-id="72329-112">You can embed an array of fixed size in a [struct](../../language-reference/builtin-types/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="72329-113">Velikost následujícího `struct` není závislá na počtu prvků v poli, protože `pathName` je to odkaz:</span><span class="sxs-lookup"><span data-stu-id="72329-113">Size of the following `struct` doesn't depend on the number of elements in the array, since `pathName` is a reference:</span></span>

[!code-csharp[Struct with embedded array](snippets/FixedKeywordExamples.cs#6)]

<span data-ttu-id="72329-114">`struct`Může obsahovat vložené pole v nebezpečném kódu.</span><span class="sxs-lookup"><span data-stu-id="72329-114">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="72329-115">V následujícím příkladu `fixedBuffer` má pole pevnou velikost.</span><span class="sxs-lookup"><span data-stu-id="72329-115">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="72329-116">Pomocí příkazu vytvoříte `fixed` ukazatel na první prvek.</span><span class="sxs-lookup"><span data-stu-id="72329-116">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="72329-117">K prvkům pole přistupujete prostřednictvím tohoto ukazatele.</span><span class="sxs-lookup"><span data-stu-id="72329-117">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="72329-118">`fixed`Příkaz připnete `fixedBuffer` pole instance do konkrétního umístění v paměti.</span><span class="sxs-lookup"><span data-stu-id="72329-118">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#7)]

<span data-ttu-id="72329-119">Velikost pole elementu 128 `char` je 256 bajtů.</span><span class="sxs-lookup"><span data-stu-id="72329-119">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="72329-120">Pevná velikost [znaková](../../language-reference/builtin-types/char.md) vyrovnávací paměť vždy bere dva bajty na znak bez ohledu na kódování.</span><span class="sxs-lookup"><span data-stu-id="72329-120">Fixed size [char](../../language-reference/builtin-types/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="72329-121">To platí i v případě, že jsou vyrovnávací paměti pro znaky zařazeny do metod nebo struktur rozhraní API pomocí `CharSet = CharSet.Auto` nebo `CharSet = CharSet.Ansi` .</span><span class="sxs-lookup"><span data-stu-id="72329-121">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="72329-122">Další informace naleznete v tématu <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="72329-122">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="72329-123">Předchozí příklad ukazuje přístup k `fixed` polím bez připnutí, která je k dispozici počínaje jazykem C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="72329-123">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="72329-124">Další společné pole s pevnou velikostí je pole [bool](../../language-reference/builtin-types/bool.md) .</span><span class="sxs-lookup"><span data-stu-id="72329-124">Another common fixed-size array is the [bool](../../language-reference/builtin-types/bool.md) array.</span></span> <span data-ttu-id="72329-125">Prvky v `bool` poli mají velikost vždy jeden bajt.</span><span class="sxs-lookup"><span data-stu-id="72329-125">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="72329-126">`bool`pole nejsou vhodná pro vytváření bitových polí nebo vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="72329-126">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

<span data-ttu-id="72329-127">Vyrovnávací paměti pevné velikosti jsou kompilovány s <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType> , který instruuje modul CLR (Common Language Runtime), který typ obsahuje nespravované pole, které může potenciálně přetečení.</span><span class="sxs-lookup"><span data-stu-id="72329-127">Fixed size buffers are compiled with the <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType>, which instructs the common language runtime (CLR) that a type contains an unmanaged array that can potentially overflow.</span></span> <span data-ttu-id="72329-128">To se podobá paměti vytvořené pomocí [stackalloc](../../language-reference/operators/stackalloc.md), která v modulu CLR automaticky povoluje funkce detekce přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="72329-128">This is similar to memory created using [stackalloc](../../language-reference/operators/stackalloc.md), which automatically enables buffer overrun detection features in the CLR.</span></span> <span data-ttu-id="72329-129">Předchozí příklad ukazuje, jak může vyrovnávací paměť s pevnou velikostí existovat v `unsafe struct` .</span><span class="sxs-lookup"><span data-stu-id="72329-129">The previous example shows how a fixed size buffer could exist in an `unsafe struct`.</span></span>

```csharp
internal unsafe struct Buffer
{
    public fixed char fixedBuffer[128];
}
```

<span data-ttu-id="72329-130">Kompilátorem generovaný C# pro `Buffer` je následující atribut:</span><span class="sxs-lookup"><span data-stu-id="72329-130">The compiler generated C# for `Buffer`, is attributed as follows:</span></span>

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

<span data-ttu-id="72329-131">Vyrovnávací paměti pevné velikosti se od standardních polí liší následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="72329-131">Fixed size buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="72329-132">Dá se použít jenom v [nezabezpečeném](../../language-reference/keywords/unsafe.md) kontextu.</span><span class="sxs-lookup"><span data-stu-id="72329-132">May only be used in an [unsafe](../../language-reference/keywords/unsafe.md) context.</span></span>
- <span data-ttu-id="72329-133">Mohou být pouze poli instancí struktur.</span><span class="sxs-lookup"><span data-stu-id="72329-133">May only be instance fields of structs.</span></span>
- <span data-ttu-id="72329-134">Jsou to vždycky vektory nebo jednorozměrná pole.</span><span class="sxs-lookup"><span data-stu-id="72329-134">They're always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="72329-135">Deklarace by měla obsahovat délku, například `fixed char id[8]` .</span><span class="sxs-lookup"><span data-stu-id="72329-135">The declaration should include the length, such as `fixed char id[8]`.</span></span> <span data-ttu-id="72329-136">Nemůžete použít `fixed char id[]` .</span><span class="sxs-lookup"><span data-stu-id="72329-136">You cannot use `fixed char id[]`.</span></span>

## <a name="see-also"></a><span data-ttu-id="72329-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72329-137">See also</span></span>

- [<span data-ttu-id="72329-138">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="72329-138">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="72329-139">Nezabezpečený kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="72329-139">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="72329-140">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="72329-140">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="72329-141">Vzájemná funkční spolupráce</span><span class="sxs-lookup"><span data-stu-id="72329-141">Interoperability</span></span>](../interop/index.md)
