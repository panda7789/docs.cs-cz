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
ms.openlocfilehash: d881a1fe3965b6e1d89e6172c887061434cd52ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418715"
---
# <a name="icordebugtypegettype-method"></a><span data-ttu-id="c0dec-102">ICorDebugType::GetType – metoda</span><span class="sxs-lookup"><span data-stu-id="c0dec-102">ICorDebugType::GetType Method</span></span>
<span data-ttu-id="c0dec-103">Získá hodnotu CorElementType, která popisuje typ nativní common language runtime (CLR) <xref:System.Type> reprezentována tento ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="c0dec-103">Gets a CorElementType value that describes the native type of the common language runtime (CLR) <xref:System.Type> represented by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0dec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0dec-104">Syntax</span></span>  
  
```  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c0dec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c0dec-105">Parameters</span></span>  
 `ty`  
 <span data-ttu-id="c0dec-106">[out] Ukazatel na hodnotu `CorElementType` výčet, který označuje modulu CLR <xref:System.Type> které tento `ICorDebugType` představuje.</span><span class="sxs-lookup"><span data-stu-id="c0dec-106">[out] A pointer to a value of the `CorElementType` enumeration that indicates the CLR <xref:System.Type> that this `ICorDebugType` represents.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0dec-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c0dec-107">Remarks</span></span>  
 <span data-ttu-id="c0dec-108">Pokud hodnota `ty` ELEMENT_TYPE_CLASS nebo Typ ELEMENT_TYPE_VALUETYPE, který, [icordebugtype::getclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) metoda může být volána k získání bez instancí typu pro obecný typ; jinak, nevolejte `ICorDebugType::GetClass`.</span><span class="sxs-lookup"><span data-stu-id="c0dec-108">If the value of `ty` is either ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, the [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) method may be called to get the uninstantiated type for a generic type; otherwise, do not call `ICorDebugType::GetClass`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0dec-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c0dec-109">Requirements</span></span>  
 <span data-ttu-id="c0dec-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0dec-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0dec-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0dec-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0dec-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0dec-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0dec-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0dec-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
