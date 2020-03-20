---
title: ICorDebugProcess6::DecodeEvent – metoda
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
ms.openlocfilehash: a0b77724a5a70461073d554a9794c5a904f6a363
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178585"
---
# <a name="icordebugprocess6decodeevent-method"></a><span data-ttu-id="edbe7-102">ICorDebugProcess6::DecodeEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="edbe7-102">ICorDebugProcess6::DecodeEvent Method</span></span>
<span data-ttu-id="edbe7-103">Dekóduje události spravovaného ladění, které byly zapouzdřeny v datové části speciálně vytvořených nativních událostí ladění výjimek.</span><span class="sxs-lookup"><span data-stu-id="edbe7-103">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edbe7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="edbe7-104">Syntax</span></span>  
  
```cpp  
HRESULT DecodeEvent(  
        [in, length_is(countBytes), size_is(countBytes)]  const BYTE pRecord[],  
        [in] DWORD countBytes,  
        [in] CorDebugRecordFormat format,  
        [in] DWORD dwFlags,
        [in] DWORD dwThreadId,
        [out] ICorDebugDebugEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="edbe7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="edbe7-105">Parameters</span></span>  
 `pRecord`  
 <span data-ttu-id="edbe7-106">[v] Ukazatel na bajtové pole z události ladění nativní výjimky, která obsahuje informace o události spravovaného ladění.</span><span class="sxs-lookup"><span data-stu-id="edbe7-106">[in] A pointer to a byte array from a native exception debug event that includes information about a managed debug event.</span></span>  
  
 `countBytes`  
 <span data-ttu-id="edbe7-107">[v] Počet prvků v `pRecord` poli bajtů.</span><span class="sxs-lookup"><span data-stu-id="edbe7-107">[in] The number of elements in the `pRecord` byte array.</span></span>  
  
 `format`  
 <span data-ttu-id="edbe7-108">[v] Člen výčtu [CorDebugRecordFormat,](cordebugrecordformat-enumeration.md) který určuje formát události nespravovaného ladění.</span><span class="sxs-lookup"><span data-stu-id="edbe7-108">[in] A [CorDebugRecordFormat](cordebugrecordformat-enumeration.md) enumeration member that specifies the format of the unmanaged debug event.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="edbe7-109">[v] Bitové pole, které závisí na cílové architektuře a určuje další informace o události ladění.</span><span class="sxs-lookup"><span data-stu-id="edbe7-109">[in] A bit field that depends on the target architecture and that specifies additional information about the debug event.</span></span> <span data-ttu-id="edbe7-110">Pro systémy Windows může být členem výčtu [CorDebugDecodeEventFlagsWindows.](cordebugdecodeeventflagswindows-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="edbe7-110">For Windows systems, it can be a member of the [CorDebugDecodeEventFlagsWindows](cordebugdecodeeventflagswindows-enumeration.md) enumeration.</span></span>  
  
 `dwThreadId`  
 <span data-ttu-id="edbe7-111">[v] Identifikátor operačního systému podprocesu, na kterém byla vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="edbe7-111">[in] The operating system identifier of the thread on which the exception was thrown.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="edbe7-112">[out] Ukazatel na adresu objektu [ICorDebugDebugEvent,](icordebugdebugevent-interface.md) který představuje dekódovanou událost spravovaného ladění.</span><span class="sxs-lookup"><span data-stu-id="edbe7-112">[out] A pointer to the address of an [ICorDebugDebugEvent](icordebugdebugevent-interface.md) object that represents a decoded managed debug event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edbe7-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="edbe7-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="edbe7-114">Tato metoda je k dispozici pouze s nativní .NET.</span><span class="sxs-lookup"><span data-stu-id="edbe7-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edbe7-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="edbe7-115">Requirements</span></span>  
 <span data-ttu-id="edbe7-116">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edbe7-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edbe7-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="edbe7-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="edbe7-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="edbe7-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="edbe7-119">**Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edbe7-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edbe7-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="edbe7-120">See also</span></span>

- [<span data-ttu-id="edbe7-121">Rozhraní ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="edbe7-121">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="edbe7-122">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="edbe7-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
