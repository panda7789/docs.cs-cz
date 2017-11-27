---
title: "ICorDebugValue3::GetSize64 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue3::GetSize64
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue3::GetSize64
helpviewer_keywords:
- GetSize64 method, ICorDebugValue3 interface [.NET Framework debugging]
- ICorDebugValue3::GetSize64 method [.NET Framework debugging]
ms.assetid: fee56a29-3154-4192-958d-71da2ced3740
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b129ebe666972052775c2c3e44e38bb6a25a176e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvalue3getsize64-method"></a><span data-ttu-id="80ae4-102">ICorDebugValue3::GetSize64 – metoda</span><span class="sxs-lookup"><span data-stu-id="80ae4-102">ICorDebugValue3::GetSize64 Method</span></span>
<span data-ttu-id="80ae4-103">Získá velikost v bajtech to [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="80ae4-103">Gets the size, in bytes, of this [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80ae4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80ae4-104">Syntax</span></span>  
  
```  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80ae4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80ae4-105">Parameters</span></span>  
 <span data-ttu-id="80ae4-106">pSize</span><span class="sxs-lookup"><span data-stu-id="80ae4-106">pSize</span></span>  
 <span data-ttu-id="80ae4-107">[out] Ukazatel na velikost v bajtech tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="80ae4-107">[out] A pointer to the size, in bytes, of this object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80ae4-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="80ae4-108">Remarks</span></span>  
 <span data-ttu-id="80ae4-109">Pokud je tato hodnota typ typu odkazu, tato metoda vrátí velikost ukazatele spíše než velikost objektu.</span><span class="sxs-lookup"><span data-stu-id="80ae4-109">If this value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="80ae4-110">`ICorDebugValue3::GetSize` Metoda se liší od [icordebugvalue::getsize –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) metoda v typu jeho výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="80ae4-110">The `ICorDebugValue3::GetSize` method differs from the [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) method in the type of its output parameter.</span></span> <span data-ttu-id="80ae4-111">V [icordebugvalue::getsize –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md), je výstupní parametr `ULONG32`; v `ICorDebugValue3::GetSize`, je `ULONG64`.</span><span class="sxs-lookup"><span data-stu-id="80ae4-111">In [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md), the output parameter is a `ULONG32`; in `ICorDebugValue3::GetSize`, it is a `ULONG64`.</span></span> <span data-ttu-id="80ae4-112">Díky tomu [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) rozhraní tak, aby odesílaly velikost pole, které překračují 2 GB.</span><span class="sxs-lookup"><span data-stu-id="80ae4-112">This enables the [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) interface to report the size of arrays that exceed 2GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80ae4-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="80ae4-113">Requirements</span></span>  
 <span data-ttu-id="80ae4-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80ae4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80ae4-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="80ae4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80ae4-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80ae4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80ae4-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80ae4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80ae4-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="80ae4-118">See Also</span></span>  
 [<span data-ttu-id="80ae4-119">ICorDebugValue3 – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="80ae4-119">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 [<span data-ttu-id="80ae4-120">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="80ae4-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
