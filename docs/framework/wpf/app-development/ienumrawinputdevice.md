---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: e0e5a112b7444872dd74cb70bb044ae233334d2a
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44706275"
---
# <a name="ienumrawinputdevice"></a><span data-ttu-id="016ec-102">IEnumRAWINPUTDEVICE</span><span class="sxs-lookup"><span data-stu-id="016ec-102">IEnumRAWINPUTDEVICE</span></span>
<span data-ttu-id="016ec-103">Toto rozhraní zobrazí nezpracované vstupní zařízení a používá se pouze podle PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="016ec-103">This interface enumerates the raw input devices, and is only used by PresentationHost.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="016ec-104">Toto rozhraní API je určen a podporovaných pro použití v místním klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="016ec-104">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="016ec-105">Členové</span><span class="sxs-lookup"><span data-stu-id="016ec-105">Members</span></span>  
  
|<span data-ttu-id="016ec-106">Člen</span><span class="sxs-lookup"><span data-stu-id="016ec-106">Member</span></span>|<span data-ttu-id="016ec-107">Popis</span><span class="sxs-lookup"><span data-stu-id="016ec-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="016ec-108">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="016ec-108">IEnumRAWINPUTDEVIC:Next</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md)|<span data-ttu-id="016ec-109">Vytvoří výčet Další `celt` elementy (to znamená, RAWINPUTDEVICE struktury) v seznamu čítače výčtu je vrácení `rgelt` spolu s skutečný počet prvků ve výčtu v `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="016ec-109">Enumerates the next `celt` elements (that is, RAWINPUTDEVICE structures) in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>|  
|[<span data-ttu-id="016ec-110">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="016ec-110">IEnumRAWINPUTDEVIC:Skip</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-skip.md)|<span data-ttu-id="016ec-111">Dává pokyn enumerátorem přeskočit na další `celt` elementy ve výčtu tak, aby na další volání [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) nevrátí tyto elementy.</span><span class="sxs-lookup"><span data-stu-id="016ec-111">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) will not return those elements.</span></span>|  
|[<span data-ttu-id="016ec-112">IEnumRAWINPUTDEVIC:Reset</span><span class="sxs-lookup"><span data-stu-id="016ec-112">IEnumRAWINPUTDEVIC:Reset</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-reset.md)|<span data-ttu-id="016ec-113">Návrat na začátek pořadí výčtu.</span><span class="sxs-lookup"><span data-stu-id="016ec-113">Resets the enumeration sequence to the beginning.</span></span>|  
|[<span data-ttu-id="016ec-114">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="016ec-114">IEnumRAWINPUTDEVIC:Clone</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-clone.md)|<span data-ttu-id="016ec-115">Vytvoří další enumerátor nezpracované vstupní zařízení pomocí stejného stavu jako aktuální enumerátor k iteraci přes stejného seznamu.</span><span class="sxs-lookup"><span data-stu-id="016ec-115">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="016ec-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="016ec-116">See Also</span></span>  
 [<span data-ttu-id="016ec-117">O vstup nezpracovaných dat</span><span class="sxs-lookup"><span data-stu-id="016ec-117">About Raw Input</span></span>](https://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/aboutrawinput.asp)
