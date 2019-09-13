---
title: 'ICorDebugExceptionDebugEvent:: GetFlags – metoda'
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb92deee21c63c935454ff7c7c4e70be6f770436
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894995"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="e7a1e-102">ICorDebugExceptionDebugEvent:: GetFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="e7a1e-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="e7a1e-103">Získá příznak označující, zda lze výjimku zachytit.</span><span class="sxs-lookup"><span data-stu-id="e7a1e-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7a1e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7a1e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7a1e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7a1e-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="e7a1e-106">mimo Ukazatel na hodnotu [CorDebugExceptionFlags –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) , která určuje, zda lze výjimku zachytit.</span><span class="sxs-lookup"><span data-stu-id="e7a1e-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7a1e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e7a1e-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7a1e-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e7a1e-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7a1e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e7a1e-109">Requirements</span></span>  
 <span data-ttu-id="e7a1e-110">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7a1e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7a1e-111">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e7a1e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7a1e-112">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7a1e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7a1e-113">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7a1e-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7a1e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7a1e-114">See also</span></span>

- [<span data-ttu-id="e7a1e-115">ICorDebugExceptionDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e7a1e-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="e7a1e-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e7a1e-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
