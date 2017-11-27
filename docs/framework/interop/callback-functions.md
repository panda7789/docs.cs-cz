---
title: "Funkce zpětného volání"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 84c3f13317f771ba81af0fc7368124c59f8a1a37
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="callback-functions"></a><span data-ttu-id="0e9ee-102">Funkce zpětného volání</span><span class="sxs-lookup"><span data-stu-id="0e9ee-102">Callback Functions</span></span>
<span data-ttu-id="0e9ee-103">Funkce zpětného volání je kód v rámci spravované aplikace, která pomáhá nespravované funkce DLL dokončení úkolu.</span><span class="sxs-lookup"><span data-stu-id="0e9ee-103">A callback function is code within a managed application that helps an unmanaged DLL function complete a task.</span></span> <span data-ttu-id="0e9ee-104">Volání funkce zpětného volání předat nepřímo ze spravované aplikace, prostřednictvím funkce knihovny DLL a zpět do spravované implementace.</span><span class="sxs-lookup"><span data-stu-id="0e9ee-104">Calls to a callback function pass indirectly from a managed application, through a DLL function, and back to the managed implementation.</span></span> <span data-ttu-id="0e9ee-105">Některé z mnoha funkcí knihovny DLL volána s platformou vyvolání vyžadují funkce zpětného volání ve spravovaném kódu správně spouštět.</span><span class="sxs-lookup"><span data-stu-id="0e9ee-105">Some of the many DLL functions called with platform invoke require a callback function in managed code to run properly.</span></span>  
  
 <span data-ttu-id="0e9ee-106">K volání většinu funkcí knihovny DLL ze spravovaného kódu, vytvořte spravované definici funkce a poté ji volat.</span><span class="sxs-lookup"><span data-stu-id="0e9ee-106">To call most DLL functions from managed code, you create a managed definition of the function and then call it.</span></span> <span data-ttu-id="0e9ee-107">Proces je jednoduchý.</span><span class="sxs-lookup"><span data-stu-id="0e9ee-107">The process is straightforward.</span></span>  
  
 <span data-ttu-id="0e9ee-108">Pomocí funkce knihovny DLL, která vyžaduje funkci zpětného volání má některé další kroky.</span><span class="sxs-lookup"><span data-stu-id="0e9ee-108">Using a DLL function that requires a callback function has some additional steps.</span></span> <span data-ttu-id="0e9ee-109">Nejdřív musí určit, zda funkce vyžaduje zpětné volání prohlížením v dokumentaci pro funkci.</span><span class="sxs-lookup"><span data-stu-id="0e9ee-109">First, you must determine whether the function requires a callback by looking at the documentation for the function.</span></span> <span data-ttu-id="0e9ee-110">Dále je nutné vytvořit funkce zpětného volání ve spravované aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0e9ee-110">Next, you have to create the callback function in your managed application.</span></span> <span data-ttu-id="0e9ee-111">Nakonec můžete volat funkce DLL předávání ukazatel do funkce zpětného volání jako argument.</span><span class="sxs-lookup"><span data-stu-id="0e9ee-111">Finally, you call the DLL function, passing a pointer to the callback function as an argument.</span></span> <span data-ttu-id="0e9ee-112">Na následujícím obrázku jsou shrnuté tyto kroky.</span><span class="sxs-lookup"><span data-stu-id="0e9ee-112">The following illustration summarizes these steps.</span></span>  
  
 <span data-ttu-id="0e9ee-113">![Vyvolání platformy zpětného volání](../../../docs/framework/interop/media/pinvokecallback.gif "pinvokecallback")</span><span class="sxs-lookup"><span data-stu-id="0e9ee-113">![Platform invoke callback](../../../docs/framework/interop/media/pinvokecallback.gif "pinvokecallback")</span></span>  
<span data-ttu-id="0e9ee-114">Funkce zpětného volání a implementace</span><span class="sxs-lookup"><span data-stu-id="0e9ee-114">Callback function and implementation</span></span>  
  
 <span data-ttu-id="0e9ee-115">Funkce zpětného volání jsou ideální pro použití v situacích, ve kterých se úloha provádí opakovaně.</span><span class="sxs-lookup"><span data-stu-id="0e9ee-115">Callback functions are ideal for use in situations in which a task is performed repeatedly.</span></span> <span data-ttu-id="0e9ee-116">Další běžné využití je s výčet funkcí, jako **EnumFontFamilies**, **EnumPrinters**, a **EnumWindows** v rozhraní API Win32.</span><span class="sxs-lookup"><span data-stu-id="0e9ee-116">Another common usage is with enumeration functions, such as **EnumFontFamilies**, **EnumPrinters**, and **EnumWindows** in the Win32 API.</span></span> <span data-ttu-id="0e9ee-117">**EnumWindows** funkce zobrazí prostřednictvím všechny existující windows v počítači, volání funkce zpětného volání provést úlohu, u všech oken.</span><span class="sxs-lookup"><span data-stu-id="0e9ee-117">The **EnumWindows** function enumerates through all existing windows on your computer, calling the callback function to perform a task on each window.</span></span> <span data-ttu-id="0e9ee-118">Pokyny a příklady naleznete v tématu [postupy: implementace funkcí zpětného volání](../../../docs/framework/interop/how-to-implement-callback-functions.md).</span><span class="sxs-lookup"><span data-stu-id="0e9ee-118">For instructions and an example, see [How to: Implement Callback Functions](../../../docs/framework/interop/how-to-implement-callback-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e9ee-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e9ee-119">See Also</span></span>  
 [<span data-ttu-id="0e9ee-120">Postupy: implementace funkcí zpětného volání</span><span class="sxs-lookup"><span data-stu-id="0e9ee-120">How to: Implement Callback Functions</span></span>](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 [<span data-ttu-id="0e9ee-121">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="0e9ee-121">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
