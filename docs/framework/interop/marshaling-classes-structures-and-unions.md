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
ms.openlocfilehash: d761d8ed7488e99f29d4844d061867915a624b96
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960014"
---
# <a name="marshaling-classes-structures-and-unions"></a><span data-ttu-id="dfe7c-102">Zařazování tříd, struktur a sjednocení</span><span class="sxs-lookup"><span data-stu-id="dfe7c-102">Marshaling Classes, Structures, and Unions</span></span>

<span data-ttu-id="dfe7c-103">Třídy a struktury jsou podobné v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-103">Classes and structures are similar in the .NET Framework.</span></span> <span data-ttu-id="dfe7c-104">Oba můžou mít pole, vlastnosti a události.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-104">Both can have fields, properties, and events.</span></span> <span data-ttu-id="dfe7c-105">Mohou mít také statické a nestatické metody.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-105">They can also have static and nonstatic methods.</span></span> <span data-ttu-id="dfe7c-106">Jedním z významných rozdílů je, že struktury jsou typy hodnot a třídy jsou odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-106">One notable difference is that structures are value types and classes are reference types.</span></span>

<span data-ttu-id="dfe7c-107">V následující tabulce jsou uvedeny možnosti zařazování pro třídy, struktury a sjednocení; popisuje jejich použití. a poskytuje odkaz na odpovídající ukázku vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-107">The following table lists marshaling options for classes, structures, and unions; describes their usage; and provides a link to the corresponding platform invoke sample.</span></span>

