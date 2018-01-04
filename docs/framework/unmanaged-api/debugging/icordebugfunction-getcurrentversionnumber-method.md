---
title: "ICorDebugFunction::GetCurrentVersionNumber – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction.GetCurrentVersionNumber
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction::GetCurrentVersionNumber
helpviewer_keywords:
- GetCurrentVersionNumber method [.NET Framework debugging]
- ICorDebugFunction::GetCurrentVersionNumber method [.NET Framework debugging]
ms.assetid: c3af1575-cbe6-457a-bc08-c53460edcbc8
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c230c8ca6da69b45d05b3319220eacfa6c1f212
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="fb91c-102">ICorDebugFunction::GetCurrentVersionNumber – metoda</span><span class="sxs-lookup"><span data-stu-id="fb91c-102">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>
<span data-ttu-id="fb91c-103">Získá číslo verze nejnovější úpravy provedené funkce představuje tento objekt ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="fb91c-103">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb91c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb91c-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb91c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb91c-105">Parameters</span></span>  
 `pnCurrentVersion`  
 <span data-ttu-id="fb91c-106">[out] Ukazatel na celočíselnou hodnotu, která je číslo verze nejnovější úpravy provedené v této funkce.</span><span class="sxs-lookup"><span data-stu-id="fb91c-106">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb91c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fb91c-107">Remarks</span></span>  
 <span data-ttu-id="fb91c-108">Číslo verze nejnovější úpravy provedené v této funkce může být větší než číslo verze funkce sám sebe.</span><span class="sxs-lookup"><span data-stu-id="fb91c-108">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="fb91c-109">Použijte buď [icordebugfunction2::getversionnumber –](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md) metoda nebo [icordebugcode::getversionnumber –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) metoda pro načtení číslo verze funkce.</span><span class="sxs-lookup"><span data-stu-id="fb91c-109">Use either the [ICorDebugFunction2::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb91c-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb91c-110">Requirements</span></span>  
 <span data-ttu-id="fb91c-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb91c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb91c-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb91c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb91c-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb91c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb91c-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb91c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
