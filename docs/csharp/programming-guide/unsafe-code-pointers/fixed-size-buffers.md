---
title: "Vyrovnávací paměti pevné velikosti (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.assetid: 6220d454-947c-4977-ac9d-9308c6ed5051
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3f99c2c6d477fca988fcca77de5ca5c2f8addd4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="cac32-102">Vyrovnávací paměti pevné velikosti (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="cac32-102">Fixed Size Buffers (C# Programming Guide)</span></span>
<span data-ttu-id="cac32-103">V jazyce C#, můžete použít [pevné](../../../csharp/language-reference/keywords/fixed-statement.md) příkaz k vytvoření vyrovnávací paměti s pevnou velikost pole ve struktuře data.</span><span class="sxs-lookup"><span data-stu-id="cac32-103">In C#, you can use the [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="cac32-104">To je užitečné, když pracujete s existující kód, jako je například kód napsaný v jiných jazycích, existující knihovny DLL nebo COM projekty.</span><span class="sxs-lookup"><span data-stu-id="cac32-104">This is useful when you are working with existing code, such as code written in other languages, pre-existing DLLs or COM projects.</span></span> <span data-ttu-id="cac32-105">Pole pevné může trvat všechny atributy nebo modifikátory, které jsou povoleny pro regulární struktura členy.</span><span class="sxs-lookup"><span data-stu-id="cac32-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="cac32-106">Pouze omezení je, že musí být typ pole `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, nebo `double`.</span><span class="sxs-lookup"><span data-stu-id="cac32-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>  
  
```  
private fixed char name[30];  
```  
  
## <a name="remarks"></a><span data-ttu-id="cac32-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cac32-107">Remarks</span></span>  
 <span data-ttu-id="cac32-108">Deklarace struktury pevné velikosti styl C++ byla obtížná v dřívějších verzích programu C#, protože struktury jazyka C# obsahující pole neobsahuje prvků pole.</span><span class="sxs-lookup"><span data-stu-id="cac32-108">In early versions of C#, declaring a C++ style fixed-size structure was difficult because a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="cac32-109">Místo toho struct obsahuje odkaz na elementy.</span><span class="sxs-lookup"><span data-stu-id="cac32-109">Instead, the struct contains a reference to the elements.</span></span>  
  
 <span data-ttu-id="cac32-110">Přidání možnosti pro vložení pole s pevnou velikostí v 2.0 C# [struktura](../../../csharp/language-reference/keywords/struct.md) při použití v [unsafe](../../../csharp/language-reference/keywords/unsafe.md) blok kódu.</span><span class="sxs-lookup"><span data-stu-id="cac32-110">C# 2.0 added the ability to embed an array of fixed size in a [struct](../../../csharp/language-reference/keywords/struct.md) when it is used in an [unsafe](../../../csharp/language-reference/keywords/unsafe.md) code block.</span></span>  
  
 <span data-ttu-id="cac32-111">Například před C# 2.0, následující `struct` by velikosti 8 bajtů.</span><span class="sxs-lookup"><span data-stu-id="cac32-111">For example, before C# 2.0, the following `struct` would be 8 bytes in size.</span></span> <span data-ttu-id="cac32-112">`pathName` Pole je odkaz na pole přidělené haldy:</span><span class="sxs-lookup"><span data-stu-id="cac32-112">The `pathName` array is a reference to the heap-allocated array:</span></span>  
  
 [!code-csharp[csProgGuidePointers#19](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_1.cs)]  
  
 <span data-ttu-id="cac32-113">Od verze 2.0 C# `struct` může obsahovat vložené pole.</span><span class="sxs-lookup"><span data-stu-id="cac32-113">Beginning with C# 2.0, a `struct` can contain an embedded array.</span></span> <span data-ttu-id="cac32-114">V následujícím příkladu `fixedBuffer` pole má pevnou velikost.</span><span class="sxs-lookup"><span data-stu-id="cac32-114">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="cac32-115">Chcete-li získat přístup k elementy pole, použijte `fixed` příkaz k vytvoření ukazatel na první prvek.</span><span class="sxs-lookup"><span data-stu-id="cac32-115">To access the elements of the array, you use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="cac32-116">`fixed` Příkaz PIN kódy instanci `fixedBuffer` do určitého umístění v paměti.</span><span class="sxs-lookup"><span data-stu-id="cac32-116">The `fixed` statement pins an instance of `fixedBuffer` to a specific location in memory.</span></span>  
  
 [!code-csharp[csProgGuidePointers#20](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_2.cs)]  
  
 <span data-ttu-id="cac32-117">Velikost 128 elementu `char` pole je 256 bajtů.</span><span class="sxs-lookup"><span data-stu-id="cac32-117">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="cac32-118">Pevná velikost [char](../../../csharp/language-reference/keywords/char.md) vyrovnávací paměti vždy provést dva bajty na znak, bez ohledu na to, kódování.</span><span class="sxs-lookup"><span data-stu-id="cac32-118">Fixed size [char](../../../csharp/language-reference/keywords/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="cac32-119">To platí i když vyrovnávací paměti char přeuspořádány metody rozhraní API nebo struktury s `CharSet = CharSet.Auto` nebo `CharSet = CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="cac32-119">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="cac32-120">Další informace naleznete v tématu <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="cac32-120">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>  
  
 <span data-ttu-id="cac32-121">Další běžné pole pevné velikosti je [bool](../../../csharp/language-reference/keywords/bool.md) pole.</span><span class="sxs-lookup"><span data-stu-id="cac32-121">Another common fixed-size array is the [bool](../../../csharp/language-reference/keywords/bool.md) array.</span></span> <span data-ttu-id="cac32-122">Prvky v `bool` pole jsou vždy jeden bajt velikost.</span><span class="sxs-lookup"><span data-stu-id="cac32-122">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="cac32-123">`bool`pole nejsou vhodné pro vytváření bitová pole nebo vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="cac32-123">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cac32-124">S výjimkou paměti vytvořené pomocí [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md), kompilátor jazyka C# a modul CLR (CLR) neprovádějte žádné kontroly přetečení vyrovnávací paměti zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="cac32-124">Except for memory created by using [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="cac32-125">Stejně jako u všech nezabezpečený kód, buďte opatrní.</span><span class="sxs-lookup"><span data-stu-id="cac32-125">As with all unsafe code, use caution.</span></span>  
  
 <span data-ttu-id="cac32-126">Nezabezpečené vyrovnávací paměti se liší od regulární pole následujícími způsoby:</span><span class="sxs-lookup"><span data-stu-id="cac32-126">Unsafe buffers differ from regular arrays in the following ways:</span></span>  
  
-   <span data-ttu-id="cac32-127">Nezabezpečené vyrovnávací paměti můžete použít pouze v kontextu unsafe.</span><span class="sxs-lookup"><span data-stu-id="cac32-127">You can only use unsafe buffers in an unsafe context.</span></span>  
  
-   <span data-ttu-id="cac32-128">Nezabezpečené vyrovnávací paměti jsou vždy vektory nebo jednorozměrná pole.</span><span class="sxs-lookup"><span data-stu-id="cac32-128">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>  
  
-   <span data-ttu-id="cac32-129">Deklarace pole by měla obsahovat počet, jako například `char id[8]`.</span><span class="sxs-lookup"><span data-stu-id="cac32-129">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="cac32-130">Nemůžete použít `char id[]` místo.</span><span class="sxs-lookup"><span data-stu-id="cac32-130">You cannot use `char id[]` instead.</span></span>  
  
-   <span data-ttu-id="cac32-131">Nezabezpečené vyrovnávací paměti lze pouze pole instance struktury v kontextu unsafe.</span><span class="sxs-lookup"><span data-stu-id="cac32-131">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cac32-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="cac32-132">See Also</span></span>  
 [<span data-ttu-id="cac32-133">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="cac32-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cac32-134">Nezabezpečený kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="cac32-134">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="cac32-135">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="cac32-135">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="cac32-136">Vzájemná funkční spolupráce</span><span class="sxs-lookup"><span data-stu-id="cac32-136">Interoperability</span></span>](../../../csharp/programming-guide/interop/index.md)
