---
title: ICorDebugMDA – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cea8f6827d3e361b3f6498e6612d8b11a2357285
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098653"
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="b2fff-102">ICorDebugMDA – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2fff-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="b2fff-103">Představuje zprávu pomocníka spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="b2fff-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b2fff-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b2fff-104">Methods</span></span>  
  
|<span data-ttu-id="b2fff-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b2fff-105">Method</span></span>|<span data-ttu-id="b2fff-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b2fff-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b2fff-107">GetDescription – metoda</span><span class="sxs-lookup"><span data-stu-id="b2fff-107">GetDescription Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|<span data-ttu-id="b2fff-108">Získá řetězec obsahující popis toto MDA.</span><span class="sxs-lookup"><span data-stu-id="b2fff-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="b2fff-109">GetFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="b2fff-109">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|<span data-ttu-id="b2fff-110">Získá příznaky spojené se toto MDA.</span><span class="sxs-lookup"><span data-stu-id="b2fff-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="b2fff-111">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="b2fff-111">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|<span data-ttu-id="b2fff-112">Získá řetězec obsahující název toto MDA.</span><span class="sxs-lookup"><span data-stu-id="b2fff-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="b2fff-113">GetOSThreadId – metoda</span><span class="sxs-lookup"><span data-stu-id="b2fff-113">GetOSThreadId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|<span data-ttu-id="b2fff-114">Získá identifikátor vlákna operačního systému, na kterém je spuštěn toto MDA.</span><span class="sxs-lookup"><span data-stu-id="b2fff-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="b2fff-115">GetXML – metoda</span><span class="sxs-lookup"><span data-stu-id="b2fff-115">GetXML Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|<span data-ttu-id="b2fff-116">Získá úplný datový proud XML spojené s toto MDA.</span><span class="sxs-lookup"><span data-stu-id="b2fff-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2fff-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b2fff-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2fff-118">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="b2fff-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2fff-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b2fff-119">Requirements</span></span>  
 <span data-ttu-id="b2fff-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2fff-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2fff-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2fff-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2fff-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2fff-122">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b2fff-123">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b2fff-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b2fff-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2fff-124">See also</span></span>

- [<span data-ttu-id="b2fff-125">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2fff-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b2fff-126">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="b2fff-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
