---
title: ICorDebugProcess5::EnableNGENPolicy – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 154243e45a41ec2ba8b02937794b372a0705d458
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219119"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a><span data-ttu-id="e6c19-102">ICorDebugProcess5::EnableNGENPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="e6c19-102">ICorDebugProcess5::EnableNGENPolicy Method</span></span>
<span data-ttu-id="e6c19-103">Nastaví hodnotu, která určuje, jak aplikace načítá nativních bitových kopií při spuštění v rámci spravovaného ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="e6c19-103">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6c19-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6c19-104">Syntax</span></span>  
  
```  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6c19-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e6c19-105">Parameters</span></span>  
 `ePolicy`  
 <span data-ttu-id="e6c19-106">[in] A [cordebugngenpolicy –](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) konstantu, která určuje, jak aplikace načítá nativních bitových kopií při spuštění v rámci spravovaného ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="e6c19-106">[in] A [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) constant that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6c19-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e6c19-107">Remarks</span></span>  
 <span data-ttu-id="e6c19-108">Pokud je zásada nastavená úspěšně, metoda vrátí `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="e6c19-108">If the policy is set successfully, the method returns `S_OK`.</span></span> <span data-ttu-id="e6c19-109">Pokud `ePolicy` je mimo rozsah výčtové hodnoty určené [cordebugngenpolicy –](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), vrátí metoda `E_INVALIDARG` a volání metody, které nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="e6c19-109">If `ePolicy` is outside the range of the enumerated values defined by [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), the method returns `E_INVALIDARG` and the method call has no effect.</span></span> <span data-ttu-id="e6c19-110">Pokud nelze aktualizovat zásady Native Image Generator (Ngen.exe), metoda vrátí `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="e6c19-110">If the policy of the Native Image Generator (Ngen.exe) cannot be updated, the method returns `E_FAIL`.</span></span>  
  
 <span data-ttu-id="e6c19-111">`ICorDebugProcess5::EnableNGenPolicy` Metodu lze volat kdykoli po celou dobu životnosti procesu.</span><span class="sxs-lookup"><span data-stu-id="e6c19-111">The `ICorDebugProcess5::EnableNGenPolicy` method can be called at any time during the lifetime of the process.</span></span> <span data-ttu-id="e6c19-112">Zásady platí pro všechny moduly, které jsou načteny po nastavení zásad.</span><span class="sxs-lookup"><span data-stu-id="e6c19-112">The policy is in effect for any modules that are loaded after the policy is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6c19-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e6c19-113">Requirements</span></span>  
 <span data-ttu-id="e6c19-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6c19-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6c19-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e6c19-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6c19-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6c19-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e6c19-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e6c19-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e6c19-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6c19-118">See also</span></span>

- [<span data-ttu-id="e6c19-119">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e6c19-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="e6c19-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e6c19-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e6c19-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="e6c19-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
