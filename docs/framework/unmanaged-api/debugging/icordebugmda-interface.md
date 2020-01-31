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
ms.openlocfilehash: a147aee1ebba57b86dbbf8a7648456b8d7494936
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793188"
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="51df7-102">ICorDebugMDA – rozhraní</span><span class="sxs-lookup"><span data-stu-id="51df7-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="51df7-103">Představuje zprávu pomocníka spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="51df7-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="51df7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="51df7-104">Methods</span></span>  
  
|<span data-ttu-id="51df7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="51df7-105">Method</span></span>|<span data-ttu-id="51df7-106">Popis</span><span class="sxs-lookup"><span data-stu-id="51df7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="51df7-107">GetDescription – metoda</span><span class="sxs-lookup"><span data-stu-id="51df7-107">GetDescription Method</span></span>](icordebugmda-getdescription-method.md)|<span data-ttu-id="51df7-108">Získá řetězec obsahující popis tohoto typu MDA.</span><span class="sxs-lookup"><span data-stu-id="51df7-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="51df7-109">GetFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="51df7-109">GetFlags Method</span></span>](icordebugmda-getflags-method.md)|<span data-ttu-id="51df7-110">Získá příznaky přidružené k tomuto MDA.</span><span class="sxs-lookup"><span data-stu-id="51df7-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="51df7-111">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="51df7-111">GetName Method</span></span>](icordebugmda-getname-method.md)|<span data-ttu-id="51df7-112">Získá řetězec obsahující název této aplikace MDA.</span><span class="sxs-lookup"><span data-stu-id="51df7-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="51df7-113">GetOSThreadId – metoda</span><span class="sxs-lookup"><span data-stu-id="51df7-113">GetOSThreadId Method</span></span>](icordebugmda-getosthreadid-method.md)|<span data-ttu-id="51df7-114">Získá identifikátor vlákna operačního systému, na kterém je tento MDA spuštěn.</span><span class="sxs-lookup"><span data-stu-id="51df7-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="51df7-115">GetXML – metoda</span><span class="sxs-lookup"><span data-stu-id="51df7-115">GetXML Method</span></span>](icordebugmda-getxml-method.md)|<span data-ttu-id="51df7-116">Získá úplný datový proud XML přidružený k tomuto MDA.</span><span class="sxs-lookup"><span data-stu-id="51df7-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51df7-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="51df7-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51df7-118">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="51df7-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51df7-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="51df7-119">Requirements</span></span>  
 <span data-ttu-id="51df7-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51df7-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51df7-121">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="51df7-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51df7-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="51df7-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51df7-123">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51df7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51df7-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51df7-124">See also</span></span>

- [<span data-ttu-id="51df7-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="51df7-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="51df7-126">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="51df7-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
