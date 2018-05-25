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
ms.openlocfilehash: be4c15f1093f359eeb9e742464b9d9e1dd5c756e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="marshaling-classes-structures-and-unions"></a><span data-ttu-id="4b15a-102">Zařazování tříd, struktur a sjednocení</span><span class="sxs-lookup"><span data-stu-id="4b15a-102">Marshaling Classes, Structures, and Unions</span></span>
<span data-ttu-id="4b15a-103">Třídy a struktury jsou podobné v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4b15a-103">Classes and structures are similar in the .NET Framework.</span></span> <span data-ttu-id="4b15a-104">Mají obě můžete polí, vlastnosti a události.</span><span class="sxs-lookup"><span data-stu-id="4b15a-104">Both can have fields, properties, and events.</span></span> <span data-ttu-id="4b15a-105">Může mít také statické a nestatické metody.</span><span class="sxs-lookup"><span data-stu-id="4b15a-105">They can also have static and nonstatic methods.</span></span> <span data-ttu-id="4b15a-106">Jeden pozoruhodný rozdíl je, že jsou typy hodnot struktury a třídy jsou odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="4b15a-106">One notable difference is that structures are value types and classes are reference types.</span></span>  
  
 <span data-ttu-id="4b15a-107">Následující tabulka uvádí možnosti zařazování tříd, struktur a sjednocení; Popisuje jejich použití; odkaz na odpovídající platformy vyvolání ukázka.</span><span class="sxs-lookup"><span data-stu-id="4b15a-107">The following table lists marshaling options for classes, structures, and unions; describes their usage; and provides a link to the corresponding platform invoke sample.</span></span>  
  
