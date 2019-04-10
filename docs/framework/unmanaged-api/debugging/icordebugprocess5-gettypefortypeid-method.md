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
ms.openlocfilehash: aeb4ad1dffe4553b243b5168037aea8b68f8244b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222053"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a><span data-ttu-id="7173e-102">ICorDebugProcess5::GetTypeForTypeID – metoda</span><span class="sxs-lookup"><span data-stu-id="7173e-102">ICorDebugProcess5::GetTypeForTypeID Method</span></span>
<span data-ttu-id="7173e-103">Identifikátor typu převede na hodnotu ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="7173e-103">Converts a type identifier to an ICorDebugType value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7173e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7173e-104">Syntax</span></span>  
  
```  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7173e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7173e-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="7173e-106">[in] Identifikátor typu.</span><span class="sxs-lookup"><span data-stu-id="7173e-106">[in] The type identifier.</span></span>  
  
 `ppType`  
 <span data-ttu-id="7173e-107">[out] Ukazatel na adresu objektu ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="7173e-107">[out] A pointer to the address of an ICorDebugType object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7173e-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7173e-108">Remarks</span></span>  
 <span data-ttu-id="7173e-109">V některých případech může vrátit metody, které vracejí typu identifikátoru s hodnotou null `COR_TYPEID` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7173e-109">In some cases, methods that return a type identifier may return a null `COR_TYPEID` value.</span></span> <span data-ttu-id="7173e-110">Pokud tato hodnota je předán jako `id` argumentu `GetTypeForTypeID` selže a vrátí metoda `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="7173e-110">If this value is passed as the `id` argument, the `GetTypeForTypeID` method will fail and return `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7173e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7173e-111">Requirements</span></span>  
 <span data-ttu-id="7173e-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7173e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7173e-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7173e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7173e-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7173e-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7173e-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7173e-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7173e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7173e-116">See also</span></span>

- [<span data-ttu-id="7173e-117">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7173e-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="7173e-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7173e-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
