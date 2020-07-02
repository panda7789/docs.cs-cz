---
title: Funkce zpětného volání
description: Přečtěte si o funkcích zpětného volání, které jsou kódem se spravovanou aplikací, která pomáhá nespravované funkci DLL dokončit úlohu.
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
ms.openlocfilehash: e28756b5ed935aff83363b38d6f33982e87718b2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621714"
---
# <a name="callback-functions"></a><span data-ttu-id="adf82-103">Funkce zpětného volání</span><span class="sxs-lookup"><span data-stu-id="adf82-103">Callback Functions</span></span>
<span data-ttu-id="adf82-104">Funkce zpětného volání je kód v rámci spravované aplikace, který pomáhá nespravované funkci DLL dokončit úlohu.</span><span class="sxs-lookup"><span data-stu-id="adf82-104">A callback function is code within a managed application that helps an unmanaged DLL function complete a task.</span></span> <span data-ttu-id="adf82-105">Volání funkce zpětného volání přecházejí nepřímo ze spravované aplikace prostřednictvím funkce knihovny DLL a zpět do spravované implementace.</span><span class="sxs-lookup"><span data-stu-id="adf82-105">Calls to a callback function pass indirectly from a managed application, through a DLL function, and back to the managed implementation.</span></span> <span data-ttu-id="adf82-106">Některé z mnoha funkcí knihoven DLL volaných s voláním platformy vyžadují funkci zpětného volání ve spravovaném kódu pro správné fungování.</span><span class="sxs-lookup"><span data-stu-id="adf82-106">Some of the many DLL functions called with platform invoke require a callback function in managed code to run properly.</span></span>  
  
 <span data-ttu-id="adf82-107">Chcete-li volat většinu funkcí knihovny DLL ze spravovaného kódu, vytvořte spravovanou definici funkce a pak ji zavolejte.</span><span class="sxs-lookup"><span data-stu-id="adf82-107">To call most DLL functions from managed code, you create a managed definition of the function and then call it.</span></span> <span data-ttu-id="adf82-108">Proces je jednoduchý.</span><span class="sxs-lookup"><span data-stu-id="adf82-108">The process is straightforward.</span></span>  
  
 <span data-ttu-id="adf82-109">Použití funkce knihovny DLL, která vyžaduje funkci zpětného volání, má několik dalších kroků.</span><span class="sxs-lookup"><span data-stu-id="adf82-109">Using a DLL function that requires a callback function has some additional steps.</span></span> <span data-ttu-id="adf82-110">Nejprve je třeba určit, zda funkce vyžaduje zpětné volání, a to tak, že si prohlédněte dokumentaci k funkci.</span><span class="sxs-lookup"><span data-stu-id="adf82-110">First, you must determine whether the function requires a callback by looking at the documentation for the function.</span></span> <span data-ttu-id="adf82-111">Dále musíte vytvořit funkci zpětného volání ve spravované aplikaci.</span><span class="sxs-lookup"><span data-stu-id="adf82-111">Next, you have to create the callback function in your managed application.</span></span> <span data-ttu-id="adf82-112">Nakonec zavolejte funkci DLL a předejte ukazatel na funkci zpětného volání jako argument.</span><span class="sxs-lookup"><span data-stu-id="adf82-112">Finally, you call the DLL function, passing a pointer to the callback function as an argument.</span></span>

 <span data-ttu-id="adf82-113">Následující obrázek shrnuje funkci zpětného volání a postup implementace:</span><span class="sxs-lookup"><span data-stu-id="adf82-113">The following illustration summarizes the callback function and implementation steps:</span></span>  
  
 ![Diagram znázorňující proces zpětného volání vyvolání platformy](./media/callback-functions/platform-invoke-callback-process.gif)  
  
 <span data-ttu-id="adf82-115">Funkce zpětného volání jsou ideální pro použití v situacích, kdy se úloha provádí opakovaně.</span><span class="sxs-lookup"><span data-stu-id="adf82-115">Callback functions are ideal for use in situations in which a task is performed repeatedly.</span></span> <span data-ttu-id="adf82-116">Další běžné použití je s funkcemi výčtu, jako jsou **EnumFontFamilies**, **EnumPrinters**a **EnumWindows** v rozhraní API systému Windows.</span><span class="sxs-lookup"><span data-stu-id="adf82-116">Another common usage is with enumeration functions, such as **EnumFontFamilies**, **EnumPrinters**, and **EnumWindows** in the Windows API.</span></span> <span data-ttu-id="adf82-117">Funkce **EnumWindows** se zobrazí ve všech stávajících oknech v počítači a voláním funkce zpětného volání provede úkol v každém okně.</span><span class="sxs-lookup"><span data-stu-id="adf82-117">The **EnumWindows** function enumerates through all existing windows on your computer, calling the callback function to perform a task on each window.</span></span> <span data-ttu-id="adf82-118">Pokyny a příklad naleznete v tématu [How to: Implementing Functions](how-to-implement-callback-functions.md).</span><span class="sxs-lookup"><span data-stu-id="adf82-118">For instructions and an example, see [How to: Implement Callback Functions](how-to-implement-callback-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adf82-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="adf82-119">See also</span></span>

- [<span data-ttu-id="adf82-120">Postupy: Implementace funkcí zpětného volání</span><span class="sxs-lookup"><span data-stu-id="adf82-120">How to: Implement Callback Functions</span></span>](how-to-implement-callback-functions.md)
- [<span data-ttu-id="adf82-121">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="adf82-121">Calling a DLL Function</span></span>](calling-a-dll-function.md)
