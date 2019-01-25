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
ms.openlocfilehash: f03b25f7206df2bde3e1cc0b58efb57a40c1a7a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685422"
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="9da1d-102">ICorDebugMDA – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9da1d-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="9da1d-103">Představuje zprávu pomocníka spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="9da1d-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9da1d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9da1d-104">Methods</span></span>  
  
|<span data-ttu-id="9da1d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9da1d-105">Method</span></span>|<span data-ttu-id="9da1d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9da1d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9da1d-107">GetDescription – metoda</span><span class="sxs-lookup"><span data-stu-id="9da1d-107">GetDescription Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|<span data-ttu-id="9da1d-108">Získá řetězec obsahující popis toto MDA.</span><span class="sxs-lookup"><span data-stu-id="9da1d-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="9da1d-109">GetFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="9da1d-109">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|<span data-ttu-id="9da1d-110">Získá příznaky spojené se toto MDA.</span><span class="sxs-lookup"><span data-stu-id="9da1d-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="9da1d-111">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="9da1d-111">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|<span data-ttu-id="9da1d-112">Získá řetězec obsahující název toto MDA.</span><span class="sxs-lookup"><span data-stu-id="9da1d-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="9da1d-113">GetOSThreadId – metoda</span><span class="sxs-lookup"><span data-stu-id="9da1d-113">GetOSThreadId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|<span data-ttu-id="9da1d-114">Získá identifikátor vlákna operačního systému, na kterém je spuštěn toto MDA.</span><span class="sxs-lookup"><span data-stu-id="9da1d-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="9da1d-115">GetXML – metoda</span><span class="sxs-lookup"><span data-stu-id="9da1d-115">GetXML Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|<span data-ttu-id="9da1d-116">Získá úplný datový proud XML spojené s toto MDA.</span><span class="sxs-lookup"><span data-stu-id="9da1d-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9da1d-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9da1d-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9da1d-118">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="9da1d-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9da1d-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9da1d-119">Requirements</span></span>  
 <span data-ttu-id="9da1d-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9da1d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9da1d-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9da1d-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9da1d-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9da1d-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9da1d-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9da1d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9da1d-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9da1d-124">See also</span></span>
- [<span data-ttu-id="9da1d-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9da1d-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="9da1d-126">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="9da1d-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
