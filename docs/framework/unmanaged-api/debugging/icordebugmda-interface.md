---
title: "ICorDebugMDA – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMDA
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMDA
helpviewer_keywords: ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 00a003ee060de59fe0eb8ce8f740a620d77a7c85
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="026d8-102">ICorDebugMDA – rozhraní</span><span class="sxs-lookup"><span data-stu-id="026d8-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="026d8-103">Představuje zprávu pomocníka spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="026d8-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="026d8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="026d8-104">Methods</span></span>  
  
|<span data-ttu-id="026d8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="026d8-105">Method</span></span>|<span data-ttu-id="026d8-106">Popis</span><span class="sxs-lookup"><span data-stu-id="026d8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="026d8-107">GetDescription – metoda</span><span class="sxs-lookup"><span data-stu-id="026d8-107">GetDescription Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|<span data-ttu-id="026d8-108">Získá řetězec, který obsahuje popis této (mda).</span><span class="sxs-lookup"><span data-stu-id="026d8-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="026d8-109">Getflags – metoda</span><span class="sxs-lookup"><span data-stu-id="026d8-109">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|<span data-ttu-id="026d8-110">Získá příznaky přidružené k této (mda).</span><span class="sxs-lookup"><span data-stu-id="026d8-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="026d8-111">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="026d8-111">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|<span data-ttu-id="026d8-112">Získá řetězec, který obsahuje název této (mda).</span><span class="sxs-lookup"><span data-stu-id="026d8-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="026d8-113">Getosthreadid – metoda</span><span class="sxs-lookup"><span data-stu-id="026d8-113">GetOSThreadId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|<span data-ttu-id="026d8-114">Získá identifikátor operačního systému přístup z více vláken, na kterém je tento MDA provádění.</span><span class="sxs-lookup"><span data-stu-id="026d8-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="026d8-115">Getxml – metoda</span><span class="sxs-lookup"><span data-stu-id="026d8-115">GetXML Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|<span data-ttu-id="026d8-116">Získá úplný datový proud XML přidružené k této (mda).</span><span class="sxs-lookup"><span data-stu-id="026d8-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="026d8-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="026d8-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="026d8-118">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="026d8-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="026d8-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="026d8-119">Requirements</span></span>  
 <span data-ttu-id="026d8-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="026d8-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="026d8-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="026d8-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="026d8-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="026d8-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="026d8-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="026d8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="026d8-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="026d8-124">See Also</span></span>  
 [<span data-ttu-id="026d8-125">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="026d8-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="026d8-126">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="026d8-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
