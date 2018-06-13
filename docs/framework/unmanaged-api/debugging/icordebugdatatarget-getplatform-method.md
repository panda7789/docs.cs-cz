---
title: ICorDebugDataTarget::GetPlatform – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetPlatform Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetPlatform
helpviewer_keywords:
- GetPlatform method [.NET Framework debugging]
- ICorDebugDataTarget::GetPlatform method [.NET Framework debugging]
ms.assetid: 9ee96c9d-7a3d-4129-a6cc-7675c7f2dda4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17ae761b2d48552aded8191ddbea26552d8da277
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411015"
---
# <a name="icordebugdatatargetgetplatform-method"></a><span data-ttu-id="2fa41-102">ICorDebugDataTarget::GetPlatform – metoda</span><span class="sxs-lookup"><span data-stu-id="2fa41-102">ICorDebugDataTarget::GetPlatform Method</span></span>
<span data-ttu-id="2fa41-103">Poskytuje informace o platformě, včetně architekturu procesoru a operačního systému, na kterém je tento cílový proces běží.</span><span class="sxs-lookup"><span data-stu-id="2fa41-103">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fa41-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fa41-104">Syntax</span></span>  
  
```  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2fa41-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2fa41-105">Parameters</span></span>  
 `pTargetPlatform`  
 <span data-ttu-id="2fa41-106">[out] Ukazatel [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) výčet, který popisuje cílové platformy.</span><span class="sxs-lookup"><span data-stu-id="2fa41-106">[out] A pointer to a [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeration that describes the target platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fa41-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2fa41-107">Remarks</span></span>  
 <span data-ttu-id="2fa41-108">`CorDebugPlatformEnum` Návratová hodnota výčtu je používán [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) rozhraní zjistěte informace o procesu cíl například velikost ukazatele, rozložení prostoru adres, registrace sady, formát instrukce, kontext rozložení a konvence volání.</span><span class="sxs-lookup"><span data-stu-id="2fa41-108">The `CorDebugPlatformEnum` enumeration return value is used by the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface to determine details of the target process such as its pointer size, address space layout, register set, instruction format, context layout, and calling conventions.</span></span>  
  
 <span data-ttu-id="2fa41-109">`pTargetPlatform` Hodnotu mohou odkazovat na platformu, která je emulovaných pro cílové místo zadání skutečné hardwarové používán.</span><span class="sxs-lookup"><span data-stu-id="2fa41-109">The `pTargetPlatform` value may refer to a platform that is being emulated for the target instead of specifying the actual hardware in use.</span></span> <span data-ttu-id="2fa41-110">Například by měl použít procesu, který je spuštěn v systému Windows v prostředí systému Windows (WOW) v 64bitové edici operačního systému Windows `CORDB_PLATFORM_WINDOWS_X86` hodnotu [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="2fa41-110">For example, a process that is running in the Windows on Windows (WOW) environment on a 64-bit edition of the Windows operating system should use the `CORDB_PLATFORM_WINDOWS_X86` value of the [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="2fa41-111">Tato metoda musí být úspěšné.</span><span class="sxs-lookup"><span data-stu-id="2fa41-111">This method must succeed.</span></span> <span data-ttu-id="2fa41-112">Pokud se nezdaří, nepoužitelná cílové platformy.</span><span class="sxs-lookup"><span data-stu-id="2fa41-112">If it fails, the target platform is unusable.</span></span> <span data-ttu-id="2fa41-113">Metoda může selhat z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="2fa41-113">The method may fail for the following reasons:</span></span>  
  
-   <span data-ttu-id="2fa41-114">Platforma, která je emulovaných pro cíl nepoužitelný.</span><span class="sxs-lookup"><span data-stu-id="2fa41-114">The platform that is being emulated for the target is unusable.</span></span>  
  
-   <span data-ttu-id="2fa41-115">Skutečné hardwarové na cílové platformy nepoužitelný.</span><span class="sxs-lookup"><span data-stu-id="2fa41-115">The actual hardware on the target platform is unusable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fa41-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2fa41-116">Requirements</span></span>  
 <span data-ttu-id="2fa41-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fa41-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fa41-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2fa41-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fa41-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fa41-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fa41-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fa41-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fa41-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="2fa41-121">See Also</span></span>  
 [<span data-ttu-id="2fa41-122">ICorDebugDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2fa41-122">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [<span data-ttu-id="2fa41-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2fa41-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="2fa41-124">Ladění</span><span class="sxs-lookup"><span data-stu-id="2fa41-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
