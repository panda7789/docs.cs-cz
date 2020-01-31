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
ms.openlocfilehash: 3759cfa330ac37d2ed62a0b8bb70b5e10cd9d12e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782451"
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a><span data-ttu-id="9057a-102">ICorDebugILCode2::GetLocalVarSigToken – metoda</span><span class="sxs-lookup"><span data-stu-id="9057a-102">ICorDebugILCode2::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="9057a-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="9057a-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="9057a-104">Získá token metadat pro podpis místní proměnné pro funkci, která je reprezentovaná touto instancí.</span><span class="sxs-lookup"><span data-stu-id="9057a-104">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9057a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9057a-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9057a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9057a-106">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="9057a-107">mimo Ukazatel na token `mdSignature` pro podpis místní proměnné pro tuto funkci nebo `mdSignatureNil`, pokud není k dispozici podpis (tj., pokud funkce nemá žádné místní proměnné).</span><span class="sxs-lookup"><span data-stu-id="9057a-107">[out] A pointer to the `mdSignature` token for the local variable signature for this function, or `mdSignatureNil` if there is no signature (that is, if the function doesn't have any local variables).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9057a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9057a-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9057a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9057a-109">Requirements</span></span>  
 <span data-ttu-id="9057a-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9057a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9057a-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9057a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9057a-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9057a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9057a-113">**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9057a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9057a-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9057a-114">See also</span></span>

- [<span data-ttu-id="9057a-115">ICorDebugILCode2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9057a-115">ICorDebugILCode2 Interface</span></span>](icordebugilcode2-interface.md)
- [<span data-ttu-id="9057a-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9057a-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
