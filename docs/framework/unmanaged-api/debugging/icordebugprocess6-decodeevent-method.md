---
title: ICorDebugProcess6::DecodeEvent – metoda
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
ms.openlocfilehash: 7c163311f9ce8f3d98ce72f45165a5e517c6c0aa
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205505"
---
# <a name="icordebugprocess6decodeevent-method"></a><span data-ttu-id="ce886-102">ICorDebugProcess6::DecodeEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="ce886-102">ICorDebugProcess6::DecodeEvent Method</span></span>
<span data-ttu-id="ce886-103">Dekóduje spravované události ladění, které byly zapouzdřeny v datové části speciálně vytvořené nativní výjimky ladění.</span><span class="sxs-lookup"><span data-stu-id="ce886-103">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce886-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce886-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ce886-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce886-105">Parameters</span></span>  
 `pRecord`  
 <span data-ttu-id="ce886-106">pro Ukazatel na pole bajtů z nativní události ladění výjimky, která obsahuje informace o spravované události ladění.</span><span class="sxs-lookup"><span data-stu-id="ce886-106">[in] A pointer to a byte array from a native exception debug event that includes information about a managed debug event.</span></span>  
  
 `countBytes`  
 <span data-ttu-id="ce886-107">pro Počet prvků v `pRecord` bajtovém poli.</span><span class="sxs-lookup"><span data-stu-id="ce886-107">[in] The number of elements in the `pRecord` byte array.</span></span>  
  
 `format`  
 <span data-ttu-id="ce886-108">pro Člen výčtu [CorDebugRecordFormat](cordebugrecordformat-enumeration.md) , který určuje formát nespravované události ladění.</span><span class="sxs-lookup"><span data-stu-id="ce886-108">[in] A [CorDebugRecordFormat](cordebugrecordformat-enumeration.md) enumeration member that specifies the format of the unmanaged debug event.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ce886-109">pro Bitové pole, které závisí na cílové architektuře a které určuje další informace o události ladění.</span><span class="sxs-lookup"><span data-stu-id="ce886-109">[in] A bit field that depends on the target architecture and that specifies additional information about the debug event.</span></span> <span data-ttu-id="ce886-110">Pro systémy Windows může být členem výčtu [CorDebugDecodeEventFlagsWindows](cordebugdecodeeventflagswindows-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="ce886-110">For Windows systems, it can be a member of the [CorDebugDecodeEventFlagsWindows](cordebugdecodeeventflagswindows-enumeration.md) enumeration.</span></span>  
  
 `dwThreadId`  
 <span data-ttu-id="ce886-111">pro Identifikátor operačního systému vlákna, na kterém byla výjimka vyvolána.</span><span class="sxs-lookup"><span data-stu-id="ce886-111">[in] The operating system identifier of the thread on which the exception was thrown.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="ce886-112">mimo Ukazatel na adresu objektu [ICorDebugDebugEvent](icordebugdebugevent-interface.md) , který představuje dekódovou spravovanou událost ladění.</span><span class="sxs-lookup"><span data-stu-id="ce886-112">[out] A pointer to the address of an [ICorDebugDebugEvent](icordebugdebugevent-interface.md) object that represents a decoded managed debug event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce886-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ce886-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce886-114">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ce886-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce886-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ce886-115">Requirements</span></span>  
 <span data-ttu-id="ce886-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce886-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce886-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ce886-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce886-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ce886-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce886-119">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce886-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce886-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce886-120">See also</span></span>

- [<span data-ttu-id="ce886-121">Rozhraní ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="ce886-121">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="ce886-122">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ce886-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
