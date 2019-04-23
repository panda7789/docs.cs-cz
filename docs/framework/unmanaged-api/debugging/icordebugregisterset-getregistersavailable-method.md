---
title: ICorDebugRegisterSet::GetRegistersAvailable – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable
helpviewer_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable method [.NET Framework debugging]
- GetRegistersAvailable method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 4ba08ffa-55a2-4662-9d6d-4738f1db60c9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f341098268f735a576bdbc5f0cea52f1a7e14f90
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59156036"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="fbe2f-102">ICorDebugRegisterSet::GetRegistersAvailable – metoda</span><span class="sxs-lookup"><span data-stu-id="fbe2f-102">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>
<span data-ttu-id="fbe2f-103">Získá o něco maskování určující, který registruje v tomto [icordebugregisterset –](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) jsou aktuálně k dispozici.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-103">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbe2f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbe2f-104">Syntax</span></span>  
  
```  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbe2f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fbe2f-105">Parameters</span></span>  
 `pAvailable`  
 <span data-ttu-id="fbe2f-106">[out] Bitová maska, která určuje, která registruje jsou aktuálně k dispozici.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-106">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbe2f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fbe2f-107">Remarks</span></span>  
 <span data-ttu-id="fbe2f-108">Registru možná nebudou k dispozici, pokud jeho hodnotu nelze určit pro dané situaci.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-108">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="fbe2f-109">Vrácené maska obsahuje trochu pro každý registr (1 << registr indexu).</span><span class="sxs-lookup"><span data-stu-id="fbe2f-109">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="fbe2f-110">Bitová hodnota je 1, pokud do registru je k dispozici, nebo 0, pokud není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="fbe2f-110">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbe2f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fbe2f-111">Requirements</span></span>  
 <span data-ttu-id="fbe2f-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbe2f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbe2f-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fbe2f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fbe2f-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fbe2f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbe2f-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbe2f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbe2f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fbe2f-116">See also</span></span>

- [<span data-ttu-id="fbe2f-117">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbe2f-117">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="fbe2f-118">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbe2f-118">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
