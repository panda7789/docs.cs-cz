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
ms.openlocfilehash: 9d8bd6ab13fa408fd7390aaeb76baee274742f48
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137692"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="f7e26-102">ICorDebugRegisterSet::GetRegistersAvailable – metoda</span><span class="sxs-lookup"><span data-stu-id="f7e26-102">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>
<span data-ttu-id="f7e26-103">Načte bitovou masku, která označuje, které Registry v tomto [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) jsou aktuálně k dispozici.</span><span class="sxs-lookup"><span data-stu-id="f7e26-103">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7e26-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7e26-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7e26-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7e26-105">Parameters</span></span>  
 `pAvailable`  
 <span data-ttu-id="f7e26-106">mimo Bitová maska, která označuje, které Registry jsou aktuálně k dispozici.</span><span class="sxs-lookup"><span data-stu-id="f7e26-106">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7e26-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f7e26-107">Remarks</span></span>  
 <span data-ttu-id="f7e26-108">Registr může být nedostupný, pokud jeho hodnotu nelze určit pro danou situaci.</span><span class="sxs-lookup"><span data-stu-id="f7e26-108">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="f7e26-109">Vrácená maska obsahuje bit pro každý registr (1 < < indexu registru).</span><span class="sxs-lookup"><span data-stu-id="f7e26-109">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="f7e26-110">Bitová hodnota je 1, pokud je registr k dispozici, nebo 0, pokud není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="f7e26-110">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7e26-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7e26-111">Requirements</span></span>  
 <span data-ttu-id="f7e26-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7e26-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7e26-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f7e26-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7e26-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f7e26-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7e26-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7e26-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7e26-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7e26-116">See also</span></span>

- [<span data-ttu-id="f7e26-117">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f7e26-117">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="f7e26-118">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f7e26-118">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
