---
title: Zařazování tříd, struktur a sjednocení
description: Přečtěte si, jak zařazovat třídy, struktury a sjednocení. Zobrazte si ukázky zařazování tříd, struktur s vnořenými strukturami, poli struktur a sjednocení.
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
ms.openlocfilehash: 5e616b5bb513939cadd8fe5c72675ba0b6e070a3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621519"
---
# <a name="marshaling-classes-structures-and-unions"></a><span data-ttu-id="dafbd-104">Zařazování tříd, struktur a sjednocení</span><span class="sxs-lookup"><span data-stu-id="dafbd-104">Marshaling Classes, Structures, and Unions</span></span>

<span data-ttu-id="dafbd-105">Třídy a struktury jsou podobné v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dafbd-105">Classes and structures are similar in the .NET Framework.</span></span> <span data-ttu-id="dafbd-106">Oba můžou mít pole, vlastnosti a události.</span><span class="sxs-lookup"><span data-stu-id="dafbd-106">Both can have fields, properties, and events.</span></span> <span data-ttu-id="dafbd-107">Mohou mít také statické a nestatické metody.</span><span class="sxs-lookup"><span data-stu-id="dafbd-107">They can also have static and nonstatic methods.</span></span> <span data-ttu-id="dafbd-108">Jedním z významných rozdílů je, že struktury jsou typy hodnot a třídy jsou odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="dafbd-108">One notable difference is that structures are value types and classes are reference types.</span></span>

<span data-ttu-id="dafbd-109">V následující tabulce jsou uvedeny možnosti zařazování pro třídy, struktury a sjednocení; popisuje jejich použití. a poskytuje odkaz na odpovídající ukázku vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="dafbd-109">The following table lists marshaling options for classes, structures, and unions; describes their usage; and provides a link to the corresponding platform invoke sample.</span></span>

