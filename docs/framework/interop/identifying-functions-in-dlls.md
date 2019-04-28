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
ms.openlocfilehash: 0ca01234bf7adaca1337053bbc2bbba0731be3cd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642955"
---
# <a name="identifying-functions-in-dlls"></a><span data-ttu-id="c0782-102">Identifikace funkcí ve knihovnách DLL</span><span class="sxs-lookup"><span data-stu-id="c0782-102">Identifying Functions in DLLs</span></span>
<span data-ttu-id="c0782-103">Identita funkce knihovny DLL se skládá z následujících elementů:</span><span class="sxs-lookup"><span data-stu-id="c0782-103">The identity of a DLL function consists of the following elements:</span></span>  
  
- <span data-ttu-id="c0782-104">Funkce názvu nebo řádu</span><span class="sxs-lookup"><span data-stu-id="c0782-104">Function name or ordinal</span></span>  
  
- <span data-ttu-id="c0782-105">Název souboru knihovny DLL, ve kterém můžete najít implementaci</span><span class="sxs-lookup"><span data-stu-id="c0782-105">Name of the DLL file in which the implementation can be found</span></span>  
  
 <span data-ttu-id="c0782-106">Například zadání **MessageBox** funkce User32.dll určuje funkci (**MessageBox**) a jeho umístění (User32.dll, User32 nebo user32).</span><span class="sxs-lookup"><span data-stu-id="c0782-106">For example, specifying the **MessageBox** function in the User32.dll identifies the function (**MessageBox**) and its location (User32.dll, User32, or user32).</span></span> <span data-ttu-id="c0782-107">Rozhraní (Windows API) Windows Microsoft může obsahovat dvě verze jednotlivých funkcí, která zpracovává znaků a řetězce: verze ANSI 1 dvoubajtového znaku zjistí a 2bajtové znaky Unicode verze.</span><span class="sxs-lookup"><span data-stu-id="c0782-107">The Microsoft Windows application programming interface (Windows API) can contain two versions of each function that handles characters and strings: a 1-byte character ANSI version and a 2-byte character Unicode version.</span></span> <span data-ttu-id="c0782-108">Pokud tento parametr nezadáte, znakové sady reprezentována <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> pole, výchozí hodnota je ANSI.</span><span class="sxs-lookup"><span data-stu-id="c0782-108">When unspecified, the character set, represented by the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field, defaults to ANSI.</span></span> <span data-ttu-id="c0782-109">Některé funkce mohou mít více než dvě verze.</span><span class="sxs-lookup"><span data-stu-id="c0782-109">Some functions can have more than two versions.</span></span>  
  
 <span data-ttu-id="c0782-110">**MessageBoxA** ANSI vstupní bod pro **MessageBox** funkce; **Funkce** je verze Unicode.</span><span class="sxs-lookup"><span data-stu-id="c0782-110">**MessageBoxA** is the ANSI entry point for the **MessageBox** function; **MessageBoxW** is the Unicode version.</span></span> <span data-ttu-id="c0782-111">Názvy funkcí pro konkrétní knihovny DLL, jako je například user32.dll, můžete vytvořit seznam spuštěním širokou škálu nástrojů příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="c0782-111">You can list function names for a specific DLL, such as user32.dll, by running a variety of command-line tools.</span></span> <span data-ttu-id="c0782-112">Například můžete použít `dumpbin /exports user32.dll` nebo `link /dump /exports user32.dll` získat názvy funkcí.</span><span class="sxs-lookup"><span data-stu-id="c0782-112">For example, you can use `dumpbin /exports user32.dll` or `link /dump /exports user32.dll` to obtain function names.</span></span>  
  
 <span data-ttu-id="c0782-113">Nespravovaná funkce můžete přejmenovat na cokoli, co chcete v rámci vašeho kódu tak dlouho, dokud mapování nový název na původní vstupní bod v knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="c0782-113">You can rename an unmanaged function to whatever you like within your code as long as you map the new name to the original entry point in the DLL.</span></span> <span data-ttu-id="c0782-114">Pokyny k přejmenování nespravovanou funkci knihovny DLL ve spravovaném zdrojovém kódu, najdete v článku [určení vstupního bodu](../../../docs/framework/interop/specifying-an-entry-point.md).</span><span class="sxs-lookup"><span data-stu-id="c0782-114">For instructions on renaming an unmanaged DLL function in managed source code, see the [Specifying an Entry Point](../../../docs/framework/interop/specifying-an-entry-point.md).</span></span>  
  
 <span data-ttu-id="c0782-115">Povolí vyvolání platformy je možné řídit podstatnou část operačního systému pomocí volání funkce v rozhraní Windows API a další knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="c0782-115">Platform invoke enables you to control a significant portion of the operating system by calling functions in the Windows API and other DLLs.</span></span> <span data-ttu-id="c0782-116">Kromě rozhraní API pro Windows existuje mnoho jiných rozhraní API a volání knihovny DLL, které jsou k dispozici prostřednictvím platformy.</span><span class="sxs-lookup"><span data-stu-id="c0782-116">In addition to the Windows API, there are numerous other APIs and DLLs available to you through platform invoke.</span></span>  
  
 <span data-ttu-id="c0782-117">Následující tabulka popisuje několik běžně používané knihovny DLL v rozhraní Windows API.</span><span class="sxs-lookup"><span data-stu-id="c0782-117">The following table describes several commonly used DLLs in the Windows API.</span></span>  
  
