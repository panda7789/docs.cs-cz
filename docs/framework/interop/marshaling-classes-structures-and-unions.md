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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d08056780fe3042983ea021e5a4cd82a14d252a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113721"
---
# <a name="marshaling-classes-structures-and-unions"></a><span data-ttu-id="ac1bd-102">Zařazování tříd, struktur a sjednocení</span><span class="sxs-lookup"><span data-stu-id="ac1bd-102">Marshaling Classes, Structures, and Unions</span></span>
<span data-ttu-id="ac1bd-103">Třídy a struktury jsou podobné jako u rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-103">Classes and structures are similar in the .NET Framework.</span></span> <span data-ttu-id="ac1bd-104">Můžete mít pole, vlastnosti a události.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-104">Both can have fields, properties, and events.</span></span> <span data-ttu-id="ac1bd-105">Můžou také mít statické a nestatické metody.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-105">They can also have static and nonstatic methods.</span></span> <span data-ttu-id="ac1bd-106">Jeden velký rozdíl je, že struktury jsou typy hodnot a třídy jsou odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-106">One notable difference is that structures are value types and classes are reference types.</span></span>  
  
 <span data-ttu-id="ac1bd-107">V následující tabulce jsou uvedeny možnosti zařazování pro třídy, struktury a sjednocení; Popisuje jejich použití; a získáte odkaz na odpovídající platformu vyvolání vzorku.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-107">The following table lists marshaling options for classes, structures, and unions; describes their usage; and provides a link to the corresponding platform invoke sample.</span></span>  
  
