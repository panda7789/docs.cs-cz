---
title: Zařazování různých typů polí
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
ms.openlocfilehash: 1490171c4dd423baa3b6c5f5e00cf133c2584cae
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124398"
---
# <a name="marshaling-different-types-of-arrays"></a><span data-ttu-id="d280a-102">Zařazování různých typů polí</span><span class="sxs-lookup"><span data-stu-id="d280a-102">Marshaling Different Types of Arrays</span></span>
<span data-ttu-id="d280a-103">Pole je typ odkazu ve spravovaném kódu, který obsahuje jeden nebo více prvků stejného typu.</span><span class="sxs-lookup"><span data-stu-id="d280a-103">An array is a reference type in managed code that contains one or more elements of the same type.</span></span> <span data-ttu-id="d280a-104">I když pole jsou odkazové typy, jsou předány jako parametry do nespravovaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="d280a-104">Although arrays are reference types, they are passed as In parameters to unmanaged functions.</span></span> <span data-ttu-id="d280a-105">Toto chování je nekonzistentní, protože spravovaná pole jsou předávána spravovaným objektům, což jsou vstupně-výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="d280a-105">This behavior is inconsistent with way managed arrays are passed to managed objects, which is as In/Out parameters.</span></span> <span data-ttu-id="d280a-106">Další podrobnosti najdete v tématu [kopírování a připnutí](copying-and-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="d280a-106">For additional details, see [Copying and Pinning](copying-and-pinning.md).</span></span>  
  
 <span data-ttu-id="d280a-107">Následující tabulka uvádí možnosti zařazování pro pole a popisuje jejich použití.</span><span class="sxs-lookup"><span data-stu-id="d280a-107">The following table lists marshaling options for arrays and describes their usage.</span></span>  
  
|<span data-ttu-id="d280a-108">skupin</span><span class="sxs-lookup"><span data-stu-id="d280a-108">Array</span></span>|<span data-ttu-id="d280a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d280a-109">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d280a-110">Celých čísel podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d280a-110">Of integers by value.</span></span>|<span data-ttu-id="d280a-111">Předá pole celých čísel jako parametr v parametru.</span><span class="sxs-lookup"><span data-stu-id="d280a-111">Passes an array of integers as an In parameter.</span></span>|  
|<span data-ttu-id="d280a-112">Celých čísel podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="d280a-112">Of integers by reference.</span></span>|<span data-ttu-id="d280a-113">Předá pole celých čísel jako vstupně-výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="d280a-113">Passes an array of integers as an In/Out parameter.</span></span>|  
|<span data-ttu-id="d280a-114">Celých čísel podle hodnoty (dvourozměrné).</span><span class="sxs-lookup"><span data-stu-id="d280a-114">Of integers by value (two-dimensional).</span></span>|<span data-ttu-id="d280a-115">Předává matici celých čísel jako parametr v parametru.</span><span class="sxs-lookup"><span data-stu-id="d280a-115">Passes a matrix of integers as an In parameter.</span></span>|  
|<span data-ttu-id="d280a-116">Řetězců podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d280a-116">Of strings by value.</span></span>|<span data-ttu-id="d280a-117">Předá pole řetězců jako parametr v parametru.</span><span class="sxs-lookup"><span data-stu-id="d280a-117">Passes an array of strings as an In parameter.</span></span>|  
|<span data-ttu-id="d280a-118">Struktury s celými čísly.</span><span class="sxs-lookup"><span data-stu-id="d280a-118">Of structures with integers.</span></span>|<span data-ttu-id="d280a-119">Předá pole struktury, které obsahují celá čísla jako parametr in.</span><span class="sxs-lookup"><span data-stu-id="d280a-119">Passes an array of structures that contain integers as an In parameter.</span></span>|  
|<span data-ttu-id="d280a-120">Struktury s řetězci.</span><span class="sxs-lookup"><span data-stu-id="d280a-120">Of structures with strings.</span></span>|<span data-ttu-id="d280a-121">Předá pole struktur, které obsahují pouze řetězce jako vstupně-výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="d280a-121">Passes an array of structures that contain only strings as an In/Out parameter.</span></span> <span data-ttu-id="d280a-122">Členy pole lze změnit.</span><span class="sxs-lookup"><span data-stu-id="d280a-122">Members of the array can be changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d280a-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="d280a-123">Example</span></span>  
 <span data-ttu-id="d280a-124">Tato ukázka předvádí, jak předat následující typy polí:</span><span class="sxs-lookup"><span data-stu-id="d280a-124">This sample demonstrates how to pass the following types of arrays:</span></span>  
  
- <span data-ttu-id="d280a-125">Pole celých čísel podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d280a-125">Array of integers by value.</span></span>  
  
- <span data-ttu-id="d280a-126">Pole celých čísel podle odkazu, které lze změnit.</span><span class="sxs-lookup"><span data-stu-id="d280a-126">Array of integers by reference, which can be resized.</span></span>  
  
- <span data-ttu-id="d280a-127">Multidimenzionální pole (matice) celých čísel podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d280a-127">Multidimensional array (matrix) of integers by value.</span></span>  
  
- <span data-ttu-id="d280a-128">Pole řetězců podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d280a-128">Array of strings by value.</span></span>  
  
- <span data-ttu-id="d280a-129">Pole struktur s celými čísly</span><span class="sxs-lookup"><span data-stu-id="d280a-129">Array of structures with integers.</span></span>  
  
- <span data-ttu-id="d280a-130">Pole struktur s řetězci.</span><span class="sxs-lookup"><span data-stu-id="d280a-130">Array of structures with strings.</span></span>  
  
 <span data-ttu-id="d280a-131">Pokud není pole explicitně zařazeno pomocí odkazu, výchozí chování zařadí pole jako parametr v parametru.</span><span class="sxs-lookup"><span data-stu-id="d280a-131">Unless an array is explicitly marshaled by reference, the default behavior marshals the array as an In parameter.</span></span> <span data-ttu-id="d280a-132">Toto chování můžete změnit použitím atributů <xref:System.Runtime.InteropServices.InAttribute> a <xref:System.Runtime.InteropServices.OutAttribute> explicitně.</span><span class="sxs-lookup"><span data-stu-id="d280a-132">You can change this behavior by applying the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes explicitly.</span></span>  
  
 <span data-ttu-id="d280a-133">Ukázka pole používá následující nespravované funkce, které jsou zobrazeny s původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="d280a-133">The Arrays sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
- <span data-ttu-id="d280a-134">**TestArrayOfInts** exportovaný z knihovny pinvokelib. dll.</span><span class="sxs-lookup"><span data-stu-id="d280a-134">**TestArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
- <span data-ttu-id="d280a-135">**TestRefArrayOfInts** exportovaný z knihovny pinvokelib. dll.</span><span class="sxs-lookup"><span data-stu-id="d280a-135">**TestRefArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
- <span data-ttu-id="d280a-136">**TestMatrixOfInts** exportovaný z knihovny pinvokelib. dll.</span><span class="sxs-lookup"><span data-stu-id="d280a-136">**TestMatrixOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
- <span data-ttu-id="d280a-137">**TestArrayOfStrings** exportovaný z knihovny pinvokelib. dll.</span><span class="sxs-lookup"><span data-stu-id="d280a-137">**TestArrayOfStrings** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
- <span data-ttu-id="d280a-138">**TestArrayOfStructs** exportovaný z knihovny pinvokelib. dll.</span><span class="sxs-lookup"><span data-stu-id="d280a-138">**TestArrayOfStructs** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
- <span data-ttu-id="d280a-139">**TestArrayOfStructs2** exportovaný z knihovny pinvokelib. dll.</span><span class="sxs-lookup"><span data-stu-id="d280a-139">**TestArrayOfStructs2** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 <span data-ttu-id="d280a-140">[Knihovny pinvokelib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) je vlastní nespravovaná knihovna, která obsahuje implementace pro dříve uvedené funkce a dvě proměnné struktury, **MYPOINT** a **MYPERSON**.</span><span class="sxs-lookup"><span data-stu-id="d280a-140">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and two structure variables, **MYPOINT** and **MYPERSON**.</span></span> <span data-ttu-id="d280a-141">Struktury obsahují následující prvky:</span><span class="sxs-lookup"><span data-stu-id="d280a-141">The structures contain the following elements:</span></span>  
  
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
  
 <span data-ttu-id="d280a-142">V této ukázce struktury `MyPoint` a `MyPerson` obsahují vložené typy.</span><span class="sxs-lookup"><span data-stu-id="d280a-142">In this sample, the `MyPoint` and `MyPerson` structures contain embedded types.</span></span> <span data-ttu-id="d280a-143">Atribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> je nastaven tak, aby bylo zajištěno, že jsou členy uspořádány v paměti sekvenčně v pořadí, ve kterém jsou zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="d280a-143">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="d280a-144">Třída `NativeMethods` obsahuje sadu metod, které jsou volány třídou `App`.</span><span class="sxs-lookup"><span data-stu-id="d280a-144">The `NativeMethods` class contains a set of methods called by the `App` class.</span></span> <span data-ttu-id="d280a-145">Konkrétní podrobnosti o předávání polí naleznete v komentářích v následující ukázce.</span><span class="sxs-lookup"><span data-stu-id="d280a-145">For specific details about passing arrays, see the comments in the following sample.</span></span> <span data-ttu-id="d280a-146">Pole, které je odkazový typ, je ve výchozím nastavení předáno jako parametr in.</span><span class="sxs-lookup"><span data-stu-id="d280a-146">An array, which is a reference type, is passed as an In parameter by default.</span></span> <span data-ttu-id="d280a-147">Aby volající mohl přijímat výsledky, **atribut** InAttribute a **subattribute** musí být explicitně aplikovány na argument obsahující pole.</span><span class="sxs-lookup"><span data-stu-id="d280a-147">For the caller to receive the results, **InAttribute** and **OutAttribute** must be applied explicitly to the argument containing the array.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="d280a-148">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="d280a-148">Declaring Prototypes</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a><span data-ttu-id="d280a-149">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="d280a-149">Calling Functions</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="d280a-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d280a-150">See also</span></span>

- [<span data-ttu-id="d280a-151">Datové typy vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="d280a-151">Platform invoke data types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="d280a-152">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="d280a-152">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
