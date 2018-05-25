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
ms.openlocfilehash: ed2a4b91608306021ce510098eaf044520cbb089
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="marshaling-different-types-of-arrays"></a><span data-ttu-id="cdc38-102">Zařazování různých typů polí</span><span class="sxs-lookup"><span data-stu-id="cdc38-102">Marshaling Different Types of Arrays</span></span>
<span data-ttu-id="cdc38-103">Pole je typu odkazu ve spravovaném kódu, který obsahuje jeden či více elementů stejného typu.</span><span class="sxs-lookup"><span data-stu-id="cdc38-103">An array is a reference type in managed code that contains one or more elements of the same type.</span></span> <span data-ttu-id="cdc38-104">I když pole jsou odkazové typy, je jsou předat jako parametry k nespravovaným funkcím.</span><span class="sxs-lookup"><span data-stu-id="cdc38-104">Although arrays are reference types, they are passed as In parameters to unmanaged functions.</span></span> <span data-ttu-id="cdc38-105">Toto chování je konzistentní způsob spravovaných polí jsou předávány spravovaných objektů, což je jako vstupně -výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="cdc38-105">This behavior is inconsistent with way managed arrays are passed to managed objects, which is as In/Out parameters.</span></span> <span data-ttu-id="cdc38-106">Další podrobnosti najdete v tématu [kopírování a přichycování](copying-and-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="cdc38-106">For additional details, see [Copying and Pinning](copying-and-pinning.md).</span></span>  
  
 <span data-ttu-id="cdc38-107">V následující tabulce je uveden seznam možností zařazování pro pole a popisuje jejich použití.</span><span class="sxs-lookup"><span data-stu-id="cdc38-107">The following table lists marshaling options for arrays and describes their usage.</span></span>  
  
|<span data-ttu-id="cdc38-108">Pole</span><span class="sxs-lookup"><span data-stu-id="cdc38-108">Array</span></span>|<span data-ttu-id="cdc38-109">Popis</span><span class="sxs-lookup"><span data-stu-id="cdc38-109">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cdc38-110">Celých čísel hodnotou.</span><span class="sxs-lookup"><span data-stu-id="cdc38-110">Of integers by value.</span></span>|<span data-ttu-id="cdc38-111">Jako parametr v předá pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="cdc38-111">Passes an array of integers as an In parameter.</span></span>|  
|<span data-ttu-id="cdc38-112">Celých čísel odkazem.</span><span class="sxs-lookup"><span data-stu-id="cdc38-112">Of integers by reference.</span></span>|<span data-ttu-id="cdc38-113">Pole celých čísel předá jako parametr v nebo na více systémů.</span><span class="sxs-lookup"><span data-stu-id="cdc38-113">Passes an array of integers as an In/Out parameter.</span></span>|  
|<span data-ttu-id="cdc38-114">Celých čísel podle hodnoty (dvourozměrná).</span><span class="sxs-lookup"><span data-stu-id="cdc38-114">Of integers by value (two-dimensional).</span></span>|<span data-ttu-id="cdc38-115">Předá jako parametr v matici celých čísel.</span><span class="sxs-lookup"><span data-stu-id="cdc38-115">Passes a matrix of integers as an In parameter.</span></span>|  
|<span data-ttu-id="cdc38-116">Řetězce podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cdc38-116">Of strings by value.</span></span>|<span data-ttu-id="cdc38-117">Jako parametr v předá pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="cdc38-117">Passes an array of strings as an In parameter.</span></span>|  
|<span data-ttu-id="cdc38-118">Struktur s celými čísly.</span><span class="sxs-lookup"><span data-stu-id="cdc38-118">Of structures with integers.</span></span>|<span data-ttu-id="cdc38-119">Předá pole struktury, které obsahují celá čísla jako parametr v.</span><span class="sxs-lookup"><span data-stu-id="cdc38-119">Passes an array of structures that contain integers as an In parameter.</span></span>|  
|<span data-ttu-id="cdc38-120">Struktur s řetězci.</span><span class="sxs-lookup"><span data-stu-id="cdc38-120">Of structures with strings.</span></span>|<span data-ttu-id="cdc38-121">Předá pole struktury, které obsahují jenom celá čísla jako parametr v nebo na více systémů.</span><span class="sxs-lookup"><span data-stu-id="cdc38-121">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="cdc38-122">Členy pole lze změnit.</span><span class="sxs-lookup"><span data-stu-id="cdc38-122">Members of the array can be changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cdc38-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="cdc38-123">Example</span></span>  
 <span data-ttu-id="cdc38-124">Tento příklad ukazuje, jak následující typy polí:</span><span class="sxs-lookup"><span data-stu-id="cdc38-124">This sample demonstrates how to pass the following types of arrays:</span></span>  
  
-   <span data-ttu-id="cdc38-125">Pole celých čísel hodnotou.</span><span class="sxs-lookup"><span data-stu-id="cdc38-125">Array of integers by value.</span></span>  
  
-   <span data-ttu-id="cdc38-126">Pole celých čísel podle odkaz, který jde změnit.</span><span class="sxs-lookup"><span data-stu-id="cdc38-126">Array of integers by reference, which can be resized.</span></span>  
  
-   <span data-ttu-id="cdc38-127">Vícerozměrná pole (matice) celých čísel hodnotou.</span><span class="sxs-lookup"><span data-stu-id="cdc38-127">Multidimensional array (matrix) of integers by value.</span></span>  
  
-   <span data-ttu-id="cdc38-128">Pole řetězců hodnotou.</span><span class="sxs-lookup"><span data-stu-id="cdc38-128">Array of strings by value.</span></span>  
  
-   <span data-ttu-id="cdc38-129">Pole struktur s celými čísly.</span><span class="sxs-lookup"><span data-stu-id="cdc38-129">Array of structures with integers.</span></span>  
  
-   <span data-ttu-id="cdc38-130">Pole struktur s řetězci.</span><span class="sxs-lookup"><span data-stu-id="cdc38-130">Array of structures with strings.</span></span>  
  
 <span data-ttu-id="cdc38-131">Pokud pole není explicitně zařazena pomocí odkazu, použije se výchozí chování zařazuje jako parametr v poli.</span><span class="sxs-lookup"><span data-stu-id="cdc38-131">Unless an array is explicitly marshaled by reference, the default behavior marshals the array as an In parameter.</span></span> <span data-ttu-id="cdc38-132">Toto chování lze změnit použitím <xref:System.Runtime.InteropServices.InAttribute> a <xref:System.Runtime.InteropServices.OutAttribute> explicitně atributy.</span><span class="sxs-lookup"><span data-stu-id="cdc38-132">You can change this behavior by applying the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes explicitly.</span></span>  
  
 <span data-ttu-id="cdc38-133">Pole – Ukázka používá následující nespravované funkce s jejich původní deklarace funkce:</span><span class="sxs-lookup"><span data-stu-id="cdc38-133">The Arrays sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="cdc38-134">**TestArrayOfInts** exportovaný z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="cdc38-134">**TestArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
-   <span data-ttu-id="cdc38-135">**TestRefArrayOfInts** exportovaný z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="cdc38-135">**TestRefArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
-   <span data-ttu-id="cdc38-136">**TestMatrixOfInts** exportovaný z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="cdc38-136">**TestMatrixOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
-   <span data-ttu-id="cdc38-137">**TestArrayOfStrings** exportovaný z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="cdc38-137">**TestArrayOfStrings** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
-   <span data-ttu-id="cdc38-138">**TestArrayOfStructs** exportovaný z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="cdc38-138">**TestArrayOfStructs** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
-   <span data-ttu-id="cdc38-139">**TestArrayOfStructs2** exportovaný z PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="cdc38-139">**TestArrayOfStructs2** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 <span data-ttu-id="cdc38-140">[PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) vlastní nespravované knihovnu, která obsahuje implementace pro výše uvedených funkcí a dvě proměnné struktury **MYPOINT** a **MYPERSON**.</span><span class="sxs-lookup"><span data-stu-id="cdc38-140">[PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) is a custom unmanaged library that contains implementations for the previously listed functions and two structure variables, **MYPOINT** and **MYPERSON**.</span></span> <span data-ttu-id="cdc38-141">Struktury obsahovat tyto prvky:</span><span class="sxs-lookup"><span data-stu-id="cdc38-141">The structures contain the following elements:</span></span>  
  
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
  
 <span data-ttu-id="cdc38-142">V této ukázce `MyPoint` a `MyPerson` struktury obsahovat vložené typy.</span><span class="sxs-lookup"><span data-stu-id="cdc38-142">In this sample, the `MyPoint` and `MyPerson` structures contain embedded types.</span></span> <span data-ttu-id="cdc38-143"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Je nastavena na hodnotu zabezpečit, aby členové jsou uspořádány v paměti postupně, v pořadí, ve kterém jsou zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="cdc38-143">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="cdc38-144">`LibWrap` Třída obsahuje sadu volá metody `App` třídy.</span><span class="sxs-lookup"><span data-stu-id="cdc38-144">The `LibWrap` class contains a set of methods called by the `App` class.</span></span> <span data-ttu-id="cdc38-145">Konkrétní podrobnosti o předávání polí najdete v tématu komentáře v následující ukázce.</span><span class="sxs-lookup"><span data-stu-id="cdc38-145">For specific details about passing arrays, see the comments in the following sample.</span></span> <span data-ttu-id="cdc38-146">Pole, která je typu odkazu, je předaná jako parametr v ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="cdc38-146">An array, which is a reference type, is passed as an In parameter by default.</span></span> <span data-ttu-id="cdc38-147">Pro volající získat výsledky **InAttribute** a **OutAttribute** musí být použita explicitně argument obsahující pole.</span><span class="sxs-lookup"><span data-stu-id="cdc38-147">For the caller to receive the results, **InAttribute** and **OutAttribute** must be applied explicitly to the argument containing the array.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="cdc38-148">Deklarace prototypů</span><span class="sxs-lookup"><span data-stu-id="cdc38-148">Declaring Prototypes</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a><span data-ttu-id="cdc38-149">Volání funkcí</span><span class="sxs-lookup"><span data-stu-id="cdc38-149">Calling Functions</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="cdc38-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="cdc38-150">See Also</span></span>  
 <span data-ttu-id="cdc38-151">[Zařazování pole typů](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="cdc38-151">[Marshaling Arrays of Types](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))</span></span>  
 <span data-ttu-id="cdc38-152">[Datové typy vyvolání platformy](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="cdc38-152">[Platform Invoke Data Types](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))</span></span>  
 [<span data-ttu-id="cdc38-153">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="cdc38-153">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
