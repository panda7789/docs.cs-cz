---
title: Zařazování různých typů polí
description: Zařazování různých typů polí, jako jsou celá čísla podle hodnoty nebo odkazu, dvojrozměrné celočíselné hodnoty podle hodnot, řetězců podle hodnot a struktur s celými čísly nebo řetězci.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
ms.openlocfilehash: f1473c7917189f0b36c96b2adcf20005c5fd6b48
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621493"
---
# <a name="marshaling-different-types-of-arrays"></a><span data-ttu-id="c4947-103">Zařazování různých typů polí</span><span class="sxs-lookup"><span data-stu-id="c4947-103">Marshaling Different Types of Arrays</span></span>
<span data-ttu-id="c4947-104">Pole je typ odkazu ve spravovaném kódu, který obsahuje jeden nebo více prvků stejného typu.</span><span class="sxs-lookup"><span data-stu-id="c4947-104">An array is a reference type in managed code that contains one or more elements of the same type.</span></span> <span data-ttu-id="c4947-105">I když pole jsou odkazové typy, jsou předány jako parametry do nespravovaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="c4947-105">Although arrays are reference types, they are passed as In parameters to unmanaged functions.</span></span> <span data-ttu-id="c4947-106">Toto chování je nekonzistentní, protože spravovaná pole jsou předávána spravovaným objektům, což jsou vstupně-výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="c4947-106">This behavior is inconsistent with way managed arrays are passed to managed objects, which is as In/Out parameters.</span></span> <span data-ttu-id="c4947-107">Další podrobnosti najdete v tématu [kopírování a připnutí](copying-and-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="c4947-107">For additional details, see [Copying and Pinning](copying-and-pinning.md).</span></span>  
  
 <span data-ttu-id="c4947-108">Následující tabulka uvádí možnosti zařazování pro pole a popisuje jejich použití.</span><span class="sxs-lookup"><span data-stu-id="c4947-108">The following table lists marshaling options for arrays and describes their usage.</span></span>  
  
|<span data-ttu-id="c4947-109">Pole</span><span class="sxs-lookup"><span data-stu-id="c4947-109">Array</span></span>|<span data-ttu-id="c4947-110">Popis</span><span class="sxs-lookup"><span data-stu-id="c4947-110">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c4947-111">Celých čísel podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c4947-111">Of integers by value.</span></span>|<span data-ttu-id="c4947-112">Předá pole celých čísel jako parametr v parametru.</span><span class="sxs-lookup"><span data-stu-id="c4947-112">Passes an array of integers as an In parameter.</span></span>|  
|<span data-ttu-id="c4947-113">Celých čísel podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="c4947-113">Of integers by reference.</span></span>|<span data-ttu-id="c4947-114">Předá pole celých čísel jako vstupně-výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="c4947-114">Passes an array of integers as an In/Out parameter.</span></span>|  
|<span data-ttu-id="c4947-115">Celých čísel podle hodnoty (dvourozměrné).</span><span class="sxs-lookup"><span data-stu-id="c4947-115">Of integers by value (two-dimensional).</span></span>|<span data-ttu-id="c4947-116">Předává matici celých čísel jako parametr v parametru.</span><span class="sxs-lookup"><span data-stu-id="c4947-116">Passes a matrix of integers as an In parameter.</span></span>|  
|<span data-ttu-id="c4947-117">Řetězců podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c4947-117">Of strings by value.</span></span>|<span data-ttu-id="c4947-118">Předá pole řetězců jako parametr v parametru.</span><span class="sxs-lookup"><span data-stu-id="c4947-118">Passes an array of strings as an In parameter.</span></span>|  
|<span data-ttu-id="c4947-119">Struktury s celými čísly.</span><span class="sxs-lookup"><span data-stu-id="c4947-119">Of structures with integers.</span></span>|<span data-ttu-id="c4947-120">Předá pole struktury, které obsahují celá čísla jako parametr in.</span><span class="sxs-lookup"><span data-stu-id="c4947-120">Passes an array of structures that contain integers as an In parameter.</span></span>|  
|<span data-ttu-id="c4947-121">Struktury s řetězci.</span><span class="sxs-lookup"><span data-stu-id="c4947-121">Of structures with strings.</span></span>|<span data-ttu-id="c4947-122">Předá pole struktur, které obsahují pouze řetězce jako vstupně-výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="c4947-122">Passes an array of structures that contain only strings as an In/Out parameter.</span></span> <span data-ttu-id="c4947-123">Členy pole lze změnit.</span><span class="sxs-lookup"><span data-stu-id="c4947-123">Members of the array can be changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c4947-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="c4947-124">Example</span></span>  
 <span data-ttu-id="c4947-125">Tato ukázka předvádí, jak předat následující typy polí:</span><span class="sxs-lookup"><span data-stu-id="c4947-125">This sample demonstrates how to pass the following types of arrays:</span></span>  
  
- <span data-ttu-id="c4947-126">Pole celých čísel podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c4947-126">Array of integers by value.</span></span>  
  
- <span data-ttu-id="c4947-127">Pole celých čísel podle odkazu, které lze změnit.</span><span class="sxs-lookup"><span data-stu-id="c4947-127">Array of integers by reference, which can be resized.</span></span>  
  
- <span data-ttu-id="c4947-128">Multidimenzionální pole (matice) celých čísel podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c4947-128">Multidimensional array (matrix) of integers by value.</span></span>  
  
- <span data-ttu-id="c4947-129">Pole řetězců podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c4947-129">Array of strings by value.</span></span>  
  
- <span data-ttu-id="c4947-130">Pole struktur s celými čísly</span><span class="sxs-lookup"><span data-stu-id="c4947-130">Array of structures with integers.</span></span>  
  
- <span data-ttu-id="c4947-131">Pole struktur s řetězci.</span><span class="sxs-lookup"><span data-stu-id="c4947-131">Array of structures with strings.</span></span>  
  
 <span data-ttu-id="c4947-132">Pokud není pole explicitně zařazeno pomocí odkazu, výchozí chování zařadí pole jako parametr v parametru.</span><span class="sxs-lookup"><span data-stu-id="c4947-132">Unless an array is explicitly marshaled by reference, the default behavior marshals the array as an In parameter.</span></span> <span data-ttu-id="c4947-133">Toto chování můžete změnit použitím <xref:System.Runtime.InteropServices.InAttribute> <xref:System.Runtime.InteropServices.OutAttribute> atributů a explicitně.</span><span class="sxs-lookup"><span data-stu-id="c4947-133">You can change this behavior by applying the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes explicitly.</span></span>  
  
 <span data-ttu-id="c4947-134">Ukázka pole používá následující nespravované funkce, které jsou zobrazeny s původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="c4947-134">The Arrays sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
- <span data-ttu-id="c4947-135">**TestArrayOfInts** exportovaný z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="c4947-135">**TestArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
- <span data-ttu-id="c4947-136">**TestRefArrayOfInts** exportovaný z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="c4947-136">**TestRefArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
- <span data-ttu-id="c4947-137">**TestMatrixOfInts** exportovaný z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="c4947-137">**TestMatrixOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
- <span data-ttu-id="c4947-138">**TestArrayOfStrings** exportovaný z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="c4947-138">**TestArrayOfStrings** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
- <span data-ttu-id="c4947-139">**TestArrayOfStructs** exportovaný z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="c4947-139">**TestArrayOfStructs** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
- <span data-ttu-id="c4947-140">**TestArrayOfStructs2** exportovaný z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="c4947-140">**TestArrayOfStructs2** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 <span data-ttu-id="c4947-141">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) je vlastní nespravovaná knihovna, která obsahuje implementace pro dříve uvedené funkce a dvě proměnné struktury, **MYPOINT** a **MYPERSON**.</span><span class="sxs-lookup"><span data-stu-id="c4947-141">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and two structure variables, **MYPOINT** and **MYPERSON**.</span></span> <span data-ttu-id="c4947-142">Struktury obsahují následující prvky:</span><span class="sxs-lookup"><span data-stu-id="c4947-142">The structures contain the following elements:</span></span>  
  
