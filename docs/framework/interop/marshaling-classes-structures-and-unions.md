---
title: Zařazování tříd, struktur a sjednocení
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, classes
- marshaling, unions
- marshaling, structures
- marshaling, samples
- data marshaling, structures
- platform invoke, marshaling data
- marshaling, classes
- data marshaling, unions
- data marshaling, samples
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: 027832a2-9b43-4fd9-9b45-7f4196261a4e
ms.openlocfilehash: 708ed6a232950cb69796f105f6f198749ed53a24
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200012"
---
# <a name="marshaling-classes-structures-and-unions"></a><span data-ttu-id="5043c-102">Zařazování tříd, struktur a sjednocení</span><span class="sxs-lookup"><span data-stu-id="5043c-102">Marshaling Classes, Structures, and Unions</span></span>

<span data-ttu-id="5043c-103">Třídy a struktury jsou podobné v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5043c-103">Classes and structures are similar in the .NET Framework.</span></span> <span data-ttu-id="5043c-104">Oba můžou mít pole, vlastnosti a události.</span><span class="sxs-lookup"><span data-stu-id="5043c-104">Both can have fields, properties, and events.</span></span> <span data-ttu-id="5043c-105">Mohou mít také statické a nestatické metody.</span><span class="sxs-lookup"><span data-stu-id="5043c-105">They can also have static and nonstatic methods.</span></span> <span data-ttu-id="5043c-106">Jedním z významných rozdílů je, že struktury jsou typy hodnot a třídy jsou odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="5043c-106">One notable difference is that structures are value types and classes are reference types.</span></span>

<span data-ttu-id="5043c-107">V následující tabulce jsou uvedeny možnosti zařazování pro třídy, struktury a sjednocení; popisuje jejich použití. a poskytuje odkaz na odpovídající ukázku vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="5043c-107">The following table lists marshaling options for classes, structures, and unions; describes their usage; and provides a link to the corresponding platform invoke sample.</span></span>

