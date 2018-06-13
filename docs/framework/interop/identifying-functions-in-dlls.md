---
title: Identifikace funkcí ve knihovnách DLL
ms.date: 03/30/2017
helpviewer_keywords:
- platform invoke, identifying functions
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- identifying DLL functions
- DLL functions
ms.assetid: 3e3f6780-6d90-4413-bad7-ba641220364d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc160678817266dc649f60dc3f2cc77044c05691
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388616"
---
# <a name="identifying-functions-in-dlls"></a><span data-ttu-id="c839f-102">Identifikace funkcí ve knihovnách DLL</span><span class="sxs-lookup"><span data-stu-id="c839f-102">Identifying Functions in DLLs</span></span>
<span data-ttu-id="c839f-103">Identitu funkce DLL se skládá z následujících elementů:</span><span class="sxs-lookup"><span data-stu-id="c839f-103">The identity of a DLL function consists of the following elements:</span></span>  
  
-   <span data-ttu-id="c839f-104">Název funkce nebo pořadí</span><span class="sxs-lookup"><span data-stu-id="c839f-104">Function name or ordinal</span></span>  
  
-   <span data-ttu-id="c839f-105">Název souboru DLL, ve kterém implementace naleznete</span><span class="sxs-lookup"><span data-stu-id="c839f-105">Name of the DLL file in which the implementation can be found</span></span>  
  
 <span data-ttu-id="c839f-106">Například zadání **MessageBox** funkce v User32.dll identifikuje funkce (**MessageBox**) a jeho umístění (User32.dll, User32 nebo user32).</span><span class="sxs-lookup"><span data-stu-id="c839f-106">For example, specifying the **MessageBox** function in the User32.dll identifies the function (**MessageBox**) and its location (User32.dll, User32, or user32).</span></span> <span data-ttu-id="c839f-107">Rozhraní (Win32 API) Microsoft Windows může obsahovat dvě verze jednotlivé funkce, která zpracovává znaky a řetězce: ANSI verze 1 znakovou a verzi 2bajtová znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="c839f-107">The Microsoft Windows application programming interface (Win32 API) can contain two versions of each function that handles characters and strings: a 1-byte character ANSI version and a 2-byte character Unicode version.</span></span> <span data-ttu-id="c839f-108">Pokud tento parametr nezadáte, znaková sada, reprezentována <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> pole, výchozí hodnota je ANSI.</span><span class="sxs-lookup"><span data-stu-id="c839f-108">When unspecified, the character set, represented by the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field, defaults to ANSI.</span></span> <span data-ttu-id="c839f-109">Některé funkce mohou mít více než dvě verze.</span><span class="sxs-lookup"><span data-stu-id="c839f-109">Some functions can have more than two versions.</span></span>  
  
 <span data-ttu-id="c839f-110">**MessageBoxA** ANSI vstupní bod pro **MessageBox** funkce; **Funkce** je verze kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="c839f-110">**MessageBoxA** is the ANSI entry point for the **MessageBox** function; **MessageBoxW** is the Unicode version.</span></span> <span data-ttu-id="c839f-111">Názvy funkcí pro konkrétní knihovny DLL, jako je například user32.dll, můžete vytvořit seznam spuštěním celou řadu nástrojů pro příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="c839f-111">You can list function names for a specific DLL, such as user32.dll, by running a variety of command-line tools.</span></span> <span data-ttu-id="c839f-112">Například můžete použít `dumpbin /exports user32.dll` nebo `link /dump /exports user32.dll` získat názvy funkcí.</span><span class="sxs-lookup"><span data-stu-id="c839f-112">For example, you can use `dumpbin /exports user32.dll` or `link /dump /exports user32.dll` to obtain function names.</span></span>  
  
 <span data-ttu-id="c839f-113">Ať se vám líbí vašeho kódu tak dlouho, dokud je nový název namapovat na původní vstupní bod v knihovně DLL, můžete přejmenovat nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="c839f-113">You can rename an unmanaged function to whatever you like within your code as long as you map the new name to the original entry point in the DLL.</span></span> <span data-ttu-id="c839f-114">Pokyny k přejmenování nespravované funkce knihovny DLL ve spravovaných zdrojovém kódu, najdete v článku [určení vstupního bodu](../../../docs/framework/interop/specifying-an-entry-point.md).</span><span class="sxs-lookup"><span data-stu-id="c839f-114">For instructions on renaming an unmanaged DLL function in managed source code, see the [Specifying an Entry Point](../../../docs/framework/interop/specifying-an-entry-point.md).</span></span>  
  
 <span data-ttu-id="c839f-115">Umožňuje vyvolání platformy vám umožňují řídit podstatnou část operačního systému při volání funkce rozhraní API Win32 a další knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="c839f-115">Platform invoke enables you to control a significant portion of the operating system by calling functions in the Win32 API and other DLLs.</span></span> <span data-ttu-id="c839f-116">Kromě rozhraní Win32 API existuje mnoho dalších rozhraní API a knihovny DLL, které jsou k dispozici prostřednictvím platformy vyvolat.</span><span class="sxs-lookup"><span data-stu-id="c839f-116">In addition to the Win32 API, there are numerous other APIs and DLLs available to you through platform invoke.</span></span>  
  
 <span data-ttu-id="c839f-117">Následující tabulka popisuje několik knihoven DLL běžně používané v rozhraní API Win32.</span><span class="sxs-lookup"><span data-stu-id="c839f-117">The following table describes several commonly used DLLs in the Win32 API.</span></span>  
  
