---
title: Metoda ICorDebugAppDomain4::GetObjectForCCW
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: 50f46394c809321f0bd256e4c8d75b76fc7c2c70
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784852"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="64a23-102">Metoda ICorDebugAppDomain4::GetObjectForCCW</span><span class="sxs-lookup"><span data-stu-id="64a23-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="64a23-103">Načte spravovaný objekt z ukazatele na obálku s přívolatelné v modelu COM.</span><span class="sxs-lookup"><span data-stu-id="64a23-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64a23-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64a23-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64a23-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="64a23-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="64a23-106">pro Ukazatel na obálku s přívolatelné v modelu COM.</span><span class="sxs-lookup"><span data-stu-id="64a23-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="64a23-107">mimo Ukazatel na adresu objektu "ICorDebugValue", který představuje spravovaný objekt, který odpovídá zadanému ukazateli doleva.</span><span class="sxs-lookup"><span data-stu-id="64a23-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64a23-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="64a23-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64a23-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="64a23-109">Requirements</span></span>  
 <span data-ttu-id="64a23-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64a23-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64a23-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="64a23-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64a23-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="64a23-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64a23-113">**Verze .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64a23-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64a23-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64a23-114">See also</span></span>

- [<span data-ttu-id="64a23-115">ICorDebugAppDomain4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="64a23-115">ICorDebugAppDomain4 Interface</span></span>](icordebugappdomain4-interface.md)
- [<span data-ttu-id="64a23-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="64a23-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
