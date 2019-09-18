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
ms.openlocfilehash: deae99f5bdc7c187997d4bad4957b2fcdccdc166
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051731"
---
# <a name="identifying-functions-in-dlls"></a><span data-ttu-id="a9c77-102">Identifikace funkcí ve knihovnách DLL</span><span class="sxs-lookup"><span data-stu-id="a9c77-102">Identifying Functions in DLLs</span></span>
<span data-ttu-id="a9c77-103">Identita funkce knihovny DLL se skládá z následujících prvků:</span><span class="sxs-lookup"><span data-stu-id="a9c77-103">The identity of a DLL function consists of the following elements:</span></span>  
  
- <span data-ttu-id="a9c77-104">Název funkce nebo ordinální číslo</span><span class="sxs-lookup"><span data-stu-id="a9c77-104">Function name or ordinal</span></span>  
  
- <span data-ttu-id="a9c77-105">Název souboru DLL, ve kterém se dá najít implementace</span><span class="sxs-lookup"><span data-stu-id="a9c77-105">Name of the DLL file in which the implementation can be found</span></span>  
  
 <span data-ttu-id="a9c77-106">Například zadání funkce **MessageBox** v User32. dll identifikuje funkci (**MessageBox**) a její umístění (User32. dll, User32 nebo user32).</span><span class="sxs-lookup"><span data-stu-id="a9c77-106">For example, specifying the **MessageBox** function in the User32.dll identifies the function (**MessageBox**) and its location (User32.dll, User32, or user32).</span></span> <span data-ttu-id="a9c77-107">Programovací rozhraní aplikace systému Microsoft Windows (rozhraní Windows API) může obsahovat dvě verze každé funkce, která zpracovává znaky a řetězce: 1 bajtovou verzi znakové sady ANSI a 2 bajtovou verzi znakové sady Unicode.</span><span class="sxs-lookup"><span data-stu-id="a9c77-107">The Microsoft Windows application programming interface (Windows API) can contain two versions of each function that handles characters and strings: a 1-byte character ANSI version and a 2-byte character Unicode version.</span></span> <span data-ttu-id="a9c77-108">Je-li tento parametr zadán, je znaková sada <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> reprezentovaná polem standardně ANSI.</span><span class="sxs-lookup"><span data-stu-id="a9c77-108">When unspecified, the character set, represented by the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field, defaults to ANSI.</span></span> <span data-ttu-id="a9c77-109">Některé funkce můžou mít víc než dvě verze.</span><span class="sxs-lookup"><span data-stu-id="a9c77-109">Some functions can have more than two versions.</span></span>  
  
 <span data-ttu-id="a9c77-110">**MessageBox** je vstupní bod ANSI pro funkci **MessageBox** ; **MessageBoxW** je verze Unicode.</span><span class="sxs-lookup"><span data-stu-id="a9c77-110">**MessageBoxA** is the ANSI entry point for the **MessageBox** function; **MessageBoxW** is the Unicode version.</span></span> <span data-ttu-id="a9c77-111">Pomocí různých nástrojů příkazového řádku můžete zobrazit seznam názvů funkcí pro konkrétní knihovnu DLL, například User32. dll.</span><span class="sxs-lookup"><span data-stu-id="a9c77-111">You can list function names for a specific DLL, such as user32.dll, by running a variety of command-line tools.</span></span> <span data-ttu-id="a9c77-112">Můžete například použít `dumpbin /exports user32.dll` nebo `link /dump /exports user32.dll` k získání názvů funkcí.</span><span class="sxs-lookup"><span data-stu-id="a9c77-112">For example, you can use `dumpbin /exports user32.dll` or `link /dump /exports user32.dll` to obtain function names.</span></span>  
  
 <span data-ttu-id="a9c77-113">Nespravovanou funkci můžete přejmenovat bez ohledu na to, co byste chtěli v kódu, Pokud namapujete nový název na původní vstupní bod v knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="a9c77-113">You can rename an unmanaged function to whatever you like within your code as long as you map the new name to the original entry point in the DLL.</span></span> <span data-ttu-id="a9c77-114">Pokyny k přejmenování nespravované funkce DLL ve spravovaném zdrojovém kódu naleznete v tématu [určení vstupního bodu](specifying-an-entry-point.md).</span><span class="sxs-lookup"><span data-stu-id="a9c77-114">For instructions on renaming an unmanaged DLL function in managed source code, see the [Specifying an Entry Point](specifying-an-entry-point.md).</span></span>  
  
 <span data-ttu-id="a9c77-115">Vyvolání platformy umožňuje řídit významnou část operačního systému voláním funkcí v rozhraní API systému Windows a dalších knihovnách DLL.</span><span class="sxs-lookup"><span data-stu-id="a9c77-115">Platform invoke enables you to control a significant portion of the operating system by calling functions in the Windows API and other DLLs.</span></span> <span data-ttu-id="a9c77-116">Kromě rozhraní API systému Windows existuje mnoho dalších rozhraní API a knihoven DLL, které jsou k dispozici prostřednictvím vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="a9c77-116">In addition to the Windows API, there are numerous other APIs and DLLs available to you through platform invoke.</span></span>  
  
 <span data-ttu-id="a9c77-117">Následující tabulka popisuje několik běžně používaných knihoven DLL v rozhraní Windows API.</span><span class="sxs-lookup"><span data-stu-id="a9c77-117">The following table describes several commonly used DLLs in the Windows API.</span></span>  
  