|<span data-ttu-id="ac1bd-108">Type</span><span class="sxs-lookup"><span data-stu-id="ac1bd-108">Type</span></span>|<span data-ttu-id="ac1bd-109">Popis</span><span class="sxs-lookup"><span data-stu-id="ac1bd-109">Description</span></span>|<span data-ttu-id="ac1bd-110">Ukázka</span><span class="sxs-lookup"><span data-stu-id="ac1bd-110">Sample</span></span>|  
|----------|-----------------|------------|  
|<span data-ttu-id="ac1bd-111">Třída podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-111">Class by value.</span></span>|<span data-ttu-id="ac1bd-112">Předá třída s atributem členů celého čísla jako vstupně-výstupní parametr, jako spravované případ.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-112">Passes a class with integer members as an In/Out parameter, like the managed case.</span></span>|<span data-ttu-id="ac1bd-113">SysTime – ukázka</span><span class="sxs-lookup"><span data-stu-id="ac1bd-113">SysTime sample</span></span>|  
|<span data-ttu-id="ac1bd-114">Struktura podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-114">Structure by value.</span></span>|<span data-ttu-id="ac1bd-115">Předává struktury jako parametry in.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-115">Passes structures as In parameters.</span></span>|<span data-ttu-id="ac1bd-116">Ukázka struktur</span><span class="sxs-lookup"><span data-stu-id="ac1bd-116">Structures sample</span></span>|  
|<span data-ttu-id="ac1bd-117">Struktura podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-117">Structure by reference.</span></span>|<span data-ttu-id="ac1bd-118">Předává struktury jako vstup a výstup parametry.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-118">Passes structures as In/Out parameters.</span></span>|<span data-ttu-id="ac1bd-119">OSInfo – ukázka</span><span class="sxs-lookup"><span data-stu-id="ac1bd-119">OSInfo sample</span></span>|  
|<span data-ttu-id="ac1bd-120">Struktura s vnořené struktury (plochý).</span><span class="sxs-lookup"><span data-stu-id="ac1bd-120">Structure with nested structures (flattened).</span></span>|<span data-ttu-id="ac1bd-121">Předává třídu, která reprezentuje strukturu s vnořené struktury v nespravované funkci.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-121">Passes a class that represents a structure with nested structures in the unmanaged function.</span></span> <span data-ttu-id="ac1bd-122">Struktura se sloučí do jednoho velké objemy struktury v spravovaný prototyp.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-122">The structure is flattened to one big structure in the managed prototype.</span></span>|<span data-ttu-id="ac1bd-123">FindFile – ukázka</span><span class="sxs-lookup"><span data-stu-id="ac1bd-123">FindFile sample</span></span>|  
|<span data-ttu-id="ac1bd-124">Struktura s ukazatelem na jinou strukturu.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-124">Structure with a pointer to another structure.</span></span>|<span data-ttu-id="ac1bd-125">Předává strukturu, která obsahuje ukazatel na strukturu druhý jako člena.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-125">Passes a structure that contains a pointer to a second structure as a member.</span></span>|<span data-ttu-id="ac1bd-126">Ukázka struktur</span><span class="sxs-lookup"><span data-stu-id="ac1bd-126">Structures Sample</span></span>|  
|<span data-ttu-id="ac1bd-127">Pole struktury s celými čísly podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-127">Array of structures with integers by value.</span></span>|<span data-ttu-id="ac1bd-128">Předá pole struktury, které obsahují pouze celá čísla jako vstupně-výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-128">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="ac1bd-129">Členy pole lze změnit.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-129">Members of the array can be changed.</span></span>|<span data-ttu-id="ac1bd-130">Ukázka polí</span><span class="sxs-lookup"><span data-stu-id="ac1bd-130">Arrays Sample</span></span>|  
|<span data-ttu-id="ac1bd-131">Pole struktury s celá čísla a řetězce podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-131">Array of structures with integers and strings by reference.</span></span>|<span data-ttu-id="ac1bd-132">Předá pole struktury, které obsahují řetězce a celá čísla jako parametr Out.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-132">Passes an array of structures that contain integers and strings as an Out parameter.</span></span> <span data-ttu-id="ac1bd-133">Volaná funkce přiděluje paměť pro pole.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-133">The called function allocates memory for the array.</span></span>|<span data-ttu-id="ac1bd-134">OutArrayOfStructs – ukázka</span><span class="sxs-lookup"><span data-stu-id="ac1bd-134">OutArrayOfStructs Sample</span></span>|  
|<span data-ttu-id="ac1bd-135">Sjednocení s typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-135">Unions with value types.</span></span>|<span data-ttu-id="ac1bd-136">Předá sjednocení s typy hodnot (celé číslo a dvojitá).</span><span class="sxs-lookup"><span data-stu-id="ac1bd-136">Passes unions with value types (integer and double).</span></span>|<span data-ttu-id="ac1bd-137">sjednocení – ukázka</span><span class="sxs-lookup"><span data-stu-id="ac1bd-137">Unions sample</span></span>|  
|<span data-ttu-id="ac1bd-138">Sjednocení s smíšené typy.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-138">Unions with mixed types.</span></span>|<span data-ttu-id="ac1bd-139">Předá sjednocení s smíšené typy (celé číslo a řetězec).</span><span class="sxs-lookup"><span data-stu-id="ac1bd-139">Passes unions with mixed types (integer and string).</span></span>|<span data-ttu-id="ac1bd-140">sjednocení – ukázka</span><span class="sxs-lookup"><span data-stu-id="ac1bd-140">Unions sample</span></span>|  
|<span data-ttu-id="ac1bd-141">Hodnoty Null ve struktuře.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-141">Null values in structure.</span></span>|<span data-ttu-id="ac1bd-142">Předá odkaz s hodnotou null (**nic** v jazyce Visual Basic) namísto odkazu na typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-142">Passes a null reference (**Nothing** in Visual Basic) instead of a reference to a value type.</span></span>|<span data-ttu-id="ac1bd-143">HandleRef – ukázka</span><span class="sxs-lookup"><span data-stu-id="ac1bd-143">HandleRef sample</span></span>|  
  
## <a name="structures-sample"></a><span data-ttu-id="ac1bd-144">Ukázka struktur</span><span class="sxs-lookup"><span data-stu-id="ac1bd-144">Structures sample</span></span>  
 <span data-ttu-id="ac1bd-145">Tento příklad ukazuje, jak předat strukturu, která odkazuje na druhý strukturu, předejte strukturu s vložené struktury a předejte strukturu s vložené pole.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-145">This sample demonstrates how to pass a structure that points to a second structure, pass a structure with an embedded structure, and pass a structure with an embedded array.</span></span>  
  
 <span data-ttu-id="ac1bd-146">Ukázka struktur používá následující nespravované funkce zobrazené s původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="ac1bd-146">The Structs sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="ac1bd-147">**TestStructInStruct** exportovaná z knihovny PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-147">**TestStructInStruct** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestStructInStruct(MYPERSON2* pPerson2);  
    ```  
  
-   <span data-ttu-id="ac1bd-148">**TestStructInStruct3** exportovaná z knihovny PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-148">**TestStructInStruct3** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestStructInStruct3(MYPERSON3 person3);  
    ```  
  
