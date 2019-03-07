---
title: ICorDebugILCode2::GetLocalVarSigToken – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetLocalVarSigToken
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 17665b77-1342-4115-94fd-9f45b0ecfb0f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ee067faddf7300512387c26ae4ce4fda2b73353
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475798"
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a><span data-ttu-id="14d86-102">ICorDebugILCode2::GetLocalVarSigToken – metoda</span><span class="sxs-lookup"><span data-stu-id="14d86-102">ICorDebugILCode2::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="14d86-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="14d86-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="14d86-104">Získá token metadat pro místní proměnné podpis pro funkci, která je reprezentovaný touto instancí.</span><span class="sxs-lookup"><span data-stu-id="14d86-104">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14d86-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14d86-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14d86-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="14d86-106">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="14d86-107">[out] Ukazatel `mdSignature` token pro místní proměnné podpis pro tuto funkci nebo `mdSignatureNil` Pokud neexistuje žádný podpis (to znamená, pokud je funkce nemá žádné místní proměnné).</span><span class="sxs-lookup"><span data-stu-id="14d86-107">[out] A pointer to the `mdSignature` token for the local variable signature for this function, or `mdSignatureNil` if there is no signature (that is, if the function doesn't have any local variables).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14d86-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14d86-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14d86-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="14d86-109">Requirements</span></span>  
 <span data-ttu-id="14d86-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14d86-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14d86-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14d86-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14d86-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14d86-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14d86-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14d86-113">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14d86-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14d86-114">See also</span></span>
- [<span data-ttu-id="14d86-115">ICorDebugILCode2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="14d86-115">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)
- [<span data-ttu-id="14d86-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="14d86-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
