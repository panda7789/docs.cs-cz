---
title: "ICorDebugMDA::GetFlags – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugMDA.GetFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetFlags
helpviewer_keywords:
- ICorDebugMDA::GetFlags method [.NET Framework debugging]
- GetFlags method [.NET Framework debugging]
ms.assetid: 87ce7c5b-fd82-453e-bf55-c8a32150b183
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9f5a44d3bf0c689c0deb0e8c59b64124173f5645
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmdagetflags-method"></a><span data-ttu-id="65d81-102">ICorDebugMDA::GetFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="65d81-102">ICorDebugMDA::GetFlags Method</span></span>
<span data-ttu-id="65d81-103">Získá příznaky přidružené Pomocník spravovaného ladění (MDA) reprezentována [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="65d81-103">Gets the flags associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65d81-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65d81-104">Syntax</span></span>  
  
```  
HRESULT GetFlags (  
    [in] CorDebugMDAFlags *pFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65d81-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65d81-105">Parameters</span></span>  
 `pFlags`  
 <span data-ttu-id="65d81-106">[v] Bitové kombinace [CorDebugMDAFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md) hodnot výčtu, které určují nastavení příznaků pro tento (mda).</span><span class="sxs-lookup"><span data-stu-id="65d81-106">[in] A bitwise combination of the [CorDebugMDAFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md) enumeration values that specify the settings of the flags for this MDA.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65d81-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65d81-107">Requirements</span></span>  
 <span data-ttu-id="65d81-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65d81-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65d81-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65d81-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65d81-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65d81-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65d81-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65d81-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65d81-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="65d81-112">See Also</span></span>  
 [<span data-ttu-id="65d81-113">ICorDebugMDA – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65d81-113">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [<span data-ttu-id="65d81-114">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="65d81-114">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
