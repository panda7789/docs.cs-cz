---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: 5249d7ea359db5d5c58ae87600f61048b465b4c1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964770"
---
# <a name="ienumrawinputdevice"></a><span data-ttu-id="6ffd9-102">IEnumRAWINPUTDEVICE</span><span class="sxs-lookup"><span data-stu-id="6ffd9-102">IEnumRAWINPUTDEVICE</span></span>
<span data-ttu-id="6ffd9-103">Toto rozhraní vytvoří výčet nezpracovaných vstupních zařízení a používá se pouze PresentationHost. exe.</span><span class="sxs-lookup"><span data-stu-id="6ffd9-103">This interface enumerates the raw input devices, and is only used by PresentationHost.exe.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ffd9-104">Toto rozhraní API je zamýšlené a podporované jenom pro použití v místním klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="6ffd9-104">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="6ffd9-105">Členové</span><span class="sxs-lookup"><span data-stu-id="6ffd9-105">Members</span></span>  
  
|<span data-ttu-id="6ffd9-106">Člen</span><span class="sxs-lookup"><span data-stu-id="6ffd9-106">Member</span></span>|<span data-ttu-id="6ffd9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6ffd9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6ffd9-108">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="6ffd9-108">IEnumRAWINPUTDEVIC:Next</span></span>](ienumrawinputdevic-next.md)|<span data-ttu-id="6ffd9-109">Vytvoří výčet dalších `celt` prvků (tj. RAWINPUTDEVICE struktury) v seznamu enumerátoru a vrátí `rgelt` je spolu se skutečným počtem výčtových prvků v `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="6ffd9-109">Enumerates the next `celt` elements (that is, RAWINPUTDEVICE structures) in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>|  
|[<span data-ttu-id="6ffd9-110">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="6ffd9-110">IEnumRAWINPUTDEVIC:Skip</span></span>](ienumrawinputdevic-skip.md)|<span data-ttu-id="6ffd9-111">Instruuje enumerátor pro přeskočení dalších `celt` prvků výčtu, aby další volání [IEnumRAWINPUTDEVIC: Next](ienumrawinputdevic-next.md) nevrátí tyto prvky.</span><span class="sxs-lookup"><span data-stu-id="6ffd9-111">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) will not return those elements.</span></span>|  
|[<span data-ttu-id="6ffd9-112">IEnumRAWINPUTDEVIC:Reset</span><span class="sxs-lookup"><span data-stu-id="6ffd9-112">IEnumRAWINPUTDEVIC:Reset</span></span>](ienumrawinputdevic-reset.md)|<span data-ttu-id="6ffd9-113">Obnoví posloupnost výčtu na začátek.</span><span class="sxs-lookup"><span data-stu-id="6ffd9-113">Resets the enumeration sequence to the beginning.</span></span>|  
|[<span data-ttu-id="6ffd9-114">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="6ffd9-114">IEnumRAWINPUTDEVIC:Clone</span></span>](ienumrawinputdevic-clone.md)|<span data-ttu-id="6ffd9-115">Vytvoří další výčet nezpracovaných vstupních zařízení se stejným stavem, jako je aktuální enumerátor pro iteraci přes stejný seznam.</span><span class="sxs-lookup"><span data-stu-id="6ffd9-115">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6ffd9-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ffd9-116">See also</span></span>

- [<span data-ttu-id="6ffd9-117">O nezpracovaném vstupu</span><span class="sxs-lookup"><span data-stu-id="6ffd9-117">About Raw Input</span></span>](/windows/desktop/inputdev/about-raw-input)
