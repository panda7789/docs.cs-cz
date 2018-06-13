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
ms.openlocfilehash: 3174be7237bcdbd5a12f38f04d6e67d9eb9a573e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421850"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="99171-102">ICorDebugRegisterSet::GetRegistersAvailable – metoda</span><span class="sxs-lookup"><span data-stu-id="99171-102">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>
<span data-ttu-id="99171-103">Získá trochu maskování, která určuje, který registruje v tomto [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) jsou nyní k dispozici.</span><span class="sxs-lookup"><span data-stu-id="99171-103">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99171-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99171-104">Syntax</span></span>  
  
```  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="99171-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99171-105">Parameters</span></span>  
 `pAvailable`  
 <span data-ttu-id="99171-106">[out] Bitová maska, která určuje, která registruje jsou nyní k dispozici.</span><span class="sxs-lookup"><span data-stu-id="99171-106">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99171-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="99171-107">Remarks</span></span>  
 <span data-ttu-id="99171-108">Registrace může nedostupná, pokud pro dané situaci nelze určit jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="99171-108">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="99171-109">Maska vrácená trochu obsahuje pro každý registr (1 << index registrace).</span><span class="sxs-lookup"><span data-stu-id="99171-109">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="99171-110">Bitová hodnota je 1, pokud zaregistrovat bude k dispozici, nebo 0, pokud není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="99171-110">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99171-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="99171-111">Requirements</span></span>  
 <span data-ttu-id="99171-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99171-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99171-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99171-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99171-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99171-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99171-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99171-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99171-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="99171-116">See Also</span></span>  
 [<span data-ttu-id="99171-117">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99171-117">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [<span data-ttu-id="99171-118">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99171-118">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