|<span data-ttu-id="5043c-108">Typ</span><span class="sxs-lookup"><span data-stu-id="5043c-108">Type</span></span>|<span data-ttu-id="5043c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="5043c-109">Description</span></span>|<span data-ttu-id="5043c-110">Ukázka</span><span class="sxs-lookup"><span data-stu-id="5043c-110">Sample</span></span>|
|----------|-----------------|------------|
|<span data-ttu-id="5043c-111">Třída podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="5043c-111">Class by value.</span></span>|<span data-ttu-id="5043c-112">Předá třídu s celočíselnými členy jako parametr in/out, jako je například spravovaný případ.</span><span class="sxs-lookup"><span data-stu-id="5043c-112">Passes a class with integer members as an In/Out parameter, like the managed case.</span></span>|[<span data-ttu-id="5043c-113">SysTime – ukázka</span><span class="sxs-lookup"><span data-stu-id="5043c-113">SysTime sample</span></span>](#systime-sample)|
|<span data-ttu-id="5043c-114">Struktura podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5043c-114">Structure by value.</span></span>|<span data-ttu-id="5043c-115">Předá struktury jako v parametrech.</span><span class="sxs-lookup"><span data-stu-id="5043c-115">Passes structures as In parameters.</span></span>|[<span data-ttu-id="5043c-116">Ukázka struktur</span><span class="sxs-lookup"><span data-stu-id="5043c-116">Structures sample</span></span>](#structures-sample)|
|<span data-ttu-id="5043c-117">Struktura podle odkazu</span><span class="sxs-lookup"><span data-stu-id="5043c-117">Structure by reference.</span></span>|<span data-ttu-id="5043c-118">Předává struktury jako vstupně-výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="5043c-118">Passes structures as In/Out parameters.</span></span>|<span data-ttu-id="5043c-119">[OSInfo – ukázka](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5043c-119">[OSInfo sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))</span></span>|
|<span data-ttu-id="5043c-120">Struktura s vnořenými strukturami (ploché).</span><span class="sxs-lookup"><span data-stu-id="5043c-120">Structure with nested structures (flattened).</span></span>|<span data-ttu-id="5043c-121">Předá třídu, která představuje strukturu s vnořenými strukturami v nespravované funkci.</span><span class="sxs-lookup"><span data-stu-id="5043c-121">Passes a class that represents a structure with nested structures in the unmanaged function.</span></span> <span data-ttu-id="5043c-122">Struktura je v rámci spravovaného prototypu Sloučená do jedné velké struktury.</span><span class="sxs-lookup"><span data-stu-id="5043c-122">The structure is flattened to one big structure in the managed prototype.</span></span>|[<span data-ttu-id="5043c-123">FindFile – ukázka</span><span class="sxs-lookup"><span data-stu-id="5043c-123">FindFile sample</span></span>](#findfile-sample)|
|<span data-ttu-id="5043c-124">Struktura s ukazatelem na jinou strukturu.</span><span class="sxs-lookup"><span data-stu-id="5043c-124">Structure with a pointer to another structure.</span></span>|<span data-ttu-id="5043c-125">Předá strukturu, která obsahuje ukazatel na druhou strukturu jako člen.</span><span class="sxs-lookup"><span data-stu-id="5043c-125">Passes a structure that contains a pointer to a second structure as a member.</span></span>|[<span data-ttu-id="5043c-126">Ukázka struktur</span><span class="sxs-lookup"><span data-stu-id="5043c-126">Structures Sample</span></span>](#structures-sample)|
|<span data-ttu-id="5043c-127">Pole struktur s celými čísly podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="5043c-127">Array of structures with integers by value.</span></span>|<span data-ttu-id="5043c-128">Předá pole struktur, které obsahují pouze celá čísla jako vstupně-výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="5043c-128">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="5043c-129">Členy pole lze změnit.</span><span class="sxs-lookup"><span data-stu-id="5043c-129">Members of the array can be changed.</span></span>|[<span data-ttu-id="5043c-130">Ukázka polí</span><span class="sxs-lookup"><span data-stu-id="5043c-130">Arrays Sample</span></span>](marshaling-different-types-of-arrays.md)|
|<span data-ttu-id="5043c-131">Pole struktur s celými čísly a řetězci podle odkazu</span><span class="sxs-lookup"><span data-stu-id="5043c-131">Array of structures with integers and strings by reference.</span></span>|<span data-ttu-id="5043c-132">Předá pole struktury, které obsahují celá čísla a řetězce jako výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="5043c-132">Passes an array of structures that contain integers and strings as an Out parameter.</span></span> <span data-ttu-id="5043c-133">Volaná funkce přiděluje paměť pro pole.</span><span class="sxs-lookup"><span data-stu-id="5043c-133">The called function allocates memory for the array.</span></span>|[<span data-ttu-id="5043c-134">Ukázka Outarrayofstructs –</span><span class="sxs-lookup"><span data-stu-id="5043c-134">OutArrayOfStructs Sample</span></span>](#outarrayofstructs-sample)|
|<span data-ttu-id="5043c-135">Sjednocení s typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="5043c-135">Unions with value types.</span></span>|<span data-ttu-id="5043c-136">Předá sjednocení s typy hodnot (Integer a Double).</span><span class="sxs-lookup"><span data-stu-id="5043c-136">Passes unions with value types (integer and double).</span></span>|[<span data-ttu-id="5043c-137">sjednocení – ukázka</span><span class="sxs-lookup"><span data-stu-id="5043c-137">Unions sample</span></span>](#unions-sample)|
|<span data-ttu-id="5043c-138">Sjednocení se smíšenými typy.</span><span class="sxs-lookup"><span data-stu-id="5043c-138">Unions with mixed types.</span></span>|<span data-ttu-id="5043c-139">Předá sjednocení se smíšenými typy (Integer a String).</span><span class="sxs-lookup"><span data-stu-id="5043c-139">Passes unions with mixed types (integer and string).</span></span>|[<span data-ttu-id="5043c-140">sjednocení – ukázka</span><span class="sxs-lookup"><span data-stu-id="5043c-140">Unions sample</span></span>](#unions-sample)|
|<span data-ttu-id="5043c-141">Struktura s rozložením pro konkrétní platformu.</span><span class="sxs-lookup"><span data-stu-id="5043c-141">Struct with platform-specific layout.</span></span>|<span data-ttu-id="5043c-142">Předá typ s definicemi nativního balení.</span><span class="sxs-lookup"><span data-stu-id="5043c-142">Passes a type with native-packing definitions.</span></span>|[<span data-ttu-id="5043c-143">Ukázka platformy</span><span class="sxs-lookup"><span data-stu-id="5043c-143">Platform sample</span></span>](#platform-sample)|
|<span data-ttu-id="5043c-144">Hodnoty null ve struktuře.</span><span class="sxs-lookup"><span data-stu-id="5043c-144">Null values in structure.</span></span>|<span data-ttu-id="5043c-145">Předá odkaz s hodnotou null (**Nothing** v Visual Basic) místo odkazu na typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5043c-145">Passes a null reference (**Nothing** in Visual Basic) instead of a reference to a value type.</span></span>|<span data-ttu-id="5043c-146">[HandleRef – ukázka](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="5043c-146">[HandleRef sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))</span></span>|

## <a name="structures-sample"></a><span data-ttu-id="5043c-147">Ukázka struktur</span><span class="sxs-lookup"><span data-stu-id="5043c-147">Structures sample</span></span>

<span data-ttu-id="5043c-148">Tato ukázka předvádí, jak předat strukturu, která odkazuje na druhou strukturu, předejte strukturu s vloženou strukturou a předejte strukturu vloženému poli.</span><span class="sxs-lookup"><span data-stu-id="5043c-148">This sample demonstrates how to pass a structure that points to a second structure, pass a structure with an embedded structure, and pass a structure with an embedded array.</span></span>  
  
<span data-ttu-id="5043c-149">Ukázka struktury používá následující nespravované funkce, které jsou zobrazeny s původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="5043c-149">The Structs sample uses the following unmanaged functions, shown with their original function declaration:</span></span>

- <span data-ttu-id="5043c-150">**TestStructInStruct** exportovaný z knihovny pinvokelib. dll.</span><span class="sxs-lookup"><span data-stu-id="5043c-150">**TestStructInStruct** exported from PinvokeLib.dll.</span></span>

    ```cpp
    int TestStructInStruct(MYPERSON2* pPerson2);
    ```

- <span data-ttu-id="5043c-151">**TestStructInStruct3** exportovaný z knihovny pinvokelib. dll.</span><span class="sxs-lookup"><span data-stu-id="5043c-151">**TestStructInStruct3** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestStructInStruct3(MYPERSON3 person3);
    ```

- <span data-ttu-id="5043c-152">**TestArrayInStruct** exportovaný z knihovny pinvokelib. dll.</span><span class="sxs-lookup"><span data-stu-id="5043c-152">**TestArrayInStruct** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestArrayInStruct(MYARRAYSTRUCT* pStruct);
    ```

<span data-ttu-id="5043c-153">[Knihovny pinvokelib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) je vlastní nespravovaná knihovna, která obsahuje implementace pro dříve uvedené funkce a čtyři struktury: **MYPERSON**, **MYPERSON2**, **MYPERSON3**a **MYARRAYSTRUCT**.</span><span class="sxs-lookup"><span data-stu-id="5043c-153">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and four structures: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, and **MYARRAYSTRUCT**.</span></span> <span data-ttu-id="5043c-154">Tyto struktury obsahují následující prvky:</span><span class="sxs-lookup"><span data-stu-id="5043c-154">These structures contain the following elements:</span></span>

```cpp
typedef struct _MYPERSON
{
   char* first;
   char* last;
} MYPERSON, *LP_MYPERSON;

typedef struct _MYPERSON2
{
   MYPERSON* person;
   int age;
} MYPERSON2, *LP_MYPERSON2;

typedef struct _MYPERSON3
{
   MYPERSON person;
   int age;
} MYPERSON3;

typedef struct _MYARRAYSTRUCT
{
   bool flag;
   int vals[ 3 ];
} MYARRAYSTRUCT;
```

<span data-ttu-id="5043c-155">Struktury spravované `MyPerson`, `MyPerson2`, `MyPerson3`a `MyArrayStruct` mají následující charakteristiky:</span><span class="sxs-lookup"><span data-stu-id="5043c-155">The managed `MyPerson`, `MyPerson2`, `MyPerson3`, and `MyArrayStruct` structures have the following characteristic:</span></span>

- <span data-ttu-id="5043c-156">`MyPerson`obsahuje pouze členy řetězce.</span><span class="sxs-lookup"><span data-stu-id="5043c-156">`MyPerson` contains only string members.</span></span> <span data-ttu-id="5043c-157">Pole [CharSet](specifying-a-character-set.md) nastaví řetězce na formát ANSI při předání do nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="5043c-157">The [CharSet](specifying-a-character-set.md) field sets the strings to ANSI format when passed to the unmanaged function.</span></span>

- <span data-ttu-id="5043c-158">`MyPerson2`obsahuje **IntPtr** ke `MyPerson` struktuře.</span><span class="sxs-lookup"><span data-stu-id="5043c-158">`MyPerson2` contains an **IntPtr** to the `MyPerson` structure.</span></span> <span data-ttu-id="5043c-159">Typ **IntPtr** nahrazuje původní ukazatel na nespravovanou strukturu, protože .NET Framework aplikace nepoužívají ukazatele, pokud není kód označen jako **nebezpečný**.</span><span class="sxs-lookup"><span data-stu-id="5043c-159">The **IntPtr** type replaces the original pointer to the unmanaged structure because .NET Framework applications do not use pointers unless the code is marked **unsafe**.</span></span>

- <span data-ttu-id="5043c-160">`MyPerson3`obsahuje `MyPerson` jako vloženou strukturu.</span><span class="sxs-lookup"><span data-stu-id="5043c-160">`MyPerson3` contains `MyPerson` as an embedded structure.</span></span> <span data-ttu-id="5043c-161">Strukturu vloženou v jiné struktuře lze sloučit umístěním prvků vložené struktury přímo do hlavní struktury, nebo může být ponechána jako vložená struktura, jak je provedeno v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="5043c-161">A structure embedded within another structure can be flattened by placing the elements of the embedded structure directly into the main structure, or it can be left as an embedded structure, as is done in this sample.</span></span>

- <span data-ttu-id="5043c-162">`MyArrayStruct`obsahuje pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="5043c-162">`MyArrayStruct` contains an array of integers.</span></span> <span data-ttu-id="5043c-163"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nastaví hodnotu <xref:System.Runtime.InteropServices.UnmanagedType> výčtu na **ByValArray**, která slouží k označení počtu prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="5043c-163">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration value to **ByValArray**, which is used to indicate the number of elements in the array.</span></span>

<span data-ttu-id="5043c-164">Pro všechny struktury v této ukázce se používá <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut, aby bylo zajištěno, že jsou členy uspořádány v paměti postupně, v pořadí, ve kterém jsou uvedeny.</span><span class="sxs-lookup"><span data-stu-id="5043c-164">For all structures in this sample, the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is applied to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>

<span data-ttu-id="5043c-165">`NativeMethods` Třída obsahuje `TestStructInStruct`spravované prototypy pro, a `TestStructInStruct3` `TestArrayInStruct` metody, které jsou `App` volány třídou.</span><span class="sxs-lookup"><span data-stu-id="5043c-165">The `NativeMethods` class contains managed prototypes for the `TestStructInStruct`, `TestStructInStruct3`, and `TestArrayInStruct` methods called by the `App` class.</span></span> <span data-ttu-id="5043c-166">Každý prototyp deklaruje jeden parametr následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5043c-166">Each prototype declares a single parameter, as follows:</span></span>

- <span data-ttu-id="5043c-167">`TestStructInStruct`deklaruje odkaz na typ `MyPerson2` jako jeho parametr.</span><span class="sxs-lookup"><span data-stu-id="5043c-167">`TestStructInStruct` declares a reference to type `MyPerson2` as its parameter.</span></span>

- <span data-ttu-id="5043c-168">`TestStructInStruct3`Deklaruje typ `MyPerson3` jako svůj parametr a předá parametr podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5043c-168">`TestStructInStruct3` declares type `MyPerson3` as its parameter and passes the parameter by value.</span></span>

- <span data-ttu-id="5043c-169">`TestArrayInStruct`deklaruje odkaz na typ `MyArrayStruct` jako jeho parametr.</span><span class="sxs-lookup"><span data-stu-id="5043c-169">`TestArrayInStruct` declares a reference to type `MyArrayStruct` as its parameter.</span></span>

<span data-ttu-id="5043c-170">Struktury jako argumenty metod jsou předávány hodnotou, pokud parametr neobsahuje klíčové slovo **ref** (**ByRef** in Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="5043c-170">Structures as arguments to methods are passed by value unless the parameter contains the **ref** (**ByRef** in Visual Basic) keyword.</span></span> <span data-ttu-id="5043c-171">Například `TestStructInStruct` metoda předává odkaz (hodnota adresy) objektu typu `MyPerson2` na nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="5043c-171">For example, the `TestStructInStruct` method passes a reference (the value of an address) to an object of type `MyPerson2` to unmanaged code.</span></span> <span data-ttu-id="5043c-172">Aby bylo možné manipulovat se strukturou, na kterou `MyPerson2` odkazuje, ukázka vytvoří vyrovnávací paměť zadané velikosti a vrátí její adresu kombinací metod <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> a. <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5043c-172">To manipulate the structure that `MyPerson2` points to, the sample creates a buffer of a specified size and returns its address by combining the <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="5043c-173">V dalším kroku zkopíruje ukázka obsah spravované struktury do nespravované vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="5043c-173">Next, the sample copies the content of the managed structure to the unmanaged buffer.</span></span> <span data-ttu-id="5043c-174">Nakonec ukázka používá <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> metodu pro zařazování dat z nespravované vyrovnávací paměti do spravovaného objektu a <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> metodu pro uvolnění nespravovaného bloku paměti.</span><span class="sxs-lookup"><span data-stu-id="5043c-174">Finally, the sample uses the <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> method to marshal data from the unmanaged buffer to a managed object and the <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> method to free the unmanaged block of memory.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="5043c-175">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="5043c-175">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#23](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
[!code-csharp[Conceptual.Interop.Marshaling#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
[!code-vb[Conceptual.Interop.Marshaling#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]

### <a name="calling-functions"></a><span data-ttu-id="5043c-176">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="5043c-176">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#24](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
[!code-csharp[Conceptual.Interop.Marshaling#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
[!code-vb[Conceptual.Interop.Marshaling#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]

## <a name="findfile-sample"></a><span data-ttu-id="5043c-177">FindFile – ukázka</span><span class="sxs-lookup"><span data-stu-id="5043c-177">FindFile sample</span></span>

<span data-ttu-id="5043c-178">Tato ukázka předvádí, jak předat strukturu, která obsahuje druhou, vloženou strukturu do nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="5043c-178">This sample demonstrates how to pass a structure that contains a second, embedded structure to an unmanaged function.</span></span> <span data-ttu-id="5043c-179">Také ukazuje, jak použít <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut k deklaraci pole s pevnou délkou v rámci struktury.</span><span class="sxs-lookup"><span data-stu-id="5043c-179">It also demonstrates how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to declare a fixed-length array within the structure.</span></span> <span data-ttu-id="5043c-180">V této ukázce jsou vložené prvky struktury přidány do nadřazené struktury.</span><span class="sxs-lookup"><span data-stu-id="5043c-180">In this sample, the embedded structure elements are added to the parent structure.</span></span> <span data-ttu-id="5043c-181">Ukázku vložené struktury, která není shrnuta, naleznete v části [struktury Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="5043c-181">For a sample of an embedded structure that is not flattened, see [Structures Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span></span>

<span data-ttu-id="5043c-182">Ukázka FindFile – používá následující nespravovanou funkci, která se zobrazuje s její původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="5043c-182">The FindFile sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="5043c-183">**FindFirstFile** exportovaný z Kernel32. dll.</span><span class="sxs-lookup"><span data-stu-id="5043c-183">**FindFirstFile** exported from Kernel32.dll.</span></span>

    ```cpp
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);
    ```

<span data-ttu-id="5043c-184">Původní struktura předaná funkci obsahuje následující prvky:</span><span class="sxs-lookup"><span data-stu-id="5043c-184">The original structure passed to the function contains the following elements:</span></span>

```cpp
typedef struct _WIN32_FIND_DATA
{
  DWORD    dwFileAttributes;
  FILETIME ftCreationTime;
  FILETIME ftLastAccessTime;
  FILETIME ftLastWriteTime;
  DWORD    nFileSizeHigh;
  DWORD    nFileSizeLow;
  DWORD    dwReserved0;
  DWORD    dwReserved1;
  TCHAR    cFileName[ MAX_PATH ];
  TCHAR    cAlternateFileName[ 14 ];
} WIN32_FIND_DATA, *PWIN32_FIND_DATA;
```

<span data-ttu-id="5043c-185">V této ukázce `FindData` třída obsahuje odpovídající datový člen pro každý prvek původní struktury a vloženou strukturu.</span><span class="sxs-lookup"><span data-stu-id="5043c-185">In this sample, the `FindData` class contains a corresponding data member for each element of the original structure and the embedded structure.</span></span> <span data-ttu-id="5043c-186">Místo dvou původních vyrovnávacích pamětí znaků třída nahradí řetězce.</span><span class="sxs-lookup"><span data-stu-id="5043c-186">In place of two original character buffers, the class substitutes strings.</span></span> <span data-ttu-id="5043c-187">**MarshalAsAttribute** nastaví <xref:System.Runtime.InteropServices.UnmanagedType> výčet na **ByValTStr**, který slouží k identifikaci vložených znakových polí s pevnou délkou, která se zobrazí v nespravovaných strukturách.</span><span class="sxs-lookup"><span data-stu-id="5043c-187">**MarshalAsAttribute** sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged structures.</span></span>

<span data-ttu-id="5043c-188">`NativeMethods` Třída obsahuje spravovaný prototyp `FindFirstFile` metody, která předá `FindData` třídu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="5043c-188">The `NativeMethods` class contains a managed prototype of the `FindFirstFile` method, which passes the `FindData` class as a parameter.</span></span> <span data-ttu-id="5043c-189">Parametr musí být deklarován s atributy <xref:System.Runtime.InteropServices.InAttribute> a <xref:System.Runtime.InteropServices.OutAttribute> , protože třídy, které jsou odkazové typy, jsou předány jako parametry ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="5043c-189">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="5043c-190">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="5043c-190">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#17](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
[!code-csharp[Conceptual.Interop.Marshaling#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
[!code-vb[Conceptual.Interop.Marshaling#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]

### <a name="calling-functions"></a><span data-ttu-id="5043c-191">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="5043c-191">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#18](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
[!code-csharp[Conceptual.Interop.Marshaling#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]

## <a name="unions-sample"></a><span data-ttu-id="5043c-192">sjednocení – ukázka</span><span class="sxs-lookup"><span data-stu-id="5043c-192">Unions sample</span></span>

<span data-ttu-id="5043c-193">Tato ukázka předvádí, jak předat struktury obsahující pouze typy hodnot a struktury obsahující typ hodnoty a řetězec jako parametry nespravované funkce, které očekávají sjednocení.</span><span class="sxs-lookup"><span data-stu-id="5043c-193">This sample demonstrates how to pass structures containing only value types, and structures containing a value type and a string as parameters to an unmanaged function expecting a union.</span></span> <span data-ttu-id="5043c-194">Sjednocení představuje umístění v paměti, které může být sdíleno dvěma nebo více proměnnými.</span><span class="sxs-lookup"><span data-stu-id="5043c-194">A union represents a memory location that can be shared by two or more variables.</span></span>

<span data-ttu-id="5043c-195">Vzor sjednocení používá následující nespravovanou funkci zobrazenou s původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="5043c-195">The Unions sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="5043c-196">**TestUnion** exportovaný z knihovny pinvokelib. dll.</span><span class="sxs-lookup"><span data-stu-id="5043c-196">**TestUnion** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestUnion(MYUNION u, int type);
    ```

<span data-ttu-id="5043c-197">[Knihovny pinvokelib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) je vlastní nespravovaná knihovna, která obsahuje implementaci dříve uvedené funkce a dvou sjednocení, **MYUNION** a **MYUNION2**.</span><span class="sxs-lookup"><span data-stu-id="5043c-197">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed function and two unions, **MYUNION** and **MYUNION2**.</span></span> <span data-ttu-id="5043c-198">Sjednocení obsahují následující prvky:</span><span class="sxs-lookup"><span data-stu-id="5043c-198">The unions contain the following elements:</span></span>

```cpp
union MYUNION
{
    int number;
    double d;
}

union MYUNION2
{
    int i;
    char str[128];
};
```

<span data-ttu-id="5043c-199">Ve spravovaném kódu jsou sjednocení definována jako struktury.</span><span class="sxs-lookup"><span data-stu-id="5043c-199">In managed code, unions are defined as structures.</span></span> <span data-ttu-id="5043c-200">`MyUnion` Struktura obsahuje dva typy hodnot jako členy: celé číslo a typ Double.</span><span class="sxs-lookup"><span data-stu-id="5043c-200">The `MyUnion` structure contains two value types as its members: an integer and a double.</span></span> <span data-ttu-id="5043c-201"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Atribut je nastaven na řízení přesné pozice jednotlivých datových členů.</span><span class="sxs-lookup"><span data-stu-id="5043c-201">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to control the precise position of each data member.</span></span> <span data-ttu-id="5043c-202"><xref:System.Runtime.InteropServices.FieldOffsetAttribute> Atribut poskytuje fyzickou pozici polí v rámci nespravované reprezentace sjednocení.</span><span class="sxs-lookup"><span data-stu-id="5043c-202">The <xref:System.Runtime.InteropServices.FieldOffsetAttribute> attribute provides the physical position of fields within the unmanaged representation of a union.</span></span> <span data-ttu-id="5043c-203">Všimněte si, že oba členové mají stejné hodnoty posunutí, takže členové mohou definovat stejnou část paměti.</span><span class="sxs-lookup"><span data-stu-id="5043c-203">Notice that both members have the same offset values, so the members can define the same piece of memory.</span></span>

<span data-ttu-id="5043c-204">`MyUnion2_1`a `MyUnion2_2` obsahují hodnotový typ (Integer) a řetězec v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="5043c-204">`MyUnion2_1` and `MyUnion2_2` contain a value type (integer) and a string, respectively.</span></span> <span data-ttu-id="5043c-205">Ve spravovaném kódu se typy hodnot a typy odkazů nepovolují překrývat.</span><span class="sxs-lookup"><span data-stu-id="5043c-205">In managed code, value types and reference types are not permitted to overlap.</span></span> <span data-ttu-id="5043c-206">Tato ukázka používá přetížení metody, aby volající mohl použít oba typy při volání stejné nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="5043c-206">This sample uses method overloading to enable the caller to use both types when calling the same unmanaged function.</span></span> <span data-ttu-id="5043c-207">Rozložení `MyUnion2_1` je explicitní a má přesnou hodnotu posunu.</span><span class="sxs-lookup"><span data-stu-id="5043c-207">The layout of `MyUnion2_1` is explicit and has a precise offset value.</span></span> <span data-ttu-id="5043c-208">Naproti tomu `MyUnion2_2` má sekvenční rozložení, protože explicitní rozložení nejsou povolena s odkazovým typem.</span><span class="sxs-lookup"><span data-stu-id="5043c-208">In contrast, `MyUnion2_2` has a sequential layout, because explicit layouts are not permitted with reference types.</span></span> <span data-ttu-id="5043c-209"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nastaví <xref:System.Runtime.InteropServices.UnmanagedType> výčet na **ByValTStr**, který se používá k identifikaci vložených znakových polí s pevnou délkou, která se zobrazí v nespravovaném vyjádření sjednocení.</span><span class="sxs-lookup"><span data-stu-id="5043c-209">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged representation of the union.</span></span>

<span data-ttu-id="5043c-210">`NativeMethods` Třída obsahuje prototypy pro metody `TestUnion` a `TestUnion2` .</span><span class="sxs-lookup"><span data-stu-id="5043c-210">The `NativeMethods` class contains the prototypes for the `TestUnion` and `TestUnion2` methods.</span></span> <span data-ttu-id="5043c-211">`TestUnion2`je přetížený pro deklaraci `MyUnion2_1` nebo `MyUnion2_2` jako parametry.</span><span class="sxs-lookup"><span data-stu-id="5043c-211">`TestUnion2` is overloaded to declare `MyUnion2_1` or `MyUnion2_2` as parameters.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="5043c-212">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="5043c-212">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#28](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
[!code-csharp[Conceptual.Interop.Marshaling#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
[!code-vb[Conceptual.Interop.Marshaling#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]

### <a name="calling-functions"></a><span data-ttu-id="5043c-213">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="5043c-213">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#29](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
[!code-csharp[Conceptual.Interop.Marshaling#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
[!code-vb[Conceptual.Interop.Marshaling#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]

## <a name="platform-sample"></a><span data-ttu-id="5043c-214">Ukázka platformy</span><span class="sxs-lookup"><span data-stu-id="5043c-214">Platform sample</span></span>

<span data-ttu-id="5043c-215">V některých scénářích `struct` se `union` rozložení může lišit v závislosti na cílové platformě.</span><span class="sxs-lookup"><span data-stu-id="5043c-215">In some scenarios, `struct` and `union` layouts can differ depending on the targeted platform.</span></span> <span data-ttu-id="5043c-216">Zvažte například typ, který [`STRRET`](/windows/win32/api/shtypes/ns-shtypes-strret) je definován ve scénáři modelu com:</span><span class="sxs-lookup"><span data-stu-id="5043c-216">For example, consider the [`STRRET`](/windows/win32/api/shtypes/ns-shtypes-strret) type when defined in a COM scenario:</span></span>

```c++
#include <pshpack8.h> /* Defines the packing of the struct */
typedef struct _STRRET
    {
    UINT uType;
    /* [switch_is][switch_type] */ union
        {
        /* [case()][string] */ LPWSTR pOleStr;
        /* [case()] */ UINT uOffset;
        /* [case()] */ char cStr[ 260 ];
        }  DUMMYUNIONNAME;
    }  STRRET;
#include <poppack.h>
```

<span data-ttu-id="5043c-217">Výše uvedená `struct` deklarace je deklarována s hlavičkou systému Windows, které mají vliv na rozložení paměti daného typu.</span><span class="sxs-lookup"><span data-stu-id="5043c-217">The above `struct` is declared with Windows' headers that influence the memory layout of the type.</span></span> <span data-ttu-id="5043c-218">Pokud je definována ve spravovaném prostředí, tyto podrobnosti o rozložení jsou potřeba ke správné spolupráci s nativním kódem.</span><span class="sxs-lookup"><span data-stu-id="5043c-218">When defined in a managed environment, these layout details are needed to properly interoperate with native code.</span></span>

<span data-ttu-id="5043c-219">Správná spravovaná definice tohoto typu v rámci 32 procesu je:</span><span class="sxs-lookup"><span data-stu-id="5043c-219">The correct managed definition of this type in a 32-bit process is:</span></span>

``` CSharp
[StructLayout(LayoutKind.Explicit, Size = 264)]
public struct STRRET_32
{
    [FieldOffset(0)]
    public uint uType;

    [FieldOffset(4)]
    public IntPtr pOleStr;

    [FieldOffset(4)]
    public uint uOffset;

    [FieldOffset(4)]
    public IntPtr cStr;
}
```

<span data-ttu-id="5043c-220">U 64 procesu se velikost *a* posunutí polí liší.</span><span class="sxs-lookup"><span data-stu-id="5043c-220">On a 64-bit process, the size *and* field offsets are different.</span></span> <span data-ttu-id="5043c-221">Správné rozložení je:</span><span class="sxs-lookup"><span data-stu-id="5043c-221">The correct layout is:</span></span>

``` CSharp
[StructLayout(LayoutKind.Explicit, Size = 272)]
public struct STRRET_64
{
    [FieldOffset(0)]
    public uint uType;

    [FieldOffset(8)]
    public IntPtr pOleStr;

    [FieldOffset(8)]
    public uint uOffset;

    [FieldOffset(8)]
    public IntPtr cStr;
}
```

<span data-ttu-id="5043c-222">Při nesprávném zvážení nativního rozložení ve scénáři spolupráce může dojít k náhodným chybám nebo horším, nesprávným výpočtům.</span><span class="sxs-lookup"><span data-stu-id="5043c-222">Failure to properly consider the native layout in an interop scenario can result in random crashes or worse, incorrect computations.</span></span>

<span data-ttu-id="5043c-223">Ve výchozím nastavení mohou být sestavení .NET spouštěna v 32 a 64 verze modulu runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="5043c-223">By default, .NET assemblies can run in both a 32-bit and 64-bit version of the .NET runtime.</span></span> <span data-ttu-id="5043c-224">Aplikace musí počkat, než čas spuštění určí, který z předchozích definic se má použít.</span><span class="sxs-lookup"><span data-stu-id="5043c-224">The app must wait until run time to decide which of the previous definitions to use.</span></span>

<span data-ttu-id="5043c-225">Následující fragment kódu ukazuje příklad, jak zvolit mezi 32 a 64 bitů definice v době běhu.</span><span class="sxs-lookup"><span data-stu-id="5043c-225">The following code snippet shows an example of how to choose between the 32-bit and 64-bit definition at run time.</span></span>

```CSharp
if (IntPtr.Size == 8)
{
    // Use the STRRET_64 definition
}
else
{
    Debug.Assert(IntPtr.Size == 4);
    // Use the STRRET_32 definition
}
```

## <a name="systime-sample"></a><span data-ttu-id="5043c-226">SysTime – ukázka</span><span class="sxs-lookup"><span data-stu-id="5043c-226">SysTime sample</span></span>

<span data-ttu-id="5043c-227">Tato ukázka předvádí, jak předat ukazatel na třídu nespravované funkci, která očekává ukazatel na strukturu.</span><span class="sxs-lookup"><span data-stu-id="5043c-227">This sample demonstrates how to pass a pointer to a class to an unmanaged function that expects a pointer to a structure.</span></span>

<span data-ttu-id="5043c-228">Ukázka sysTime – používá následující nespravovanou funkci, která se zobrazuje s její původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="5043c-228">The SysTime sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="5043c-229">**GetSystemTime** exportovaný z Kernel32. dll.</span><span class="sxs-lookup"><span data-stu-id="5043c-229">**GetSystemTime** exported from Kernel32.dll.</span></span>

    ```cpp
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);
    ```

<span data-ttu-id="5043c-230">Původní struktura předaná funkci obsahuje následující prvky:</span><span class="sxs-lookup"><span data-stu-id="5043c-230">The original structure passed to the function contains the following elements:</span></span>

```cpp
typedef struct _SYSTEMTIME {
    WORD wYear;
    WORD wMonth;
    WORD wDayOfWeek;
    WORD wDay;
    WORD wHour;
    WORD wMinute;
    WORD wSecond;
    WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME;
```

<span data-ttu-id="5043c-231">V této ukázce `SystemTime` třída obsahuje prvky původní struktury reprezentované jako členy třídy.</span><span class="sxs-lookup"><span data-stu-id="5043c-231">In this sample, the `SystemTime` class contains the elements of the original structure represented as class members.</span></span> <span data-ttu-id="5043c-232"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Atribut je nastaven tak, aby bylo zajištěno, že jsou členy uspořádány v paměti sekvenčně v pořadí, ve kterém jsou zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="5043c-232">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>

<span data-ttu-id="5043c-233">`NativeMethods` Třída obsahuje spravovaný prototyp `GetSystemTime` metody, která ve výchozím nastavení předává `SystemTime` třídu jako vstupně-výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="5043c-233">The `NativeMethods` class contains a managed prototype of the `GetSystemTime` method, which passes the `SystemTime` class as an In/Out parameter by default.</span></span> <span data-ttu-id="5043c-234">Parametr musí být deklarován s atributy <xref:System.Runtime.InteropServices.InAttribute> a <xref:System.Runtime.InteropServices.OutAttribute> , protože třídy, které jsou odkazové typy, jsou předány jako parametry ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="5043c-234">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span> <span data-ttu-id="5043c-235">Aby volající mohl přijímat výsledky, musí být tyto [směrové atributy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) aplikovány explicitně.</span><span class="sxs-lookup"><span data-stu-id="5043c-235">For the caller to receive the results, these [directional attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) must be applied explicitly.</span></span> <span data-ttu-id="5043c-236">`App` Třída vytvoří novou instanci `SystemTime` třídy a přistupuje k jejím datovým polím.</span><span class="sxs-lookup"><span data-stu-id="5043c-236">The `App` class creates a new instance of the `SystemTime` class and accesses its data fields.</span></span>

### <a name="code-samples"></a><span data-ttu-id="5043c-237">Ukázky kódů</span><span class="sxs-lookup"><span data-stu-id="5043c-237">Code Samples</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#25](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
[!code-csharp[Conceptual.Interop.Marshaling#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
[!code-vb[Conceptual.Interop.Marshaling#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]

## <a name="outarrayofstructs-sample"></a><span data-ttu-id="5043c-238">OutArrayOfStructs – ukázka</span><span class="sxs-lookup"><span data-stu-id="5043c-238">OutArrayOfStructs sample</span></span>

<span data-ttu-id="5043c-239">Tento příklad ukazuje, jak předat pole struktur obsahující celá čísla a řetězce jako výstupní parametry nespravované funkci.</span><span class="sxs-lookup"><span data-stu-id="5043c-239">This sample shows how to pass an array of structures that contains integers and strings as Out parameters to an unmanaged function.</span></span>

<span data-ttu-id="5043c-240">Tento příklad ukazuje, jak volat nativní funkci pomocí <xref:System.Runtime.InteropServices.Marshal> třídy a pomocí nebezpečného kódu.</span><span class="sxs-lookup"><span data-stu-id="5043c-240">This sample demonstrates how to call a native function by using the <xref:System.Runtime.InteropServices.Marshal> class and by using unsafe code.</span></span>

<span data-ttu-id="5043c-241">Tato ukázka používá funkce obálky a vyvolání platformy definované v [knihovny pinvokelib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), které jsou také k dispozici ve zdrojových souborech.</span><span class="sxs-lookup"><span data-stu-id="5043c-241">This sample uses a wrapper functions and platform invokes defined in [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), also provided in the source files.</span></span> <span data-ttu-id="5043c-242">Používá `TestOutArrayOfStructs` funkci a `MYSTRSTRUCT2` strukturu.</span><span class="sxs-lookup"><span data-stu-id="5043c-242">It uses the `TestOutArrayOfStructs` function and the `MYSTRSTRUCT2` structure.</span></span> <span data-ttu-id="5043c-243">Struktura obsahuje následující prvky:</span><span class="sxs-lookup"><span data-stu-id="5043c-243">The structure contains the following elements:</span></span>

```cpp
typedef struct _MYSTRSTRUCT2
{
   char* buffer;
   UINT size;
} MYSTRSTRUCT2;
```

<span data-ttu-id="5043c-244">`MyStruct` Třída obsahuje objekt řetězce znaků ANSI.</span><span class="sxs-lookup"><span data-stu-id="5043c-244">The `MyStruct` class contains a string object of ANSI characters.</span></span> <span data-ttu-id="5043c-245"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> Pole určuje formát ANSI.</span><span class="sxs-lookup"><span data-stu-id="5043c-245">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field specifies ANSI format.</span></span> <span data-ttu-id="5043c-246">`MyUnsafeStruct`, je struktura obsahující <xref:System.IntPtr> typ místo řetězce.</span><span class="sxs-lookup"><span data-stu-id="5043c-246">`MyUnsafeStruct`, is a structure containing an <xref:System.IntPtr> type instead of a string.</span></span>

<span data-ttu-id="5043c-247">`NativeMethods` Třída obsahuje přetíženou metodu `TestOutArrayOfStructs` prototypu.</span><span class="sxs-lookup"><span data-stu-id="5043c-247">The `NativeMethods` class contains the overloaded `TestOutArrayOfStructs` prototype method.</span></span> <span data-ttu-id="5043c-248">Pokud metoda deklaruje ukazatel jako parametr, třída by měla být označena `unsafe` klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="5043c-248">If a method declares a pointer as a parameter, the class should be marked with the `unsafe` keyword.</span></span> <span data-ttu-id="5043c-249">Vzhledem k tomu, že Visual Basic nemůže použít nezabezpečený kód, přetíženou metodu, nezabezpečený modifikátor a `MyUnsafeStruct` strukturu jsou zbytečné.</span><span class="sxs-lookup"><span data-stu-id="5043c-249">Because Visual Basic cannot use unsafe code, the overloaded method, unsafe modifier, and the `MyUnsafeStruct` structure are unnecessary.</span></span>

<span data-ttu-id="5043c-250">`App` Třída implementuje `UsingMarshaling` metodu, která provádí všechny úlohy, které jsou nezbytné k předání pole.</span><span class="sxs-lookup"><span data-stu-id="5043c-250">The `App` class implements the `UsingMarshaling` method, which performs all the tasks necessary to pass the array.</span></span> <span data-ttu-id="5043c-251">Pole je označeno pomocí `out` klíčového`ByRef` slova (v Visual Basic) k označení toho, že data přecházejí z volaného volajícího.</span><span class="sxs-lookup"><span data-stu-id="5043c-251">The array is marked with the `out` (`ByRef` in Visual Basic) keyword to indicate that data passes from callee to caller.</span></span> <span data-ttu-id="5043c-252">Implementace používá následující <xref:System.Runtime.InteropServices.Marshal> metody třídy:</span><span class="sxs-lookup"><span data-stu-id="5043c-252">The implementation uses the following <xref:System.Runtime.InteropServices.Marshal> class methods:</span></span>

- <span data-ttu-id="5043c-253"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A>pro zařazování dat z nespravované vyrovnávací paměti do spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="5043c-253"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> to marshal data from the unmanaged buffer to a managed object.</span></span>

- <span data-ttu-id="5043c-254"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A>uvolnění paměti rezervované pro řetězce ve struktuře.</span><span class="sxs-lookup"><span data-stu-id="5043c-254"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> to release the memory reserved for strings in the structure.</span></span>

- <span data-ttu-id="5043c-255"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>uvolnění paměti rezervované pro dané pole.</span><span class="sxs-lookup"><span data-stu-id="5043c-255"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> to release the memory reserved for the array.</span></span>

<span data-ttu-id="5043c-256">Jak už jsme uvedli, C# umožňuje nezabezpečený kód a Visual Basic ne.</span><span class="sxs-lookup"><span data-stu-id="5043c-256">As previously mentioned, C# allows unsafe code and Visual Basic does not.</span></span> <span data-ttu-id="5043c-257">V ukázce jazyka C# `UsingUnsafePointer` je alternativou implementace metody, která používá ukazatele namísto <xref:System.Runtime.InteropServices.Marshal> třídy k předání pole obsahujícího `MyUnsafeStruct` strukturu.</span><span class="sxs-lookup"><span data-stu-id="5043c-257">In the C# sample, `UsingUnsafePointer` is an alternative method implementation that uses pointers instead of the <xref:System.Runtime.InteropServices.Marshal> class to pass back the array containing the `MyUnsafeStruct` structure.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="5043c-258">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="5043c-258">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#20](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
[!code-csharp[Conceptual.Interop.Marshaling#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
[!code-vb[Conceptual.Interop.Marshaling#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]

### <a name="calling-functions"></a><span data-ttu-id="5043c-259">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="5043c-259">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#21](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
[!code-csharp[Conceptual.Interop.Marshaling#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
[!code-vb[Conceptual.Interop.Marshaling#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]

## <a name="see-also"></a><span data-ttu-id="5043c-260">Viz také</span><span class="sxs-lookup"><span data-stu-id="5043c-260">See also</span></span>

- [<span data-ttu-id="5043c-261">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="5043c-261">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
- [<span data-ttu-id="5043c-262">Zařazování řetězců</span><span class="sxs-lookup"><span data-stu-id="5043c-262">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="5043c-263">Zařazování různých typů polí</span><span class="sxs-lookup"><span data-stu-id="5043c-263">Marshaling Different Types of Arrays</span></span>](marshaling-different-types-of-arrays.md)
