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
ms.openlocfilehash: 35fdcd4bc3c9dbf6408f501256ce0df0174f9374
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135652"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="ba20b-102">ICorDebugProcess5::GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="ba20b-102">ICorDebugProcess5::GetObject Method</span></span>
<span data-ttu-id="ba20b-103">Převede adresu objektu na objekt "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="ba20b-103">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba20b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba20b-104">Syntax</span></span>  
  
```  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,   
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba20b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ba20b-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="ba20b-106">[in] Adresa objektu.</span><span class="sxs-lookup"><span data-stu-id="ba20b-106">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="ba20b-107">[out] Ukazatel na adresu objektu "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="ba20b-107">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba20b-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ba20b-108">Remarks</span></span>  
 <span data-ttu-id="ba20b-109">Pokud `addr` neodkazuje na platný spravovaný objekt, `GetObject` vrátí metoda `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="ba20b-109">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba20b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ba20b-110">Requirements</span></span>  
 <span data-ttu-id="ba20b-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba20b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba20b-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba20b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba20b-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba20b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba20b-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba20b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba20b-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba20b-115">See also</span></span>

- [<span data-ttu-id="ba20b-116">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba20b-116">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="ba20b-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ba20b-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