|<span data-ttu-id="c839f-118">DLL</span><span class="sxs-lookup"><span data-stu-id="c839f-118">DLL</span></span>|<span data-ttu-id="c839f-119">Popis obsahu</span><span class="sxs-lookup"><span data-stu-id="c839f-119">Description of Contents</span></span>|  
|---------|-----------------------------|  
|<span data-ttu-id="c839f-120">Gdi32.dll</span><span class="sxs-lookup"><span data-stu-id="c839f-120">GDI32.dll</span></span>|<span data-ttu-id="c839f-121">Grafické rozhraní zařízení (GDI) funkce pro výstup, jako jsou ty pro vykreslování a písma správu zařízení.</span><span class="sxs-lookup"><span data-stu-id="c839f-121">Graphics Device Interface (GDI) functions for device output, such as those for drawing and font management.</span></span>|  
|<span data-ttu-id="c839f-122">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c839f-122">Kernel32.dll</span></span>|<span data-ttu-id="c839f-123">Funkce nízké úrovně operačního systému pro správu paměti a zpracování prostředků.</span><span class="sxs-lookup"><span data-stu-id="c839f-123">Low-level operating system functions for memory management and resource handling.</span></span>|  
|<span data-ttu-id="c839f-124">User32.dll</span><span class="sxs-lookup"><span data-stu-id="c839f-124">User32.dll</span></span>|<span data-ttu-id="c839f-125">Funkce správy systému Windows pro zpracování zpráv, časovače, nabídky a komunikace.</span><span class="sxs-lookup"><span data-stu-id="c839f-125">Windows management functions for message handling, timers, menus, and communications.</span></span>|  
  
 <span data-ttu-id="c839f-126">Úplnou dokumentaci k rozhraní API Win32 najdete v části sada SDK pro platformu.</span><span class="sxs-lookup"><span data-stu-id="c839f-126">For complete documentation on the Win32 API, see the Platform SDK.</span></span> <span data-ttu-id="c839f-127">Příklady, které ukazují, jak vytvořit. Na základě NET deklarace, který se má použít s platformou vyvolání najdete v tématu [zařazování dat s vyvolání platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="c839f-127">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c839f-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="c839f-128">See Also</span></span>  
 [<span data-ttu-id="c839f-129">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="c839f-129">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 [<span data-ttu-id="c839f-130">Určení vstupního bodu</span><span class="sxs-lookup"><span data-stu-id="c839f-130">Specifying an Entry Point</span></span>](../../../docs/framework/interop/specifying-an-entry-point.md)  
 [<span data-ttu-id="c839f-131">Vytvoření třídy k umístění funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="c839f-131">Creating a Class to Hold DLL Functions</span></span>](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md)  
 [<span data-ttu-id="c839f-132">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="c839f-132">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="c839f-133">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="c839f-133">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