```cpp
typedef struct _MYPOINT  
{  
   int x;
   int y;
} MYPOINT;  
  
typedef struct _MYPERSON  
{  
   char* first;
   char* last;
} MYPERSON;  
```  
  
 <span data-ttu-id="c4947-143">V této ukázce `MyPoint` `MyPerson` struktury a obsahují vložené typy.</span><span class="sxs-lookup"><span data-stu-id="c4947-143">In this sample, the `MyPoint` and `MyPerson` structures contain embedded types.</span></span> <span data-ttu-id="c4947-144"><xref:System.Runtime.InteropServices.StructLayoutAttribute>Atribut je nastaven tak, aby bylo zajištěno, že jsou členy uspořádány v paměti sekvenčně v pořadí, ve kterém jsou zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="c4947-144">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="c4947-145">`NativeMethods`Třída obsahuje sadu metod, které jsou volány `App` třídou.</span><span class="sxs-lookup"><span data-stu-id="c4947-145">The `NativeMethods` class contains a set of methods called by the `App` class.</span></span> <span data-ttu-id="c4947-146">Konkrétní podrobnosti o předávání polí naleznete v komentářích v následující ukázce.</span><span class="sxs-lookup"><span data-stu-id="c4947-146">For specific details about passing arrays, see the comments in the following sample.</span></span> <span data-ttu-id="c4947-147">Pole, které je odkazový typ, je ve výchozím nastavení předáno jako parametr in.</span><span class="sxs-lookup"><span data-stu-id="c4947-147">An array, which is a reference type, is passed as an In parameter by default.</span></span> <span data-ttu-id="c4947-148">Aby volající mohl přijímat výsledky, **atribut** InAttribute a **subattribute** musí být explicitně aplikovány na argument obsahující pole.</span><span class="sxs-lookup"><span data-stu-id="c4947-148">For the caller to receive the results, **InAttribute** and **OutAttribute** must be applied explicitly to the argument containing the array.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="c4947-149">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="c4947-149">Declaring Prototypes</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a><span data-ttu-id="c4947-150">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="c4947-150">Calling Functions</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="c4947-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4947-151">See also</span></span>

- [<span data-ttu-id="c4947-152">Datové typy vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="c4947-152">Platform invoke data types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="c4947-153">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="c4947-153">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
