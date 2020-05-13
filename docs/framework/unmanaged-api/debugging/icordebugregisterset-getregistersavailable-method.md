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
ms.openlocfilehash: 74eef0c1ec456d647e5a58e5009d2c77e5002289
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378294"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="33683-102">ICorDebugRegisterSet::GetRegistersAvailable – metoda</span><span class="sxs-lookup"><span data-stu-id="33683-102">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>
<span data-ttu-id="33683-103">Načte bitovou masku, která označuje, které Registry v tomto [ICorDebugRegisterSet](icordebugregisterset-interface.md) jsou aktuálně k dispozici.</span><span class="sxs-lookup"><span data-stu-id="33683-103">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33683-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33683-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33683-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33683-105">Parameters</span></span>  
 `pAvailable`  
 <span data-ttu-id="33683-106">mimo Bitová maska, která označuje, které Registry jsou aktuálně k dispozici.</span><span class="sxs-lookup"><span data-stu-id="33683-106">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33683-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="33683-107">Remarks</span></span>  
 <span data-ttu-id="33683-108">Registr může být nedostupný, pokud jeho hodnotu nelze určit pro danou situaci.</span><span class="sxs-lookup"><span data-stu-id="33683-108">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="33683-109">Vrácená maska obsahuje bit pro každý registr (1 << index registru).</span><span class="sxs-lookup"><span data-stu-id="33683-109">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="33683-110">Bitová hodnota je 1, pokud je registr k dispozici, nebo 0, pokud není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="33683-110">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33683-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="33683-111">Requirements</span></span>  
 <span data-ttu-id="33683-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33683-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33683-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="33683-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33683-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="33683-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33683-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33683-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33683-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="33683-116">See also</span></span>

- [<span data-ttu-id="33683-117">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="33683-117">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="33683-118">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="33683-118">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
