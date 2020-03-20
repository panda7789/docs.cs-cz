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
ms.openlocfilehash: 66c7ba5989952edb55f21aab960ad7395a92ae0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181367"
---
# <a name="marshaling-different-types-of-arrays"></a><span data-ttu-id="5a053-102">Zařazování různých typů polí</span><span class="sxs-lookup"><span data-stu-id="5a053-102">Marshaling Different Types of Arrays</span></span>
<span data-ttu-id="5a053-103">Pole je typ odkazu ve spravovaném kódu, který obsahuje jeden nebo více prvků stejného typu.</span><span class="sxs-lookup"><span data-stu-id="5a053-103">An array is a reference type in managed code that contains one or more elements of the same type.</span></span> <span data-ttu-id="5a053-104">Přestože pole jsou typy odkazů, jsou předány jako V parametry nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="5a053-104">Although arrays are reference types, they are passed as In parameters to unmanaged functions.</span></span> <span data-ttu-id="5a053-105">Toto chování je v rozporu s způsob, jakým jsou spravovaná pole předávána spravovaným objektům, což je jako parametry In/Out.</span><span class="sxs-lookup"><span data-stu-id="5a053-105">This behavior is inconsistent with way managed arrays are passed to managed objects, which is as In/Out parameters.</span></span> <span data-ttu-id="5a053-106">Další podrobnosti naleznete v [tématu Kopírování a připnutí](copying-and-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="5a053-106">For additional details, see [Copying and Pinning](copying-and-pinning.md).</span></span>  
  
 <span data-ttu-id="5a053-107">V následující tabulce jsou uvedeny možnosti zařazování polí a popisuje jejich použití.</span><span class="sxs-lookup"><span data-stu-id="5a053-107">The following table lists marshaling options for arrays and describes their usage.</span></span>  
  
|<span data-ttu-id="5a053-108">Pole</span><span class="sxs-lookup"><span data-stu-id="5a053-108">Array</span></span>|<span data-ttu-id="5a053-109">Popis</span><span class="sxs-lookup"><span data-stu-id="5a053-109">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5a053-110">Celá čísla podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5a053-110">Of integers by value.</span></span>|<span data-ttu-id="5a053-111">Předá pole celá čísla jako In parametr.</span><span class="sxs-lookup"><span data-stu-id="5a053-111">Passes an array of integers as an In parameter.</span></span>|  
|<span data-ttu-id="5a053-112">Celá čísla odkazem.</span><span class="sxs-lookup"><span data-stu-id="5a053-112">Of integers by reference.</span></span>|<span data-ttu-id="5a053-113">Předá pole celá čísla jako in/out parametr.</span><span class="sxs-lookup"><span data-stu-id="5a053-113">Passes an array of integers as an In/Out parameter.</span></span>|  
|<span data-ttu-id="5a053-114">Celá čísla podle hodnoty (dvojrozměrné).</span><span class="sxs-lookup"><span data-stu-id="5a053-114">Of integers by value (two-dimensional).</span></span>|<span data-ttu-id="5a053-115">Předá matici celá čísla jako In parametr.</span><span class="sxs-lookup"><span data-stu-id="5a053-115">Passes a matrix of integers as an In parameter.</span></span>|  
|<span data-ttu-id="5a053-116">Řetězců podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5a053-116">Of strings by value.</span></span>|<span data-ttu-id="5a053-117">Předá pole řetězců jako In parametr.</span><span class="sxs-lookup"><span data-stu-id="5a053-117">Passes an array of strings as an In parameter.</span></span>|  
|<span data-ttu-id="5a053-118">Struktur s celámi.</span><span class="sxs-lookup"><span data-stu-id="5a053-118">Of structures with integers.</span></span>|<span data-ttu-id="5a053-119">Předá pole struktur, které obsahují celá čísla jako In parametr.</span><span class="sxs-lookup"><span data-stu-id="5a053-119">Passes an array of structures that contain integers as an In parameter.</span></span>|  
|<span data-ttu-id="5a053-120">Struktur s řetězci.</span><span class="sxs-lookup"><span data-stu-id="5a053-120">Of structures with strings.</span></span>|<span data-ttu-id="5a053-121">Předá pole struktur, které obsahují pouze řetězce jako in/out parametr.</span><span class="sxs-lookup"><span data-stu-id="5a053-121">Passes an array of structures that contain only strings as an In/Out parameter.</span></span> <span data-ttu-id="5a053-122">Členy pole lze změnit.</span><span class="sxs-lookup"><span data-stu-id="5a053-122">Members of the array can be changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5a053-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="5a053-123">Example</span></span>  
 <span data-ttu-id="5a053-124">Tato ukázka ukazuje, jak předat následující typy polí:</span><span class="sxs-lookup"><span data-stu-id="5a053-124">This sample demonstrates how to pass the following types of arrays:</span></span>  
  
- <span data-ttu-id="5a053-125">Pole celá čísla podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5a053-125">Array of integers by value.</span></span>  
  
- <span data-ttu-id="5a053-126">Pole celá čísla podle odkazu, které lze velikost.</span><span class="sxs-lookup"><span data-stu-id="5a053-126">Array of integers by reference, which can be resized.</span></span>  
  
- <span data-ttu-id="5a053-127">Vícerozměrné pole (matice) celá čísla podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5a053-127">Multidimensional array (matrix) of integers by value.</span></span>  
  
- <span data-ttu-id="5a053-128">Pole řetězců podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5a053-128">Array of strings by value.</span></span>  
  
- <span data-ttu-id="5a053-129">Pole struktur s celá čísla.</span><span class="sxs-lookup"><span data-stu-id="5a053-129">Array of structures with integers.</span></span>  
  
- <span data-ttu-id="5a053-130">Pole struktur s řetězci.</span><span class="sxs-lookup"><span data-stu-id="5a053-130">Array of structures with strings.</span></span>  
  
 <span data-ttu-id="5a053-131">Pokud pole je explicitně zařazenodkaz, výchozí chování zařazuje pole jako In parametr.</span><span class="sxs-lookup"><span data-stu-id="5a053-131">Unless an array is explicitly marshaled by reference, the default behavior marshals the array as an In parameter.</span></span> <span data-ttu-id="5a053-132">Toto chování můžete změnit <xref:System.Runtime.InteropServices.InAttribute> <xref:System.Runtime.InteropServices.OutAttribute> použitím atributů a explicitně.</span><span class="sxs-lookup"><span data-stu-id="5a053-132">You can change this behavior by applying the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes explicitly.</span></span>  
  
 <span data-ttu-id="5a053-133">Ukázka pole používá následující nespravované funkce zobrazené s jejich původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="5a053-133">The Arrays sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
- <span data-ttu-id="5a053-134">**TestArrayOfInts** exportován z souboru PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="5a053-134">**TestArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
- <span data-ttu-id="5a053-135">**TestRefArrayOfInts** exportován z souboru PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="5a053-135">**TestRefArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
- <span data-ttu-id="5a053-136">**TestMatrixOfInts** exportován z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="5a053-136">**TestMatrixOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
- <span data-ttu-id="5a053-137">**TestArrayOfStrings** exportovány z souboru PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="5a053-137">**TestArrayOfStrings** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
- <span data-ttu-id="5a053-138">**TestArrayOfStructs** exportován z souboru PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="5a053-138">**TestArrayOfStructs** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
- <span data-ttu-id="5a053-139">**TestArrayOfStructs2** exportován z souboru PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="5a053-139">**TestArrayOfStructs2** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 <span data-ttu-id="5a053-140">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) je vlastní nespravovaná knihovna, která obsahuje implementace pro dříve uvedené funkce a dvě proměnné struktury, **MYPOINT** a **MYPERSON**.</span><span class="sxs-lookup"><span data-stu-id="5a053-140">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and two structure variables, **MYPOINT** and **MYPERSON**.</span></span> <span data-ttu-id="5a053-141">Struktury obsahují následující prvky:</span><span class="sxs-lookup"><span data-stu-id="5a053-141">The structures contain the following elements:</span></span>  
  
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
  
 <span data-ttu-id="5a053-142">V této ukázce `MyPoint` `MyPerson` a struktury obsahují vložené typy.</span><span class="sxs-lookup"><span data-stu-id="5a053-142">In this sample, the `MyPoint` and `MyPerson` structures contain embedded types.</span></span> <span data-ttu-id="5a053-143">Atribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> je nastaven tak, aby bylo zajištěno, že členy jsou uspořádány v paměti postupně, v pořadí, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="5a053-143">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="5a053-144">Třída `NativeMethods` obsahuje sadu metod volaných třídou. `App`</span><span class="sxs-lookup"><span data-stu-id="5a053-144">The `NativeMethods` class contains a set of methods called by the `App` class.</span></span> <span data-ttu-id="5a053-145">Konkrétní podrobnosti o předávání polí naleznete v komentářích v následující ukázce.</span><span class="sxs-lookup"><span data-stu-id="5a053-145">For specific details about passing arrays, see the comments in the following sample.</span></span> <span data-ttu-id="5a053-146">Pole, které je typem odkazu, je ve výchozím nastavení předáno jako parametr In.</span><span class="sxs-lookup"><span data-stu-id="5a053-146">An array, which is a reference type, is passed as an In parameter by default.</span></span> <span data-ttu-id="5a053-147">Aby volající obdržel výsledky, musí být **inAttribute** a **OutAttribute** explicitně použity na argument obsahující pole.</span><span class="sxs-lookup"><span data-stu-id="5a053-147">For the caller to receive the results, **InAttribute** and **OutAttribute** must be applied explicitly to the argument containing the array.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="5a053-148">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="5a053-148">Declaring Prototypes</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a><span data-ttu-id="5a053-149">Volající funkce</span><span class="sxs-lookup"><span data-stu-id="5a053-149">Calling Functions</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="5a053-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a053-150">See also</span></span>

- [<span data-ttu-id="5a053-151">Platforma vyvolat datové typy</span><span class="sxs-lookup"><span data-stu-id="5a053-151">Platform invoke data types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="5a053-152">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="5a053-152">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
