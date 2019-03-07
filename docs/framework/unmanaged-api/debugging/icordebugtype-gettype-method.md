---
title: ICorDebugType::GetType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6b36c524921a4fecf8bc5ddcbace62af6450b6d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492423"
---
# <a name="icordebugtypegettype-method"></a><span data-ttu-id="64b91-102">ICorDebugType::GetType – metoda</span><span class="sxs-lookup"><span data-stu-id="64b91-102">ICorDebugType::GetType Method</span></span>
<span data-ttu-id="64b91-103">Získá hodnotu corelementtype –, který popisuje nativní typ modulu common language runtime (CLR) <xref:System.Type> reprezentována tento ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="64b91-103">Gets a CorElementType value that describes the native type of the common language runtime (CLR) <xref:System.Type> represented by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64b91-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64b91-104">Syntax</span></span>  
  
```  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64b91-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="64b91-105">Parameters</span></span>  
 `ty`  
 <span data-ttu-id="64b91-106">[out] Ukazatel na hodnotu `CorElementType` výčet, který označuje CLR <xref:System.Type> , že tento `ICorDebugType` představuje.</span><span class="sxs-lookup"><span data-stu-id="64b91-106">[out] A pointer to a value of the `CorElementType` enumeration that indicates the CLR <xref:System.Type> that this `ICorDebugType` represents.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64b91-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="64b91-107">Remarks</span></span>  
 <span data-ttu-id="64b91-108">Pokud hodnota `ty` za řetězcem ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE, [icordebugtype::getclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) metoda může být volána k získání nevytvořeným instancím typu pro obecný typ; v opačném případě Nevolejte `ICorDebugType::GetClass`.</span><span class="sxs-lookup"><span data-stu-id="64b91-108">If the value of `ty` is either ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, the [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) method may be called to get the uninstantiated type for a generic type; otherwise, do not call `ICorDebugType::GetClass`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64b91-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="64b91-109">Requirements</span></span>  
 <span data-ttu-id="64b91-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64b91-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64b91-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64b91-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64b91-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64b91-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64b91-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64b91-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
