---
title: Vyrovnávací paměti pevné velikosti (Průvodce programováním v C#)
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 310c5eed5507f75239efc78b6132fbc91211d29e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339589"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="d8bf6-102">Vyrovnávací paměti pevné velikosti (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="d8bf6-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="d8bf6-103">V jazyce C#, můžete použít [pevné](../../language-reference/keywords/fixed-statement.md) příkaz k vytvoření vyrovnávací paměti s pevnou velikost pole ve struktuře data.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="d8bf6-104">Vyrovnávací paměti pevné velikosti jsou užitečné, když píšete tohoto zprostředkovatele komunikace s zdroje dat pro metody z dalších jazyků nebo platformy.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="d8bf6-105">Pole pevné může trvat všechny atributy nebo modifikátory, které jsou povoleny pro regulární struktura členy.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="d8bf6-106">Pouze omezení je, že musí být typ pole `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, nebo `double`.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="d8bf6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d8bf6-107">Remarks</span></span>

<span data-ttu-id="d8bf6-108">Struktury jazyka C# obsahující pole v bezpečném kódu neobsahuje prvků pole.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="d8bf6-109">Místo toho struct obsahuje odkaz na elementy.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="d8bf6-110">Můžete vložit pole s pevnou velikostí v [struktura](../../language-reference/keywords/struct.md) při použití v [unsafe](../../language-reference/keywords/unsafe.md) blok kódu.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-110">You can embed an array of fixed size in a [struct](../../language-reference/keywords/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="d8bf6-111">Následující `struct` je velikost 8 bajtů.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-111">The following `struct` is 8 bytes in size.</span></span> <span data-ttu-id="d8bf6-112">`pathName` Pole je odkaz:</span><span class="sxs-lookup"><span data-stu-id="d8bf6-112">The `pathName` array is a reference:</span></span>

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

<span data-ttu-id="d8bf6-113">A `struct` může obsahovat vložené pole v nezabezpečený kód.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-113">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="d8bf6-114">V následujícím příkladu `fixedBuffer` pole má pevnou velikost.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-114">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="d8bf6-115">Můžete použít `fixed` příkaz k vytvoření ukazatel na první prvek.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-115">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="d8bf6-116">Elementy pole přistupujete prostřednictvím tento ukazatel.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-116">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="d8bf6-117">`fixed` Příkaz PIN `fixedBuffer` pole instance do určitého umístění v paměti.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-117">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

<span data-ttu-id="d8bf6-118">Velikost 128 elementu `char` pole je 256 bajtů.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-118">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="d8bf6-119">Pevná velikost [char](../../language-reference/keywords/char.md) vyrovnávací paměti vždy provést dva bajty na znak, bez ohledu na to, kódování.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-119">Fixed size [char](../../language-reference/keywords/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="d8bf6-120">To platí i když vyrovnávací paměti char přeuspořádány metody rozhraní API nebo struktury s `CharSet = CharSet.Auto` nebo `CharSet = CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-120">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="d8bf6-121">Další informace naleznete v tématu <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-121">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="d8bf6-122">V předchozím příkladu představuje přístup k `fixed` pole bez připojení, které je k dispozici počínaje C# 7.3...</span><span class="sxs-lookup"><span data-stu-id="d8bf6-122">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3..</span></span>

<span data-ttu-id="d8bf6-123">Další běžné pole pevné velikosti je [bool](../../language-reference/keywords/bool.md) pole.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-123">Another common fixed-size array is the [bool](../../language-reference/keywords/bool.md) array.</span></span> <span data-ttu-id="d8bf6-124">Prvky v `bool` pole jsou vždy jeden bajt velikost.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-124">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="d8bf6-125">`bool` pole nejsou vhodné pro vytváření bitová pole nebo vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-125">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

> [!NOTE]
> <span data-ttu-id="d8bf6-126">S výjimkou paměti vytvořené pomocí [stackalloc](../../language-reference/keywords/stackalloc.md), kompilátor jazyka C# a modul CLR (CLR) neprovádějte žádné kontroly přetečení vyrovnávací paměti zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-126">Except for memory created by using [stackalloc](../../language-reference/keywords/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="d8bf6-127">Stejně jako u všech nezabezpečený kód, buďte opatrní.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-127">As with all unsafe code, use caution.</span></span>

<span data-ttu-id="d8bf6-128">Nezabezpečené vyrovnávací paměti se liší od regulární pole následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="d8bf6-128">Unsafe buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="d8bf6-129">Nezabezpečené vyrovnávací paměti můžete použít pouze v kontextu unsafe.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-129">You can only use unsafe buffers in an unsafe context.</span></span>
- <span data-ttu-id="d8bf6-130">Nezabezpečené vyrovnávací paměti jsou vždy vektory nebo jednorozměrná pole.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-130">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="d8bf6-131">Deklarace pole by měla obsahovat počet, jako například `char id[8]`.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-131">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="d8bf6-132">Nemůžete použít `char id[]`.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-132">You cannot use `char id[]`.</span></span>
- <span data-ttu-id="d8bf6-133">Nezabezpečené vyrovnávací paměti lze pouze pole instance struktury v kontextu unsafe.</span><span class="sxs-lookup"><span data-stu-id="d8bf6-133">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8bf6-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8bf6-134">See Also</span></span>

[<span data-ttu-id="d8bf6-135">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d8bf6-135">C# Programming Guide</span></span>](../index.md)  
[<span data-ttu-id="d8bf6-136">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="d8bf6-136">Unsafe Code and Pointers</span></span>](index.md)  
[<span data-ttu-id="d8bf6-137">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="d8bf6-137">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)  
[<span data-ttu-id="d8bf6-138">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="d8bf6-138">Interoperability</span></span>](../interop/index.md)