|<span data-ttu-id="dafbd-110">Typ</span><span class="sxs-lookup"><span data-stu-id="dafbd-110">Type</span></span>|<span data-ttu-id="dafbd-111">Popis</span><span class="sxs-lookup"><span data-stu-id="dafbd-111">Description</span></span>|<span data-ttu-id="dafbd-112">Ukázka</span><span class="sxs-lookup"><span data-stu-id="dafbd-112">Sample</span></span>|
|----------|-----------------|------------|
|<span data-ttu-id="dafbd-113">Třída podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="dafbd-113">Class by value.</span></span>|<span data-ttu-id="dafbd-114">Předá třídu s celočíselnými členy jako parametr in/out, jako je například spravovaný případ.</span><span class="sxs-lookup"><span data-stu-id="dafbd-114">Passes a class with integer members as an In/Out parameter, like the managed case.</span></span>|[<span data-ttu-id="dafbd-115">SysTime – ukázka</span><span class="sxs-lookup"><span data-stu-id="dafbd-115">SysTime sample</span></span>](#systime-sample)|
|<span data-ttu-id="dafbd-116">Struktura podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="dafbd-116">Structure by value.</span></span>|<span data-ttu-id="dafbd-117">Předá struktury jako v parametrech.</span><span class="sxs-lookup"><span data-stu-id="dafbd-117">Passes structures as In parameters.</span></span>|[<span data-ttu-id="dafbd-118">Ukázka struktur</span><span class="sxs-lookup"><span data-stu-id="dafbd-118">Structures sample</span></span>](#structures-sample)|
|<span data-ttu-id="dafbd-119">Struktura podle odkazu</span><span class="sxs-lookup"><span data-stu-id="dafbd-119">Structure by reference.</span></span>|<span data-ttu-id="dafbd-120">Předává struktury jako vstupně-výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="dafbd-120">Passes structures as In/Out parameters.</span></span>|<span data-ttu-id="dafbd-121">[OSInfo – ukázka](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dafbd-121">[OSInfo sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))</span></span>|
|<span data-ttu-id="dafbd-122">Struktura s vnořenými strukturami (ploché).</span><span class="sxs-lookup"><span data-stu-id="dafbd-122">Structure with nested structures (flattened).</span></span>|<span data-ttu-id="dafbd-123">Předá třídu, která představuje strukturu s vnořenými strukturami v nespravované funkci.</span><span class="sxs-lookup"><span data-stu-id="dafbd-123">Passes a class that represents a structure with nested structures in the unmanaged function.</span></span> <span data-ttu-id="dafbd-124">Struktura je v rámci spravovaného prototypu Sloučená do jedné velké struktury.</span><span class="sxs-lookup"><span data-stu-id="dafbd-124">The structure is flattened to one big structure in the managed prototype.</span></span>|[<span data-ttu-id="dafbd-125">FindFile – ukázka</span><span class="sxs-lookup"><span data-stu-id="dafbd-125">FindFile sample</span></span>](#findfile-sample)|
|<span data-ttu-id="dafbd-126">Struktura s ukazatelem na jinou strukturu.</span><span class="sxs-lookup"><span data-stu-id="dafbd-126">Structure with a pointer to another structure.</span></span>|<span data-ttu-id="dafbd-127">Předá strukturu, která obsahuje ukazatel na druhou strukturu jako člen.</span><span class="sxs-lookup"><span data-stu-id="dafbd-127">Passes a structure that contains a pointer to a second structure as a member.</span></span>|[<span data-ttu-id="dafbd-128">Ukázka struktur</span><span class="sxs-lookup"><span data-stu-id="dafbd-128">Structures Sample</span></span>](#structures-sample)|
|<span data-ttu-id="dafbd-129">Pole struktur s celými čísly podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="dafbd-129">Array of structures with integers by value.</span></span>|<span data-ttu-id="dafbd-130">Předá pole struktur, které obsahují pouze celá čísla jako vstupně-výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="dafbd-130">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="dafbd-131">Členy pole lze změnit.</span><span class="sxs-lookup"><span data-stu-id="dafbd-131">Members of the array can be changed.</span></span>|[<span data-ttu-id="dafbd-132">Ukázka polí</span><span class="sxs-lookup"><span data-stu-id="dafbd-132">Arrays Sample</span></span>](marshaling-different-types-of-arrays.md)|
|<span data-ttu-id="dafbd-133">Pole struktur s celými čísly a řetězci podle odkazu</span><span class="sxs-lookup"><span data-stu-id="dafbd-133">Array of structures with integers and strings by reference.</span></span>|<span data-ttu-id="dafbd-134">Předá pole struktury, které obsahují celá čísla a řetězce jako výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="dafbd-134">Passes an array of structures that contain integers and strings as an Out parameter.</span></span> <span data-ttu-id="dafbd-135">Volaná funkce přiděluje paměť pro pole.</span><span class="sxs-lookup"><span data-stu-id="dafbd-135">The called function allocates memory for the array.</span></span>|[<span data-ttu-id="dafbd-136">Ukázka Outarrayofstructs –</span><span class="sxs-lookup"><span data-stu-id="dafbd-136">OutArrayOfStructs Sample</span></span>](#outarrayofstructs-sample)|
|<span data-ttu-id="dafbd-137">Sjednocení s typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="dafbd-137">Unions with value types.</span></span>|<span data-ttu-id="dafbd-138">Předá sjednocení s typy hodnot (Integer a Double).</span><span class="sxs-lookup"><span data-stu-id="dafbd-138">Passes unions with value types (integer and double).</span></span>|[<span data-ttu-id="dafbd-139">sjednocení – ukázka</span><span class="sxs-lookup"><span data-stu-id="dafbd-139">Unions sample</span></span>](#unions-sample)|
|<span data-ttu-id="dafbd-140">Sjednocení se smíšenými typy.</span><span class="sxs-lookup"><span data-stu-id="dafbd-140">Unions with mixed types.</span></span>|<span data-ttu-id="dafbd-141">Předá sjednocení se smíšenými typy (Integer a String).</span><span class="sxs-lookup"><span data-stu-id="dafbd-141">Passes unions with mixed types (integer and string).</span></span>|[<span data-ttu-id="dafbd-142">sjednocení – ukázka</span><span class="sxs-lookup"><span data-stu-id="dafbd-142">Unions sample</span></span>](#unions-sample)|
|<span data-ttu-id="dafbd-143">Struktura s rozložením pro konkrétní platformu.</span><span class="sxs-lookup"><span data-stu-id="dafbd-143">Struct with platform-specific layout.</span></span>|<span data-ttu-id="dafbd-144">Předá typ s definicemi nativního balení.</span><span class="sxs-lookup"><span data-stu-id="dafbd-144">Passes a type with native-packing definitions.</span></span>|[<span data-ttu-id="dafbd-145">Ukázka platformy</span><span class="sxs-lookup"><span data-stu-id="dafbd-145">Platform sample</span></span>](#platform-sample)|
|<span data-ttu-id="dafbd-146">Hodnoty null ve struktuře.</span><span class="sxs-lookup"><span data-stu-id="dafbd-146">Null values in structure.</span></span>|<span data-ttu-id="dafbd-147">Předá odkaz s hodnotou null (**Nothing** v Visual Basic) místo odkazu na typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="dafbd-147">Passes a null reference (**Nothing** in Visual Basic) instead of a reference to a value type.</span></span>|<span data-ttu-id="dafbd-148">[HandleRef – ukázka](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="dafbd-148">[HandleRef sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))</span></span>|

## <a name="structures-sample"></a><span data-ttu-id="dafbd-149">Ukázka struktur</span><span class="sxs-lookup"><span data-stu-id="dafbd-149">Structures sample</span></span>

<span data-ttu-id="dafbd-150">Tato ukázka předvádí, jak předat strukturu, která odkazuje na druhou strukturu, předejte strukturu s vloženou strukturou a předejte strukturu vloženému poli.</span><span class="sxs-lookup"><span data-stu-id="dafbd-150">This sample demonstrates how to pass a structure that points to a second structure, pass a structure with an embedded structure, and pass a structure with an embedded array.</span></span>  
  
<span data-ttu-id="dafbd-151">Ukázka struktury používá následující nespravované funkce, které jsou zobrazeny s původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="dafbd-151">The Structs sample uses the following unmanaged functions, shown with their original function declaration:</span></span>

- <span data-ttu-id="dafbd-152">**TestStructInStruct** exportovaný z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="dafbd-152">**TestStructInStruct** exported from PinvokeLib.dll.</span></span>

    ```cpp
    int TestStructInStruct(MYPERSON2* pPerson2);
    ```

- <span data-ttu-id="dafbd-153">**TestStructInStruct3** exportovaný z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="dafbd-153">**TestStructInStruct3** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestStructInStruct3(MYPERSON3 person3);
    ```

- <span data-ttu-id="dafbd-154">**TestArrayInStruct** exportovaný z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="dafbd-154">**TestArrayInStruct** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestArrayInStruct(MYARRAYSTRUCT* pStruct);
    ```

<span data-ttu-id="dafbd-155">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) je vlastní nespravovaná knihovna, která obsahuje implementace pro dříve uvedené funkce a čtyři struktury: **MYPERSON**, **MYPERSON2**, **MYPERSON3**a **MYARRAYSTRUCT**.</span><span class="sxs-lookup"><span data-stu-id="dafbd-155">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and four structures: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, and **MYARRAYSTRUCT**.</span></span> <span data-ttu-id="dafbd-156">Tyto struktury obsahují následující prvky:</span><span class="sxs-lookup"><span data-stu-id="dafbd-156">These structures contain the following elements:</span></span>

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

<span data-ttu-id="dafbd-157">Struktury spravované `MyPerson` , `MyPerson2` , `MyPerson3` a `MyArrayStruct` mají následující charakteristiky:</span><span class="sxs-lookup"><span data-stu-id="dafbd-157">The managed `MyPerson`, `MyPerson2`, `MyPerson3`, and `MyArrayStruct` structures have the following characteristic:</span></span>

- <span data-ttu-id="dafbd-158">`MyPerson`obsahuje pouze členy řetězce.</span><span class="sxs-lookup"><span data-stu-id="dafbd-158">`MyPerson` contains only string members.</span></span> <span data-ttu-id="dafbd-159">Pole [CharSet](specifying-a-character-set.md) nastaví řetězce na formát ANSI při předání do nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="dafbd-159">The [CharSet](specifying-a-character-set.md) field sets the strings to ANSI format when passed to the unmanaged function.</span></span>

- <span data-ttu-id="dafbd-160">`MyPerson2`obsahuje **IntPtr** ke `MyPerson` struktuře.</span><span class="sxs-lookup"><span data-stu-id="dafbd-160">`MyPerson2` contains an **IntPtr** to the `MyPerson` structure.</span></span> <span data-ttu-id="dafbd-161">Typ **IntPtr** nahrazuje původní ukazatel na nespravovanou strukturu, protože .NET Framework aplikace nepoužívají ukazatele, pokud není kód označen jako **nebezpečný**.</span><span class="sxs-lookup"><span data-stu-id="dafbd-161">The **IntPtr** type replaces the original pointer to the unmanaged structure because .NET Framework applications do not use pointers unless the code is marked **unsafe**.</span></span>

- <span data-ttu-id="dafbd-162">`MyPerson3`obsahuje `MyPerson` jako vloženou strukturu.</span><span class="sxs-lookup"><span data-stu-id="dafbd-162">`MyPerson3` contains `MyPerson` as an embedded structure.</span></span> <span data-ttu-id="dafbd-163">Strukturu vloženou v jiné struktuře lze sloučit umístěním prvků vložené struktury přímo do hlavní struktury, nebo může být ponechána jako vložená struktura, jak je provedeno v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="dafbd-163">A structure embedded within another structure can be flattened by placing the elements of the embedded structure directly into the main structure, or it can be left as an embedded structure, as is done in this sample.</span></span>

- <span data-ttu-id="dafbd-164">`MyArrayStruct`obsahuje pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="dafbd-164">`MyArrayStruct` contains an array of integers.</span></span> <span data-ttu-id="dafbd-165"><xref:System.Runtime.InteropServices.MarshalAsAttribute>Atribut nastaví <xref:System.Runtime.InteropServices.UnmanagedType> hodnotu výčtu na **ByValArray**, která slouží k označení počtu prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="dafbd-165">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration value to **ByValArray**, which is used to indicate the number of elements in the array.</span></span>

<span data-ttu-id="dafbd-166">Pro všechny struktury v této ukázce se <xref:System.Runtime.InteropServices.StructLayoutAttribute> používá atribut, aby bylo zajištěno, že jsou členy uspořádány v paměti postupně, v pořadí, ve kterém jsou uvedeny.</span><span class="sxs-lookup"><span data-stu-id="dafbd-166">For all structures in this sample, the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is applied to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>

<span data-ttu-id="dafbd-167">`NativeMethods`Třída obsahuje spravované prototypy pro `TestStructInStruct` , `TestStructInStruct3` a metody, které `TestArrayInStruct` jsou volány `App` třídou.</span><span class="sxs-lookup"><span data-stu-id="dafbd-167">The `NativeMethods` class contains managed prototypes for the `TestStructInStruct`, `TestStructInStruct3`, and `TestArrayInStruct` methods called by the `App` class.</span></span> <span data-ttu-id="dafbd-168">Každý prototyp deklaruje jeden parametr následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="dafbd-168">Each prototype declares a single parameter, as follows:</span></span>

- <span data-ttu-id="dafbd-169">`TestStructInStruct`deklaruje odkaz na typ `MyPerson2` jako jeho parametr.</span><span class="sxs-lookup"><span data-stu-id="dafbd-169">`TestStructInStruct` declares a reference to type `MyPerson2` as its parameter.</span></span>

- <span data-ttu-id="dafbd-170">`TestStructInStruct3`Deklaruje typ `MyPerson3` jako svůj parametr a předá parametr podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="dafbd-170">`TestStructInStruct3` declares type `MyPerson3` as its parameter and passes the parameter by value.</span></span>

- <span data-ttu-id="dafbd-171">`TestArrayInStruct`deklaruje odkaz na typ `MyArrayStruct` jako jeho parametr.</span><span class="sxs-lookup"><span data-stu-id="dafbd-171">`TestArrayInStruct` declares a reference to type `MyArrayStruct` as its parameter.</span></span>

<span data-ttu-id="dafbd-172">Struktury jako argumenty metod jsou předávány hodnotou, pokud parametr neobsahuje klíčové slovo **ref** (**ByRef** in Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="dafbd-172">Structures as arguments to methods are passed by value unless the parameter contains the **ref** (**ByRef** in Visual Basic) keyword.</span></span> <span data-ttu-id="dafbd-173">Například `TestStructInStruct` Metoda předává odkaz (hodnota adresy) objektu typu `MyPerson2` na nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="dafbd-173">For example, the `TestStructInStruct` method passes a reference (the value of an address) to an object of type `MyPerson2` to unmanaged code.</span></span> <span data-ttu-id="dafbd-174">Aby bylo možné manipulovat se strukturou, `MyPerson2` na kterou odkazuje, ukázka vytvoří vyrovnávací paměť zadané velikosti a vrátí její adresu kombinací <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metod a.</span><span class="sxs-lookup"><span data-stu-id="dafbd-174">To manipulate the structure that `MyPerson2` points to, the sample creates a buffer of a specified size and returns its address by combining the <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="dafbd-175">V dalším kroku zkopíruje ukázka obsah spravované struktury do nespravované vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="dafbd-175">Next, the sample copies the content of the managed structure to the unmanaged buffer.</span></span> <span data-ttu-id="dafbd-176">Nakonec ukázka používá <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> metodu pro zařazování dat z nespravované vyrovnávací paměti do spravovaného objektu a <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> metodu pro uvolnění nespravovaného bloku paměti.</span><span class="sxs-lookup"><span data-stu-id="dafbd-176">Finally, the sample uses the <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> method to marshal data from the unmanaged buffer to a managed object and the <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> method to free the unmanaged block of memory.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="dafbd-177">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="dafbd-177">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#23](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
[!code-csharp[Conceptual.Interop.Marshaling#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
[!code-vb[Conceptual.Interop.Marshaling#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]

### <a name="calling-functions"></a><span data-ttu-id="dafbd-178">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="dafbd-178">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#24](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
[!code-csharp[Conceptual.Interop.Marshaling#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
[!code-vb[Conceptual.Interop.Marshaling#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]

## <a name="findfile-sample"></a><span data-ttu-id="dafbd-179">FindFile – ukázka</span><span class="sxs-lookup"><span data-stu-id="dafbd-179">FindFile sample</span></span>

<span data-ttu-id="dafbd-180">Tato ukázka předvádí, jak předat strukturu, která obsahuje druhou, vloženou strukturu do nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="dafbd-180">This sample demonstrates how to pass a structure that contains a second, embedded structure to an unmanaged function.</span></span> <span data-ttu-id="dafbd-181">Také ukazuje, jak použít <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut k deklaraci pole s pevnou délkou v rámci struktury.</span><span class="sxs-lookup"><span data-stu-id="dafbd-181">It also demonstrates how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to declare a fixed-length array within the structure.</span></span> <span data-ttu-id="dafbd-182">V této ukázce jsou vložené prvky struktury přidány do nadřazené struktury.</span><span class="sxs-lookup"><span data-stu-id="dafbd-182">In this sample, the embedded structure elements are added to the parent structure.</span></span> <span data-ttu-id="dafbd-183">Ukázku vložené struktury, která není shrnuta, naleznete v části [struktury Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="dafbd-183">For a sample of an embedded structure that is not flattened, see [Structures Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span></span>

<span data-ttu-id="dafbd-184">Ukázka FindFile – používá následující nespravovanou funkci, která se zobrazuje s její původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="dafbd-184">The FindFile sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="dafbd-185">**FindFirstFile** exportovaný z Kernel32.dll.</span><span class="sxs-lookup"><span data-stu-id="dafbd-185">**FindFirstFile** exported from Kernel32.dll.</span></span>

    ```cpp
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);
    ```

<span data-ttu-id="dafbd-186">Původní struktura předaná funkci obsahuje následující prvky:</span><span class="sxs-lookup"><span data-stu-id="dafbd-186">The original structure passed to the function contains the following elements:</span></span>

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

<span data-ttu-id="dafbd-187">V této ukázce `FindData` Třída obsahuje odpovídající datový člen pro každý prvek původní struktury a vloženou strukturu.</span><span class="sxs-lookup"><span data-stu-id="dafbd-187">In this sample, the `FindData` class contains a corresponding data member for each element of the original structure and the embedded structure.</span></span> <span data-ttu-id="dafbd-188">Místo dvou původních vyrovnávacích pamětí znaků třída nahradí řetězce.</span><span class="sxs-lookup"><span data-stu-id="dafbd-188">In place of two original character buffers, the class substitutes strings.</span></span> <span data-ttu-id="dafbd-189">**MarshalAsAttribute** nastaví <xref:System.Runtime.InteropServices.UnmanagedType> výčet na **ByValTStr**, který slouží k identifikaci vložených znakových polí s pevnou délkou, která se zobrazí v nespravovaných strukturách.</span><span class="sxs-lookup"><span data-stu-id="dafbd-189">**MarshalAsAttribute** sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged structures.</span></span>

<span data-ttu-id="dafbd-190">`NativeMethods`Třída obsahuje spravovaný prototyp `FindFirstFile` metody, která předá `FindData` třídu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="dafbd-190">The `NativeMethods` class contains a managed prototype of the `FindFirstFile` method, which passes the `FindData` class as a parameter.</span></span> <span data-ttu-id="dafbd-191">Parametr musí být deklarován s <xref:System.Runtime.InteropServices.InAttribute> <xref:System.Runtime.InteropServices.OutAttribute> atributy a, protože třídy, které jsou odkazové typy, jsou předány jako parametry ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="dafbd-191">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="dafbd-192">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="dafbd-192">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#17](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
[!code-csharp[Conceptual.Interop.Marshaling#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
[!code-vb[Conceptual.Interop.Marshaling#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]

### <a name="calling-functions"></a><span data-ttu-id="dafbd-193">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="dafbd-193">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#18](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
[!code-csharp[Conceptual.Interop.Marshaling#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]

## <a name="unions-sample"></a><span data-ttu-id="dafbd-194">sjednocení – ukázka</span><span class="sxs-lookup"><span data-stu-id="dafbd-194">Unions sample</span></span>

<span data-ttu-id="dafbd-195">Tato ukázka předvádí, jak předat struktury obsahující pouze typy hodnot a struktury obsahující typ hodnoty a řetězec jako parametry nespravované funkce, které očekávají sjednocení.</span><span class="sxs-lookup"><span data-stu-id="dafbd-195">This sample demonstrates how to pass structures containing only value types, and structures containing a value type and a string as parameters to an unmanaged function expecting a union.</span></span> <span data-ttu-id="dafbd-196">Sjednocení představuje umístění v paměti, které může být sdíleno dvěma nebo více proměnnými.</span><span class="sxs-lookup"><span data-stu-id="dafbd-196">A union represents a memory location that can be shared by two or more variables.</span></span>

<span data-ttu-id="dafbd-197">Vzor sjednocení používá následující nespravovanou funkci zobrazenou s původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="dafbd-197">The Unions sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="dafbd-198">**TestUnion** exportovaný z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="dafbd-198">**TestUnion** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestUnion(MYUNION u, int type);
    ```

<span data-ttu-id="dafbd-199">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) je vlastní nespravovaná knihovna, která obsahuje implementaci dříve uvedené funkce a dvou sjednocení, **MYUNION** a **MYUNION2**.</span><span class="sxs-lookup"><span data-stu-id="dafbd-199">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed function and two unions, **MYUNION** and **MYUNION2**.</span></span> <span data-ttu-id="dafbd-200">Sjednocení obsahují následující prvky:</span><span class="sxs-lookup"><span data-stu-id="dafbd-200">The unions contain the following elements:</span></span>

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

<span data-ttu-id="dafbd-201">Ve spravovaném kódu jsou sjednocení definována jako struktury.</span><span class="sxs-lookup"><span data-stu-id="dafbd-201">In managed code, unions are defined as structures.</span></span> <span data-ttu-id="dafbd-202">`MyUnion`Struktura obsahuje dva typy hodnot jako členy: celé číslo a typ Double.</span><span class="sxs-lookup"><span data-stu-id="dafbd-202">The `MyUnion` structure contains two value types as its members: an integer and a double.</span></span> <span data-ttu-id="dafbd-203"><xref:System.Runtime.InteropServices.StructLayoutAttribute>Atribut je nastaven na řízení přesné pozice jednotlivých datových členů.</span><span class="sxs-lookup"><span data-stu-id="dafbd-203">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to control the precise position of each data member.</span></span> <span data-ttu-id="dafbd-204"><xref:System.Runtime.InteropServices.FieldOffsetAttribute>Atribut poskytuje fyzickou pozici polí v rámci nespravované reprezentace sjednocení.</span><span class="sxs-lookup"><span data-stu-id="dafbd-204">The <xref:System.Runtime.InteropServices.FieldOffsetAttribute> attribute provides the physical position of fields within the unmanaged representation of a union.</span></span> <span data-ttu-id="dafbd-205">Všimněte si, že oba členové mají stejné hodnoty posunutí, takže členové mohou definovat stejnou část paměti.</span><span class="sxs-lookup"><span data-stu-id="dafbd-205">Notice that both members have the same offset values, so the members can define the same piece of memory.</span></span>

<span data-ttu-id="dafbd-206">`MyUnion2_1`a `MyUnion2_2` obsahují hodnotový typ (Integer) a řetězec v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="dafbd-206">`MyUnion2_1` and `MyUnion2_2` contain a value type (integer) and a string, respectively.</span></span> <span data-ttu-id="dafbd-207">Ve spravovaném kódu se typy hodnot a typy odkazů nepovolují překrývat.</span><span class="sxs-lookup"><span data-stu-id="dafbd-207">In managed code, value types and reference types are not permitted to overlap.</span></span> <span data-ttu-id="dafbd-208">Tato ukázka používá přetížení metody, aby volající mohl použít oba typy při volání stejné nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="dafbd-208">This sample uses method overloading to enable the caller to use both types when calling the same unmanaged function.</span></span> <span data-ttu-id="dafbd-209">Rozložení `MyUnion2_1` je explicitní a má přesnou hodnotu posunu.</span><span class="sxs-lookup"><span data-stu-id="dafbd-209">The layout of `MyUnion2_1` is explicit and has a precise offset value.</span></span> <span data-ttu-id="dafbd-210">Naproti tomu `MyUnion2_2` má sekvenční rozložení, protože explicitní rozložení nejsou povolena s odkazovým typem.</span><span class="sxs-lookup"><span data-stu-id="dafbd-210">In contrast, `MyUnion2_2` has a sequential layout, because explicit layouts are not permitted with reference types.</span></span> <span data-ttu-id="dafbd-211"><xref:System.Runtime.InteropServices.MarshalAsAttribute>Atribut nastaví <xref:System.Runtime.InteropServices.UnmanagedType> výčet na **ByValTStr**, který se používá k identifikaci vložených znakových polí s pevnou délkou, která se zobrazí v nespravovaném vyjádření sjednocení.</span><span class="sxs-lookup"><span data-stu-id="dafbd-211">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged representation of the union.</span></span>

<span data-ttu-id="dafbd-212">`NativeMethods`Třída obsahuje prototypy pro `TestUnion` `TestUnion2` metody a.</span><span class="sxs-lookup"><span data-stu-id="dafbd-212">The `NativeMethods` class contains the prototypes for the `TestUnion` and `TestUnion2` methods.</span></span> <span data-ttu-id="dafbd-213">`TestUnion2`je přetížený pro deklaraci `MyUnion2_1` nebo `MyUnion2_2` jako parametry.</span><span class="sxs-lookup"><span data-stu-id="dafbd-213">`TestUnion2` is overloaded to declare `MyUnion2_1` or `MyUnion2_2` as parameters.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="dafbd-214">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="dafbd-214">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#28](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
[!code-csharp[Conceptual.Interop.Marshaling#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
[!code-vb[Conceptual.Interop.Marshaling#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]

### <a name="calling-functions"></a><span data-ttu-id="dafbd-215">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="dafbd-215">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#29](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
[!code-csharp[Conceptual.Interop.Marshaling#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
[!code-vb[Conceptual.Interop.Marshaling#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]

## <a name="platform-sample"></a><span data-ttu-id="dafbd-216">Ukázka platformy</span><span class="sxs-lookup"><span data-stu-id="dafbd-216">Platform sample</span></span>

<span data-ttu-id="dafbd-217">V některých scénářích `struct` se `union` rozložení může lišit v závislosti na cílové platformě.</span><span class="sxs-lookup"><span data-stu-id="dafbd-217">In some scenarios, `struct` and `union` layouts can differ depending on the targeted platform.</span></span> <span data-ttu-id="dafbd-218">Zvažte například typ, který je [`STRRET`](/windows/win32/api/shtypes/ns-shtypes-strret) definován ve scénáři modelu com:</span><span class="sxs-lookup"><span data-stu-id="dafbd-218">For example, consider the [`STRRET`](/windows/win32/api/shtypes/ns-shtypes-strret) type when defined in a COM scenario:</span></span>

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

<span data-ttu-id="dafbd-219">Výše uvedená `struct` deklarace je deklarována s hlavičkou systému Windows, které mají vliv na rozložení paměti daného typu.</span><span class="sxs-lookup"><span data-stu-id="dafbd-219">The above `struct` is declared with Windows' headers that influence the memory layout of the type.</span></span> <span data-ttu-id="dafbd-220">Pokud je definována ve spravovaném prostředí, tyto podrobnosti o rozložení jsou potřeba ke správné spolupráci s nativním kódem.</span><span class="sxs-lookup"><span data-stu-id="dafbd-220">When defined in a managed environment, these layout details are needed to properly interoperate with native code.</span></span>

<span data-ttu-id="dafbd-221">Správná spravovaná definice tohoto typu v rámci 32 procesu je:</span><span class="sxs-lookup"><span data-stu-id="dafbd-221">The correct managed definition of this type in a 32-bit process is:</span></span>

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

<span data-ttu-id="dafbd-222">U 64 procesu se velikost *a* posunutí polí liší.</span><span class="sxs-lookup"><span data-stu-id="dafbd-222">On a 64-bit process, the size *and* field offsets are different.</span></span> <span data-ttu-id="dafbd-223">Správné rozložení je:</span><span class="sxs-lookup"><span data-stu-id="dafbd-223">The correct layout is:</span></span>

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

<span data-ttu-id="dafbd-224">Při nesprávném zvážení nativního rozložení ve scénáři spolupráce může dojít k náhodným chybám nebo horším, nesprávným výpočtům.</span><span class="sxs-lookup"><span data-stu-id="dafbd-224">Failure to properly consider the native layout in an interop scenario can result in random crashes or worse, incorrect computations.</span></span>

<span data-ttu-id="dafbd-225">Ve výchozím nastavení mohou být sestavení .NET spouštěna v 32 a 64 verze modulu runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="dafbd-225">By default, .NET assemblies can run in both a 32-bit and 64-bit version of the .NET runtime.</span></span> <span data-ttu-id="dafbd-226">Aplikace musí počkat, než čas spuštění určí, který z předchozích definic se má použít.</span><span class="sxs-lookup"><span data-stu-id="dafbd-226">The app must wait until run time to decide which of the previous definitions to use.</span></span>

<span data-ttu-id="dafbd-227">Následující fragment kódu ukazuje příklad, jak zvolit mezi 32 a 64 bitů definice v době běhu.</span><span class="sxs-lookup"><span data-stu-id="dafbd-227">The following code snippet shows an example of how to choose between the 32-bit and 64-bit definition at run time.</span></span>

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

## <a name="systime-sample"></a><span data-ttu-id="dafbd-228">SysTime – ukázka</span><span class="sxs-lookup"><span data-stu-id="dafbd-228">SysTime sample</span></span>

<span data-ttu-id="dafbd-229">Tato ukázka předvádí, jak předat ukazatel na třídu nespravované funkci, která očekává ukazatel na strukturu.</span><span class="sxs-lookup"><span data-stu-id="dafbd-229">This sample demonstrates how to pass a pointer to a class to an unmanaged function that expects a pointer to a structure.</span></span>

<span data-ttu-id="dafbd-230">Ukázka sysTime – používá následující nespravovanou funkci, která se zobrazuje s její původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="dafbd-230">The SysTime sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="dafbd-231">**GetSystemTime** exportovaný z Kernel32.dll.</span><span class="sxs-lookup"><span data-stu-id="dafbd-231">**GetSystemTime** exported from Kernel32.dll.</span></span>

    ```cpp
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);
    ```

<span data-ttu-id="dafbd-232">Původní struktura předaná funkci obsahuje následující prvky:</span><span class="sxs-lookup"><span data-stu-id="dafbd-232">The original structure passed to the function contains the following elements:</span></span>

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

<span data-ttu-id="dafbd-233">V této ukázce `SystemTime` Třída obsahuje prvky původní struktury reprezentované jako členy třídy.</span><span class="sxs-lookup"><span data-stu-id="dafbd-233">In this sample, the `SystemTime` class contains the elements of the original structure represented as class members.</span></span> <span data-ttu-id="dafbd-234"><xref:System.Runtime.InteropServices.StructLayoutAttribute>Atribut je nastaven tak, aby bylo zajištěno, že jsou členy uspořádány v paměti sekvenčně v pořadí, ve kterém jsou zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="dafbd-234">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>

<span data-ttu-id="dafbd-235">`NativeMethods`Třída obsahuje spravovaný prototyp `GetSystemTime` metody, která `SystemTime` ve výchozím nastavení předává třídu jako vstupně-výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="dafbd-235">The `NativeMethods` class contains a managed prototype of the `GetSystemTime` method, which passes the `SystemTime` class as an In/Out parameter by default.</span></span> <span data-ttu-id="dafbd-236">Parametr musí být deklarován s <xref:System.Runtime.InteropServices.InAttribute> <xref:System.Runtime.InteropServices.OutAttribute> atributy a, protože třídy, které jsou odkazové typy, jsou předány jako parametry ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="dafbd-236">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span> <span data-ttu-id="dafbd-237">Aby volající mohl přijímat výsledky, musí být tyto [směrové atributy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) aplikovány explicitně.</span><span class="sxs-lookup"><span data-stu-id="dafbd-237">For the caller to receive the results, these [directional attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) must be applied explicitly.</span></span> <span data-ttu-id="dafbd-238">`App`Třída vytvoří novou instanci `SystemTime` třídy a přistupuje k jejím datovým polím.</span><span class="sxs-lookup"><span data-stu-id="dafbd-238">The `App` class creates a new instance of the `SystemTime` class and accesses its data fields.</span></span>

### <a name="code-samples"></a><span data-ttu-id="dafbd-239">Ukázky kódů</span><span class="sxs-lookup"><span data-stu-id="dafbd-239">Code Samples</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#25](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
[!code-csharp[Conceptual.Interop.Marshaling#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
[!code-vb[Conceptual.Interop.Marshaling#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]

## <a name="outarrayofstructs-sample"></a><span data-ttu-id="dafbd-240">OutArrayOfStructs – ukázka</span><span class="sxs-lookup"><span data-stu-id="dafbd-240">OutArrayOfStructs sample</span></span>

<span data-ttu-id="dafbd-241">Tento příklad ukazuje, jak předat pole struktur obsahující celá čísla a řetězce jako výstupní parametry nespravované funkci.</span><span class="sxs-lookup"><span data-stu-id="dafbd-241">This sample shows how to pass an array of structures that contains integers and strings as Out parameters to an unmanaged function.</span></span>

<span data-ttu-id="dafbd-242">Tento příklad ukazuje, jak volat nativní funkci pomocí <xref:System.Runtime.InteropServices.Marshal> třídy a pomocí nebezpečného kódu.</span><span class="sxs-lookup"><span data-stu-id="dafbd-242">This sample demonstrates how to call a native function by using the <xref:System.Runtime.InteropServices.Marshal> class and by using unsafe code.</span></span>

<span data-ttu-id="dafbd-243">Tato ukázka používá funkce obálky a vyvolání platformy definované v [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), které jsou také k dispozici ve zdrojových souborech.</span><span class="sxs-lookup"><span data-stu-id="dafbd-243">This sample uses a wrapper functions and platform invokes defined in [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), also provided in the source files.</span></span> <span data-ttu-id="dafbd-244">Používá `TestOutArrayOfStructs` funkci a `MYSTRSTRUCT2` strukturu.</span><span class="sxs-lookup"><span data-stu-id="dafbd-244">It uses the `TestOutArrayOfStructs` function and the `MYSTRSTRUCT2` structure.</span></span> <span data-ttu-id="dafbd-245">Struktura obsahuje následující prvky:</span><span class="sxs-lookup"><span data-stu-id="dafbd-245">The structure contains the following elements:</span></span>

```cpp
typedef struct _MYSTRSTRUCT2
{
   char* buffer;
   UINT size;
} MYSTRSTRUCT2;
```

<span data-ttu-id="dafbd-246">`MyStruct`Třída obsahuje objekt řetězce znaků ANSI.</span><span class="sxs-lookup"><span data-stu-id="dafbd-246">The `MyStruct` class contains a string object of ANSI characters.</span></span> <span data-ttu-id="dafbd-247"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>Pole určuje formát ANSI.</span><span class="sxs-lookup"><span data-stu-id="dafbd-247">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field specifies ANSI format.</span></span> <span data-ttu-id="dafbd-248">`MyUnsafeStruct`, je struktura obsahující <xref:System.IntPtr> typ místo řetězce.</span><span class="sxs-lookup"><span data-stu-id="dafbd-248">`MyUnsafeStruct`, is a structure containing an <xref:System.IntPtr> type instead of a string.</span></span>

<span data-ttu-id="dafbd-249">`NativeMethods`Třída obsahuje přetíženou `TestOutArrayOfStructs` metodu prototypu.</span><span class="sxs-lookup"><span data-stu-id="dafbd-249">The `NativeMethods` class contains the overloaded `TestOutArrayOfStructs` prototype method.</span></span> <span data-ttu-id="dafbd-250">Pokud metoda deklaruje ukazatel jako parametr, třída by měla být označena `unsafe` klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="dafbd-250">If a method declares a pointer as a parameter, the class should be marked with the `unsafe` keyword.</span></span> <span data-ttu-id="dafbd-251">Vzhledem k tomu, že Visual Basic nemůže použít nezabezpečený kód, přetíženou metodu, nezabezpečený modifikátor a `MyUnsafeStruct` strukturu jsou zbytečné.</span><span class="sxs-lookup"><span data-stu-id="dafbd-251">Because Visual Basic cannot use unsafe code, the overloaded method, unsafe modifier, and the `MyUnsafeStruct` structure are unnecessary.</span></span>

<span data-ttu-id="dafbd-252">`App`Třída implementuje `UsingMarshaling` metodu, která provádí všechny úlohy, které jsou nezbytné k předání pole.</span><span class="sxs-lookup"><span data-stu-id="dafbd-252">The `App` class implements the `UsingMarshaling` method, which performs all the tasks necessary to pass the array.</span></span> <span data-ttu-id="dafbd-253">Pole je označeno pomocí `out` `ByRef` klíčového slova (v Visual Basic) k označení toho, že data přecházejí z volaného volajícího.</span><span class="sxs-lookup"><span data-stu-id="dafbd-253">The array is marked with the `out` (`ByRef` in Visual Basic) keyword to indicate that data passes from callee to caller.</span></span> <span data-ttu-id="dafbd-254">Implementace používá následující <xref:System.Runtime.InteropServices.Marshal> metody třídy:</span><span class="sxs-lookup"><span data-stu-id="dafbd-254">The implementation uses the following <xref:System.Runtime.InteropServices.Marshal> class methods:</span></span>

- <span data-ttu-id="dafbd-255"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A>pro zařazování dat z nespravované vyrovnávací paměti do spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="dafbd-255"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> to marshal data from the unmanaged buffer to a managed object.</span></span>

- <span data-ttu-id="dafbd-256"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A>uvolnění paměti rezervované pro řetězce ve struktuře.</span><span class="sxs-lookup"><span data-stu-id="dafbd-256"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> to release the memory reserved for strings in the structure.</span></span>

- <span data-ttu-id="dafbd-257"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>uvolnění paměti rezervované pro dané pole.</span><span class="sxs-lookup"><span data-stu-id="dafbd-257"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> to release the memory reserved for the array.</span></span>

<span data-ttu-id="dafbd-258">Jak už jsme uvedli, C# umožňuje nezabezpečený kód a Visual Basic ne.</span><span class="sxs-lookup"><span data-stu-id="dafbd-258">As previously mentioned, C# allows unsafe code and Visual Basic does not.</span></span> <span data-ttu-id="dafbd-259">V ukázce jazyka C# `UsingUnsafePointer` je alternativou implementace metody, která používá ukazatele namísto <xref:System.Runtime.InteropServices.Marshal> třídy k předání pole obsahujícího `MyUnsafeStruct` strukturu.</span><span class="sxs-lookup"><span data-stu-id="dafbd-259">In the C# sample, `UsingUnsafePointer` is an alternative method implementation that uses pointers instead of the <xref:System.Runtime.InteropServices.Marshal> class to pass back the array containing the `MyUnsafeStruct` structure.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="dafbd-260">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="dafbd-260">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#20](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
[!code-csharp[Conceptual.Interop.Marshaling#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
[!code-vb[Conceptual.Interop.Marshaling#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]

### <a name="calling-functions"></a><span data-ttu-id="dafbd-261">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="dafbd-261">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#21](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
[!code-csharp[Conceptual.Interop.Marshaling#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
[!code-vb[Conceptual.Interop.Marshaling#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]

## <a name="see-also"></a><span data-ttu-id="dafbd-262">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dafbd-262">See also</span></span>

- [<span data-ttu-id="dafbd-263">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="dafbd-263">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
- [<span data-ttu-id="dafbd-264">Zařazování řetězců</span><span class="sxs-lookup"><span data-stu-id="dafbd-264">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="dafbd-265">Zařazování různých typů polí</span><span class="sxs-lookup"><span data-stu-id="dafbd-265">Marshaling Different Types of Arrays</span></span>](marshaling-different-types-of-arrays.md)
