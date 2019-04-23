---
title: ICorDebugProcess6::DecodeEvent – metoda
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a392e236f180771a9b05526a0db569f27f6f7d8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59230743"
---
# <a name="icordebugprocess6decodeevent-method"></a><span data-ttu-id="21335-102">ICorDebugProcess6::DecodeEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="21335-102">ICorDebugProcess6::DecodeEvent Method</span></span>
<span data-ttu-id="21335-103">Dekóduje spravované ladění události, které byly zapouzdřené v datové části události speciálně nativní výjimka ladění.</span><span class="sxs-lookup"><span data-stu-id="21335-103">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21335-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21335-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="21335-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="21335-105">Parameters</span></span>  
 `pRecord`  
 <span data-ttu-id="21335-106">[in] Ukazatele na pole bajtů z nativní výjimka ladění události, která obsahuje informace o události spravované ladění.</span><span class="sxs-lookup"><span data-stu-id="21335-106">[in] A pointer to a byte array from a native exception debug event that includes information about a managed debug event.</span></span>  
  
 `countBytes`  
 <span data-ttu-id="21335-107">[in] Počet prvků v `pRecord` bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="21335-107">[in] The number of elements in the `pRecord` byte array.</span></span>  
  
 `format`  
 <span data-ttu-id="21335-108">[in] A [CorDebugRecordFormat](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md) člen výčtu, která určují formát nespravované ladění událostí.</span><span class="sxs-lookup"><span data-stu-id="21335-108">[in] A [CorDebugRecordFormat](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md) enumeration member that specifies the format of the unmanaged debug event.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="21335-109">[in] Bitové pole, která závisí na Cílová architektura a který určuje další informace o ladění události.</span><span class="sxs-lookup"><span data-stu-id="21335-109">[in] A bit field that depends on the target architecture and that specifies additional information about the debug event.</span></span> <span data-ttu-id="21335-110">Pro systémy Windows, může být členem skupiny [CorDebugDecodeEventFlagsWindows](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="21335-110">For Windows systems, it can be a member of the [CorDebugDecodeEventFlagsWindows](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md) enumeration.</span></span>  
  
 `dwThreadId`  
 <span data-ttu-id="21335-111">[in] Operační systém identifikátor vlákna, na kterém byla výjimka vydána.</span><span class="sxs-lookup"><span data-stu-id="21335-111">[in] The operating system identifier of the thread on which the exception was thrown.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="21335-112">[out] Ukazatel na adresu [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) objekt, který představuje událost dekódovaný spravované ladění.</span><span class="sxs-lookup"><span data-stu-id="21335-112">[out] A pointer to the address of an [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) object that represents a decoded managed debug event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21335-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="21335-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21335-114">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="21335-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21335-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="21335-115">Requirements</span></span>  
 <span data-ttu-id="21335-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21335-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21335-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21335-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21335-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21335-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21335-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21335-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21335-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="21335-120">See also</span></span>

- [<span data-ttu-id="21335-121">ICorDebugProcess6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21335-121">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="21335-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="21335-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