|<span data-ttu-id="4b15a-108">Typ</span><span class="sxs-lookup"><span data-stu-id="4b15a-108">Type</span></span>|<span data-ttu-id="4b15a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="4b15a-109">Description</span></span>|<span data-ttu-id="4b15a-110">Ukázka</span><span class="sxs-lookup"><span data-stu-id="4b15a-110">Sample</span></span>|  
|----------|-----------------|------------|  
|<span data-ttu-id="4b15a-111">Třída hodnotou.</span><span class="sxs-lookup"><span data-stu-id="4b15a-111">Class by value.</span></span>|<span data-ttu-id="4b15a-112">Jako parametr v nebo na více systémů, jako spravované případě předá třídu se členy celé číslo.</span><span class="sxs-lookup"><span data-stu-id="4b15a-112">Passes a class with integer members as an In/Out parameter, like the managed case.</span></span>|<span data-ttu-id="4b15a-113">SysTime – ukázka</span><span class="sxs-lookup"><span data-stu-id="4b15a-113">SysTime sample</span></span>|  
|<span data-ttu-id="4b15a-114">Struktura hodnotou.</span><span class="sxs-lookup"><span data-stu-id="4b15a-114">Structure by value.</span></span>|<span data-ttu-id="4b15a-115">Předá struktury jako parametry.</span><span class="sxs-lookup"><span data-stu-id="4b15a-115">Passes structures as In parameters.</span></span>|<span data-ttu-id="4b15a-116">Ukázka struktury</span><span class="sxs-lookup"><span data-stu-id="4b15a-116">Structures sample</span></span>|  
|<span data-ttu-id="4b15a-117">Struktura odkazem.</span><span class="sxs-lookup"><span data-stu-id="4b15a-117">Structure by reference.</span></span>|<span data-ttu-id="4b15a-118">Předá struktury jako vstupně -výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="4b15a-118">Passes structures as In/Out parameters.</span></span>|<span data-ttu-id="4b15a-119">OSInfo – ukázka</span><span class="sxs-lookup"><span data-stu-id="4b15a-119">OSInfo sample</span></span>|  
|<span data-ttu-id="4b15a-120">Struktura s vnořené struktury (průmětu).</span><span class="sxs-lookup"><span data-stu-id="4b15a-120">Structure with nested structures (flattened).</span></span>|<span data-ttu-id="4b15a-121">Předá třídu, která reprezentuje strukturu s vnořené struktury v nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="4b15a-121">Passes a class that represents a structure with nested structures in the unmanaged function.</span></span> <span data-ttu-id="4b15a-122">Struktura je průmětu do jeden velký struktury v spravované prototypu.</span><span class="sxs-lookup"><span data-stu-id="4b15a-122">The structure is flattened to one big structure in the managed prototype.</span></span>|<span data-ttu-id="4b15a-123">FindFile – ukázka</span><span class="sxs-lookup"><span data-stu-id="4b15a-123">FindFile sample</span></span>|  
|<span data-ttu-id="4b15a-124">Struktura pomocí ukazatele do jiné struktury.</span><span class="sxs-lookup"><span data-stu-id="4b15a-124">Structure with a pointer to another structure.</span></span>|<span data-ttu-id="4b15a-125">Předá strukturu, která obsahuje ukazatel na druhý struktura jako člena.</span><span class="sxs-lookup"><span data-stu-id="4b15a-125">Passes a structure that contains a pointer to a second structure as a member.</span></span>|<span data-ttu-id="4b15a-126">Ukázka struktur</span><span class="sxs-lookup"><span data-stu-id="4b15a-126">Structures Sample</span></span>|  
|<span data-ttu-id="4b15a-127">Pole struktur s celými čísly hodnotou.</span><span class="sxs-lookup"><span data-stu-id="4b15a-127">Array of structures with integers by value.</span></span>|<span data-ttu-id="4b15a-128">Předá pole struktury, které obsahují jenom celá čísla jako parametr v nebo na více systémů.</span><span class="sxs-lookup"><span data-stu-id="4b15a-128">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="4b15a-129">Členy pole lze změnit.</span><span class="sxs-lookup"><span data-stu-id="4b15a-129">Members of the array can be changed.</span></span>|<span data-ttu-id="4b15a-130">Ukázka polí</span><span class="sxs-lookup"><span data-stu-id="4b15a-130">Arrays Sample</span></span>|  
|<span data-ttu-id="4b15a-131">Pole struktur s celá čísla a řetězce odkazem.</span><span class="sxs-lookup"><span data-stu-id="4b15a-131">Array of structures with integers and strings by reference.</span></span>|<span data-ttu-id="4b15a-132">Předá pole struktury, které obsahují celá čísla a řetězce jako parametr typu Out.</span><span class="sxs-lookup"><span data-stu-id="4b15a-132">Passes an array of structures that contain integers and strings as an Out parameter.</span></span> <span data-ttu-id="4b15a-133">Volaná funkce přidělí paměť pro pole.</span><span class="sxs-lookup"><span data-stu-id="4b15a-133">The called function allocates memory for the array.</span></span>|<span data-ttu-id="4b15a-134">OutArrayOfStructs – ukázka</span><span class="sxs-lookup"><span data-stu-id="4b15a-134">OutArrayOfStructs Sample</span></span>|  
|<span data-ttu-id="4b15a-135">Sjednocení s typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="4b15a-135">Unions with value types.</span></span>|<span data-ttu-id="4b15a-136">Předá sjednocení s typy hodnot (celé číslo a dvojitou).</span><span class="sxs-lookup"><span data-stu-id="4b15a-136">Passes unions with value types (integer and double).</span></span>|<span data-ttu-id="4b15a-137">sjednocení – ukázka</span><span class="sxs-lookup"><span data-stu-id="4b15a-137">Unions sample</span></span>|  
|<span data-ttu-id="4b15a-138">Sjednocení s smíšený typy.</span><span class="sxs-lookup"><span data-stu-id="4b15a-138">Unions with mixed types.</span></span>|<span data-ttu-id="4b15a-139">Předá sjednocení s smíšený typy (celé číslo a řetězec).</span><span class="sxs-lookup"><span data-stu-id="4b15a-139">Passes unions with mixed types (integer and string).</span></span>|<span data-ttu-id="4b15a-140">sjednocení – ukázka</span><span class="sxs-lookup"><span data-stu-id="4b15a-140">Unions sample</span></span>|  
|<span data-ttu-id="4b15a-141">Hodnoty Null ve struktuře.</span><span class="sxs-lookup"><span data-stu-id="4b15a-141">Null values in structure.</span></span>|<span data-ttu-id="4b15a-142">Předá odkaz s hodnotou null (**nic** v jazyce Visual Basic) namísto odkaz na typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4b15a-142">Passes a null reference (**Nothing** in Visual Basic) instead of a reference to a value type.</span></span>|<span data-ttu-id="4b15a-143">HandleRef – ukázka</span><span class="sxs-lookup"><span data-stu-id="4b15a-143">HandleRef sample</span></span>|  
  
## <a name="structures-sample"></a><span data-ttu-id="4b15a-144">Ukázka struktury</span><span class="sxs-lookup"><span data-stu-id="4b15a-144">Structures sample</span></span>  
 <span data-ttu-id="4b15a-145">Tento příklad ukazuje, jak předat strukturu, která odkazuje na druhý struktura, předejte strukturu s vložené struktury a předat struktura s vloženého pole.</span><span class="sxs-lookup"><span data-stu-id="4b15a-145">This sample demonstrates how to pass a structure that points to a second structure, pass a structure with an embedded structure, and pass a structure with an embedded array.</span></span>  
  
 <span data-ttu-id="4b15a-146">Ukázka struktury používá následující nespravované funkce s jejich původní deklarace funkce:</span><span class="sxs-lookup"><span data-stu-id="4b15a-146">The Structs sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="4b15a-147">**TestStructInStruct** exportovaný z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="4b15a-147">**TestStructInStruct** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestStructInStruct(MYPERSON2* pPerson2);  
    ```  
  
-   <span data-ttu-id="4b15a-148">**TestStructInStruct3** exportovaný z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="4b15a-148">**TestStructInStruct3** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestStructInStruct3(MYPERSON3 person3);  
    ```  
  
