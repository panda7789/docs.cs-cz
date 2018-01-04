---
title: "Zařazování řetězců"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- marshaling, samples
- platform invoke, marshaling data
- data marshaling, strings
- data marshaling, samples
- data marshaling, platform invoke
- marshaling. strings
- marshaling, platform invoke
- sample applications [.NET Framework], marshaling strings
ms.assetid: e21b078b-70fb-4905-be26-c097ab2433ff
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 89dace5ba946f2c6bd1384f23ffcff797e99bdd4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="marshaling-strings"></a><span data-ttu-id="7a5fe-102">Zařazování řetězců</span><span class="sxs-lookup"><span data-stu-id="7a5fe-102">Marshaling Strings</span></span>
<span data-ttu-id="7a5fe-103">Vyvolání platformy parametrů řetězce kopie, převod je z formátu rozhraní .NET Framework (Unicode) na nespravované formát (ANSI), v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-103">Platform invoke copies string parameters, converting them from the .NET Framework format (Unicode) to the unmanaged format (ANSI), if needed.</span></span> <span data-ttu-id="7a5fe-104">Protože jsou neměnné spravované řetězce, vyvolání platformy je zpět z nespravované paměti spravované paměti při nekopíruje funkce vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-104">Because managed strings are immutable, platform invoke does not copy them back from unmanaged memory to managed memory when the function returns.</span></span>  
  
 <span data-ttu-id="7a5fe-105">V následující tabulce je uveden seznam možností zařazování pro řetězce, popisuje jejich využití a obsahuje odkaz na odpovídající ukázce rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-105">The following table lists marshaling options for strings, describes their usage, and provides a link to the corresponding .NET Framework sample.</span></span>  
  