|<span data-ttu-id="dfe7c-108">Type</span><span class="sxs-lookup"><span data-stu-id="dfe7c-108">Type</span></span>|<span data-ttu-id="dfe7c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="dfe7c-109">Description</span></span>|<span data-ttu-id="dfe7c-110">Ukázka</span><span class="sxs-lookup"><span data-stu-id="dfe7c-110">Sample</span></span>|
|----------|-----------------|------------|
|<span data-ttu-id="dfe7c-111">Třída podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="dfe7c-111">Class by value.</span></span>|<span data-ttu-id="dfe7c-112">Předá třídu s celočíselnými členy jako parametr in/out, jako je například spravovaný případ.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-112">Passes a class with integer members as an In/Out parameter, like the managed case.</span></span>|[<span data-ttu-id="dfe7c-113">Ukázka sysTime –</span><span class="sxs-lookup"><span data-stu-id="dfe7c-113">SysTime sample</span></span>](#systime-sample)|
|<span data-ttu-id="dfe7c-114">Struktura podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-114">Structure by value.</span></span>|<span data-ttu-id="dfe7c-115">Předá struktury jako v parametrech.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-115">Passes structures as In parameters.</span></span>|[<span data-ttu-id="dfe7c-116">Ukázka struktur</span><span class="sxs-lookup"><span data-stu-id="dfe7c-116">Structures sample</span></span>](#structures-sample)|
|<span data-ttu-id="dfe7c-117">Struktura podle odkazu</span><span class="sxs-lookup"><span data-stu-id="dfe7c-117">Structure by reference.</span></span>|<span data-ttu-id="dfe7c-118">Předává struktury jako vstupně-výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-118">Passes structures as In/Out parameters.</span></span>|<span data-ttu-id="dfe7c-119">[Ukázka OSINFO –](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dfe7c-119">[OSInfo sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))</span></span>|
|<span data-ttu-id="dfe7c-120">Struktura s vnořenými strukturami (ploché).</span><span class="sxs-lookup"><span data-stu-id="dfe7c-120">Structure with nested structures (flattened).</span></span>|<span data-ttu-id="dfe7c-121">Předá třídu, která představuje strukturu s vnořenými strukturami v nespravované funkci.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-121">Passes a class that represents a structure with nested structures in the unmanaged function.</span></span> <span data-ttu-id="dfe7c-122">Struktura je v rámci spravovaného prototypu Sloučená do jedné velké struktury.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-122">The structure is flattened to one big structure in the managed prototype.</span></span>|[<span data-ttu-id="dfe7c-123">Ukázka FindFile –</span><span class="sxs-lookup"><span data-stu-id="dfe7c-123">FindFile sample</span></span>](#findfile-sample)|
|<span data-ttu-id="dfe7c-124">Struktura s ukazatelem na jinou strukturu.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-124">Structure with a pointer to another structure.</span></span>|<span data-ttu-id="dfe7c-125">Předá strukturu, která obsahuje ukazatel na druhou strukturu jako člen.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-125">Passes a structure that contains a pointer to a second structure as a member.</span></span>|[<span data-ttu-id="dfe7c-126">Ukázka struktur</span><span class="sxs-lookup"><span data-stu-id="dfe7c-126">Structures Sample</span></span>](#structures-sample)|
|<span data-ttu-id="dfe7c-127">Pole struktur s celými čísly podle hodnoty</span><span class="sxs-lookup"><span data-stu-id="dfe7c-127">Array of structures with integers by value.</span></span>|<span data-ttu-id="dfe7c-128">Předá pole struktur, které obsahují pouze celá čísla jako vstupně-výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-128">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="dfe7c-129">Členy pole lze změnit.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-129">Members of the array can be changed.</span></span>|[<span data-ttu-id="dfe7c-130">Ukázka polí</span><span class="sxs-lookup"><span data-stu-id="dfe7c-130">Arrays Sample</span></span>](marshaling-different-types-of-arrays.md)|
|<span data-ttu-id="dfe7c-131">Pole struktur s celými čísly a řetězci podle odkazu</span><span class="sxs-lookup"><span data-stu-id="dfe7c-131">Array of structures with integers and strings by reference.</span></span>|<span data-ttu-id="dfe7c-132">Předá pole struktury, které obsahují celá čísla a řetězce jako výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-132">Passes an array of structures that contain integers and strings as an Out parameter.</span></span> <span data-ttu-id="dfe7c-133">Volaná funkce přiděluje paměť pro pole.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-133">The called function allocates memory for the array.</span></span>|[<span data-ttu-id="dfe7c-134">Ukázka Outarrayofstructs –</span><span class="sxs-lookup"><span data-stu-id="dfe7c-134">OutArrayOfStructs Sample</span></span>](#outarrayofstructs-sample)|
|<span data-ttu-id="dfe7c-135">Sjednocení s typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-135">Unions with value types.</span></span>|<span data-ttu-id="dfe7c-136">Předá sjednocení s typy hodnot (Integer a Double).</span><span class="sxs-lookup"><span data-stu-id="dfe7c-136">Passes unions with value types (integer and double).</span></span>|[<span data-ttu-id="dfe7c-137">Sjednocení – ukázka</span><span class="sxs-lookup"><span data-stu-id="dfe7c-137">Unions sample</span></span>](#unions-sample)|
|<span data-ttu-id="dfe7c-138">Sjednocení se smíšenými typy.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-138">Unions with mixed types.</span></span>|<span data-ttu-id="dfe7c-139">Předá sjednocení se smíšenými typy (Integer a String).</span><span class="sxs-lookup"><span data-stu-id="dfe7c-139">Passes unions with mixed types (integer and string).</span></span>|[<span data-ttu-id="dfe7c-140">Sjednocení – ukázka</span><span class="sxs-lookup"><span data-stu-id="dfe7c-140">Unions sample</span></span>](#unions-sample)|
|<span data-ttu-id="dfe7c-141">Hodnoty null ve struktuře.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-141">Null values in structure.</span></span>|<span data-ttu-id="dfe7c-142">Předá odkaz s hodnotou null (**Nothing** v Visual Basic) místo odkazu na typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-142">Passes a null reference (**Nothing** in Visual Basic) instead of a reference to a value type.</span></span>|<span data-ttu-id="dfe7c-143">[Ukázka HandleRef –](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="dfe7c-143">[HandleRef sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))</span></span>|

## <a name="structures-sample"></a><span data-ttu-id="dfe7c-144">Ukázka struktur</span><span class="sxs-lookup"><span data-stu-id="dfe7c-144">Structures sample</span></span>

<span data-ttu-id="dfe7c-145">Tato ukázka předvádí, jak předat strukturu, která odkazuje na druhou strukturu, předejte strukturu s vloženou strukturou a předejte strukturu vloženému poli.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-145">This sample demonstrates how to pass a structure that points to a second structure, pass a structure with an embedded structure, and pass a structure with an embedded array.</span></span>  
  
<span data-ttu-id="dfe7c-146">Ukázka struktury používá následující nespravované funkce, které jsou zobrazeny s původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="dfe7c-146">The Structs sample uses the following unmanaged functions, shown with their original function declaration:</span></span>

- <span data-ttu-id="dfe7c-147">**TestStructInStruct** exportovaný z knihovny pinvokelib. dll.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-147">**TestStructInStruct** exported from PinvokeLib.dll.</span></span>

    ```cpp
    int TestStructInStruct(MYPERSON2* pPerson2);
    ```

- <span data-ttu-id="dfe7c-148">**TestStructInStruct3** exportovaný z knihovny pinvokelib. dll.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-148">**TestStructInStruct3** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestStructInStruct3(MYPERSON3 person3);
    ```

- <span data-ttu-id="dfe7c-149">**TestArrayInStruct** exportovaný z knihovny pinvokelib. dll.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-149">**TestArrayInStruct** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestArrayInStruct(MYARRAYSTRUCT* pStruct);
    ```

<span data-ttu-id="dfe7c-150">[Knihovny pinvokelib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) je vlastní nespravovaná knihovna, která obsahuje implementace pro dříve uvedené funkce a čtyři struktury: **MYPERSON**, **MYPERSON2**, **MYPERSON3**a **MYARRAYSTRUCT**.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-150">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and four structures: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, and **MYARRAYSTRUCT**.</span></span> <span data-ttu-id="dfe7c-151">Tyto struktury obsahují následující prvky:</span><span class="sxs-lookup"><span data-stu-id="dfe7c-151">These structures contain the following elements:</span></span>

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

<span data-ttu-id="dfe7c-152">Spravované `MyPerson`, `MyPerson2`, `MyPerson3`a struktury `MyArrayStruct` mají následující charakteristiky:</span><span class="sxs-lookup"><span data-stu-id="dfe7c-152">The managed `MyPerson`, `MyPerson2`, `MyPerson3`, and `MyArrayStruct` structures have the following characteristic:</span></span>

- <span data-ttu-id="dfe7c-153">`MyPerson` obsahuje pouze řetězcové členy.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-153">`MyPerson` contains only string members.</span></span> <span data-ttu-id="dfe7c-154">Pole [CharSet](specifying-a-character-set.md) nastaví řetězce na formát ANSI při předání do nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-154">The [CharSet](specifying-a-character-set.md) field sets the strings to ANSI format when passed to the unmanaged function.</span></span>

- <span data-ttu-id="dfe7c-155">`MyPerson2` obsahuje **IntPtr** ke struktuře `MyPerson`.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-155">`MyPerson2` contains an **IntPtr** to the `MyPerson` structure.</span></span> <span data-ttu-id="dfe7c-156">Typ **IntPtr** nahrazuje původní ukazatel na nespravovanou strukturu, protože .NET Framework aplikace nepoužívají ukazatele, pokud není kód označen jako **nebezpečný**.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-156">The **IntPtr** type replaces the original pointer to the unmanaged structure because .NET Framework applications do not use pointers unless the code is marked **unsafe**.</span></span>

- <span data-ttu-id="dfe7c-157">`MyPerson3` obsahuje `MyPerson` jako vloženou strukturu.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-157">`MyPerson3` contains `MyPerson` as an embedded structure.</span></span> <span data-ttu-id="dfe7c-158">Strukturu vloženou v jiné struktuře lze sloučit umístěním prvků vložené struktury přímo do hlavní struktury, nebo může být ponechána jako vložená struktura, jak je provedeno v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-158">A structure embedded within another structure can be flattened by placing the elements of the embedded structure directly into the main structure, or it can be left as an embedded structure, as is done in this sample.</span></span>

- <span data-ttu-id="dfe7c-159">`MyArrayStruct` obsahuje pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-159">`MyArrayStruct` contains an array of integers.</span></span> <span data-ttu-id="dfe7c-160">Atribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> nastaví hodnotu výčtu <xref:System.Runtime.InteropServices.UnmanagedType> na **ByValArray**, která slouží k označení počtu prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-160">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration value to **ByValArray**, which is used to indicate the number of elements in the array.</span></span>

<span data-ttu-id="dfe7c-161">Pro všechny struktury v této ukázce je použit atribut <xref:System.Runtime.InteropServices.StructLayoutAttribute>, aby bylo zajištěno, že jsou členy uspořádány v paměti sekvenčně v pořadí, ve kterém jsou uvedeny.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-161">For all structures in this sample, the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is applied to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>

<span data-ttu-id="dfe7c-162">Třída `NativeMethods` obsahuje spravované prototypy pro `TestStructInStruct`, `TestStructInStruct3`a metody `TestArrayInStruct`, které jsou volány `App` třídou.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-162">The `NativeMethods` class contains managed prototypes for the `TestStructInStruct`, `TestStructInStruct3`, and `TestArrayInStruct` methods called by the `App` class.</span></span> <span data-ttu-id="dfe7c-163">Každý prototyp deklaruje jeden parametr následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="dfe7c-163">Each prototype declares a single parameter, as follows:</span></span>

- <span data-ttu-id="dfe7c-164">`TestStructInStruct` deklaruje odkaz na typ `MyPerson2` jako svůj parametr.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-164">`TestStructInStruct` declares a reference to type `MyPerson2` as its parameter.</span></span>

- <span data-ttu-id="dfe7c-165">`TestStructInStruct3` deklaruje typ `MyPerson3` jako svůj parametr a předá parametr podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-165">`TestStructInStruct3` declares type `MyPerson3` as its parameter and passes the parameter by value.</span></span>

- <span data-ttu-id="dfe7c-166">`TestArrayInStruct` deklaruje odkaz na typ `MyArrayStruct` jako svůj parametr.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-166">`TestArrayInStruct` declares a reference to type `MyArrayStruct` as its parameter.</span></span>

<span data-ttu-id="dfe7c-167">Struktury jako argumenty metod jsou předávány hodnotou, pokud parametr neobsahuje klíčové slovo **ref** (**ByRef** in Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="dfe7c-167">Structures as arguments to methods are passed by value unless the parameter contains the **ref** (**ByRef** in Visual Basic) keyword.</span></span> <span data-ttu-id="dfe7c-168">Například metoda `TestStructInStruct` předává odkaz (hodnotu adresy) objektu typu `MyPerson2` nespravovanému kódu.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-168">For example, the `TestStructInStruct` method passes a reference (the value of an address) to an object of type `MyPerson2` to unmanaged code.</span></span> <span data-ttu-id="dfe7c-169">Aby bylo možné manipulovat se strukturou, na kterou `MyPerson2` odkazuje, ukázka vytvoří vyrovnávací paměť zadané velikosti a vrátí její adresu kombinováním metod <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> a <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-169">To manipulate the structure that `MyPerson2` points to, the sample creates a buffer of a specified size and returns its address by combining the <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="dfe7c-170">V dalším kroku zkopíruje ukázka obsah spravované struktury do nespravované vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-170">Next, the sample copies the content of the managed structure to the unmanaged buffer.</span></span> <span data-ttu-id="dfe7c-171">Nakonec ukázka používá metodu <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> k zařazování dat z nespravované vyrovnávací paměti do spravovaného objektu a metoda <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> pro uvolnění nespravovaného bloku paměti.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-171">Finally, the sample uses the <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> method to marshal data from the unmanaged buffer to a managed object and the <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> method to free the unmanaged block of memory.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="dfe7c-172">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="dfe7c-172">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#23](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
[!code-csharp[Conceptual.Interop.Marshaling#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
[!code-vb[Conceptual.Interop.Marshaling#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]

### <a name="calling-functions"></a><span data-ttu-id="dfe7c-173">Funkce volání</span><span class="sxs-lookup"><span data-stu-id="dfe7c-173">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#24](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
[!code-csharp[Conceptual.Interop.Marshaling#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
[!code-vb[Conceptual.Interop.Marshaling#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]

## <a name="findfile-sample"></a><span data-ttu-id="dfe7c-174">FindFile – ukázka</span><span class="sxs-lookup"><span data-stu-id="dfe7c-174">FindFile sample</span></span>

<span data-ttu-id="dfe7c-175">Tato ukázka předvádí, jak předat strukturu, která obsahuje druhou, vloženou strukturu do nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-175">This sample demonstrates how to pass a structure that contains a second, embedded structure to an unmanaged function.</span></span> <span data-ttu-id="dfe7c-176">Také ukazuje, jak použít atribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> k deklaraci pole s pevnou délkou v rámci struktury.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-176">It also demonstrates how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to declare a fixed-length array within the structure.</span></span> <span data-ttu-id="dfe7c-177">V této ukázce jsou vložené prvky struktury přidány do nadřazené struktury.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-177">In this sample, the embedded structure elements are added to the parent structure.</span></span> <span data-ttu-id="dfe7c-178">Ukázku vložené struktury, která není shrnuta, naleznete v části [struktury Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="dfe7c-178">For a sample of an embedded structure that is not flattened, see [Structures Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span></span>

<span data-ttu-id="dfe7c-179">Ukázka FindFile – používá následující nespravovanou funkci, která se zobrazuje s její původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="dfe7c-179">The FindFile sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="dfe7c-180">**FindFirstFile** exportovaný z Kernel32. dll.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-180">**FindFirstFile** exported from Kernel32.dll.</span></span>

    ```cpp
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);
    ```

<span data-ttu-id="dfe7c-181">Původní struktura předaná funkci obsahuje následující prvky:</span><span class="sxs-lookup"><span data-stu-id="dfe7c-181">The original structure passed to the function contains the following elements:</span></span>

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

<span data-ttu-id="dfe7c-182">V této ukázce třída `FindData` obsahuje odpovídající datový člen pro každý prvek původní struktury a vloženou strukturu.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-182">In this sample, the `FindData` class contains a corresponding data member for each element of the original structure and the embedded structure.</span></span> <span data-ttu-id="dfe7c-183">Místo dvou původních vyrovnávacích pamětí znaků třída nahradí řetězce.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-183">In place of two original character buffers, the class substitutes strings.</span></span> <span data-ttu-id="dfe7c-184">**MarshalAsAttribute** nastaví výčet <xref:System.Runtime.InteropServices.UnmanagedType> na **ByValTStr**, který slouží k identifikaci vložených znakových polí s pevnou délkou, která se zobrazí v nespravovaných strukturách.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-184">**MarshalAsAttribute** sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged structures.</span></span>

<span data-ttu-id="dfe7c-185">Třída `NativeMethods` obsahuje spravovaný prototyp metody `FindFirstFile`, která předá třídu `FindData` jako parametr.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-185">The `NativeMethods` class contains a managed prototype of the `FindFirstFile` method, which passes the `FindData` class as a parameter.</span></span> <span data-ttu-id="dfe7c-186">Parametr musí být deklarován s atributy <xref:System.Runtime.InteropServices.InAttribute> a <xref:System.Runtime.InteropServices.OutAttribute>, protože třídy, které jsou odkazové typy, jsou předány jako parametry ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-186">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="dfe7c-187">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="dfe7c-187">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#17](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
[!code-csharp[Conceptual.Interop.Marshaling#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
[!code-vb[Conceptual.Interop.Marshaling#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]

### <a name="calling-functions"></a><span data-ttu-id="dfe7c-188">Funkce volání</span><span class="sxs-lookup"><span data-stu-id="dfe7c-188">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#18](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
[!code-csharp[Conceptual.Interop.Marshaling#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]

## <a name="unions-sample"></a><span data-ttu-id="dfe7c-189">sjednocení – ukázka</span><span class="sxs-lookup"><span data-stu-id="dfe7c-189">Unions sample</span></span>

<span data-ttu-id="dfe7c-190">Tato ukázka předvádí, jak předat struktury obsahující pouze typy hodnot a struktury obsahující typ hodnoty a řetězec jako parametry nespravované funkce, které očekávají sjednocení.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-190">This sample demonstrates how to pass structures containing only value types, and structures containing a value type and a string as parameters to an unmanaged function expecting a union.</span></span> <span data-ttu-id="dfe7c-191">Sjednocení představuje umístění v paměti, které může být sdíleno dvěma nebo více proměnnými.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-191">A union represents a memory location that can be shared by two or more variables.</span></span>

<span data-ttu-id="dfe7c-192">Vzor sjednocení používá následující nespravovanou funkci zobrazenou s původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="dfe7c-192">The Unions sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="dfe7c-193">**TestUnion** exportovaný z knihovny pinvokelib. dll.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-193">**TestUnion** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestUnion(MYUNION u, int type);
    ```

<span data-ttu-id="dfe7c-194">[Knihovny pinvokelib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) je vlastní nespravovaná knihovna, která obsahuje implementaci dříve uvedené funkce a dvou sjednocení, **MYUNION** a **MYUNION2**.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-194">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed function and two unions, **MYUNION** and **MYUNION2**.</span></span> <span data-ttu-id="dfe7c-195">Sjednocení obsahují následující prvky:</span><span class="sxs-lookup"><span data-stu-id="dfe7c-195">The unions contain the following elements:</span></span>

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

<span data-ttu-id="dfe7c-196">Ve spravovaném kódu jsou sjednocení definována jako struktury.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-196">In managed code, unions are defined as structures.</span></span> <span data-ttu-id="dfe7c-197">Struktura `MyUnion` obsahuje dva typy hodnot jako členy: celé číslo a typ Double.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-197">The `MyUnion` structure contains two value types as its members: an integer and a double.</span></span> <span data-ttu-id="dfe7c-198">Atribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> je nastaven na kontrolu nad přesným umístěním každého datového člena.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-198">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to control the precise position of each data member.</span></span> <span data-ttu-id="dfe7c-199">Atribut <xref:System.Runtime.InteropServices.FieldOffsetAttribute> poskytuje fyzickou pozici polí v rámci nespravované reprezentace sjednocení.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-199">The <xref:System.Runtime.InteropServices.FieldOffsetAttribute> attribute provides the physical position of fields within the unmanaged representation of a union.</span></span> <span data-ttu-id="dfe7c-200">Všimněte si, že oba členové mají stejné hodnoty posunutí, takže členové mohou definovat stejnou část paměti.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-200">Notice that both members have the same offset values, so the members can define the same piece of memory.</span></span>

<span data-ttu-id="dfe7c-201">`MyUnion2_1` a `MyUnion2_2` obsahují hodnotový typ (Integer) a řetězec v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-201">`MyUnion2_1` and `MyUnion2_2` contain a value type (integer) and a string, respectively.</span></span> <span data-ttu-id="dfe7c-202">Ve spravovaném kódu se typy hodnot a typy odkazů nepovolují překrývat.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-202">In managed code, value types and reference types are not permitted to overlap.</span></span> <span data-ttu-id="dfe7c-203">Tato ukázka používá přetížení metody, aby volající mohl použít oba typy při volání stejné nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-203">This sample uses method overloading to enable the caller to use both types when calling the same unmanaged function.</span></span> <span data-ttu-id="dfe7c-204">Rozložení `MyUnion2_1` je explicitní a má přesnou hodnotu posunu.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-204">The layout of `MyUnion2_1` is explicit and has a precise offset value.</span></span> <span data-ttu-id="dfe7c-205">Naproti tomu `MyUnion2_2` má sekvenční rozložení, protože pro typy odkazů nejsou povolena explicitní rozložení.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-205">In contrast, `MyUnion2_2` has a sequential layout, because explicit layouts are not permitted with reference types.</span></span> <span data-ttu-id="dfe7c-206">Atribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> nastaví výčet <xref:System.Runtime.InteropServices.UnmanagedType> na **ByValTStr**, který se používá k identifikaci vložených znakových polí s pevnou délkou, která se zobrazí v nespravovaném vyjádření sjednocení.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-206">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged representation of the union.</span></span>

<span data-ttu-id="dfe7c-207">Třída `NativeMethods` obsahuje prototypy pro metody `TestUnion` a `TestUnion2`.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-207">The `NativeMethods` class contains the prototypes for the `TestUnion` and `TestUnion2` methods.</span></span> <span data-ttu-id="dfe7c-208">`TestUnion2` je přetížena pro deklaraci `MyUnion2_1` nebo `MyUnion2_2` jako parametrů.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-208">`TestUnion2` is overloaded to declare `MyUnion2_1` or `MyUnion2_2` as parameters.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="dfe7c-209">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="dfe7c-209">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#28](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
[!code-csharp[Conceptual.Interop.Marshaling#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
[!code-vb[Conceptual.Interop.Marshaling#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]

### <a name="calling-functions"></a><span data-ttu-id="dfe7c-210">Funkce volání</span><span class="sxs-lookup"><span data-stu-id="dfe7c-210">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#29](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
[!code-csharp[Conceptual.Interop.Marshaling#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
[!code-vb[Conceptual.Interop.Marshaling#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]

## <a name="systime-sample"></a><span data-ttu-id="dfe7c-211">SysTime – ukázka</span><span class="sxs-lookup"><span data-stu-id="dfe7c-211">SysTime sample</span></span>

<span data-ttu-id="dfe7c-212">Tato ukázka předvádí, jak předat ukazatel na třídu nespravované funkci, která očekává ukazatel na strukturu.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-212">This sample demonstrates how to pass a pointer to a class to an unmanaged function that expects a pointer to a structure.</span></span>

<span data-ttu-id="dfe7c-213">Ukázka sysTime – používá následující nespravovanou funkci, která se zobrazuje s její původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="dfe7c-213">The SysTime sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="dfe7c-214">**GetSystemTime** exportovaný z Kernel32. dll.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-214">**GetSystemTime** exported from Kernel32.dll.</span></span>

    ```cpp
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);
    ```

<span data-ttu-id="dfe7c-215">Původní struktura předaná funkci obsahuje následující prvky:</span><span class="sxs-lookup"><span data-stu-id="dfe7c-215">The original structure passed to the function contains the following elements:</span></span>

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

<span data-ttu-id="dfe7c-216">V této ukázce třída `SystemTime` obsahuje prvky původní struktury reprezentované jako členy třídy.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-216">In this sample, the `SystemTime` class contains the elements of the original structure represented as class members.</span></span> <span data-ttu-id="dfe7c-217">Atribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> je nastaven, aby bylo zajištěno, že členové jsou uspořádáni v paměti sekvenčně v pořadí, ve kterém jsou uvedeni.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-217">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>

<span data-ttu-id="dfe7c-218">Třída `NativeMethods` obsahuje spravovaný prototyp metody `GetSystemTime`, která ve výchozím nastavení předává třídu `SystemTime` jako vstupně-výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-218">The `NativeMethods` class contains a managed prototype of the `GetSystemTime` method, which passes the `SystemTime` class as an In/Out parameter by default.</span></span> <span data-ttu-id="dfe7c-219">Parametr musí být deklarován s atributy <xref:System.Runtime.InteropServices.InAttribute> a <xref:System.Runtime.InteropServices.OutAttribute>, protože třídy, které jsou odkazové typy, jsou předány jako parametry ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-219">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span> <span data-ttu-id="dfe7c-220">Aby volající mohl přijímat výsledky, musí být tyto [směrové atributy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) aplikovány explicitně.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-220">For the caller to receive the results, these [directional attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) must be applied explicitly.</span></span> <span data-ttu-id="dfe7c-221">Třída `App` vytvoří novou instanci třídy `SystemTime` a přistupuje k jejím datovým polím.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-221">The `App` class creates a new instance of the `SystemTime` class and accesses its data fields.</span></span>

### <a name="code-samples"></a><span data-ttu-id="dfe7c-222">Ukázky kódu</span><span class="sxs-lookup"><span data-stu-id="dfe7c-222">Code Samples</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#25](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
[!code-csharp[Conceptual.Interop.Marshaling#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
[!code-vb[Conceptual.Interop.Marshaling#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]

## <a name="outarrayofstructs-sample"></a><span data-ttu-id="dfe7c-223">OutArrayOfStructs – ukázka</span><span class="sxs-lookup"><span data-stu-id="dfe7c-223">OutArrayOfStructs sample</span></span>

<span data-ttu-id="dfe7c-224">Tento příklad ukazuje, jak předat pole struktur obsahující celá čísla a řetězce jako výstupní parametry nespravované funkci.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-224">This sample shows how to pass an array of structures that contains integers and strings as Out parameters to an unmanaged function.</span></span>

<span data-ttu-id="dfe7c-225">Tento příklad ukazuje, jak volat nativní funkci pomocí třídy <xref:System.Runtime.InteropServices.Marshal> a pomocí nebezpečného kódu.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-225">This sample demonstrates how to call a native function by using the <xref:System.Runtime.InteropServices.Marshal> class and by using unsafe code.</span></span>

<span data-ttu-id="dfe7c-226">Tato ukázka používá funkce obálky a vyvolání platformy definované v [knihovny pinvokelib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), které jsou také k dispozici ve zdrojových souborech.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-226">This sample uses a wrapper functions and platform invokes defined in [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), also provided in the source files.</span></span> <span data-ttu-id="dfe7c-227">Používá funkci `TestOutArrayOfStructs` a strukturu `MYSTRSTRUCT2`.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-227">It uses the `TestOutArrayOfStructs` function and the `MYSTRSTRUCT2` structure.</span></span> <span data-ttu-id="dfe7c-228">Struktura obsahuje následující prvky:</span><span class="sxs-lookup"><span data-stu-id="dfe7c-228">The structure contains the following elements:</span></span>

```cpp
typedef struct _MYSTRSTRUCT2
{
   char* buffer;
   UINT size;
} MYSTRSTRUCT2;
```

<span data-ttu-id="dfe7c-229">Třída `MyStruct` obsahuje objekt řetězce znaků ANSI.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-229">The `MyStruct` class contains a string object of ANSI characters.</span></span> <span data-ttu-id="dfe7c-230">Pole <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> určuje formát ANSI.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-230">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field specifies ANSI format.</span></span> <span data-ttu-id="dfe7c-231">`MyUnsafeStruct`je struktura obsahující <xref:System.IntPtr> typu místo řetězce.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-231">`MyUnsafeStruct`, is a structure containing an <xref:System.IntPtr> type instead of a string.</span></span>

<span data-ttu-id="dfe7c-232">Třída `NativeMethods` obsahuje přetíženou metodu `TestOutArrayOfStructs` prototypu.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-232">The `NativeMethods` class contains the overloaded `TestOutArrayOfStructs` prototype method.</span></span> <span data-ttu-id="dfe7c-233">Pokud metoda deklaruje ukazatel jako parametr, třída by měla být označena klíčovým slovem `unsafe`.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-233">If a method declares a pointer as a parameter, the class should be marked with the `unsafe` keyword.</span></span> <span data-ttu-id="dfe7c-234">Vzhledem k tomu, že Visual Basic nemůže použít nezabezpečený kód, přetíženou metodu, nezabezpečený modifikátor a `MyUnsafeStruct` strukturu jsou zbytečné.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-234">Because Visual Basic cannot use unsafe code, the overloaded method, unsafe modifier, and the `MyUnsafeStruct` structure are unnecessary.</span></span>

<span data-ttu-id="dfe7c-235">Třída `App` implementuje `UsingMarshaling` metodu, která provádí všechny úlohy nezbytné k předání pole.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-235">The `App` class implements the `UsingMarshaling` method, which performs all the tasks necessary to pass the array.</span></span> <span data-ttu-id="dfe7c-236">Pole je označeno pomocí klíčového slova `out` (`ByRef` in Visual Basic) k označení toho, že data přecházejí ze volaného volajícího.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-236">The array is marked with the `out` (`ByRef` in Visual Basic) keyword to indicate that data passes from callee to caller.</span></span> <span data-ttu-id="dfe7c-237">Implementace používá následující metody třídy <xref:System.Runtime.InteropServices.Marshal>:</span><span class="sxs-lookup"><span data-stu-id="dfe7c-237">The implementation uses the following <xref:System.Runtime.InteropServices.Marshal> class methods:</span></span>

- <span data-ttu-id="dfe7c-238"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> zařazovat data z nespravované vyrovnávací paměti do spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-238"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> to marshal data from the unmanaged buffer to a managed object.</span></span>

- <span data-ttu-id="dfe7c-239"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> uvolnění paměti rezervované pro řetězce ve struktuře.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-239"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> to release the memory reserved for strings in the structure.</span></span>

- <span data-ttu-id="dfe7c-240">pro uvolnění paměti rezervované pro pole <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-240"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> to release the memory reserved for the array.</span></span>

<span data-ttu-id="dfe7c-241">Jak už jsme uvedli C# , umožňuje nezabezpečený kód a Visual Basic ne.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-241">As previously mentioned, C# allows unsafe code and Visual Basic does not.</span></span> <span data-ttu-id="dfe7c-242">V C# ukázce je `UsingUnsafePointer` alternativou implementace metody, která používá ukazatele namísto <xref:System.Runtime.InteropServices.Marshal> třídy k předání pole obsahujícího strukturu `MyUnsafeStruct`.</span><span class="sxs-lookup"><span data-stu-id="dfe7c-242">In the C# sample, `UsingUnsafePointer` is an alternative method implementation that uses pointers instead of the <xref:System.Runtime.InteropServices.Marshal> class to pass back the array containing the `MyUnsafeStruct` structure.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="dfe7c-243">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="dfe7c-243">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#20](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
[!code-csharp[Conceptual.Interop.Marshaling#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
[!code-vb[Conceptual.Interop.Marshaling#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]

### <a name="calling-functions"></a><span data-ttu-id="dfe7c-244">Funkce volání</span><span class="sxs-lookup"><span data-stu-id="dfe7c-244">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#21](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
[!code-csharp[Conceptual.Interop.Marshaling#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
[!code-vb[Conceptual.Interop.Marshaling#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]

## <a name="see-also"></a><span data-ttu-id="dfe7c-245">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dfe7c-245">See also</span></span>

- [<span data-ttu-id="dfe7c-246">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="dfe7c-246">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
- [<span data-ttu-id="dfe7c-247">Zařazování řetězců</span><span class="sxs-lookup"><span data-stu-id="dfe7c-247">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="dfe7c-248">Zařazování různých typů polí</span><span class="sxs-lookup"><span data-stu-id="dfe7c-248">Marshaling Different Types of Arrays</span></span>](marshaling-different-types-of-arrays.md)
