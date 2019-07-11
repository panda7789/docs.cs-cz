---
title: ICorDebugType::GetFirstTypeParameter – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetFirstTypeParameter
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetFirstTypeParameter
helpviewer_keywords:
- ICorDebugType::GetFirstTypeParameter method [.NET Framework debugging]
- GetFirstTypeParameter method [.NET Framework debugging]
ms.assetid: 35bb594f-af6a-4349-83fe-e98702674e03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3031cf2d9509f94b50c386b44e6d9e5d9ee5509c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768227"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a><span data-ttu-id="0e507-102">ICorDebugType::GetFirstTypeParameter – metoda</span><span class="sxs-lookup"><span data-stu-id="0e507-102">ICorDebugType::GetFirstTypeParameter Method</span></span>
<span data-ttu-id="0e507-103">Získá ukazatel rozhraní k ICorDebugType, který představuje první <xref:System.Type> parametr typu představovaného tímto rozhraním `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="0e507-103">Gets an interface pointer to an ICorDebugType that represents the first <xref:System.Type> parameter of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e507-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e507-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e507-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0e507-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="0e507-106">[out] Ukazatel na adresu `ICorDebugType` objekt, který představuje první parametr.</span><span class="sxs-lookup"><span data-stu-id="0e507-106">[out] A pointer to the address of an `ICorDebugType` object that represents the first parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e507-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0e507-107">Remarks</span></span>  
 <span data-ttu-id="0e507-108">`GetFirstTypeParameter` je možné volat v případech, kde Další informace o typu zahrnuje, maximálně jeden parametr typu.</span><span class="sxs-lookup"><span data-stu-id="0e507-108">`GetFirstTypeParameter` can be called in cases where the additional information about the type involves, at most, one type parameter.</span></span> <span data-ttu-id="0e507-109">Zejména může sloužit Pokud je typ ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF nebo ELEMENT_TYPE_PTR, je určeno [icordebugtype::gettype –](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="0e507-109">In particular, it can be used if the type is an ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR, as indicated by the [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e507-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0e507-110">Requirements</span></span>  
 <span data-ttu-id="0e507-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e507-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e507-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e507-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e507-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e507-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e507-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e507-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