|<span data-ttu-id="7a5fe-106">String</span><span class="sxs-lookup"><span data-stu-id="7a5fe-106">String</span></span>|<span data-ttu-id="7a5fe-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7a5fe-107">Description</span></span>|<span data-ttu-id="7a5fe-108">Ukázka</span><span class="sxs-lookup"><span data-stu-id="7a5fe-108">Sample</span></span>|  
|------------|-----------------|------------|  
|<span data-ttu-id="7a5fe-109">Podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-109">By value.</span></span>|<span data-ttu-id="7a5fe-110">Předá řetězce jako parametry.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-110">Passes strings as In parameters.</span></span>|[<span data-ttu-id="7a5fe-111">MsgBox –</span><span class="sxs-lookup"><span data-stu-id="7a5fe-111">MsgBox</span></span>](../../../docs/framework/interop/msgbox-sample.md)|  
|<span data-ttu-id="7a5fe-112">Jako výsledek.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-112">As result.</span></span>|<span data-ttu-id="7a5fe-113">Vrátí řetězce z nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-113">Returns strings from unmanaged code.</span></span>|[<span data-ttu-id="7a5fe-114">Řetězce</span><span class="sxs-lookup"><span data-stu-id="7a5fe-114">Strings</span></span>](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|<span data-ttu-id="7a5fe-115">Odkazem.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-115">By reference.</span></span>|<span data-ttu-id="7a5fe-116">Předá řetězce jako vstup/výstup parametry s využitím <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-116">Passes strings as In/Out parameters using <xref:System.Text.StringBuilder>.</span></span>|[<span data-ttu-id="7a5fe-117">Vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="7a5fe-117">Buffers</span></span>](http://msdn.microsoft.com/en-us/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5)|  
|<span data-ttu-id="7a5fe-118">Ve struktuře hodnotou.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-118">In a structure by value.</span></span>|<span data-ttu-id="7a5fe-119">Předá řetězce ve struktuře, která je v parametru.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-119">Passes strings in a structure that is an In parameter.</span></span>|[<span data-ttu-id="7a5fe-120">Struktury</span><span class="sxs-lookup"><span data-stu-id="7a5fe-120">Structs</span></span>](http://msdn.microsoft.com/en-us/96a62265-dcf9-4608-bc0a-1f762ab9f48e)|  
|<span data-ttu-id="7a5fe-121">Ve struktuře odkazem **(char\*)**.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-121">In a structure by reference **(char\*)**.</span></span>|<span data-ttu-id="7a5fe-122">Předá řetězce ve struktuře, která je parametr v nebo na více systémů.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-122">Passes strings in a structure that is an In/Out parameter.</span></span> <span data-ttu-id="7a5fe-123">Nespravované funkce očekává ukazatel na znak vyrovnávací paměť a velikost vyrovnávací paměti je členem strukturu.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-123">The unmanaged function expects a pointer to a character buffer and the buffer size is a member of the structure.</span></span>|[<span data-ttu-id="7a5fe-124">Řetězce</span><span class="sxs-lookup"><span data-stu-id="7a5fe-124">Strings</span></span>](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|<span data-ttu-id="7a5fe-125">Ve struktuře odkazem **(char[])**.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-125">In a structure by reference **(char[])**.</span></span>|<span data-ttu-id="7a5fe-126">Předá řetězce ve struktuře, která je parametr v nebo na více systémů.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-126">Passes strings in a structure that is an In/Out parameter.</span></span> <span data-ttu-id="7a5fe-127">Nespravované funkce očekává, že vyrovnávací paměť embedded znak.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-127">The unmanaged function expects an embedded character buffer.</span></span>|[<span data-ttu-id="7a5fe-128">Osinfo –</span><span class="sxs-lookup"><span data-stu-id="7a5fe-128">OSInfo</span></span>](http://msdn.microsoft.com/en-us/69d89067-507b-41fe-859d-30bf3ff29455)|  
|<span data-ttu-id="7a5fe-129">Ve třídě hodnotou **(char\*)**.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-129">In a class by value **(char\*)**.</span></span>|<span data-ttu-id="7a5fe-130">Předá řetězce do třídy (třídy je parametr v nebo na více systémů).</span><span class="sxs-lookup"><span data-stu-id="7a5fe-130">Passes strings in a class (a class is an In/Out parameter).</span></span> <span data-ttu-id="7a5fe-131">Nespravované funkce očekává ukazatel na znak.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-131">The unmanaged function expects a pointer to a character buffer.</span></span>|[<span data-ttu-id="7a5fe-132">OpenFileDlg</span><span class="sxs-lookup"><span data-stu-id="7a5fe-132">OpenFileDlg</span></span>](http://msdn.microsoft.com/en-us/b7dea792-cb92-4baf-ac7b-6a24803e6c75)|  
|<span data-ttu-id="7a5fe-133">Ve třídě hodnotou **(char[])**.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-133">In a class by value **(char[])**.</span></span>|<span data-ttu-id="7a5fe-134">Předá řetězce do třídy (třídy je parametr v nebo na více systémů).</span><span class="sxs-lookup"><span data-stu-id="7a5fe-134">Passes strings in a class (a class is an In/Out parameter).</span></span> <span data-ttu-id="7a5fe-135">Nespravované funkce očekává, že vyrovnávací paměť embedded znak.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-135">The unmanaged function expects an embedded character buffer.</span></span>|[<span data-ttu-id="7a5fe-136">Osinfo –</span><span class="sxs-lookup"><span data-stu-id="7a5fe-136">OSInfo</span></span>](http://msdn.microsoft.com/en-us/69d89067-507b-41fe-859d-30bf3ff29455)|  
|<span data-ttu-id="7a5fe-137">Jako pole řetězců hodnotou.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-137">As an array of strings by value.</span></span>|<span data-ttu-id="7a5fe-138">Vytvoří pole řetězců, je předaná hodnota.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-138">Creates an array of strings that is passed by value.</span></span>|[<span data-ttu-id="7a5fe-139">Pole</span><span class="sxs-lookup"><span data-stu-id="7a5fe-139">Arrays</span></span>](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
|<span data-ttu-id="7a5fe-140">Jako pole struktury, které obsahují hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-140">As an array of structures that contain strings by value.</span></span>|<span data-ttu-id="7a5fe-141">Vytvoří pole struktury, která obsahují řetězce a pole je předaná hodnota.</span><span class="sxs-lookup"><span data-stu-id="7a5fe-141">Creates an array of structures that contain strings and the array is passed by value.</span></span>|[<span data-ttu-id="7a5fe-142">Pole</span><span class="sxs-lookup"><span data-stu-id="7a5fe-142">Arrays</span></span>](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a><span data-ttu-id="7a5fe-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a5fe-143">See Also</span></span>  
 [<span data-ttu-id="7a5fe-144">Zařazování dat s voláním platformy</span><span class="sxs-lookup"><span data-stu-id="7a5fe-144">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 [<span data-ttu-id="7a5fe-145">Datové typy vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="7a5fe-145">Platform Invoke Data Types</span></span>](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [<span data-ttu-id="7a5fe-146">Zařazování tříd, struktur a sjednocení</span><span class="sxs-lookup"><span data-stu-id="7a5fe-146">Marshaling Classes, Structures, and Unions</span></span>](../../../docs/framework/interop/marshaling-classes-structures-and-unions.md)  
 [<span data-ttu-id="7a5fe-147">Zařazování pole typů</span><span class="sxs-lookup"><span data-stu-id="7a5fe-147">Marshaling Arrays of Types</span></span>](http://msdn.microsoft.com/en-us/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)  
 [<span data-ttu-id="7a5fe-148">Různé zařazování ukázky</span><span class="sxs-lookup"><span data-stu-id="7a5fe-148">Miscellaneous Marshaling Samples</span></span>](http://msdn.microsoft.com/en-us/a915c948-54e9-4d0f-a525-95a77fd8ed70)
