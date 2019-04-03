---
title: Funkce zpětného volání
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81a502ab3c0f9f2faf4685c5d61c66f2eab83e7f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820878"
---
# <a name="callback-functions"></a><span data-ttu-id="c70f1-102">Funkce zpětného volání</span><span class="sxs-lookup"><span data-stu-id="c70f1-102">Callback Functions</span></span>
<span data-ttu-id="c70f1-103">Funkce zpětného volání je kód v rámci spravované aplikace, která pomáhá nespravovanou funkci knihovny DLL dokončení úkolu.</span><span class="sxs-lookup"><span data-stu-id="c70f1-103">A callback function is code within a managed application that helps an unmanaged DLL function complete a task.</span></span> <span data-ttu-id="c70f1-104">Volání funkce zpětného volání při předání nepřímo z aplikace spravované prostřednictvím funkce knihovny DLL a zpět na spravovanou implementaci.</span><span class="sxs-lookup"><span data-stu-id="c70f1-104">Calls to a callback function pass indirectly from a managed application, through a DLL function, and back to the managed implementation.</span></span> <span data-ttu-id="c70f1-105">Některé z mnoha funkcí knihovny DLL volána s platformou vyvolat vyžadují funkce zpětného volání ve spravovaném kódu správně spustit.</span><span class="sxs-lookup"><span data-stu-id="c70f1-105">Some of the many DLL functions called with platform invoke require a callback function in managed code to run properly.</span></span>  
  
 <span data-ttu-id="c70f1-106">Pro volání většinu funkcí knihovny DLL ze spravovaného kódu, vytvoří definici spravované funkce a následně ji zavolat.</span><span class="sxs-lookup"><span data-stu-id="c70f1-106">To call most DLL functions from managed code, you create a managed definition of the function and then call it.</span></span> <span data-ttu-id="c70f1-107">Proces je jednoduchý.</span><span class="sxs-lookup"><span data-stu-id="c70f1-107">The process is straightforward.</span></span>  
  
 <span data-ttu-id="c70f1-108">Pomocí funkce knihovny DLL, která vyžaduje funkci zpětného volání obsahuje několik dalších kroků.</span><span class="sxs-lookup"><span data-stu-id="c70f1-108">Using a DLL function that requires a callback function has some additional steps.</span></span> <span data-ttu-id="c70f1-109">Nejprve musíte určit, jestli funkce vyžaduje zobrazením v dokumentaci pro funkci zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="c70f1-109">First, you must determine whether the function requires a callback by looking at the documentation for the function.</span></span> <span data-ttu-id="c70f1-110">V dalším kroku je nutné vytvořit funkci zpětného volání ve spravované aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c70f1-110">Next, you have to create the callback function in your managed application.</span></span> <span data-ttu-id="c70f1-111">Nakonec můžete volat funkce knihovny DLL předání ukazatele na funkci zpětného volání jako argument.</span><span class="sxs-lookup"><span data-stu-id="c70f1-111">Finally, you call the DLL function, passing a pointer to the callback function as an argument.</span></span> 
 
 <span data-ttu-id="c70f1-112">Následující obrázek obsahuje souhrn zpětného volání funkce a provedení kroků:</span><span class="sxs-lookup"><span data-stu-id="c70f1-112">The following illustration summarizes the callback function and implementation steps:</span></span>  
  
 ![Diagram zobrazující platformu vyvolání zpětného volání procesu.](./media/callback-functions/platform-invoke-callback-process.gif)  
  
 <span data-ttu-id="c70f1-114">Funkce zpětného volání jsou ideální pro použití v situacích, ve kterých se úloha provádí opakovaně.</span><span class="sxs-lookup"><span data-stu-id="c70f1-114">Callback functions are ideal for use in situations in which a task is performed repeatedly.</span></span> <span data-ttu-id="c70f1-115">Jiné běžné použití je výčet funkcí, jako například **EnumFontFamilies**, **EnumPrinters**, a **EnumWindows** v rozhraní Windows API.</span><span class="sxs-lookup"><span data-stu-id="c70f1-115">Another common usage is with enumeration functions, such as **EnumFontFamilies**, **EnumPrinters**, and **EnumWindows** in the Windows API.</span></span> <span data-ttu-id="c70f1-116">**EnumWindows** funkce vytvoří výčet prostřednictvím všechny existující windows v počítači, zavoláním funkce zpětného volání k provedení úkolu na každé okno.</span><span class="sxs-lookup"><span data-stu-id="c70f1-116">The **EnumWindows** function enumerates through all existing windows on your computer, calling the callback function to perform a task on each window.</span></span> <span data-ttu-id="c70f1-117">Pokyny a příklad najdete v tématu [jak: Implementace funkcí zpětného volání](../../../docs/framework/interop/how-to-implement-callback-functions.md).</span><span class="sxs-lookup"><span data-stu-id="c70f1-117">For instructions and an example, see [How to: Implement Callback Functions](../../../docs/framework/interop/how-to-implement-callback-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c70f1-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c70f1-118">See also</span></span>
- [<span data-ttu-id="c70f1-119">Postupy: Implementace funkcí zpětného volání</span><span class="sxs-lookup"><span data-stu-id="c70f1-119">How to: Implement Callback Functions</span></span>](../../../docs/framework/interop/how-to-implement-callback-functions.md)
- [<span data-ttu-id="c70f1-120">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="c70f1-120">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
