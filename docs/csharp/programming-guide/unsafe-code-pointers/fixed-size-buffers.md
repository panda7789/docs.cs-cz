---
title: Velikost vyrovnávací paměti – pevná C# Průvodce programováním
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 5bfd9f3f559e4780b910a2e5a3430b08a2183ee3
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833504"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="8f256-102">Vyrovnávací paměti pevné velikosti (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="8f256-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="8f256-103">V jazyce C#, můžete použít [oprava](../../language-reference/keywords/fixed-statement.md) příkaz vytvoří vyrovnávací paměti s pevnou velikostí pole v datové struktuře.</span><span class="sxs-lookup"><span data-stu-id="8f256-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="8f256-104">Vyrovnávací paměti pevné velikosti jsou užitečné, když píšete tohoto zprostředkovatele komunikace s objekty zdroje dat pro metody v jiných jazycích či platformách.</span><span class="sxs-lookup"><span data-stu-id="8f256-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="8f256-105">Oprava pole můžete provést všechny atributy nebo modifikátory, které jsou povoleny pro členy struktury regulárních.</span><span class="sxs-lookup"><span data-stu-id="8f256-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="8f256-106">Jediným omezením je, že musí být typu pole `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, nebo `double`.</span><span class="sxs-lookup"><span data-stu-id="8f256-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="8f256-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8f256-107">Remarks</span></span>

<span data-ttu-id="8f256-108">V nouzovém kódu struktura jazyka C#, která obsahuje pole neobsahuje prvků pole.</span><span class="sxs-lookup"><span data-stu-id="8f256-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="8f256-109">Místo toho struktura obsahuje odkaz na prvky.</span><span class="sxs-lookup"><span data-stu-id="8f256-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="8f256-110">Můžete vložit pole s pevnou velikostí v [struktury](../../language-reference/keywords/struct.md) když se používá v [unsafe](../../language-reference/keywords/unsafe.md) blok kódu.</span><span class="sxs-lookup"><span data-stu-id="8f256-110">You can embed an array of fixed size in a [struct](../../language-reference/keywords/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="8f256-111">Následující `struct` je velikosti 8 bajtů.</span><span class="sxs-lookup"><span data-stu-id="8f256-111">The following `struct` is 8 bytes in size.</span></span> <span data-ttu-id="8f256-112">`pathName` Pole je odkaz:</span><span class="sxs-lookup"><span data-stu-id="8f256-112">The `pathName` array is a reference:</span></span>

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

<span data-ttu-id="8f256-113">A `struct` může obsahovat vložené pole v nezabezpečený kód.</span><span class="sxs-lookup"><span data-stu-id="8f256-113">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="8f256-114">V následujícím příkladu `fixedBuffer` pole má pevnou velikost.</span><span class="sxs-lookup"><span data-stu-id="8f256-114">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="8f256-115">Můžete použít `fixed` příkaz Vytvořit ukazatel na první prvek.</span><span class="sxs-lookup"><span data-stu-id="8f256-115">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="8f256-116">Přístup k prvkům pole pomocí tohoto ukazatele.</span><span class="sxs-lookup"><span data-stu-id="8f256-116">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="8f256-117">`fixed` Příkaz PIN kódy `fixedBuffer` pole instance na konkrétní umístění v paměti.</span><span class="sxs-lookup"><span data-stu-id="8f256-117">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

<span data-ttu-id="8f256-118">Velikost 128 elementu `char` pole je 256 bajtů.</span><span class="sxs-lookup"><span data-stu-id="8f256-118">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="8f256-119">Pevná velikost [char](../../language-reference/keywords/char.md) vyrovnávacích pamětí vždy provést dva bajty na znak, bez ohledu na to, kódování.</span><span class="sxs-lookup"><span data-stu-id="8f256-119">Fixed size [char](../../language-reference/keywords/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="8f256-120">To platí i, když jsou char vyrovnávací paměti zařazeny do metody rozhraní API nebo struktury s `CharSet = CharSet.Auto` nebo `CharSet = CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="8f256-120">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="8f256-121">Další informace naleznete v tématu <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="8f256-121">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="8f256-122">Předchozí příklad ukazuje `fixed` pole bez Připnutí, které je k dispozici od verze C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="8f256-122">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="8f256-123">Další běžné pevnou velikost pole je [bool](../../language-reference/keywords/bool.md) pole.</span><span class="sxs-lookup"><span data-stu-id="8f256-123">Another common fixed-size array is the [bool](../../language-reference/keywords/bool.md) array.</span></span> <span data-ttu-id="8f256-124">Prvky v `bool` pole jsou vždy jeden bajt velikosti.</span><span class="sxs-lookup"><span data-stu-id="8f256-124">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="8f256-125">`bool` pole nejsou vhodné pro vytvoření bitové pole nebo vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="8f256-125">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

> [!NOTE]
> <span data-ttu-id="8f256-126">S výjimkou paměti vytvořené využitím [stackalloc](../../language-reference/operators/stackalloc.md), kompilátor jazyka C# a common language runtime (CLR) nebude provádět žádné bezpečnostní kontroly přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="8f256-126">Except for memory created by using [stackalloc](../../language-reference/operators/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="8f256-127">Stejně jako u všech nebezpečný kód, buďte opatrní.</span><span class="sxs-lookup"><span data-stu-id="8f256-127">As with all unsafe code, use caution.</span></span>

<span data-ttu-id="8f256-128">Nezabezpečené vyrovnávací paměti se liší od pravidelných polí následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="8f256-128">Unsafe buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="8f256-129">Nezabezpečené vyrovnávací paměti lze použít pouze v nezabezpečeném kontextu.</span><span class="sxs-lookup"><span data-stu-id="8f256-129">You can only use unsafe buffers in an unsafe context.</span></span>
- <span data-ttu-id="8f256-130">Nezabezpečené vyrovnávací paměti jsou vždy vektorů nebo jednorozměrná pole.</span><span class="sxs-lookup"><span data-stu-id="8f256-130">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="8f256-131">Deklarace pole by měla obsahovat počet, jako například `char id[8]`.</span><span class="sxs-lookup"><span data-stu-id="8f256-131">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="8f256-132">Nemůžete použít `char id[]`.</span><span class="sxs-lookup"><span data-stu-id="8f256-132">You cannot use `char id[]`.</span></span>
- <span data-ttu-id="8f256-133">Nezabezpečené vyrovnávací paměti může být pouze pole instancí struktur v nezabezpečeném kontextu.</span><span class="sxs-lookup"><span data-stu-id="8f256-133">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f256-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8f256-134">See also</span></span>

- [<span data-ttu-id="8f256-135">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8f256-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8f256-136">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="8f256-136">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="8f256-137">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="8f256-137">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="8f256-138">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="8f256-138">Interoperability</span></span>](../interop/index.md)
