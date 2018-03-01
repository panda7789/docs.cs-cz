---
title: "ICorDebugChain::EnumerateFrames – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d9df99c239568948c04f61ca4ec5e2b9207930f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchainenumerateframes-method"></a><span data-ttu-id="bdbfe-102">ICorDebugChain::EnumerateFrames – metoda</span><span class="sxs-lookup"><span data-stu-id="bdbfe-102">ICorDebugChain::EnumerateFrames Method</span></span>
<span data-ttu-id="bdbfe-103">Získá enumerátor, který obsahuje všechny rámce zásobníku spravovaných v řetězu, počínaje nejnovější rámečku.</span><span class="sxs-lookup"><span data-stu-id="bdbfe-103">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdbfe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bdbfe-104">Syntax</span></span>  
  
```  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bdbfe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bdbfe-105">Parameters</span></span>  
 `ppFrames`  
 <span data-ttu-id="bdbfe-106">[out] Ukazatel na adresu ICorDebugFrameEnum objekt, který je enumerátor pro rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="bdbfe-106">[out] A pointer to the address of an ICorDebugFrameEnum object that is the enumerator for the stack frames.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdbfe-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bdbfe-107">Remarks</span></span>  
 <span data-ttu-id="bdbfe-108">Řetězu představuje zásobníku volání fyzické pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="bdbfe-108">The chain represents the physical call stack for the thread.</span></span>  
  
 <span data-ttu-id="bdbfe-109">`EnumerateFrames` Metoda by měla být volána pouze pro spravované řetězy.</span><span class="sxs-lookup"><span data-stu-id="bdbfe-109">The `EnumerateFrames` method should be called only for managed chains.</span></span> <span data-ttu-id="bdbfe-110">Rozhraní API pro ladění neposkytuje metody pro získání snímky obsažené v nespravované řetězy.</span><span class="sxs-lookup"><span data-stu-id="bdbfe-110">The debugging API does not provide methods for obtaining frames contained in unmanaged chains.</span></span> <span data-ttu-id="bdbfe-111">Ladicí program musí získat tyto informace používat jiným způsobem.</span><span class="sxs-lookup"><span data-stu-id="bdbfe-111">The debugger must use other means to obtain this information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdbfe-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bdbfe-112">Requirements</span></span>  
 <span data-ttu-id="bdbfe-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdbfe-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdbfe-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bdbfe-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bdbfe-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdbfe-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdbfe-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdbfe-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
