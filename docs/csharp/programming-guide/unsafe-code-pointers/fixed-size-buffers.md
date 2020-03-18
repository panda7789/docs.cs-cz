---
title: Buffery s pevnou velikostí – programovací průvodce C#
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 6770497b23212f1786b4f4a620ed2b650079c44b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157023"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="10d66-102">Vyrovnávací paměti pevné velikosti (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="10d66-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="10d66-103">V C# můžete použít [příkaz fixed](../../language-reference/keywords/fixed-statement.md) k vytvoření vyrovnávací paměti s polem s pevnou velikostí v datové struktuře.</span><span class="sxs-lookup"><span data-stu-id="10d66-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="10d66-104">Vyrovnávací paměti s pevnou velikostí jsou užitečné při psaní metod, které interop se zdroji dat z jiných jazyků nebo platforem.</span><span class="sxs-lookup"><span data-stu-id="10d66-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="10d66-105">Pevné pole může trvat všechny atributy nebo modifikátory, které jsou povoleny pro pravidelné členy struktury.</span><span class="sxs-lookup"><span data-stu-id="10d66-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="10d66-106">Jediným omezením je, že `bool`typ `byte` `char`pole `short` `int`musí `long` `sbyte`být `ushort` `uint`, `ulong` `float`, `double`, , , , , , , , , nebo .</span><span class="sxs-lookup"><span data-stu-id="10d66-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="10d66-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="10d66-107">Remarks</span></span>

<span data-ttu-id="10d66-108">V bezpečném kódu c# struktura, která obsahuje pole neobsahuje prvky pole.</span><span class="sxs-lookup"><span data-stu-id="10d66-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="10d66-109">Místo toho struktura obsahuje odkaz na prvky.</span><span class="sxs-lookup"><span data-stu-id="10d66-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="10d66-110">Pole s pevnou velikostí můžete vložit [do struktury,](../../language-reference/builtin-types/struct.md) pokud se používá v [nebezpečném](../../language-reference/keywords/unsafe.md) bloku kódu.</span><span class="sxs-lookup"><span data-stu-id="10d66-110">You can embed an array of fixed size in a [struct](../../language-reference/builtin-types/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="10d66-111">Velikost následujícího `struct` nezávisí na počtu prvků v poli, `pathName` protože je odkaz:</span><span class="sxs-lookup"><span data-stu-id="10d66-111">Size of the following `struct` doesn't depend on the number of elements in the array, since `pathName` is a reference:</span></span>

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

<span data-ttu-id="10d66-112">A `struct` může obsahovat vložené pole v nebezpečném kódu.</span><span class="sxs-lookup"><span data-stu-id="10d66-112">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="10d66-113">V následujícím příkladu `fixedBuffer` má pole pevnou velikost.</span><span class="sxs-lookup"><span data-stu-id="10d66-113">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="10d66-114">Příkaz slouží `fixed` k vytvoření ukazatele na první prvek.</span><span class="sxs-lookup"><span data-stu-id="10d66-114">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="10d66-115">Přístup k prvkům pole prostřednictvím tohoto ukazatele.</span><span class="sxs-lookup"><span data-stu-id="10d66-115">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="10d66-116">Příkaz `fixed` připne `fixedBuffer` pole instance na určité místo v paměti.</span><span class="sxs-lookup"><span data-stu-id="10d66-116">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

<span data-ttu-id="10d66-117">Velikost pole 128 `char` element je 256 bajtů.</span><span class="sxs-lookup"><span data-stu-id="10d66-117">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="10d66-118">Pevná velikost [char](../../language-reference/builtin-types/char.md) vyrovnávací paměti vždy trvat dva bajty na znak, bez ohledu na kódování.</span><span class="sxs-lookup"><span data-stu-id="10d66-118">Fixed size [char](../../language-reference/builtin-types/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="10d66-119">To platí i v případě, že jsou vyrovnávací paměti `CharSet = CharSet.Auto` znaku zařazeny do metod rozhraní API nebo struktur s nebo `CharSet = CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="10d66-119">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="10d66-120">Další informace naleznete v tématu <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="10d66-120">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="10d66-121">Předchozí příklad ukazuje přístup `fixed` k polím bez připnutí, který je k dispozici počínaje C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="10d66-121">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="10d66-122">Dalším běžným polem s pevnou velikostí je [bool](../../language-reference/builtin-types/bool.md) pole.</span><span class="sxs-lookup"><span data-stu-id="10d66-122">Another common fixed-size array is the [bool](../../language-reference/builtin-types/bool.md) array.</span></span> <span data-ttu-id="10d66-123">Prvky v `bool` poli jsou vždy jeden bajt ve velikosti.</span><span class="sxs-lookup"><span data-stu-id="10d66-123">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="10d66-124">`bool`pole nejsou vhodná pro vytváření bitových polí nebo vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="10d66-124">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

> [!NOTE]
> <span data-ttu-id="10d66-125">S výjimkou paměti vytvořené pomocí [stackalloc](../../language-reference/operators/stackalloc.md), kompilátor Jazyka C# a clr (COMMON Language Runtime) neprovádějí žádné kontroly přetečení vyrovnávací paměti zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="10d66-125">Except for memory created by using [stackalloc](../../language-reference/operators/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="10d66-126">Stejně jako u všech nebezpečných kódů buďte opatrní.</span><span class="sxs-lookup"><span data-stu-id="10d66-126">As with all unsafe code, use caution.</span></span>

<span data-ttu-id="10d66-127">Nebezpečné vyrovnávací paměti se liší od běžných polí následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="10d66-127">Unsafe buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="10d66-128">Nebezpečné vyrovnávací paměti lze použít pouze v nebezpečném kontextu.</span><span class="sxs-lookup"><span data-stu-id="10d66-128">You can only use unsafe buffers in an unsafe context.</span></span>
- <span data-ttu-id="10d66-129">Nebezpečné vyrovnávací paměti jsou vždy vektory nebo jednorozměrná pole.</span><span class="sxs-lookup"><span data-stu-id="10d66-129">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="10d66-130">Deklarace pole by měla obsahovat `char id[8]`počet, například .</span><span class="sxs-lookup"><span data-stu-id="10d66-130">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="10d66-131">Nelze použít `char id[]`.</span><span class="sxs-lookup"><span data-stu-id="10d66-131">You cannot use `char id[]`.</span></span>
- <span data-ttu-id="10d66-132">Nebezpečné vyrovnávací paměti mohou být pouze pole instance struktur v nebezpečném kontextu.</span><span class="sxs-lookup"><span data-stu-id="10d66-132">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>

## <a name="see-also"></a><span data-ttu-id="10d66-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="10d66-133">See also</span></span>

- [<span data-ttu-id="10d66-134">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="10d66-134">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="10d66-135">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="10d66-135">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="10d66-136">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="10d66-136">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="10d66-137">Vzájemná funkční spolupráce</span><span class="sxs-lookup"><span data-stu-id="10d66-137">Interoperability</span></span>](../interop/index.md)