|<span data-ttu-id="a9c77-118">DLL</span><span class="sxs-lookup"><span data-stu-id="a9c77-118">DLL</span></span>|<span data-ttu-id="a9c77-119">Popis obsahu</span><span class="sxs-lookup"><span data-stu-id="a9c77-119">Description of Contents</span></span>|  
|---------|-----------------------------|  
|<span data-ttu-id="a9c77-120">GDI32.dll</span><span class="sxs-lookup"><span data-stu-id="a9c77-120">GDI32.dll</span></span>|<span data-ttu-id="a9c77-121">Funkce GDI (GDI) pro výstup zařízení, například pro vykreslování a správu písem.</span><span class="sxs-lookup"><span data-stu-id="a9c77-121">Graphics Device Interface (GDI) functions for device output, such as those for drawing and font management.</span></span>|  
|<span data-ttu-id="a9c77-122">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="a9c77-122">Kernel32.dll</span></span>|<span data-ttu-id="a9c77-123">Funkce operačního systému nižší úrovně pro správu paměti a zpracování prostředků.</span><span class="sxs-lookup"><span data-stu-id="a9c77-123">Low-level operating system functions for memory management and resource handling.</span></span>|  
|<span data-ttu-id="a9c77-124">User32.dll</span><span class="sxs-lookup"><span data-stu-id="a9c77-124">User32.dll</span></span>|<span data-ttu-id="a9c77-125">Funkce správy systému Windows pro zpracování zpráv, časovače, nabídky a komunikaci.</span><span class="sxs-lookup"><span data-stu-id="a9c77-125">Windows management functions for message handling, timers, menus, and communications.</span></span>|  
  
 <span data-ttu-id="a9c77-126">Úplnou dokumentaci k rozhraní API systému Windows najdete v sadě SDK platformy.</span><span class="sxs-lookup"><span data-stu-id="a9c77-126">For complete documentation on the Windows API, see the Platform SDK.</span></span> <span data-ttu-id="a9c77-127">Příklady, které ukazují, jak vytvořit. Deklarace založené na síti, které se mají použít s voláním platformy, najdete v tématu [zařazování dat pomocí vyvolání platformy](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="a9c77-127">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9c77-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9c77-128">See also</span></span>

- [<span data-ttu-id="a9c77-129">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="a9c77-129">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="a9c77-130">Určení vstupního bodu</span><span class="sxs-lookup"><span data-stu-id="a9c77-130">Specifying an Entry Point</span></span>](specifying-an-entry-point.md)
- [<span data-ttu-id="a9c77-131">Vytvoření třídy k umístění funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="a9c77-131">Creating a Class to Hold DLL Functions</span></span>](creating-a-class-to-hold-dll-functions.md)
- [<span data-ttu-id="a9c77-132">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="a9c77-132">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="a9c77-133">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="a9c77-133">Calling a DLL Function</span></span>](calling-a-dll-function.md)
