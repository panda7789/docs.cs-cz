---
title: "ICorDebugProcess6::DecodeEvent – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c0186fb91a4c47f1988af58577cee1b7a64987a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess6decodeevent-method"></a><span data-ttu-id="e1e24-102">ICorDebugProcess6::DecodeEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="e1e24-102">ICorDebugProcess6::DecodeEvent Method</span></span>
<span data-ttu-id="e1e24-103">Dekóduje spravované ladění události, které byly zapouzdřené v datové části události ladění speciálního nativní výjimky.</span><span class="sxs-lookup"><span data-stu-id="e1e24-103">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1e24-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1e24-104">Syntax</span></span>  
  
```  
HRESULT DecodeEvent(  
        [in, length_is(countBytes), size_is(countBytes)]  const BYTE pRecord[],  
        [in] DWORD countBytes,  
        [in] CorDebugRecordFormat format,  
        [in] DWORD dwFlags,   
        [in] DWORD dwThreadId,   
        [out] ICorDebugDebugEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1e24-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1e24-105">Parameters</span></span>  
 `pRecord`  
 <span data-ttu-id="e1e24-106">[v] Ukazatel na bajtové pole z události ladění nativní výjimky, které obsahují informace o události spravovaného ladění.</span><span class="sxs-lookup"><span data-stu-id="e1e24-106">[in] A pointer to a byte array from a native exception debug event that includes information about a managed debug event.</span></span>  
  
 `countBytes`  
 <span data-ttu-id="e1e24-107">[v] Počet elementů ve `pRecord` bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="e1e24-107">[in] The number of elements in the `pRecord` byte array.</span></span>  
  
 `format`  
 <span data-ttu-id="e1e24-108">[v] A [CorDebugRecordFormat](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md) člen výčtu, která určují formát nespravované ladění událostí.</span><span class="sxs-lookup"><span data-stu-id="e1e24-108">[in] A [CorDebugRecordFormat](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md) enumeration member that specifies the format of the unmanaged debug event.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e1e24-109">[v] Bitová pole, závisí na cílové architektury a který určuje další informace o ladění událostí.</span><span class="sxs-lookup"><span data-stu-id="e1e24-109">[in] A bit field that depends on the target architecture and that specifies additional information about the debug event.</span></span> <span data-ttu-id="e1e24-110">Pro systémy Windows, může být členem skupiny [CorDebugDecodeEventFlagsWindows](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="e1e24-110">For Windows systems, it can be a member of the [CorDebugDecodeEventFlagsWindows](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md) enumeration.</span></span>  
  
 `dwThreadId`  
 <span data-ttu-id="e1e24-111">[v] Identifikátor operačního systému vláken, na kterém byla výjimka vydána.</span><span class="sxs-lookup"><span data-stu-id="e1e24-111">[in] The operating system identifier of the thread on which the exception was thrown.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="e1e24-112">[out] Ukazatel na adresu [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) objekt, který reprezentuje dekódované spravované ladění událostí.</span><span class="sxs-lookup"><span data-stu-id="e1e24-112">[out] A pointer to the address of an [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) object that represents a decoded managed debug event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1e24-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e1e24-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1e24-114">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="e1e24-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1e24-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e1e24-115">Requirements</span></span>  
 <span data-ttu-id="e1e24-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1e24-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1e24-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1e24-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1e24-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1e24-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1e24-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1e24-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1e24-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1e24-120">See Also</span></span>  
 [<span data-ttu-id="e1e24-121">Rozhraní ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="e1e24-121">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="e1e24-122">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="e1e24-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