|<span data-ttu-id="c0782-118">DLL</span><span class="sxs-lookup"><span data-stu-id="c0782-118">DLL</span></span>|<span data-ttu-id="c0782-119">Popis obsahu</span><span class="sxs-lookup"><span data-stu-id="c0782-119">Description of Contents</span></span>|  
|---------|-----------------------------|  
|<span data-ttu-id="c0782-120">GDI32.dll</span><span class="sxs-lookup"><span data-stu-id="c0782-120">GDI32.dll</span></span>|<span data-ttu-id="c0782-121">Grafické funkce rozhraní zařízení (GDI) pro zařízení výstup, třeba kroky týkající se správy pro vykreslování a písma.</span><span class="sxs-lookup"><span data-stu-id="c0782-121">Graphics Device Interface (GDI) functions for device output, such as those for drawing and font management.</span></span>|  
|<span data-ttu-id="c0782-122">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c0782-122">Kernel32.dll</span></span>|<span data-ttu-id="c0782-123">Funkce nízké úrovně operačního systému pro správu paměti a zpracování prostředků.</span><span class="sxs-lookup"><span data-stu-id="c0782-123">Low-level operating system functions for memory management and resource handling.</span></span>|  
|<span data-ttu-id="c0782-124">User32.dll</span><span class="sxs-lookup"><span data-stu-id="c0782-124">User32.dll</span></span>|<span data-ttu-id="c0782-125">Funkce správy Windows pro zpracování zpráv, časovače, nabídky a komunikace.</span><span class="sxs-lookup"><span data-stu-id="c0782-125">Windows management functions for message handling, timers, menus, and communications.</span></span>|  
  
 <span data-ttu-id="c0782-126">Úplnou dokumentaci k rozhraní API pro Windows naleznete v tématu Platform SDK.</span><span class="sxs-lookup"><span data-stu-id="c0782-126">For complete documentation on the Windows API, see the Platform SDK.</span></span> <span data-ttu-id="c0782-127">Příklady, které ukazují, jak vytvořit. Na základě NET deklarace pro použití s platformu vyvolání, naleznete v tématu [zařazování dat pomocí vyvolání platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="c0782-127">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0782-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c0782-128">See also</span></span>

- [<span data-ttu-id="c0782-129">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="c0782-129">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="c0782-130">Určení vstupního bodu</span><span class="sxs-lookup"><span data-stu-id="c0782-130">Specifying an Entry Point</span></span>](../../../docs/framework/interop/specifying-an-entry-point.md)
- [<span data-ttu-id="c0782-131">Vytvoření třídy k umístění funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="c0782-131">Creating a Class to Hold DLL Functions</span></span>](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md)
- [<span data-ttu-id="c0782-132">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="c0782-132">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="c0782-133">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="c0782-133">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
