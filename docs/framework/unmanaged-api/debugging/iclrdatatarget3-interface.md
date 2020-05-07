---
title: ICLRDataTarget3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRDataTarget3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type:
- apiref
ms.openlocfilehash: af944a9c2bb04f37b06f27cfbe38e23c9613d768
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860413"
---
# <a name="iclrdatatarget3-interface"></a><span data-ttu-id="40a08-102">ICLRDataTarget3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40a08-102">ICLRDataTarget3 Interface</span></span>
<span data-ttu-id="40a08-103">Podtřída [ICLRDataTarget2](iclrdatatarget2-interface.md) , která poskytuje přístup k informacím o výjimce.</span><span class="sxs-lookup"><span data-stu-id="40a08-103">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="40a08-104">Metody</span><span class="sxs-lookup"><span data-stu-id="40a08-104">Methods</span></span>  
  
|<span data-ttu-id="40a08-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="40a08-105">Method</span></span>|<span data-ttu-id="40a08-106">Popis</span><span class="sxs-lookup"><span data-stu-id="40a08-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="40a08-107">GetExceptionRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="40a08-107">GetExceptionRecord Method</span></span>](iclrdatatarget3-getexceptionrecord-method.md)|<span data-ttu-id="40a08-108">Je volána službami modulu Common Language Runtime (CLR) pro přístup k datům za účelem získání záznamu o výjimce související s cílovým procesem.</span><span class="sxs-lookup"><span data-stu-id="40a08-108">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span>|  
|[<span data-ttu-id="40a08-109">GetExceptionContextRecord – metoda</span><span class="sxs-lookup"><span data-stu-id="40a08-109">GetExceptionContextRecord Method</span></span>](iclrdatatarget3-getexceptioncontextrecord-method.md)|<span data-ttu-id="40a08-110">Je volána službami modulu CLR pro přístup k datům za účelem získání záznamu o kontextu souvisejícím s cílovým procesem.</span><span class="sxs-lookup"><span data-stu-id="40a08-110">Called by the CLR data access services to retrieve the context record associated with the target process.</span></span>|  
|[<span data-ttu-id="40a08-111">GetExceptionThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="40a08-111">GetExceptionThreadID Method</span></span>](iclrdatatarget3-getexceptionthreadid-method.md)|<span data-ttu-id="40a08-112">Volá se službami CLR Data Access, aby získaly ID vlákna, které vyvolalo výjimku.</span><span class="sxs-lookup"><span data-stu-id="40a08-112">Called by the CLR data access services to get the ID of the thread that threw the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40a08-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="40a08-113">Remarks</span></span>  
 <span data-ttu-id="40a08-114">Klient API (tzn. ladicí program) musí implementovat toto rozhraní v závislosti na konkrétním cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="40a08-114">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="40a08-115">Například živý proces bude mít jinou implementaci než výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="40a08-115">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="40a08-116">Cíl nemusí podporovat změny jeho oblastí paměti.</span><span class="sxs-lookup"><span data-stu-id="40a08-116">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40a08-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="40a08-117">Requirements</span></span>  
 <span data-ttu-id="40a08-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40a08-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40a08-119">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="40a08-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="40a08-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="40a08-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40a08-121">**Verze .NET Framework:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="40a08-121">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40a08-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="40a08-122">See also</span></span>

- [<span data-ttu-id="40a08-123">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40a08-123">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
- [<span data-ttu-id="40a08-124">ICLRDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40a08-124">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="40a08-125">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40a08-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
