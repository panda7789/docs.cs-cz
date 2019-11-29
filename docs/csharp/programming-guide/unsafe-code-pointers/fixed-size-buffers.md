---
title: Vyrovnávací paměti pevné velikosti – C# Průvodce programováním
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: deb057929871ffb50da466e3628c34f336ffd5ee
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552401"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="f0c29-102">Vyrovnávací paměti pevné velikosti (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="f0c29-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="f0c29-103">V C#nástroji můžete použít příkaz [fixed](../../language-reference/keywords/fixed-statement.md) pro vytvoření vyrovnávací paměti s pevnou velikostí pole v datové struktuře.</span><span class="sxs-lookup"><span data-stu-id="f0c29-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="f0c29-104">Vyrovnávací paměti pevné velikosti jsou užitečné, když píšete metody, které podporují spolupráci se zdroji dat z jiných jazyků nebo platforem.</span><span class="sxs-lookup"><span data-stu-id="f0c29-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="f0c29-105">Pevné pole může mít libovolné atributy nebo modifikátory, které jsou povoleny pro běžné členy struktury.</span><span class="sxs-lookup"><span data-stu-id="f0c29-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="f0c29-106">Jediným omezením je, že typ pole musí být `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`nebo `double`.</span><span class="sxs-lookup"><span data-stu-id="f0c29-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="f0c29-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f0c29-107">Remarks</span></span>

<span data-ttu-id="f0c29-108">V bezpečném kódu C# struktura obsahující pole neobsahuje prvky pole.</span><span class="sxs-lookup"><span data-stu-id="f0c29-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="f0c29-109">Místo toho struktura obsahuje odkaz na prvky.</span><span class="sxs-lookup"><span data-stu-id="f0c29-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="f0c29-110">Pole s pevnou velikostí můžete vložit do [struktury](../../language-reference/keywords/struct.md) , pokud se používá v [nebezpečném](../../language-reference/keywords/unsafe.md) bloku kódu.</span><span class="sxs-lookup"><span data-stu-id="f0c29-110">You can embed an array of fixed size in a [struct](../../language-reference/keywords/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="f0c29-111">Následující `struct` mají velikost 8 bajtů.</span><span class="sxs-lookup"><span data-stu-id="f0c29-111">The following `struct` is 8 bytes in size.</span></span> <span data-ttu-id="f0c29-112">Pole `pathName` je odkazem:</span><span class="sxs-lookup"><span data-stu-id="f0c29-112">The `pathName` array is a reference:</span></span>

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

<span data-ttu-id="f0c29-113">`struct` může obsahovat vložené pole v nebezpečném kódu.</span><span class="sxs-lookup"><span data-stu-id="f0c29-113">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="f0c29-114">V následujícím příkladu má pole `fixedBuffer` pevnou velikost.</span><span class="sxs-lookup"><span data-stu-id="f0c29-114">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="f0c29-115">Pomocí příkazu `fixed` vytvoříte ukazatel na první prvek.</span><span class="sxs-lookup"><span data-stu-id="f0c29-115">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="f0c29-116">K prvkům pole přistupujete prostřednictvím tohoto ukazatele.</span><span class="sxs-lookup"><span data-stu-id="f0c29-116">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="f0c29-117">Příkaz `fixed` připnete pole instance `fixedBuffer` do konkrétního umístění v paměti.</span><span class="sxs-lookup"><span data-stu-id="f0c29-117">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

<span data-ttu-id="f0c29-118">Velikost elementu 128 `char` pole je 256 bajtů.</span><span class="sxs-lookup"><span data-stu-id="f0c29-118">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="f0c29-119">Pevná velikost [znaková](../../language-reference/builtin-types/char.md) vyrovnávací paměť vždy bere dva bajty na znak bez ohledu na kódování.</span><span class="sxs-lookup"><span data-stu-id="f0c29-119">Fixed size [char](../../language-reference/builtin-types/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="f0c29-120">To platí i v případě, že jsou vyrovnávací paměti pro znaky zařazeny do metod nebo struktur rozhraní API pomocí `CharSet = CharSet.Auto` nebo `CharSet = CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="f0c29-120">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="f0c29-121">Další informace najdete v tématu <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="f0c29-121">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="f0c29-122">Předchozí příklad ukazuje přístup k polím `fixed` bez připnutí, která je k dispozici od C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="f0c29-122">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="f0c29-123">Další společné pole s pevnou velikostí je pole [bool](../../language-reference/builtin-types/bool.md) .</span><span class="sxs-lookup"><span data-stu-id="f0c29-123">Another common fixed-size array is the [bool](../../language-reference/builtin-types/bool.md) array.</span></span> <span data-ttu-id="f0c29-124">Prvky v poli `bool` mají velikost vždy jeden bajt.</span><span class="sxs-lookup"><span data-stu-id="f0c29-124">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="f0c29-125">`bool` pole nejsou vhodná pro vytváření bitových polí nebo vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="f0c29-125">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

> [!NOTE]
> <span data-ttu-id="f0c29-126">S výjimkou paměti vytvořené pomocí [stackalloc](../../language-reference/operators/stackalloc.md) C# kompilátor a modul CLR (Common Language Runtime) neprovádí žádné kontroly přetečení vyrovnávací paměti zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f0c29-126">Except for memory created by using [stackalloc](../../language-reference/operators/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="f0c29-127">Stejně jako u veškerého nebezpečného kódu buďte opatrní.</span><span class="sxs-lookup"><span data-stu-id="f0c29-127">As with all unsafe code, use caution.</span></span>

<span data-ttu-id="f0c29-128">Nebezpečné vyrovnávací paměti se liší od regulárních polí následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="f0c29-128">Unsafe buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="f0c29-129">V nebezpečném kontextu můžete použít jenom nebezpečné vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="f0c29-129">You can only use unsafe buffers in an unsafe context.</span></span>
- <span data-ttu-id="f0c29-130">Nebezpečné vyrovnávací paměti jsou vždy vektory nebo jednorozměrná pole.</span><span class="sxs-lookup"><span data-stu-id="f0c29-130">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="f0c29-131">Deklarace pole by měla zahrnovat počet, například `char id[8]`.</span><span class="sxs-lookup"><span data-stu-id="f0c29-131">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="f0c29-132">Nemůžete použít `char id[]`.</span><span class="sxs-lookup"><span data-stu-id="f0c29-132">You cannot use `char id[]`.</span></span>
- <span data-ttu-id="f0c29-133">Nebezpečné vyrovnávací paměti mohou být pouze pole instancí struktur v nezabezpečeném kontextu.</span><span class="sxs-lookup"><span data-stu-id="f0c29-133">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0c29-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f0c29-134">See also</span></span>

- [<span data-ttu-id="f0c29-135">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f0c29-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f0c29-136">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="f0c29-136">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="f0c29-137">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="f0c29-137">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="f0c29-138">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="f0c29-138">Interoperability</span></span>](../interop/index.md)
