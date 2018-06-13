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
ms.openlocfilehash: 13498c58c7625edfa4954b8da8837f1bd60c976d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423413"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a><span data-ttu-id="a16bf-102">ICorDebugProcess5::GetTypeForTypeID – metoda</span><span class="sxs-lookup"><span data-stu-id="a16bf-102">ICorDebugProcess5::GetTypeForTypeID Method</span></span>
<span data-ttu-id="a16bf-103">Převede identifikátor typ na hodnotu ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="a16bf-103">Converts a type identifier to an ICorDebugType value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a16bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a16bf-104">Syntax</span></span>  
  
```  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a16bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a16bf-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="a16bf-106">[v] Identifikátor typu.</span><span class="sxs-lookup"><span data-stu-id="a16bf-106">[in] The type identifier.</span></span>  
  
 `ppType`  
 <span data-ttu-id="a16bf-107">[out] Ukazatel na adresu ICorDebugType objektu.</span><span class="sxs-lookup"><span data-stu-id="a16bf-107">[out] A pointer to the address of an ICorDebugType object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a16bf-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a16bf-108">Remarks</span></span>  
 <span data-ttu-id="a16bf-109">V některých případech může metody, které vracejí identifikátor typu vrátit hodnotu null `COR_TYPEID` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a16bf-109">In some cases, methods that return a type identifier may return a null `COR_TYPEID` value.</span></span> <span data-ttu-id="a16bf-110">Pokud tato hodnota se předá jako `id` argument, `GetTypeForTypeID` metoda se nezdaří a vrátí `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="a16bf-110">If this value is passed as the `id` argument, the `GetTypeForTypeID` method will fail and return `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a16bf-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a16bf-111">Requirements</span></span>  
 <span data-ttu-id="a16bf-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a16bf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a16bf-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a16bf-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a16bf-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a16bf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a16bf-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a16bf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a16bf-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a16bf-116">See Also</span></span>  
 [<span data-ttu-id="a16bf-117">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a16bf-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="a16bf-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a16bf-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
