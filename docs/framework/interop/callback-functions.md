---
title: Funkce zpětného volání
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
ms.openlocfilehash: 8b8bb4dff4f73247282060c0b4fd778ae0169b1f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181520"
---
# <a name="callback-functions"></a><span data-ttu-id="29498-102">Funkce zpětného volání</span><span class="sxs-lookup"><span data-stu-id="29498-102">Callback Functions</span></span>
<span data-ttu-id="29498-103">Funkce zpětného volání je kód v rámci spravované aplikace, který pomáhá nespravované funkci DLL dokončit úlohu.</span><span class="sxs-lookup"><span data-stu-id="29498-103">A callback function is code within a managed application that helps an unmanaged DLL function complete a task.</span></span> <span data-ttu-id="29498-104">Volání funkce zpětného volání přecházejí nepřímo ze spravované aplikace prostřednictvím funkce knihovny DLL a zpět do spravované implementace.</span><span class="sxs-lookup"><span data-stu-id="29498-104">Calls to a callback function pass indirectly from a managed application, through a DLL function, and back to the managed implementation.</span></span> <span data-ttu-id="29498-105">Některé z mnoha funkcí knihoven DLL volaných s voláním platformy vyžadují funkci zpětného volání ve spravovaném kódu pro správné fungování.</span><span class="sxs-lookup"><span data-stu-id="29498-105">Some of the many DLL functions called with platform invoke require a callback function in managed code to run properly.</span></span>  
  
 <span data-ttu-id="29498-106">Chcete-li volat většinu funkcí knihovny DLL ze spravovaného kódu, vytvořte spravovanou definici funkce a pak ji zavolejte.</span><span class="sxs-lookup"><span data-stu-id="29498-106">To call most DLL functions from managed code, you create a managed definition of the function and then call it.</span></span> <span data-ttu-id="29498-107">Proces je jednoduchý.</span><span class="sxs-lookup"><span data-stu-id="29498-107">The process is straightforward.</span></span>  
  
 <span data-ttu-id="29498-108">Použití funkce knihovny DLL, která vyžaduje funkci zpětného volání, má několik dalších kroků.</span><span class="sxs-lookup"><span data-stu-id="29498-108">Using a DLL function that requires a callback function has some additional steps.</span></span> <span data-ttu-id="29498-109">Nejprve je třeba určit, zda funkce vyžaduje zpětné volání, a to tak, že si prohlédněte dokumentaci k funkci.</span><span class="sxs-lookup"><span data-stu-id="29498-109">First, you must determine whether the function requires a callback by looking at the documentation for the function.</span></span> <span data-ttu-id="29498-110">Dále musíte vytvořit funkci zpětného volání ve spravované aplikaci.</span><span class="sxs-lookup"><span data-stu-id="29498-110">Next, you have to create the callback function in your managed application.</span></span> <span data-ttu-id="29498-111">Nakonec zavolejte funkci DLL a předejte ukazatel na funkci zpětného volání jako argument.</span><span class="sxs-lookup"><span data-stu-id="29498-111">Finally, you call the DLL function, passing a pointer to the callback function as an argument.</span></span>

 <span data-ttu-id="29498-112">Následující obrázek shrnuje funkci zpětného volání a postup implementace:</span><span class="sxs-lookup"><span data-stu-id="29498-112">The following illustration summarizes the callback function and implementation steps:</span></span>  
  
 ![Diagram znázorňující proces zpětného volání vyvolání platformy](./media/callback-functions/platform-invoke-callback-process.gif)  
  
 <span data-ttu-id="29498-114">Funkce zpětného volání jsou ideální pro použití v situacích, kdy se úloha provádí opakovaně.</span><span class="sxs-lookup"><span data-stu-id="29498-114">Callback functions are ideal for use in situations in which a task is performed repeatedly.</span></span> <span data-ttu-id="29498-115">Další běžné použití je s funkcemi výčtu, jako jsou **EnumFontFamilies**, **EnumPrinters**a **EnumWindows** v rozhraní API systému Windows.</span><span class="sxs-lookup"><span data-stu-id="29498-115">Another common usage is with enumeration functions, such as **EnumFontFamilies**, **EnumPrinters**, and **EnumWindows** in the Windows API.</span></span> <span data-ttu-id="29498-116">Funkce **EnumWindows** se zobrazí ve všech stávajících oknech v počítači a voláním funkce zpětného volání provede úkol v každém okně.</span><span class="sxs-lookup"><span data-stu-id="29498-116">The **EnumWindows** function enumerates through all existing windows on your computer, calling the callback function to perform a task on each window.</span></span> <span data-ttu-id="29498-117">Pokyny a příklad naleznete v tématu [How to: Implementing Functions](how-to-implement-callback-functions.md).</span><span class="sxs-lookup"><span data-stu-id="29498-117">For instructions and an example, see [How to: Implement Callback Functions](how-to-implement-callback-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29498-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="29498-118">See also</span></span>

- [<span data-ttu-id="29498-119">Postupy: Implementace funkcí zpětného volání</span><span class="sxs-lookup"><span data-stu-id="29498-119">How to: Implement Callback Functions</span></span>](how-to-implement-callback-functions.md)
- [<span data-ttu-id="29498-120">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="29498-120">Calling a DLL Function</span></span>](calling-a-dll-function.md)