-   <span data-ttu-id="ac1bd-149">**TestArrayInStruct** exportovaná z knihovny PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-149">**TestArrayInStruct** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestArrayInStruct( MYARRAYSTRUCT* pStruct );  
    ```  
  
 <span data-ttu-id="ac1bd-150">[Knihovny PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) je vlastní nespravovaná knihovna, která obsahuje implementace dříve uvedených funkcí a čtyři struktury: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, a **MYARRAYSTRUCT**.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-150">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and four structures: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, and **MYARRAYSTRUCT**.</span></span> <span data-ttu-id="ac1bd-151">Tyto struktury obsahují následující prvky:</span><span class="sxs-lookup"><span data-stu-id="ac1bd-151">These structures contain the following elements:</span></span>  
  
```  
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
  
 <span data-ttu-id="ac1bd-152">Spravovanou `MyPerson`, `MyPerson2`, `MyPerson3`, a `MyArrayStruct` struktury mají následující charakteristiky:</span><span class="sxs-lookup"><span data-stu-id="ac1bd-152">The managed `MyPerson`, `MyPerson2`, `MyPerson3`, and `MyArrayStruct` structures have the following characteristic:</span></span>  
  
-   <span data-ttu-id="ac1bd-153">`MyPerson` obsahuje pouze členy řetězec.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-153">`MyPerson` contains only string members.</span></span> <span data-ttu-id="ac1bd-154">[CharSet](specifying-a-character-set.md) pole nastaví řetězce formátu ANSI předány nespravované funkci.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-154">The [CharSet](specifying-a-character-set.md) field sets the strings to ANSI format when passed to the unmanaged function.</span></span>  
  
-   <span data-ttu-id="ac1bd-155">`MyPerson2` obsahuje **IntPtr** k `MyPerson` struktury.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-155">`MyPerson2` contains an **IntPtr** to the `MyPerson` structure.</span></span> <span data-ttu-id="ac1bd-156">**IntPtr** typ nahradí původní ukazatel na nespravované struktury, protože aplikace rozhraní .NET Framework nepoužívejte ukazatele, pokud kód je označen **nebezpečné**.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-156">The **IntPtr** type replaces the original pointer to the unmanaged structure because .NET Framework applications do not use pointers unless the code is marked **unsafe**.</span></span>  
  
-   <span data-ttu-id="ac1bd-157">`MyPerson3` obsahuje `MyPerson` jako vložené struktury.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-157">`MyPerson3` contains `MyPerson` as an embedded structure.</span></span> <span data-ttu-id="ac1bd-158">Struktura vložených v jiné struktuře můžete plochý tak, že prvky vložené struktury přímo do hlavní struktury nebo ji lze ponechat jako vložené struktury, jak je tomu v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-158">A structure embedded within another structure can be flattened by placing the elements of the embedded structure directly into the main structure, or it can be left as an embedded structure, as is done in this sample.</span></span>  
  
-   <span data-ttu-id="ac1bd-159">`MyArrayStruct` obsahuje pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-159">`MyArrayStruct` contains an array of integers.</span></span> <span data-ttu-id="ac1bd-160"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nastaví <xref:System.Runtime.InteropServices.UnmanagedType> hodnotu výčtu pro **ByValArray**, který se používá k určení počtu prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-160">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration value to **ByValArray**, which is used to indicate the number of elements in the array.</span></span>  
  
 <span data-ttu-id="ac1bd-161">Pro všechny struktury v této ukázce <xref:System.Runtime.InteropServices.StructLayoutAttribute> atributu se použije pro zajištění, že členové jsou uspořádáni v paměti sekvenčně, v pořadí, v jakém jsou uvedeny.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-161">For all structures in this sample, the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is applied to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="ac1bd-162">`LibWrap` Třída obsahuje spravované prototypy pro `TestStructInStruct`, `TestStructInStruct3`, a `TestArrayInStruct` volané metody `App` třídy.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-162">The `LibWrap` class contains managed prototypes for the `TestStructInStruct`, `TestStructInStruct3`, and `TestArrayInStruct` methods called by the `App` class.</span></span> <span data-ttu-id="ac1bd-163">Každý prototyp deklaruje jediný parametr, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ac1bd-163">Each prototype declares a single parameter, as follows:</span></span>  
  
