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
ms.openlocfilehash: 9810a8a55fc9c5296bffa5106551f9734dcd61bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199905"
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a><span data-ttu-id="b79f4-102">ICorDebugILCode2::GetLocalVarSigToken – metoda</span><span class="sxs-lookup"><span data-stu-id="b79f4-102">ICorDebugILCode2::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="b79f4-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="b79f4-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b79f4-104">Získá token metadat pro místní proměnné podpis pro funkci, která je reprezentovaný touto instancí.</span><span class="sxs-lookup"><span data-stu-id="b79f4-104">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b79f4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b79f4-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b79f4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b79f4-106">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="b79f4-107">[out] Ukazatel `mdSignature` token pro místní proměnné podpis pro tuto funkci nebo `mdSignatureNil` Pokud neexistuje žádný podpis (to znamená, pokud je funkce nemá žádné místní proměnné).</span><span class="sxs-lookup"><span data-stu-id="b79f4-107">[out] A pointer to the `mdSignature` token for the local variable signature for this function, or `mdSignatureNil` if there is no signature (that is, if the function doesn't have any local variables).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b79f4-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b79f4-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b79f4-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b79f4-109">Requirements</span></span>  
 <span data-ttu-id="b79f4-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b79f4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b79f4-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b79f4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b79f4-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b79f4-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b79f4-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b79f4-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b79f4-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b79f4-114">See also</span></span>

- [<span data-ttu-id="b79f4-115">Rozhraní ICorDebugILCode2</span><span class="sxs-lookup"><span data-stu-id="b79f4-115">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)
- [<span data-ttu-id="b79f4-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b79f4-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
