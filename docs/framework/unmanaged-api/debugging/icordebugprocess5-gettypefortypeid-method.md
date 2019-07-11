---
title: ICorDebugProcess5::GetTypeForTypeID – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeForTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeForTypeID
helpviewer_keywords:
- GetTypeForTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeForTypeID method [.NET Framework debugging]
ms.assetid: e0eed5a8-fa6d-4818-bd00-7babcea30325
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f37fab4d877ae804996f46290e3576cecc5a25ca
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767611"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a><span data-ttu-id="f9023-102">ICorDebugProcess5::GetTypeForTypeID – metoda</span><span class="sxs-lookup"><span data-stu-id="f9023-102">ICorDebugProcess5::GetTypeForTypeID Method</span></span>
<span data-ttu-id="f9023-103">Identifikátor typu převede na hodnotu ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="f9023-103">Converts a type identifier to an ICorDebugType value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9023-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9023-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9023-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9023-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="f9023-106">[in] Identifikátor typu.</span><span class="sxs-lookup"><span data-stu-id="f9023-106">[in] The type identifier.</span></span>  
  
 `ppType`  
 <span data-ttu-id="f9023-107">[out] Ukazatel na adresu objektu ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="f9023-107">[out] A pointer to the address of an ICorDebugType object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9023-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f9023-108">Remarks</span></span>  
 <span data-ttu-id="f9023-109">V některých případech může vrátit metody, které vracejí typu identifikátoru s hodnotou null `COR_TYPEID` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f9023-109">In some cases, methods that return a type identifier may return a null `COR_TYPEID` value.</span></span> <span data-ttu-id="f9023-110">Pokud tato hodnota je předán jako `id` argumentu `GetTypeForTypeID` selže a vrátí metoda `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="f9023-110">If this value is passed as the `id` argument, the `GetTypeForTypeID` method will fail and return `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9023-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9023-111">Requirements</span></span>  
 <span data-ttu-id="f9023-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9023-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9023-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9023-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9023-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9023-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9023-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9023-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9023-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9023-116">See also</span></span>

- [<span data-ttu-id="f9023-117">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9023-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="f9023-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f9023-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
