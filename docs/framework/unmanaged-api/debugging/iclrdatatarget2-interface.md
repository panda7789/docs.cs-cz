---
title: ICLRDataTarget2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2
helpviewer_keywords:
- ICLRDataTarget2 interface [.NET Framework debugging]
ms.assetid: 94249397-861b-4294-a538-cf01466a66d3
topic_type:
- apiref
ms.openlocfilehash: 6b2700b2f12e312f06640a06e5ec82fbc58f2ca9
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860465"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="fdd0a-102">ICLRDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fdd0a-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="fdd0a-103">Podtřída [ICLRDataTarget](iclrdatatarget-interface.md) , která je používána vrstvou služeb přístupu k datům k manipulaci s oblastmi virtuální paměti v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="fdd0a-103">A subclass of [ICLRDataTarget](iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fdd0a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fdd0a-104">Methods</span></span>  
  
|<span data-ttu-id="fdd0a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fdd0a-105">Method</span></span>|<span data-ttu-id="fdd0a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="fdd0a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fdd0a-107">AllocVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="fdd0a-107">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="fdd0a-108">Přidělí paměť v adresním prostoru cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="fdd0a-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="fdd0a-109">FreeVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="fdd0a-109">FreeVirtual Method</span></span>](iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="fdd0a-110">Uvolní paměť, která byla dříve přidělena v adresním prostoru cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="fdd0a-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdd0a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fdd0a-111">Remarks</span></span>  
 <span data-ttu-id="fdd0a-112">Klient API (tzn. ladicí program) musí implementovat toto rozhraní v závislosti na konkrétním cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="fdd0a-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="fdd0a-113">Například živý proces bude mít jinou implementaci než výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="fdd0a-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="fdd0a-114">Cíl nemusí podporovat změny jeho oblastí paměti.</span><span class="sxs-lookup"><span data-stu-id="fdd0a-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdd0a-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fdd0a-115">Requirements</span></span>  
 <span data-ttu-id="fdd0a-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdd0a-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdd0a-117">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="fdd0a-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="fdd0a-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fdd0a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fdd0a-119">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdd0a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdd0a-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="fdd0a-120">See also</span></span>

- [<span data-ttu-id="fdd0a-121">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fdd0a-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
- [<span data-ttu-id="fdd0a-122">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fdd0a-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
