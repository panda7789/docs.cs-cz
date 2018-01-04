---
title: "ICorDebugProcess5::EnableNGENPolicy – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5::EnableNGenPolicy
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dca0df7b0be643d53bb5b9a03bd3abbb186d69dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5enablengenpolicy-method"></a><span data-ttu-id="ee45b-102">ICorDebugProcess5::EnableNGENPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="ee45b-102">ICorDebugProcess5::EnableNGENPolicy Method</span></span>
<span data-ttu-id="ee45b-103">Nastaví hodnotu, která určuje, jak aplikace načte nativní bitové kopie při spuštění pod spravované ladicí program.</span><span class="sxs-lookup"><span data-stu-id="ee45b-103">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee45b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee45b-104">Syntax</span></span>  
  
```  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ee45b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ee45b-105">Parameters</span></span>  
 `ePolicy`  
 <span data-ttu-id="ee45b-106">[v] A [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) konstanta, která určuje, jak aplikace načte nativní bitové kopie při spuštění pod spravované ladicí program.</span><span class="sxs-lookup"><span data-stu-id="ee45b-106">[in] A [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) constant that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee45b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ee45b-107">Remarks</span></span>  
 <span data-ttu-id="ee45b-108">Pokud je zásada nastavená úspěšně, vrátí metoda `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="ee45b-108">If the policy is set successfully, the method returns `S_OK`.</span></span> <span data-ttu-id="ee45b-109">Pokud `ePolicy` je mimo rozsah výčtové hodnoty definované [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), vrátí metoda `E_INVALIDARG` a volání metody, které nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="ee45b-109">If `ePolicy` is outside the range of the enumerated values defined by [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), the method returns `E_INVALIDARG` and the method call has no effect.</span></span> <span data-ttu-id="ee45b-110">Pokud nelze aktualizovat zásady generátor (Ngen.exe), vrátí metoda `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="ee45b-110">If the policy of the Native Image Generator (Ngen.exe) cannot be updated, the method returns `E_FAIL`.</span></span>  
  
 <span data-ttu-id="ee45b-111">`ICorDebugProcess5::EnableNGenPolicy` Nelze volat metodu v průběhu životního cyklu procesu.</span><span class="sxs-lookup"><span data-stu-id="ee45b-111">The `ICorDebugProcess5::EnableNGenPolicy` method can be called at any time during the lifetime of the process.</span></span> <span data-ttu-id="ee45b-112">Pro všechny moduly, které jsou načteny po nastavení zásad platí zásady.</span><span class="sxs-lookup"><span data-stu-id="ee45b-112">The policy is in effect for any modules that are loaded after the policy is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee45b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ee45b-113">Requirements</span></span>  
 <span data-ttu-id="ee45b-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee45b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee45b-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee45b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee45b-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee45b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee45b-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee45b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee45b-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee45b-118">See Also</span></span>  
 [<span data-ttu-id="ee45b-119">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ee45b-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="ee45b-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ee45b-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="ee45b-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="ee45b-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
