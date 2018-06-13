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
ms.openlocfilehash: c598491acd27223a8a41234ddf2c6b8e6f005d52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423140"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a><span data-ttu-id="b7a99-102">ICorDebugProcess5::EnableNGENPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="b7a99-102">ICorDebugProcess5::EnableNGENPolicy Method</span></span>
<span data-ttu-id="b7a99-103">Nastaví hodnotu, která určuje, jak aplikace načte nativní bitové kopie při spuštění pod spravované ladicí program.</span><span class="sxs-lookup"><span data-stu-id="b7a99-103">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7a99-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7a99-104">Syntax</span></span>  
  
```  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7a99-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7a99-105">Parameters</span></span>  
 `ePolicy`  
 <span data-ttu-id="b7a99-106">[v] A [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) konstanta, která určuje, jak aplikace načte nativní bitové kopie při spuštění pod spravované ladicí program.</span><span class="sxs-lookup"><span data-stu-id="b7a99-106">[in] A [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) constant that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7a99-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b7a99-107">Remarks</span></span>  
 <span data-ttu-id="b7a99-108">Pokud je zásada nastavená úspěšně, vrátí metoda `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="b7a99-108">If the policy is set successfully, the method returns `S_OK`.</span></span> <span data-ttu-id="b7a99-109">Pokud `ePolicy` je mimo rozsah výčtové hodnoty definované [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), vrátí metoda `E_INVALIDARG` a volání metody, které nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="b7a99-109">If `ePolicy` is outside the range of the enumerated values defined by [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), the method returns `E_INVALIDARG` and the method call has no effect.</span></span> <span data-ttu-id="b7a99-110">Pokud nelze aktualizovat zásady generátor (Ngen.exe), vrátí metoda `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="b7a99-110">If the policy of the Native Image Generator (Ngen.exe) cannot be updated, the method returns `E_FAIL`.</span></span>  
  
 <span data-ttu-id="b7a99-111">`ICorDebugProcess5::EnableNGenPolicy` Nelze volat metodu v průběhu životního cyklu procesu.</span><span class="sxs-lookup"><span data-stu-id="b7a99-111">The `ICorDebugProcess5::EnableNGenPolicy` method can be called at any time during the lifetime of the process.</span></span> <span data-ttu-id="b7a99-112">Pro všechny moduly, které jsou načteny po nastavení zásad platí zásady.</span><span class="sxs-lookup"><span data-stu-id="b7a99-112">The policy is in effect for any modules that are loaded after the policy is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7a99-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7a99-113">Requirements</span></span>  
 <span data-ttu-id="b7a99-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7a99-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7a99-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7a99-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7a99-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7a99-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7a99-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7a99-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7a99-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7a99-118">See Also</span></span>  
 [<span data-ttu-id="b7a99-119">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7a99-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="b7a99-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b7a99-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b7a99-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="b7a99-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
