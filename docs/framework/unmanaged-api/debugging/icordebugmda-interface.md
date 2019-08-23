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
ms.openlocfilehash: a662185bb84e9a66573b43b26ffcd256ecb943f5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909855"
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="e5b0a-102">ICorDebugMDA – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5b0a-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="e5b0a-103">Představuje zprávu pomocníka spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="e5b0a-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e5b0a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e5b0a-104">Methods</span></span>  
  
|<span data-ttu-id="e5b0a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e5b0a-105">Method</span></span>|<span data-ttu-id="e5b0a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e5b0a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e5b0a-107">GetDescription – metoda</span><span class="sxs-lookup"><span data-stu-id="e5b0a-107">GetDescription Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|<span data-ttu-id="e5b0a-108">Získá řetězec obsahující popis tohoto typu MDA.</span><span class="sxs-lookup"><span data-stu-id="e5b0a-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="e5b0a-109">GetFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="e5b0a-109">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|<span data-ttu-id="e5b0a-110">Získá příznaky přidružené k tomuto MDA.</span><span class="sxs-lookup"><span data-stu-id="e5b0a-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="e5b0a-111">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="e5b0a-111">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|<span data-ttu-id="e5b0a-112">Získá řetězec obsahující název této aplikace MDA.</span><span class="sxs-lookup"><span data-stu-id="e5b0a-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="e5b0a-113">GetOSThreadId – metoda</span><span class="sxs-lookup"><span data-stu-id="e5b0a-113">GetOSThreadId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|<span data-ttu-id="e5b0a-114">Získá identifikátor vlákna operačního systému, na kterém je tento MDA spuštěn.</span><span class="sxs-lookup"><span data-stu-id="e5b0a-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="e5b0a-115">GetXML – metoda</span><span class="sxs-lookup"><span data-stu-id="e5b0a-115">GetXML Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|<span data-ttu-id="e5b0a-116">Získá úplný datový proud XML přidružený k tomuto MDA.</span><span class="sxs-lookup"><span data-stu-id="e5b0a-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5b0a-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e5b0a-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5b0a-118">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="e5b0a-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5b0a-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5b0a-119">Requirements</span></span>  
 <span data-ttu-id="e5b0a-120">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5b0a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5b0a-121">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e5b0a-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5b0a-122">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5b0a-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5b0a-123">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5b0a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5b0a-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5b0a-124">See also</span></span>

- [<span data-ttu-id="e5b0a-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e5b0a-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e5b0a-126">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="e5b0a-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
