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
ms.openlocfilehash: de570507c4312f09def0908b9d56e5371c63527e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207296"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="6de81-102">ICorDebugProcess5::GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="6de81-102">ICorDebugProcess5::GetObject Method</span></span>
<span data-ttu-id="6de81-103">Převede adresu objektu na objekt "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="6de81-103">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6de81-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6de81-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6de81-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6de81-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="6de81-106">pro Adresa objektu.</span><span class="sxs-lookup"><span data-stu-id="6de81-106">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="6de81-107">mimo Ukazatel na adresu objektu "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="6de81-107">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6de81-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6de81-108">Remarks</span></span>  
 <span data-ttu-id="6de81-109">Pokud neodkazuje `addr` na platný spravovaný objekt, `GetObject` vrátí metoda `E_FAIL` .</span><span class="sxs-lookup"><span data-stu-id="6de81-109">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6de81-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6de81-110">Requirements</span></span>  
 <span data-ttu-id="6de81-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6de81-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6de81-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6de81-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6de81-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6de81-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6de81-114">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6de81-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6de81-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="6de81-115">See also</span></span>

- [<span data-ttu-id="6de81-116">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6de81-116">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="6de81-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6de81-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