-   <span data-ttu-id="ac1bd-164">`TestStructInStruct` deklaruje odkaz na typ `MyPerson2` jako svůj parametr.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-164">`TestStructInStruct` declares a reference to type `MyPerson2` as its parameter.</span></span>  
  
-   <span data-ttu-id="ac1bd-165">`TestStructInStruct3` deklaruje typ `MyPerson3` jako svůj parametr a předá podle hodnoty parametru.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-165">`TestStructInStruct3` declares type `MyPerson3` as its parameter and passes the parameter by value.</span></span>  
  
-   <span data-ttu-id="ac1bd-166">`TestArrayInStruct` deklaruje odkaz na typ `MyArrayStruct` jako svůj parametr.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-166">`TestArrayInStruct` declares a reference to type `MyArrayStruct` as its parameter.</span></span>  
  
 <span data-ttu-id="ac1bd-167">Struktury jako argumenty metod jsou předávány hodnotou, pokud parametr obsahuje **ref** (**ByRef** v jazyce Visual Basic) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-167">Structures as arguments to methods are passed by value unless the parameter contains the **ref** (**ByRef** in Visual Basic) keyword.</span></span> <span data-ttu-id="ac1bd-168">Například `TestStructInStruct` metoda předává odkazem (hodnota adresy) na objekt typu `MyPerson2` nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-168">For example, the `TestStructInStruct` method passes a reference (the value of an address) to an object of type `MyPerson2` to unmanaged code.</span></span> <span data-ttu-id="ac1bd-169">K manipulaci s strukturu, která `MyPerson2` odkazuje na ukázky vytvoří vyrovnávací paměti o zadané velikosti a vrátí jeho adresu tím, že zkombinujete <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> a <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-169">To manipulate the structure that `MyPerson2` points to, the sample creates a buffer of a specified size and returns its address by combining the <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="ac1bd-170">Dále ukázka zkopíruje obsah spravovaná struktura do nespravované vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-170">Next, the sample copies the content of the managed structure to the unmanaged buffer.</span></span> <span data-ttu-id="ac1bd-171">Nakonec příklad používá <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> metodu zařazování dat z vyrovnávací paměti nespravovaného do spravovaného objektu a <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> metodu pro uvolnění nespravovaných blok paměti.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-171">Finally, the sample uses the <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> method to marshal data from the unmanaged buffer to a managed object and the <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> method to free the unmanaged block of memory.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="ac1bd-172">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="ac1bd-172">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
 [!code-csharp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
 [!code-vb[Conceptual.Interop.Marshaling#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]  
  
### <a name="calling-functions"></a><span data-ttu-id="ac1bd-173">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="ac1bd-173">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
 [!code-csharp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
 [!code-vb[Conceptual.Interop.Marshaling#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]  
  
## <a name="findfile-sample"></a><span data-ttu-id="ac1bd-174">FindFile – ukázka</span><span class="sxs-lookup"><span data-stu-id="ac1bd-174">FindFile sample</span></span>  
 <span data-ttu-id="ac1bd-175">Tato ukázka předvádí, jak předat strukturu, která obsahuje druhý, vložené struktury nespravované funkci.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-175">This sample demonstrates how to pass a structure that contains a second, embedded structure to an unmanaged function.</span></span> <span data-ttu-id="ac1bd-176">Také ukazuje, jak používat <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut, chcete-li deklarovat pole s pevnou délkou v rámci struktury.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-176">It also demonstrates how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to declare a fixed-length array within the structure.</span></span> <span data-ttu-id="ac1bd-177">V této ukázce jsou elementy vložené struktury přidány pro nadřazenou strukturu.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-177">In this sample, the embedded structure elements are added to the parent structure.</span></span> <span data-ttu-id="ac1bd-178">Ukázka vložené struktury, která se nesloučí, naleznete v tématu [ukázka struktur](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ac1bd-178">For a sample of an embedded structure that is not flattened, see [Structures Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span></span>  
  
 <span data-ttu-id="ac1bd-179">Findfile – Ukázka používá následující nespravovanou funkci zobrazenou s původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="ac1bd-179">The FindFile sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="ac1bd-180">**FindFirstFile** exportovaná ze souboru Kernel32.dll.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-180">**FindFirstFile** exported from Kernel32.dll.</span></span>  
  
    ```  
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);  
    ```  
  
 <span data-ttu-id="ac1bd-181">Původní struktura předaná funkci obsahuje následující prvky:</span><span class="sxs-lookup"><span data-stu-id="ac1bd-181">The original structure passed to the function contains the following elements:</span></span>  
  
```  
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
  
 <span data-ttu-id="ac1bd-182">V této ukázce `FindData` třída obsahuje odpovídající datový člen pro každý prvek původní struktury a vložené struktury.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-182">In this sample, the `FindData` class contains a corresponding data member for each element of the original structure and the embedded structure.</span></span> <span data-ttu-id="ac1bd-183">Místo dvou původní znak vyrovnávacích pamětí nahradí třída řetězce.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-183">In place of two original character buffers, the class substitutes strings.</span></span> <span data-ttu-id="ac1bd-184">**MarshalAsAttribute** nastaví <xref:System.Runtime.InteropServices.UnmanagedType> výčet **ByValTStr**, který se používá k identifikaci vložený, znaků pevné délky pole, která se zobrazí v rámci nespravované struktury.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-184">**MarshalAsAttribute** sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged structures.</span></span>  
  
 <span data-ttu-id="ac1bd-185">`LibWrap` Třída obsahuje spravovaný prototyp metody `FindFirstFile` metodu, která předává `FindData` jako parametr předávat třídu.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-185">The `LibWrap` class contains a managed prototype of the `FindFirstFile` method, which passes the `FindData` class as a parameter.</span></span> <span data-ttu-id="ac1bd-186">Parametr musí být deklarován s <xref:System.Runtime.InteropServices.InAttribute> a <xref:System.Runtime.InteropServices.OutAttribute> atributy, protože třídy, které jsou odkazové typy, jsou předány jako parametry in ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-186">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="ac1bd-187">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="ac1bd-187">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
 [!code-csharp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
 [!code-vb[Conceptual.Interop.Marshaling#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]  
  
### <a name="calling-functions"></a><span data-ttu-id="ac1bd-188">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="ac1bd-188">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
 [!code-csharp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]  
  
## <a name="unions-sample"></a><span data-ttu-id="ac1bd-189">sjednocení – ukázka</span><span class="sxs-lookup"><span data-stu-id="ac1bd-189">Unions sample</span></span>  
 <span data-ttu-id="ac1bd-190">Tato ukázka předvádí, jak předat struktury obsahující pouze typy hodnot a struktury obsahující hodnotový typ a řetězec jako parametry pro nespravovaná funkce očekává sjednocení.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-190">This sample demonstrates how to pass structures containing only value types, and structures containing a value type and a string as parameters to an unmanaged function expecting a union.</span></span> <span data-ttu-id="ac1bd-191">Sjednocení představuje umístění paměti, které je možné sdílet mezi dvěma nebo více proměnných.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-191">A union represents a memory location that can be shared by two or more variables.</span></span>  
  
 <span data-ttu-id="ac1bd-192">Ukázka spojení používá následující nespravovanou funkci zobrazenou s původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="ac1bd-192">The Unions sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="ac1bd-193">**TestUnion** exportovaná z knihovny PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-193">**TestUnion** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestUnion(MYUNION u, int type);  
    ```  
  
 <span data-ttu-id="ac1bd-194">[Knihovny PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) je vlastní nespravovaná knihovna, která obsahuje implementace dříve uvedených funkcí a dvě spojení **MYUNION** a **MYUNION2**.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-194">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed function and two unions, **MYUNION** and **MYUNION2**.</span></span> <span data-ttu-id="ac1bd-195">Sjednocení obsahovat následující prvky:</span><span class="sxs-lookup"><span data-stu-id="ac1bd-195">The unions contain the following elements:</span></span>  
  
```  
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
  
 <span data-ttu-id="ac1bd-196">Ve spravovaném kódu sjednocení jsou definovány jako struktury.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-196">In managed code, unions are defined as structures.</span></span> <span data-ttu-id="ac1bd-197">`MyUnion` Struktura obsahuje dva typy hodnot jako členy: celé číslo a typ double.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-197">The `MyUnion` structure contains two value types as its members: an integer and a double.</span></span> <span data-ttu-id="ac1bd-198"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Atribut je nastaven na ovládací prvek přesné pozice každého datového člena.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-198">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to control the precise position of each data member.</span></span> <span data-ttu-id="ac1bd-199"><xref:System.Runtime.InteropServices.FieldOffsetAttribute> Atribut obsahuje fyzické umístění pole ve sjednocení nespravované reprezentace.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-199">The <xref:System.Runtime.InteropServices.FieldOffsetAttribute> attribute provides the physical position of fields within the unmanaged representation of a union.</span></span> <span data-ttu-id="ac1bd-200">Všimněte si, že oba členy mají stejné hodnoty posunu, aby členové mohli definovat stejnou část paměti.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-200">Notice that both members have the same offset values, so the members can define the same piece of memory.</span></span>  
  
 <span data-ttu-id="ac1bd-201">`MyUnion2_1` a `MyUnion2_2` obsahovat hodnotu typu (integer) a řetězec, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-201">`MyUnion2_1` and `MyUnion2_2` contain a value type (integer) and a string, respectively.</span></span> <span data-ttu-id="ac1bd-202">Ve spravovaném kódu nejsou povoleny typy hodnot a odkazové typy překrytí.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-202">In managed code, value types and reference types are not permitted to overlap.</span></span> <span data-ttu-id="ac1bd-203">Tato ukázka používá metody přetížení pro povolení volajícím použít oba typy při volání metody stejnou nespravovanou funkci.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-203">This sample uses method overloading to enable the caller to use both types when calling the same unmanaged function.</span></span> <span data-ttu-id="ac1bd-204">Rozložení `MyUnion2_1` je explicitní a má přesnou hodnotu posunu.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-204">The layout of `MyUnion2_1` is explicit and has a precise offset value.</span></span> <span data-ttu-id="ac1bd-205">Naproti tomu `MyUnion2_2` má sekvenční rozložení, protože explicitní rozložení se nedá vymezit přes typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-205">In contrast, `MyUnion2_2` has a sequential layout, because explicit layouts are not permitted with reference types.</span></span> <span data-ttu-id="ac1bd-206"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nastaví <xref:System.Runtime.InteropServices.UnmanagedType> výčet **ByValTStr**, který se používá k identifikaci vložený, znaků pevné délky pole, která se zobrazí v rámci nespravované reprezentace sjednocení.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-206">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged representation of the union.</span></span>  
  
 <span data-ttu-id="ac1bd-207">`LibWrap` Třída obsahuje prototypy pro `TestUnion` a `TestUnion2` metody.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-207">The `LibWrap` class contains the prototypes for the `TestUnion` and `TestUnion2` methods.</span></span> <span data-ttu-id="ac1bd-208">`TestUnion2` je přetížena pro deklaraci `MyUnion2_1` nebo `MyUnion2_2` jako parametry.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-208">`TestUnion2` is overloaded to declare `MyUnion2_1` or `MyUnion2_2` as parameters.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="ac1bd-209">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="ac1bd-209">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
 [!code-csharp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
 [!code-vb[Conceptual.Interop.Marshaling#28](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]  
  
### <a name="calling-functions"></a><span data-ttu-id="ac1bd-210">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="ac1bd-210">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
 [!code-csharp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
 [!code-vb[Conceptual.Interop.Marshaling#29](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]  
  
## <a name="systime-sample"></a><span data-ttu-id="ac1bd-211">SysTime – ukázka</span><span class="sxs-lookup"><span data-stu-id="ac1bd-211">SysTime sample</span></span>  
 <span data-ttu-id="ac1bd-212">Tato ukázka předvádí, jak předat ukazatel na třídu nespravované funkci, která očekává ukazatel na strukturu.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-212">This sample demonstrates how to pass a pointer to a class to an unmanaged function that expects a pointer to a structure.</span></span>  
  
 <span data-ttu-id="ac1bd-213">Systime – Ukázka používá následující nespravovanou funkci zobrazenou s původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="ac1bd-213">The SysTime sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="ac1bd-214">**GetSystemTime** exportovaná ze souboru Kernel32.dll.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-214">**GetSystemTime** exported from Kernel32.dll.</span></span>  
  
    ```  
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);  
    ```  
  
 <span data-ttu-id="ac1bd-215">Původní struktura předaná funkci obsahuje následující prvky:</span><span class="sxs-lookup"><span data-stu-id="ac1bd-215">The original structure passed to the function contains the following elements:</span></span>  
  
```  
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
  
 <span data-ttu-id="ac1bd-216">V této ukázce `SystemTime` třída obsahuje prvky původní struktury reprezentovaná jako členy třídy.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-216">In this sample, the `SystemTime` class contains the elements of the original structure represented as class members.</span></span> <span data-ttu-id="ac1bd-217"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Atribut je nastaven na Ujistěte se, že členové jsou uspořádáni v paměti sekvenčně, v pořadí, v jakém jsou uvedeny.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-217">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="ac1bd-218">`LibWrap` Třída obsahuje spravovaný prototyp metody `GetSystemTime` metodu, která předává `SystemTime` třídy jako vstupně -výstupní parametr ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-218">The `LibWrap` class contains a managed prototype of the `GetSystemTime` method, which passes the `SystemTime` class as an In/Out parameter by default.</span></span> <span data-ttu-id="ac1bd-219">Parametr musí být deklarován s <xref:System.Runtime.InteropServices.InAttribute> a <xref:System.Runtime.InteropServices.OutAttribute> atributy, protože třídy, které jsou odkazové typy, jsou předány jako parametry in ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-219">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span> <span data-ttu-id="ac1bd-220">Pro volajícího na příjem výsledků tyto [směrové atributy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) musí být použito explicitně.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-220">For the caller to receive the results, these [directional attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) must be applied explicitly.</span></span> <span data-ttu-id="ac1bd-221">`App` Vytvoří novou instanci třídy `SystemTime` třídy a přistupuje k jeho datová pole.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-221">The `App` class creates a new instance of the `SystemTime` class and accesses its data fields.</span></span>  
  
### <a name="code-samples"></a><span data-ttu-id="ac1bd-222">Ukázky kódu</span><span class="sxs-lookup"><span data-stu-id="ac1bd-222">Code Samples</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
 [!code-csharp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
 [!code-vb[Conceptual.Interop.Marshaling#25](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]  
  
## <a name="outarrayofstructs-sample"></a><span data-ttu-id="ac1bd-223">OutArrayOfStructs – ukázka</span><span class="sxs-lookup"><span data-stu-id="ac1bd-223">OutArrayOfStructs sample</span></span>  
 <span data-ttu-id="ac1bd-224">Tento příklad ukazuje, jak předat pole struktury, která obsahuje celá čísla a řetězce jako výstupní parametry nespravované funkci.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-224">This sample shows how to pass an array of structures that contains integers and strings as Out parameters to an unmanaged function.</span></span>  
  
 <span data-ttu-id="ac1bd-225">Tato ukázka předvádí, jak volat nativní funkce pomocí <xref:System.Runtime.InteropServices.Marshal> třídy a pomocí nezabezpečený kód.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-225">This sample demonstrates how to call a native function by using the <xref:System.Runtime.InteropServices.Marshal> class and by using unsafe code.</span></span>  
  
 <span data-ttu-id="ac1bd-226">Tato ukázka používá funkce obálky, a vyvolá platformu podle [knihovny PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), k dispozici také ve zdrojových souborech.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-226">This sample uses a wrapper functions and platform invokes defined in [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), also provided in the source files.</span></span> <span data-ttu-id="ac1bd-227">Používá `TestOutArrayOfStructs` funkce a `MYSTRSTRUCT2` struktury.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-227">It uses the `TestOutArrayOfStructs` function and the `MYSTRSTRUCT2` structure.</span></span> <span data-ttu-id="ac1bd-228">Struktura obsahuje následující prvky:</span><span class="sxs-lookup"><span data-stu-id="ac1bd-228">The structure contains the following elements:</span></span>  
  
```  
typedef struct _MYSTRSTRUCT2  
{  
   char* buffer;  
   UINT size;   
} MYSTRSTRUCT2;  
```  
  
 <span data-ttu-id="ac1bd-229">`MyStruct` Třída obsahuje objekt řetězce znaků ANSI.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-229">The `MyStruct` class contains a string object of ANSI characters.</span></span> <span data-ttu-id="ac1bd-230"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> Pole určuje formátu ANSI.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-230">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field specifies ANSI format.</span></span> <span data-ttu-id="ac1bd-231">`MyUnsafeStruct`, je struktura obsahující <xref:System.IntPtr> typ namísto řetězce.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-231">`MyUnsafeStruct`, is a structure containing an <xref:System.IntPtr> type instead of a string.</span></span>  
  
 <span data-ttu-id="ac1bd-232">`LibWrap` Třída obsahuje přetížené `TestOutArrayOfStructs` prototyp metody.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-232">The `LibWrap` class contains the overloaded `TestOutArrayOfStructs` prototype method.</span></span> <span data-ttu-id="ac1bd-233">Metoda deklaruje ukazatel, jako parametr, by měly být třídy označené `unsafe` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-233">If a method declares a pointer as a parameter, the class should be marked with the `unsafe` keyword.</span></span> <span data-ttu-id="ac1bd-234">Protože [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] nelze použít nezabezpečený kód, přetěžované metody, modifikátor unsafe a `MyUnsafeStruct` struktura nejsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-234">Because [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] cannot use unsafe code, the overloaded method, unsafe modifier, and the `MyUnsafeStruct` structure are unnecessary.</span></span>  
  
 <span data-ttu-id="ac1bd-235">`App` Implementuje třída `UsingMarshaling` metodu, která provádí všechny úkoly, které jsou nutné předat pole.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-235">The `App` class implements the `UsingMarshaling` method, which performs all the tasks necessary to pass the array.</span></span> <span data-ttu-id="ac1bd-236">Pole je označeno `out` (`ByRef` v jazyce Visual Basic) předá – klíčové slovo k označení tato data z volaný volající.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-236">The array is marked with the `out` (`ByRef` in Visual Basic) keyword to indicate that data passes from callee to caller.</span></span> <span data-ttu-id="ac1bd-237">Implementace používá následující <xref:System.Runtime.InteropServices.Marshal> metody třídy:</span><span class="sxs-lookup"><span data-stu-id="ac1bd-237">The implementation uses the following <xref:System.Runtime.InteropServices.Marshal> class methods:</span></span>  
  
-   <span data-ttu-id="ac1bd-238"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> zařazování dat z vyrovnávací paměti nespravovaného do spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-238"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> to marshal data from the unmanaged buffer to a managed object.</span></span>  
  
-   <span data-ttu-id="ac1bd-239"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> k uvolnění paměti vyhrazená pro řetězce ve struktuře.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-239"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> to release the memory reserved for strings in the structure.</span></span>  
  
-   <span data-ttu-id="ac1bd-240"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> k uvolnění paměti vyhrazená pro pole.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-240"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> to release the memory reserved for the array.</span></span>  
  
 <span data-ttu-id="ac1bd-241">Jak už jsme zmínili, C# umožňuje nezabezpečený kód a [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] tak není.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-241">As previously mentioned, C# allows unsafe code and [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] does not.</span></span> <span data-ttu-id="ac1bd-242">V C# ukázce `UsingUnsafePointer` je to alternativní metoda pro implementace, která používá ukazatele namísto <xref:System.Runtime.InteropServices.Marshal> třídy předat zpět na pole obsahující `MyUnsafeStruct` struktury.</span><span class="sxs-lookup"><span data-stu-id="ac1bd-242">In the C# sample, `UsingUnsafePointer` is an alternative method implementation that uses pointers instead of the <xref:System.Runtime.InteropServices.Marshal> class to pass back the array containing the `MyUnsafeStruct` structure.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="ac1bd-243">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="ac1bd-243">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
 [!code-csharp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
 [!code-vb[Conceptual.Interop.Marshaling#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]  
  
### <a name="calling-functions"></a><span data-ttu-id="ac1bd-244">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="ac1bd-244">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
 [!code-csharp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
 [!code-vb[Conceptual.Interop.Marshaling#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="ac1bd-245">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac1bd-245">See also</span></span>

- [<span data-ttu-id="ac1bd-246">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="ac1bd-246">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
- [<span data-ttu-id="ac1bd-247">Zařazování řetězců</span><span class="sxs-lookup"><span data-stu-id="ac1bd-247">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="ac1bd-248">Zařazování různých typů polí</span><span class="sxs-lookup"><span data-stu-id="ac1bd-248">Marshaling Different Types of Arrays</span></span>](marshaling-different-types-of-arrays.md)
