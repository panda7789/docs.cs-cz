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
ms.openlocfilehash: e4d297023d96de83965c3d04ca9efe2613fd54d0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084449"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="eb003-102">ICorDebugProcess5::GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="eb003-102">ICorDebugProcess5::GetObject Method</span></span>
<span data-ttu-id="eb003-103">Převede adresu objektu na objekt "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="eb003-103">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb003-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb003-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,   
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb003-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb003-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="eb003-106">pro Adresa objektu.</span><span class="sxs-lookup"><span data-stu-id="eb003-106">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="eb003-107">mimo Ukazatel na adresu objektu "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="eb003-107">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb003-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb003-108">Remarks</span></span>  
 <span data-ttu-id="eb003-109">Pokud `addr` neukazuje na platný spravovaný objekt, metoda `GetObject` vrátí `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="eb003-109">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb003-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eb003-110">Requirements</span></span>  
 <span data-ttu-id="eb003-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb003-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb003-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="eb003-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb003-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="eb003-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb003-114">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb003-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb003-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb003-115">See also</span></span>

- [<span data-ttu-id="eb003-116">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb003-116">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="eb003-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="eb003-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
