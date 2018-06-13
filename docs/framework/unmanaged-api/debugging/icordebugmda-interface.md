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
ms.openlocfilehash: 550b39445dfe4d97e712e9a4c73aa0f497b3fce5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420963"
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="6e501-102">ICorDebugMDA – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e501-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="6e501-103">Představuje zprávu pomocníka spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="6e501-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e501-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6e501-104">Methods</span></span>  
  
|<span data-ttu-id="6e501-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6e501-105">Method</span></span>|<span data-ttu-id="6e501-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6e501-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6e501-107">GetDescription – metoda</span><span class="sxs-lookup"><span data-stu-id="6e501-107">GetDescription Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|<span data-ttu-id="6e501-108">Získá řetězec, který obsahuje popis této (mda).</span><span class="sxs-lookup"><span data-stu-id="6e501-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="6e501-109">GetFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="6e501-109">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|<span data-ttu-id="6e501-110">Získá příznaky přidružené k této (mda).</span><span class="sxs-lookup"><span data-stu-id="6e501-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="6e501-111">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="6e501-111">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|<span data-ttu-id="6e501-112">Získá řetězec, který obsahuje název této (mda).</span><span class="sxs-lookup"><span data-stu-id="6e501-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="6e501-113">GetOSThreadId – metoda</span><span class="sxs-lookup"><span data-stu-id="6e501-113">GetOSThreadId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|<span data-ttu-id="6e501-114">Získá identifikátor operačního systému přístup z více vláken, na kterém je tento MDA provádění.</span><span class="sxs-lookup"><span data-stu-id="6e501-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="6e501-115">GetXML – metoda</span><span class="sxs-lookup"><span data-stu-id="6e501-115">GetXML Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|<span data-ttu-id="6e501-116">Získá úplný datový proud XML přidružené k této (mda).</span><span class="sxs-lookup"><span data-stu-id="6e501-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e501-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6e501-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e501-118">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="6e501-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e501-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6e501-119">Requirements</span></span>  
 <span data-ttu-id="6e501-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e501-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e501-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e501-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e501-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e501-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e501-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e501-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e501-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e501-124">See Also</span></span>  
 [<span data-ttu-id="6e501-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6e501-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6e501-126">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="6e501-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
