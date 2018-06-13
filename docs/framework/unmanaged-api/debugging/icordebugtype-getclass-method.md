---
title: ICorDebugType::GetClass – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff2258faa8bc766c8c769f4e135f868334516b96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422556"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="6f093-102">ICorDebugType::GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="6f093-102">ICorDebugType::GetClass Method</span></span>
<span data-ttu-id="6f093-103">Získá ukazatele rozhraní umožňuje ICorDebugClass, který představuje bez instancí obecného typu.</span><span class="sxs-lookup"><span data-stu-id="6f093-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f093-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f093-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f093-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f093-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="6f093-106">[out] Ukazatel na adresu `ICorDebugClass` rozhraní, které představuje bez instancí obecného typu.</span><span class="sxs-lookup"><span data-stu-id="6f093-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f093-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6f093-107">Remarks</span></span>  
 <span data-ttu-id="6f093-108">`GetClass` je možné volat jenom za určitých podmínek.</span><span class="sxs-lookup"><span data-stu-id="6f093-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="6f093-109">Volání [icordebugtype::gettype –](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) před voláním `GetClass`.</span><span class="sxs-lookup"><span data-stu-id="6f093-109">Call [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="6f093-110">Pokud `ICorDebugType::GetType` vrátí CorElementType hodnotu, která je ELEMENT_TYPE_CLASS nebo Typ ELEMENT_TYPE_VALUETYPE, který, `GetClass` lze volat pro získání bez instancí typu pro obecného typu.</span><span class="sxs-lookup"><span data-stu-id="6f093-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f093-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6f093-111">Requirements</span></span>  
 <span data-ttu-id="6f093-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f093-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f093-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f093-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f093-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f093-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f093-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f093-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
