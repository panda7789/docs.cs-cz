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
ms.openlocfilehash: 540ca78c5548d4fbdd3338671ea02314736f15cd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792364"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="a6206-102">ICorDebugProcess5::GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="a6206-102">ICorDebugProcess5::GetObject Method</span></span>
<span data-ttu-id="a6206-103">Převede adresu objektu na objekt "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="a6206-103">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6206-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6206-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,   
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6206-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6206-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="a6206-106">pro Adresa objektu.</span><span class="sxs-lookup"><span data-stu-id="a6206-106">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="a6206-107">mimo Ukazatel na adresu objektu "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="a6206-107">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6206-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a6206-108">Remarks</span></span>  
 <span data-ttu-id="a6206-109">Pokud `addr` neukazuje na platný spravovaný objekt, metoda `GetObject` vrátí `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="a6206-109">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6206-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a6206-110">Requirements</span></span>  
 <span data-ttu-id="a6206-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6206-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6206-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a6206-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6206-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a6206-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6206-114">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6206-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6206-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6206-115">See also</span></span>

- [<span data-ttu-id="a6206-116">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a6206-116">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="a6206-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a6206-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
