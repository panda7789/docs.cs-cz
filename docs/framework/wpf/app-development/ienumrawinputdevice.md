---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: 04caca0c580d26fde7fc9a3e3a11b7a8fed26d65
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225518"
---
# <a name="ienumrawinputdevice"></a><span data-ttu-id="8d7ca-102">IEnumRAWINPUTDEVICE</span><span class="sxs-lookup"><span data-stu-id="8d7ca-102">IEnumRAWINPUTDEVICE</span></span>
<span data-ttu-id="8d7ca-103">Toto rozhraní zobrazí nezpracované vstupní zařízení a používá se pouze podle PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="8d7ca-103">This interface enumerates the raw input devices, and is only used by PresentationHost.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d7ca-104">Toto rozhraní API je určen a podporovaných pro použití v místním klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="8d7ca-104">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="8d7ca-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8d7ca-105">Members</span></span>  
  
|<span data-ttu-id="8d7ca-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8d7ca-106">Member</span></span>|<span data-ttu-id="8d7ca-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8d7ca-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8d7ca-108">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="8d7ca-108">IEnumRAWINPUTDEVIC:Next</span></span>](ienumrawinputdevic-next.md)|<span data-ttu-id="8d7ca-109">Vytvoří výčet Další `celt` elementy (to znamená, RAWINPUTDEVICE struktury) v seznamu čítače výčtu je vrácení `rgelt` spolu s skutečný počet prvků ve výčtu v `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="8d7ca-109">Enumerates the next `celt` elements (that is, RAWINPUTDEVICE structures) in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>|  
|[<span data-ttu-id="8d7ca-110">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="8d7ca-110">IEnumRAWINPUTDEVIC:Skip</span></span>](ienumrawinputdevic-skip.md)|<span data-ttu-id="8d7ca-111">Dává pokyn enumerátorem přeskočit na další `celt` elementy ve výčtu tak, aby na další volání [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) nevrátí tyto elementy.</span><span class="sxs-lookup"><span data-stu-id="8d7ca-111">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) will not return those elements.</span></span>|  
|[<span data-ttu-id="8d7ca-112">IEnumRAWINPUTDEVIC:Reset</span><span class="sxs-lookup"><span data-stu-id="8d7ca-112">IEnumRAWINPUTDEVIC:Reset</span></span>](ienumrawinputdevic-reset.md)|<span data-ttu-id="8d7ca-113">Návrat na začátek pořadí výčtu.</span><span class="sxs-lookup"><span data-stu-id="8d7ca-113">Resets the enumeration sequence to the beginning.</span></span>|  
|[<span data-ttu-id="8d7ca-114">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="8d7ca-114">IEnumRAWINPUTDEVIC:Clone</span></span>](ienumrawinputdevic-clone.md)|<span data-ttu-id="8d7ca-115">Vytvoří další enumerátor nezpracované vstupní zařízení pomocí stejného stavu jako aktuální enumerátor k iteraci přes stejného seznamu.</span><span class="sxs-lookup"><span data-stu-id="8d7ca-115">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8d7ca-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d7ca-116">See also</span></span>

- [<span data-ttu-id="8d7ca-117">O vstup nezpracovaných dat</span><span class="sxs-lookup"><span data-stu-id="8d7ca-117">About Raw Input</span></span>](/windows/desktop/inputdev/about-raw-input)
