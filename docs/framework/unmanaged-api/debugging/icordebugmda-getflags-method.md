---
title: ICorDebugMDA::GetFlags – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd8878ffb2894122822617a42314f8ed9a33ad1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413745"
---
# <a name="icordebugmdagetflags-method"></a><span data-ttu-id="820ec-102">ICorDebugMDA::GetFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="820ec-102">ICorDebugMDA::GetFlags Method</span></span>
<span data-ttu-id="820ec-103">Získá příznaky přidružené Pomocník spravovaného ladění (MDA) reprezentována [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="820ec-103">Gets the flags associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="820ec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="820ec-104">Syntax</span></span>  
  
```  
HRESULT GetFlags (  
    [in] CorDebugMDAFlags *pFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="820ec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="820ec-105">Parameters</span></span>  
 `pFlags`  
 <span data-ttu-id="820ec-106">[v] Bitové kombinace [CorDebugMDAFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md) hodnot výčtu, které určují nastavení příznaků pro tento (mda).</span><span class="sxs-lookup"><span data-stu-id="820ec-106">[in] A bitwise combination of the [CorDebugMDAFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md) enumeration values that specify the settings of the flags for this MDA.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="820ec-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="820ec-107">Requirements</span></span>  
 <span data-ttu-id="820ec-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="820ec-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="820ec-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="820ec-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="820ec-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="820ec-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="820ec-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="820ec-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="820ec-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="820ec-112">See Also</span></span>  
 [<span data-ttu-id="820ec-113">ICorDebugMDA – rozhraní</span><span class="sxs-lookup"><span data-stu-id="820ec-113">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [<span data-ttu-id="820ec-114">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="820ec-114">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
