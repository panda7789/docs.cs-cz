---
title: ICorDebugHeapValue2::CreateHandle – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2.CreateHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type:
- apiref
ms.openlocfilehash: b9eab1274f2d0ad562c0dec6adeddb85c6cfc458
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138381"
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="8c982-102">ICorDebugHeapValue2::CreateHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="8c982-102">ICorDebugHeapValue2::CreateHandle Method</span></span>
<span data-ttu-id="8c982-103">Vytvoří popisovač zadaného typu pro hodnotu haldy reprezentované tímto objektem ICorDebugHeapValue2.</span><span class="sxs-lookup"><span data-stu-id="8c982-103">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c982-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c982-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c982-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c982-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="8c982-106">pro Hodnota výčtu CorDebugHandleType –, která určuje typ popisovače, který má být vytvořen.</span><span class="sxs-lookup"><span data-stu-id="8c982-106">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="8c982-107">mimo Ukazatel na adresu objektu ICorDebugHandleValue, který představuje nový popisovač pro tuto hodnotu haldy.</span><span class="sxs-lookup"><span data-stu-id="8c982-107">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c982-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c982-108">Remarks</span></span>  
 <span data-ttu-id="8c982-109">Popisovač bude vytvořen v doméně aplikace, která je přidružena k hodnotě haldy, a stane se neplatným, pokud se doména aplikace uvolní.</span><span class="sxs-lookup"><span data-stu-id="8c982-109">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="8c982-110">Více volání této funkce pro stejnou hodnotu haldy vytvoří více popisovačů.</span><span class="sxs-lookup"><span data-stu-id="8c982-110">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="8c982-111">Vzhledem k tomu, že obslužné rutiny ovlivňují výkon uvolňování paměti, by měl ladicí program omezit na poměrně malý počet popisovačů (přibližně 256), které jsou aktivní v čase.</span><span class="sxs-lookup"><span data-stu-id="8c982-111">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c982-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c982-112">Requirements</span></span>  
 <span data-ttu-id="8c982-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c982-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c982-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8c982-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c982-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8c982-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c982-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c982-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
