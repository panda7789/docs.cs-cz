---
title: ICorDebugProcess5::GetObject – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetObject method [.NET Framework debugging]
ms.assetid: c8111502-5a20-447f-9dc2-76e8acd7ed5a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 56b5796a6edb3d9fb7e0dc1072951a93a6e508a3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502511"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="a0e6a-102">ICorDebugProcess5::GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="a0e6a-102">ICorDebugProcess5::GetObject Method</span></span>
<span data-ttu-id="a0e6a-103">Převede adresu objektu na objekt "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="a0e6a-103">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0e6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0e6a-104">Syntax</span></span>  
  
```  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,   
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0e6a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0e6a-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="a0e6a-106">[in] Adresa objektu.</span><span class="sxs-lookup"><span data-stu-id="a0e6a-106">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="a0e6a-107">[out] Ukazatel na adresu objektu "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="a0e6a-107">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0e6a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0e6a-108">Remarks</span></span>  
 <span data-ttu-id="a0e6a-109">Pokud `addr` neodkazuje na platný spravovaný objekt, `GetObject` vrátí metoda `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="a0e6a-109">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0e6a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a0e6a-110">Requirements</span></span>  
 <span data-ttu-id="a0e6a-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0e6a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0e6a-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0e6a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0e6a-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0e6a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0e6a-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0e6a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0e6a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0e6a-115">See also</span></span>
- [<span data-ttu-id="a0e6a-116">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0e6a-116">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="a0e6a-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a0e6a-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
