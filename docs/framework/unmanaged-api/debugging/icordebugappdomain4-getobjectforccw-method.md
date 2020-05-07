---
title: Metoda ICorDebugAppDomain4::GetObjectForCCW
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: a175a6b6c91c284348580e1d9dc9ef0c5f5fc5df
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895120"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="50e54-102">Metoda ICorDebugAppDomain4::GetObjectForCCW</span><span class="sxs-lookup"><span data-stu-id="50e54-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="50e54-103">Načte spravovaný objekt z ukazatele na obálku s přívolatelné v modelu COM.</span><span class="sxs-lookup"><span data-stu-id="50e54-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50e54-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50e54-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50e54-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="50e54-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="50e54-106">pro Ukazatel na obálku s přívolatelné v modelu COM.</span><span class="sxs-lookup"><span data-stu-id="50e54-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="50e54-107">mimo Ukazatel na adresu objektu "ICorDebugValue", který představuje spravovaný objekt, který odpovídá zadanému ukazateli doleva.</span><span class="sxs-lookup"><span data-stu-id="50e54-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50e54-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="50e54-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50e54-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="50e54-109">Requirements</span></span>  
 <span data-ttu-id="50e54-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50e54-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50e54-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="50e54-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50e54-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="50e54-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50e54-113">**Verze .NET Framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50e54-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50e54-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="50e54-114">See also</span></span>

- [<span data-ttu-id="50e54-115">Rozhraní ICorDebugAppDomain4</span><span class="sxs-lookup"><span data-stu-id="50e54-115">ICorDebugAppDomain4 Interface</span></span>](icordebugappdomain4-interface.md)
- [<span data-ttu-id="50e54-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="50e54-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