-   <span data-ttu-id="4b15a-149">**TestArrayInStruct** exportovaný z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="4b15a-149">**TestArrayInStruct** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestArrayInStruct( MYARRAYSTRUCT* pStruct );  
    ```  
  
 <span data-ttu-id="4b15a-150">[PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) vlastní nespravované knihovnu, která obsahuje implementace pro výše uvedených funkcí a čtyři struktury: **MYPERSON**, **MYPERSON2**,  **MYPERSON3**, a **MYARRAYSTRUCT**.</span><span class="sxs-lookup"><span data-stu-id="4b15a-150">[PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) is a custom unmanaged library that contains implementations for the previously listed functions and four structures: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, and **MYARRAYSTRUCT**.</span></span> <span data-ttu-id="4b15a-151">Tyto struktury obsahovat tyto prvky:</span><span class="sxs-lookup"><span data-stu-id="4b15a-151">These structures contain the following elements:</span></span>  
  
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
  
 <span data-ttu-id="4b15a-152">Spravovaný `MyPerson`, `MyPerson2`, `MyPerson3`, a `MyArrayStruct` struktury mít následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="4b15a-152">The managed `MyPerson`, `MyPerson2`, `MyPerson3`, and `MyArrayStruct` structures have the following characteristic:</span></span>  
  
-   <span data-ttu-id="4b15a-153">`MyPerson` obsahuje pouze členové řetězec.</span><span class="sxs-lookup"><span data-stu-id="4b15a-153">`MyPerson` contains only string members.</span></span> <span data-ttu-id="4b15a-154">[CharSet](specifying-a-character-set.md) pole nastaví řetězce formátu ANSI při nespravované funkci byl předán.</span><span class="sxs-lookup"><span data-stu-id="4b15a-154">The [CharSet](specifying-a-character-set.md) field sets the strings to ANSI format when passed to the unmanaged function.</span></span>  
  
-   <span data-ttu-id="4b15a-155">`MyPerson2` obsahuje **IntPtr** k `MyPerson` struktura.</span><span class="sxs-lookup"><span data-stu-id="4b15a-155">`MyPerson2` contains an **IntPtr** to the `MyPerson` structure.</span></span> <span data-ttu-id="4b15a-156">**IntPtr** typ nahradí původní ukazatel na strukturu nespravované, protože aplikace rozhraní .NET Framework ukazatele nepoužívejte, pokud kód je označen **unsafe**.</span><span class="sxs-lookup"><span data-stu-id="4b15a-156">The **IntPtr** type replaces the original pointer to the unmanaged structure because .NET Framework applications do not use pointers unless the code is marked **unsafe**.</span></span>  
  
-   <span data-ttu-id="4b15a-157">`MyPerson3` obsahuje `MyPerson` jako vložené struktury.</span><span class="sxs-lookup"><span data-stu-id="4b15a-157">`MyPerson3` contains `MyPerson` as an embedded structure.</span></span> <span data-ttu-id="4b15a-158">Struktura vložených v rámci jiné struktury můžete vyrovnány tím, že umístíte elementy vložené struktury přímo do hlavní struktury nebo je možné ho nechat jako vložené struktury, jak se provádí v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="4b15a-158">A structure embedded within another structure can be flattened by placing the elements of the embedded structure directly into the main structure, or it can be left as an embedded structure, as is done in this sample.</span></span>  
  
-   <span data-ttu-id="4b15a-159">`MyArrayStruct` obsahuje pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="4b15a-159">`MyArrayStruct` contains an array of integers.</span></span> <span data-ttu-id="4b15a-160"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nastaví <xref:System.Runtime.InteropServices.UnmanagedType> hodnotu výčtu **ByValArray**, který slouží k označení počet prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="4b15a-160">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration value to **ByValArray**, which is used to indicate the number of elements in the array.</span></span>  
  
 <span data-ttu-id="4b15a-161">Pro všechny struktury v této ukázce <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut se používá k zajištění, že členové jsou uspořádány v paměti postupně, v pořadí, ve kterém jsou zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="4b15a-161">For all structures in this sample, the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is applied to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="4b15a-162">`LibWrap` Třída obsahuje spravovaných prototypy pro `TestStructInStruct`, `TestStructInStruct3`, a `TestArrayInStruct` volá metody `App` třídy.</span><span class="sxs-lookup"><span data-stu-id="4b15a-162">The `LibWrap` class contains managed prototypes for the `TestStructInStruct`, `TestStructInStruct3`, and `TestArrayInStruct` methods called by the `App` class.</span></span> <span data-ttu-id="4b15a-163">Každý prototypu deklaruje jeden parametr, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="4b15a-163">Each prototype declares a single parameter, as follows:</span></span>  
  
-   <span data-ttu-id="4b15a-164">`TestStructInStruct` deklaruje odkaz na typ `MyPerson2` jako jeho parametr.</span><span class="sxs-lookup"><span data-stu-id="4b15a-164">`TestStructInStruct` declares a reference to type `MyPerson2` as its parameter.</span></span>  
  
-   <span data-ttu-id="4b15a-165">`TestStructInStruct3` deklaruje typ `MyPerson3` jako jeho parametr a předá parametr hodnotou.</span><span class="sxs-lookup"><span data-stu-id="4b15a-165">`TestStructInStruct3` declares type `MyPerson3` as its parameter and passes the parameter by value.</span></span>  
  
-   <span data-ttu-id="4b15a-166">`TestArrayInStruct` deklaruje odkaz na typ `MyArrayStruct` jako jeho parametr.</span><span class="sxs-lookup"><span data-stu-id="4b15a-166">`TestArrayInStruct` declares a reference to type `MyArrayStruct` as its parameter.</span></span>  
  
 <span data-ttu-id="4b15a-167">Struktury jako argumenty pro metody jsou předanou hodnotu, pokud parametr obsahuje **ref** (**ByRef** v jazyce Visual Basic) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="4b15a-167">Structures as arguments to methods are passed by value unless the parameter contains the **ref** (**ByRef** in Visual Basic) keyword.</span></span> <span data-ttu-id="4b15a-168">Například `TestStructInStruct` metoda předá odkaz (hodnota adresy) na objekt typu `MyPerson2` na nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="4b15a-168">For example, the `TestStructInStruct` method passes a reference (the value of an address) to an object of type `MyPerson2` to unmanaged code.</span></span> <span data-ttu-id="4b15a-169">K manipulaci s strukturu, `MyPerson2` odkazuje na ukázku vytvoří zadaná velikost vyrovnávací paměti a vrátí jeho adresy tím, že zkombinujete <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> a <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="4b15a-169">To manipulate the structure that `MyPerson2` points to, the sample creates a buffer of a specified size and returns its address by combining the <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="4b15a-170">V dalším kroku ukázku zkopíruje obsah struktury spravovaných do nespravovaných vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4b15a-170">Next, the sample copies the content of the managed structure to the unmanaged buffer.</span></span> <span data-ttu-id="4b15a-171">Nakonec ukázce se používá <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> metoda zařazování dat z vyrovnávací paměti nespravovaného do spravovaného objektu a <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> metoda uvolnit nespravované bloku paměti.</span><span class="sxs-lookup"><span data-stu-id="4b15a-171">Finally, the sample uses the <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> method to marshal data from the unmanaged buffer to a managed object and the <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> method to free the unmanaged block of memory.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="4b15a-172">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="4b15a-172">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
 [!code-csharp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
 [!code-vb[Conceptual.Interop.Marshaling#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]  
  
### <a name="calling-functions"></a><span data-ttu-id="4b15a-173">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="4b15a-173">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
 [!code-csharp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
 [!code-vb[Conceptual.Interop.Marshaling#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]  
  
## <a name="findfile-sample"></a><span data-ttu-id="4b15a-174">FindFile – ukázka</span><span class="sxs-lookup"><span data-stu-id="4b15a-174">FindFile sample</span></span>  
 <span data-ttu-id="4b15a-175">Tento příklad znázorňuje, jak předat strukturu, která obsahuje strukturu, druhý, vložené do nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="4b15a-175">This sample demonstrates how to pass a structure that contains a second, embedded structure to an unmanaged function.</span></span> <span data-ttu-id="4b15a-176">Také ukazuje, jak používat <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut pevnou délkou pole v rámci strukturu deklarovat.</span><span class="sxs-lookup"><span data-stu-id="4b15a-176">It also demonstrates how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to declare a fixed-length array within the structure.</span></span> <span data-ttu-id="4b15a-177">V této ukázce jsou elementy vložené struktury přidat pro nadřazenou strukturu.</span><span class="sxs-lookup"><span data-stu-id="4b15a-177">In this sample, the embedded structure elements are added to the parent structure.</span></span> <span data-ttu-id="4b15a-178">Ukázka vložené struktury, která se nesloučí, najdete v části [ukázka struktury](https://msdn.microsoft.com/library/96a62265-dcf9-4608-bc0a-1f762ab9f48e(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4b15a-178">For a sample of an embedded structure that is not flattened, see [Structures Sample](https://msdn.microsoft.com/library/96a62265-dcf9-4608-bc0a-1f762ab9f48e(v=vs.100)).</span></span>  
  
 <span data-ttu-id="4b15a-179">Ukázka FindFile používá následující nespravované funkce, zobrazí se jeho původní funkce deklaraci:</span><span class="sxs-lookup"><span data-stu-id="4b15a-179">The FindFile sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="4b15a-180">**FindFirstFile** exportovaný z Kernel32.dll.</span><span class="sxs-lookup"><span data-stu-id="4b15a-180">**FindFirstFile** exported from Kernel32.dll.</span></span>  
  
    ```  
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);  
    ```  
  
 <span data-ttu-id="4b15a-181">Původní struktura předaný funkci obsahuje následující prvky:</span><span class="sxs-lookup"><span data-stu-id="4b15a-181">The original structure passed to the function contains the following elements:</span></span>  
  
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
  
 <span data-ttu-id="4b15a-182">V této ukázce `FindData` třída obsahuje odpovídající datových členů pro každý prvek původní struktury a vložené struktury.</span><span class="sxs-lookup"><span data-stu-id="4b15a-182">In this sample, the `FindData` class contains a corresponding data member for each element of the original structure and the embedded structure.</span></span> <span data-ttu-id="4b15a-183">Místo dvou původní znak vyrovnávací paměti nahradí třída řetězce.</span><span class="sxs-lookup"><span data-stu-id="4b15a-183">In place of two original character buffers, the class substitutes strings.</span></span> <span data-ttu-id="4b15a-184">**MarshalAsAttribute** nastaví <xref:System.Runtime.InteropServices.UnmanagedType> výčet **ByValTStr**, který se používá k identifikaci vložený, maticových pevnou délkou znak, který se zobrazí v rámci nespravované struktury.</span><span class="sxs-lookup"><span data-stu-id="4b15a-184">**MarshalAsAttribute** sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged structures.</span></span>  
  
 <span data-ttu-id="4b15a-185">`LibWrap` Třída obsahuje spravované prototyp `FindFirstFile` metodu, která předá `FindData` třída jako parametr.</span><span class="sxs-lookup"><span data-stu-id="4b15a-185">The `LibWrap` class contains a managed prototype of the `FindFirstFile` method, which passes the `FindData` class as a parameter.</span></span> <span data-ttu-id="4b15a-186">Parametr musí být deklarován s <xref:System.Runtime.InteropServices.InAttribute> a <xref:System.Runtime.InteropServices.OutAttribute> atributů, protože jsou třídy, které jsou odkazové typy, předat jako parametry ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="4b15a-186">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="4b15a-187">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="4b15a-187">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
 [!code-csharp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
 [!code-vb[Conceptual.Interop.Marshaling#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]  
  
### <a name="calling-functions"></a><span data-ttu-id="4b15a-188">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="4b15a-188">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
 [!code-csharp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]  
  
## <a name="unions-sample"></a><span data-ttu-id="4b15a-189">sjednocení – ukázka</span><span class="sxs-lookup"><span data-stu-id="4b15a-189">Unions sample</span></span>  
 <span data-ttu-id="4b15a-190">Tento příklad znázorňuje, jak předat struktury obsahující pouze typy hodnot a struktury obsahující řetězec a typ hodnoty jako parametry do nespravované funkce byl očekáván sjednocení.</span><span class="sxs-lookup"><span data-stu-id="4b15a-190">This sample demonstrates how to pass structures containing only value types, and structures containing a value type and a string as parameters to an unmanaged function expecting a union.</span></span> <span data-ttu-id="4b15a-191">Sjednocení představuje umístění paměti, které může být sdílen dvěma nebo více proměnných.</span><span class="sxs-lookup"><span data-stu-id="4b15a-191">A union represents a memory location that can be shared by two or more variables.</span></span>  
  
 <span data-ttu-id="4b15a-192">Ukázka sjednocení funkce následující nespravované, zobrazí se jeho původní funkce deklaraci:</span><span class="sxs-lookup"><span data-stu-id="4b15a-192">The Unions sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="4b15a-193">**TestUnion** exportovaný z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="4b15a-193">**TestUnion** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestUnion(MYUNION u, int type);  
    ```  
  
 <span data-ttu-id="4b15a-194">[PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) vlastní nespravované knihovnu, která obsahuje implementaci pro funkci výše uvedených a dvě sjednocení **MYUNION** a **MYUNION2**.</span><span class="sxs-lookup"><span data-stu-id="4b15a-194">[PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) is a custom unmanaged library that contains an implementation for the previously listed function and two unions, **MYUNION** and **MYUNION2**.</span></span> <span data-ttu-id="4b15a-195">Sjednocení obsahovat tyto prvky:</span><span class="sxs-lookup"><span data-stu-id="4b15a-195">The unions contain the following elements:</span></span>  
  
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
  
 <span data-ttu-id="4b15a-196">Ve spravovaném kódu sjednocení definovány jako struktury.</span><span class="sxs-lookup"><span data-stu-id="4b15a-196">In managed code, unions are defined as structures.</span></span> <span data-ttu-id="4b15a-197">`MyUnion` Struktura obsahuje dva typy hodnot jako členy: celé číslo a datový typ double.</span><span class="sxs-lookup"><span data-stu-id="4b15a-197">The `MyUnion` structure contains two value types as its members: an integer and a double.</span></span> <span data-ttu-id="4b15a-198"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Nastavený atribut pro řízení přesné pozice každého datového člena.</span><span class="sxs-lookup"><span data-stu-id="4b15a-198">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to control the precise position of each data member.</span></span> <span data-ttu-id="4b15a-199"><xref:System.Runtime.InteropServices.FieldOffsetAttribute> Atribut poskytuje fyzické umístění polí v rámci nespravované reprezentace spojení.</span><span class="sxs-lookup"><span data-stu-id="4b15a-199">The <xref:System.Runtime.InteropServices.FieldOffsetAttribute> attribute provides the physical position of fields within the unmanaged representation of a union.</span></span> <span data-ttu-id="4b15a-200">Všimněte si, že oba členové mají stejné hodnoty posunutí tak členy můžete definovat stejnou část paměti.</span><span class="sxs-lookup"><span data-stu-id="4b15a-200">Notice that both members have the same offset values, so the members can define the same piece of memory.</span></span>  
  
 <span data-ttu-id="4b15a-201">`MyUnion2_1` a `MyUnion2_2` obsahovat řetězec a hodnota typu (integer) v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="4b15a-201">`MyUnion2_1` and `MyUnion2_2` contain a value type (integer) and a string, respectively.</span></span> <span data-ttu-id="4b15a-202">Ve spravovaném kódu nejsou povolené typy hodnot a typy odkazu překrytí.</span><span class="sxs-lookup"><span data-stu-id="4b15a-202">In managed code, value types and reference types are not permitted to overlap.</span></span> <span data-ttu-id="4b15a-203">Tato ukázka používá metodu přetížení povolit volající pro oba typy při volání nespravovaného stejné funkce.</span><span class="sxs-lookup"><span data-stu-id="4b15a-203">This sample uses method overloading to enable the caller to use both types when calling the same unmanaged function.</span></span> <span data-ttu-id="4b15a-204">Rozložení `MyUnion2_1` explicitní a má hodnotu přesné posunutí.</span><span class="sxs-lookup"><span data-stu-id="4b15a-204">The layout of `MyUnion2_1` is explicit and has a precise offset value.</span></span> <span data-ttu-id="4b15a-205">Naproti tomu `MyUnion2_2` má sekvenční rozložení, protože explicitní rozložení nejsou povoleny pro odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="4b15a-205">In contrast, `MyUnion2_2` has a sequential layout, because explicit layouts are not permitted with reference types.</span></span> <span data-ttu-id="4b15a-206"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nastaví <xref:System.Runtime.InteropServices.UnmanagedType> výčet **ByValTStr**, který se používá k identifikaci vložený, maticových pevnou délkou znak, který se zobrazí v rámci reprezentace nespravovaná sjednocení.</span><span class="sxs-lookup"><span data-stu-id="4b15a-206">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged representation of the union.</span></span>  
  
 <span data-ttu-id="4b15a-207">`LibWrap` Třída obsahuje prototypy pro `TestUnion` a `TestUnion2` metody.</span><span class="sxs-lookup"><span data-stu-id="4b15a-207">The `LibWrap` class contains the prototypes for the `TestUnion` and `TestUnion2` methods.</span></span> <span data-ttu-id="4b15a-208">`TestUnion2` je přetížena deklarovat `MyUnion2_1` nebo `MyUnion2_2` jako parametry.</span><span class="sxs-lookup"><span data-stu-id="4b15a-208">`TestUnion2` is overloaded to declare `MyUnion2_1` or `MyUnion2_2` as parameters.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="4b15a-209">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="4b15a-209">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
 [!code-csharp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
 [!code-vb[Conceptual.Interop.Marshaling#28](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]  
  
### <a name="calling-functions"></a><span data-ttu-id="4b15a-210">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="4b15a-210">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
 [!code-csharp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
 [!code-vb[Conceptual.Interop.Marshaling#29](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]  
  
## <a name="systime-sample"></a><span data-ttu-id="4b15a-211">SysTime – ukázka</span><span class="sxs-lookup"><span data-stu-id="4b15a-211">SysTime sample</span></span>  
 <span data-ttu-id="4b15a-212">Tento příklad znázorňuje, jak předat ukazatel na třídu k nespravované funkci, která očekává ukazatel na strukturu.</span><span class="sxs-lookup"><span data-stu-id="4b15a-212">This sample demonstrates how to pass a pointer to a class to an unmanaged function that expects a pointer to a structure.</span></span>  
  
 <span data-ttu-id="4b15a-213">Ukázka SysTime používá následující nespravované funkce, zobrazí se jeho původní funkce deklaraci:</span><span class="sxs-lookup"><span data-stu-id="4b15a-213">The SysTime sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="4b15a-214">**GetSystemTime** exportovaný z Kernel32.dll.</span><span class="sxs-lookup"><span data-stu-id="4b15a-214">**GetSystemTime** exported from Kernel32.dll.</span></span>  
  
    ```  
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);  
    ```  
  
 <span data-ttu-id="4b15a-215">Původní struktura předaný funkci obsahuje následující prvky:</span><span class="sxs-lookup"><span data-stu-id="4b15a-215">The original structure passed to the function contains the following elements:</span></span>  
  
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
  
 <span data-ttu-id="4b15a-216">V této ukázce `SystemTime` třída obsahuje prvky původní struktura reprezentován jako členové třídy.</span><span class="sxs-lookup"><span data-stu-id="4b15a-216">In this sample, the `SystemTime` class contains the elements of the original structure represented as class members.</span></span> <span data-ttu-id="4b15a-217"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Je nastavena na hodnotu zabezpečit, aby členové jsou uspořádány v paměti postupně, v pořadí, ve kterém jsou zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="4b15a-217">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="4b15a-218">`LibWrap` Třída obsahuje spravované prototyp `GetSystemTime` metodu, která předá `SystemTime` třída jako ve vstupně -výstupnímu parametru ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="4b15a-218">The `LibWrap` class contains a managed prototype of the `GetSystemTime` method, which passes the `SystemTime` class as an In/Out parameter by default.</span></span> <span data-ttu-id="4b15a-219">Parametr musí být deklarován s <xref:System.Runtime.InteropServices.InAttribute> a <xref:System.Runtime.InteropServices.OutAttribute> atributů, protože jsou třídy, které jsou odkazové typy, předat jako parametry ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="4b15a-219">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span> <span data-ttu-id="4b15a-220">Pro volající získat výsledky tyto [směrovou atributy](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100)) musí být explicitně použity.</span><span class="sxs-lookup"><span data-stu-id="4b15a-220">For the caller to receive the results, these [directional attributes](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100)) must be applied explicitly.</span></span> <span data-ttu-id="4b15a-221">`App` Vytvoří novou instanci třídy `SystemTime` třídy a přistupuje k jeho datová pole.</span><span class="sxs-lookup"><span data-stu-id="4b15a-221">The `App` class creates a new instance of the `SystemTime` class and accesses its data fields.</span></span>  
  
### <a name="code-samples"></a><span data-ttu-id="4b15a-222">Ukázky kódu</span><span class="sxs-lookup"><span data-stu-id="4b15a-222">Code Samples</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
 [!code-csharp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
 [!code-vb[Conceptual.Interop.Marshaling#25](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]  
  
## <a name="outarrayofstructs-sample"></a><span data-ttu-id="4b15a-223">OutArrayOfStructs – ukázka</span><span class="sxs-lookup"><span data-stu-id="4b15a-223">OutArrayOfStructs sample</span></span>  
 <span data-ttu-id="4b15a-224">Tento příklad ukazuje, jak předat pole struktury, které obsahuje celá čísla a řetězce jako výstupní parametry do nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="4b15a-224">This sample shows how to pass an array of structures that contains integers and strings as Out parameters to an unmanaged function.</span></span>  
  
 <span data-ttu-id="4b15a-225">Tento příklad ukazuje způsob volání nativní funkce pomocí <xref:System.Runtime.InteropServices.Marshal> třídy a pomocí nezabezpečený kód.</span><span class="sxs-lookup"><span data-stu-id="4b15a-225">This sample demonstrates how to call a native function by using the <xref:System.Runtime.InteropServices.Marshal> class and by using unsafe code.</span></span>  
  
 <span data-ttu-id="4b15a-226">Tato ukázka používá funkce obálky a vyvolá platformy definovaný v [PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)), také zadaný ve zdrojových souborech.</span><span class="sxs-lookup"><span data-stu-id="4b15a-226">This sample uses a wrapper functions and platform invokes defined in [PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)), also provided in the source files.</span></span> <span data-ttu-id="4b15a-227">Použije `TestOutArrayOfStructs` funkce a `MYSTRSTRUCT2` struktury.</span><span class="sxs-lookup"><span data-stu-id="4b15a-227">It uses the `TestOutArrayOfStructs` function and the `MYSTRSTRUCT2` structure.</span></span> <span data-ttu-id="4b15a-228">Struktura obsahuje následující prvky:</span><span class="sxs-lookup"><span data-stu-id="4b15a-228">The structure contains the following elements:</span></span>  
  
```  
typedef struct _MYSTRSTRUCT2  
{  
   char* buffer;  
   UINT size;   
} MYSTRSTRUCT2;  
```  
  
 <span data-ttu-id="4b15a-229">`MyStruct` Třída obsahuje objekt řetězec znaků ANSI.</span><span class="sxs-lookup"><span data-stu-id="4b15a-229">The `MyStruct` class contains a string object of ANSI characters.</span></span> <span data-ttu-id="4b15a-230"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> Pole určuje formát ANSI.</span><span class="sxs-lookup"><span data-stu-id="4b15a-230">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field specifies ANSI format.</span></span> <span data-ttu-id="4b15a-231">`MyUnsafeStruct`, je strukturou obsahující <xref:System.IntPtr> typu místo řetězec.</span><span class="sxs-lookup"><span data-stu-id="4b15a-231">`MyUnsafeStruct`, is a structure containing an <xref:System.IntPtr> type instead of a string.</span></span>  
  
 <span data-ttu-id="4b15a-232">`LibWrap` Třída obsahuje přetížené `TestOutArrayOfStructs` metoda prototypu.</span><span class="sxs-lookup"><span data-stu-id="4b15a-232">The `LibWrap` class contains the overloaded `TestOutArrayOfStructs` prototype method.</span></span> <span data-ttu-id="4b15a-233">Pokud metoda deklaruje ukazatel jako parametr, třída by měl být označen s `unsafe` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="4b15a-233">If a method declares a pointer as a parameter, the class should be marked with the `unsafe` keyword.</span></span> <span data-ttu-id="4b15a-234">Protože [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] nelze použít nezabezpečený kód, přetížené metody, unsafe modifikátor a `MyUnsafeStruct` struktura nejsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="4b15a-234">Because [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] cannot use unsafe code, the overloaded method, unsafe modifier, and the `MyUnsafeStruct` structure are unnecessary.</span></span>  
  
 <span data-ttu-id="4b15a-235">`App` Třída implementuje `UsingMarshaling` metodu, která provádí všechny úlohy, které jsou nutné předat pole.</span><span class="sxs-lookup"><span data-stu-id="4b15a-235">The `App` class implements the `UsingMarshaling` method, which performs all the tasks necessary to pass the array.</span></span> <span data-ttu-id="4b15a-236">Toto pole je označené jako `out` (`ByRef` v jazyce Visual Basic) předává – klíčové slovo označíte, že data z volaný volajícího.</span><span class="sxs-lookup"><span data-stu-id="4b15a-236">The array is marked with the `out` (`ByRef` in Visual Basic) keyword to indicate that data passes from callee to caller.</span></span> <span data-ttu-id="4b15a-237">Implementace používá následující <xref:System.Runtime.InteropServices.Marshal> metody třídy:</span><span class="sxs-lookup"><span data-stu-id="4b15a-237">The implementation uses the following <xref:System.Runtime.InteropServices.Marshal> class methods:</span></span>  
  
-   <span data-ttu-id="4b15a-238"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> zařazování dat z vyrovnávací paměti nespravovaného do spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="4b15a-238"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> to marshal data from the unmanaged buffer to a managed object.</span></span>  
  
-   <span data-ttu-id="4b15a-239"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> Chcete-li uvolnit paměť vyhrazené pro řetězce ve struktuře.</span><span class="sxs-lookup"><span data-stu-id="4b15a-239"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> to release the memory reserved for strings in the structure.</span></span>  
  
-   <span data-ttu-id="4b15a-240"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> k uvolnění paměti vyhrazené pro pole.</span><span class="sxs-lookup"><span data-stu-id="4b15a-240"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> to release the memory reserved for the array.</span></span>  
  
 <span data-ttu-id="4b15a-241">Jak už jsme zmínili, C# umožňuje nezabezpečený kód a [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] neexistuje.</span><span class="sxs-lookup"><span data-stu-id="4b15a-241">As previously mentioned, C# allows unsafe code and [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] does not.</span></span> <span data-ttu-id="4b15a-242">V jazyce C# ukázce `UsingUnsafePointer` je alternativní metoda pro implementace, která používá ukazatele místo <xref:System.Runtime.InteropServices.Marshal> třída předat zpět obsahující pole `MyUnsafeStruct` struktura.</span><span class="sxs-lookup"><span data-stu-id="4b15a-242">In the C# sample, `UsingUnsafePointer` is an alternative method implementation that uses pointers instead of the <xref:System.Runtime.InteropServices.Marshal> class to pass back the array containing the `MyUnsafeStruct` structure.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="4b15a-243">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="4b15a-243">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
 [!code-csharp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
 [!code-vb[Conceptual.Interop.Marshaling#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]  
  
### <a name="calling-functions"></a><span data-ttu-id="4b15a-244">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="4b15a-244">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
 [!code-csharp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
 [!code-vb[Conceptual.Interop.Marshaling#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="4b15a-245">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b15a-245">See Also</span></span>  
 [<span data-ttu-id="4b15a-246">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="4b15a-246">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)  
 <span data-ttu-id="4b15a-247">[Datové typy vyvolání platformy](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4b15a-247">[Platform Invoke Data Types](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))</span></span>  
 [<span data-ttu-id="4b15a-248">Zařazování řetězců</span><span class="sxs-lookup"><span data-stu-id="4b15a-248">Marshaling Strings</span></span>](marshaling-strings.md)  
 <span data-ttu-id="4b15a-249">[Zařazování pole typů](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4b15a-249">[Marshaling Arrays of Types](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))</span></span>
