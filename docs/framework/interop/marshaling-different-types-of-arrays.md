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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef5c9acab6fd8fa852b619eeeee150eb33b69507
ms.sourcegitcommit: 5c2176883dc3107445702724a7caa7ac2f6cb0d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2019
ms.locfileid: "58890433"
---
# <a name="marshaling-different-types-of-arrays"></a><span data-ttu-id="188ca-102">Zařazování různých typů polí</span><span class="sxs-lookup"><span data-stu-id="188ca-102">Marshaling Different Types of Arrays</span></span>
<span data-ttu-id="188ca-103">Pole je typem odkazu ve spravovaném kódu, který obsahuje jeden nebo víc elementů stejného typu.</span><span class="sxs-lookup"><span data-stu-id="188ca-103">An array is a reference type in managed code that contains one or more elements of the same type.</span></span> <span data-ttu-id="188ca-104">I když pole jsou typy odkazů, jsou předány jako parametry in k nespravovaným funkcím.</span><span class="sxs-lookup"><span data-stu-id="188ca-104">Although arrays are reference types, they are passed as In parameters to unmanaged functions.</span></span> <span data-ttu-id="188ca-105">Toto chování je konzistentní se způsobem spravovaných polí jsou předány do spravovaných objektů, což je jako vstup a výstup parametry.</span><span class="sxs-lookup"><span data-stu-id="188ca-105">This behavior is inconsistent with way managed arrays are passed to managed objects, which is as In/Out parameters.</span></span> <span data-ttu-id="188ca-106">Další podrobnosti najdete v tématu [kopírování a přichycování](copying-and-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="188ca-106">For additional details, see [Copying and Pinning](copying-and-pinning.md).</span></span>  
  
 <span data-ttu-id="188ca-107">V následující tabulce jsou uvedeny možnosti zařazování pro pole a popisuje jejich použití.</span><span class="sxs-lookup"><span data-stu-id="188ca-107">The following table lists marshaling options for arrays and describes their usage.</span></span>  
  
|<span data-ttu-id="188ca-108">Pole</span><span class="sxs-lookup"><span data-stu-id="188ca-108">Array</span></span>|<span data-ttu-id="188ca-109">Popis</span><span class="sxs-lookup"><span data-stu-id="188ca-109">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="188ca-110">Celých čísel podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="188ca-110">Of integers by value.</span></span>|<span data-ttu-id="188ca-111">Pole celých čísel se předá jako parametr In.</span><span class="sxs-lookup"><span data-stu-id="188ca-111">Passes an array of integers as an In parameter.</span></span>|  
|<span data-ttu-id="188ca-112">Celých čísel podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="188ca-112">Of integers by reference.</span></span>|<span data-ttu-id="188ca-113">Pole celých čísel se předá jako parametr In/Out.</span><span class="sxs-lookup"><span data-stu-id="188ca-113">Passes an array of integers as an In/Out parameter.</span></span>|  
|<span data-ttu-id="188ca-114">Celých čísel podle hodnoty (dvojrozměrné).</span><span class="sxs-lookup"><span data-stu-id="188ca-114">Of integers by value (two-dimensional).</span></span>|<span data-ttu-id="188ca-115">Matice celých čísel se předá jako parametr In.</span><span class="sxs-lookup"><span data-stu-id="188ca-115">Passes a matrix of integers as an In parameter.</span></span>|  
|<span data-ttu-id="188ca-116">Z řetězce podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="188ca-116">Of strings by value.</span></span>|<span data-ttu-id="188ca-117">Pole řetězců, které se předá jako parametr In.</span><span class="sxs-lookup"><span data-stu-id="188ca-117">Passes an array of strings as an In parameter.</span></span>|  
|<span data-ttu-id="188ca-118">Struktury s celými čísly.</span><span class="sxs-lookup"><span data-stu-id="188ca-118">Of structures with integers.</span></span>|<span data-ttu-id="188ca-119">Předá pole struktury, které obsahují celých čísel jako parametr In.</span><span class="sxs-lookup"><span data-stu-id="188ca-119">Passes an array of structures that contain integers as an In parameter.</span></span>|  
|<span data-ttu-id="188ca-120">Struktury s řetězci.</span><span class="sxs-lookup"><span data-stu-id="188ca-120">Of structures with strings.</span></span>|<span data-ttu-id="188ca-121">Předá pole struktur, které obsahují řetězce pouze jako vstupně-výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="188ca-121">Passes an array of structures that contain only strings as an In/Out parameter.</span></span> <span data-ttu-id="188ca-122">Členy pole lze změnit.</span><span class="sxs-lookup"><span data-stu-id="188ca-122">Members of the array can be changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="188ca-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="188ca-123">Example</span></span>  
 <span data-ttu-id="188ca-124">Tato ukázka demonstruje následující typy polí:</span><span class="sxs-lookup"><span data-stu-id="188ca-124">This sample demonstrates how to pass the following types of arrays:</span></span>  
  
-   <span data-ttu-id="188ca-125">Pole celých čísel podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="188ca-125">Array of integers by value.</span></span>  
  
-   <span data-ttu-id="188ca-126">Pole celých čísel podle odkazu, který se dá změnit.</span><span class="sxs-lookup"><span data-stu-id="188ca-126">Array of integers by reference, which can be resized.</span></span>  
  
-   <span data-ttu-id="188ca-127">Vícerozměrná pole (matice) celých čísel podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="188ca-127">Multidimensional array (matrix) of integers by value.</span></span>  
  
-   <span data-ttu-id="188ca-128">Pole řetězců podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="188ca-128">Array of strings by value.</span></span>  
  
-   <span data-ttu-id="188ca-129">Pole struktury s celými čísly.</span><span class="sxs-lookup"><span data-stu-id="188ca-129">Array of structures with integers.</span></span>  
  
-   <span data-ttu-id="188ca-130">Pole struktury s řetězci.</span><span class="sxs-lookup"><span data-stu-id="188ca-130">Array of structures with strings.</span></span>  
  
 <span data-ttu-id="188ca-131">Pokud pole je explicitně zařazen podle odkazu, zařazuje výchozí chování pole jako parametr In.</span><span class="sxs-lookup"><span data-stu-id="188ca-131">Unless an array is explicitly marshaled by reference, the default behavior marshals the array as an In parameter.</span></span> <span data-ttu-id="188ca-132">Toto chování lze změnit použitím <xref:System.Runtime.InteropServices.InAttribute> a <xref:System.Runtime.InteropServices.OutAttribute> atributy explicitně.</span><span class="sxs-lookup"><span data-stu-id="188ca-132">You can change this behavior by applying the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes explicitly.</span></span>  
  
 <span data-ttu-id="188ca-133">Ukázka polí používá následující nespravované funkce zobrazené s původní deklarací funkce:</span><span class="sxs-lookup"><span data-stu-id="188ca-133">The Arrays sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="188ca-134">**TestArrayOfInts** exportovaná z knihovny PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="188ca-134">**TestArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
-   <span data-ttu-id="188ca-135">**TestRefArrayOfInts** exportovaná z knihovny PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="188ca-135">**TestRefArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
-   <span data-ttu-id="188ca-136">**TestMatrixOfInts** exportovaná z knihovny PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="188ca-136">**TestMatrixOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
-   <span data-ttu-id="188ca-137">**TestArrayOfStrings** exportovaná z knihovny PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="188ca-137">**TestArrayOfStrings** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
-   <span data-ttu-id="188ca-138">**TestArrayOfStructs** exportovaná z knihovny PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="188ca-138">**TestArrayOfStructs** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
-   <span data-ttu-id="188ca-139">**TestArrayOfStructs2** exportovaná z knihovny PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="188ca-139">**TestArrayOfStructs2** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 <span data-ttu-id="188ca-140">[Knihovny PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) je vlastní nespravovaná knihovna, která obsahuje implementace dříve uvedených funkcí a dvě proměnné struktury **MYPOINT** a **MYPERSON**.</span><span class="sxs-lookup"><span data-stu-id="188ca-140">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and two structure variables, **MYPOINT** and **MYPERSON**.</span></span> <span data-ttu-id="188ca-141">Struktury obsahují následující prvky:</span><span class="sxs-lookup"><span data-stu-id="188ca-141">The structures contain the following elements:</span></span>  
  
```  
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
  
 <span data-ttu-id="188ca-142">V této ukázce `MyPoint` a `MyPerson` obsahuje vestavěné typy.</span><span class="sxs-lookup"><span data-stu-id="188ca-142">In this sample, the `MyPoint` and `MyPerson` structures contain embedded types.</span></span> <span data-ttu-id="188ca-143"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Atribut je nastaven na Ujistěte se, že členové jsou uspořádáni v paměti sekvenčně, v pořadí, v jakém jsou uvedeny.</span><span class="sxs-lookup"><span data-stu-id="188ca-143">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="188ca-144">`LibWrap` Třída obsahuje sadu metod, které jsou volány `App` třídy.</span><span class="sxs-lookup"><span data-stu-id="188ca-144">The `LibWrap` class contains a set of methods called by the `App` class.</span></span> <span data-ttu-id="188ca-145">Konkrétní podrobnosti o předávání polí naleznete v tématu komentáře v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="188ca-145">For specific details about passing arrays, see the comments in the following sample.</span></span> <span data-ttu-id="188ca-146">Pole, která je typem odkazu, je předán jako parametr In ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="188ca-146">An array, which is a reference type, is passed as an In parameter by default.</span></span> <span data-ttu-id="188ca-147">Pro volajícího na příjem výsledků **InAttribute** a **OutAttribute** se musí použít explicitní argument obsahující pole.</span><span class="sxs-lookup"><span data-stu-id="188ca-147">For the caller to receive the results, **InAttribute** and **OutAttribute** must be applied explicitly to the argument containing the array.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="188ca-148">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="188ca-148">Declaring Prototypes</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a><span data-ttu-id="188ca-149">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="188ca-149">Calling Functions</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="188ca-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="188ca-150">See also</span></span>
- [<span data-ttu-id="188ca-151">Datové typy vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="188ca-151">Platform invoke data types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="188ca-152">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="188ca-152">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
