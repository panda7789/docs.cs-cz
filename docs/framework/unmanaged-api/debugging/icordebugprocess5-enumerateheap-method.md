---
title: ICorDebugProcess5::EnumerateHeap – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b404b7762e085eb44f0bd3b448fcee9eab9a3c3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103906"
---
# <a name="icordebugprocess5enumerateheap-method"></a><span data-ttu-id="b3f3d-102">ICorDebugProcess5::EnumerateHeap – metoda</span><span class="sxs-lookup"><span data-stu-id="b3f3d-102">ICorDebugProcess5::EnumerateHeap Method</span></span>
<span data-ttu-id="b3f3d-103">Získá enumerátor pro objekty na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="b3f3d-103">Gets an enumerator for the objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3f3d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3f3d-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3f3d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b3f3d-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="b3f3d-106">[out] Ukazatel na adresu [icordebugheapenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) rozhraní objektu, který je enumerátor pro objekty, které jsou umístěny na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="b3f3d-106">[out] A pointer to the address of an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object that is an enumerator for the objects that reside on the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3f3d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3f3d-107">Remarks</span></span>  
 <span data-ttu-id="b3f3d-108">Před voláním `ICorDebugProcess5::EnumerateHeap` metoda, měli byste zavolat [icordebugprocess5::getgcheapinformation –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metoda a zkoumat hodnoty `areGCStructuresValid` pole vráceného [cor_heapinfo –](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) Ujistěte se, že haldě uvolňování paměti v jejím aktuálním stavu vyčíslitelný objekt.</span><span class="sxs-lookup"><span data-stu-id="b3f3d-108">Before calling the `ICorDebugProcess5::EnumerateHeap` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="b3f3d-109">Kromě toho `ICorDebugProcess5::EnumerateHeap` vrátí `E_FAIL` Pokud připojíte příliš brzy během životnosti procesu před paměť, pro je přidělena spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="b3f3d-109">In addition, the `ICorDebugProcess5::EnumerateHeap` returns `E_FAIL` if you attach too early in the lifetime of the process, before memory for the managed heap is allocated.</span></span>  
  
 <span data-ttu-id="b3f3d-110">[Icordebugheapenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) objektu rozhraní je standardní výčet odvozený od icordebugenum – rozhraní, která umožňuje vytvořit výčet [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objekty.</span><span class="sxs-lookup"><span data-stu-id="b3f3d-110">The [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects.</span></span> <span data-ttu-id="b3f3d-111">Naplní tuto metodu [icordebugheapenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) objektu kolekce s [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instancí, které poskytují informace o všech objektech.</span><span class="sxs-lookup"><span data-stu-id="b3f3d-111">This method populates the [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) collection object with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about all objects.</span></span> <span data-ttu-id="b3f3d-112">Kolekce může zahrnovat také [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instancí, které poskytují informace o objektech, které nejsou žádné kořenem objektu, ale nebyla ještě shromažďuje systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b3f3d-112">The collection may also include [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about objects that are not rooted by any object but have not yet been collected by the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3f3d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b3f3d-113">Requirements</span></span>  
 <span data-ttu-id="b3f3d-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3f3d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3f3d-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b3f3d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3f3d-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3f3d-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b3f3d-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b3f3d-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b3f3d-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3f3d-118">See also</span></span>

- [<span data-ttu-id="b3f3d-119">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3f3d-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="b3f3d-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3f3d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
