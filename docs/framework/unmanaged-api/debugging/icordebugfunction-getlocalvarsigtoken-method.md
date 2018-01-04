---
title: "ICorDebugFunction::GetLocalVarSigToken – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction.GetLocalVarSigToken
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction::GetLocalVarSigToken
helpviewer_keywords:
- ICorDebugFunction::GetLocalVarSigToken method [.NET Framework debugging]
- GetLocalVarSigToken method [.NET Framework debugging]
ms.assetid: 31e53494-bcc9-4981-91a4-f7e0f02cad48
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfd2998393429d26f4670edfeae44b83893f479d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunctiongetlocalvarsigtoken-method"></a><span data-ttu-id="69f29-102">ICorDebugFunction::GetLocalVarSigToken – metoda</span><span class="sxs-lookup"><span data-stu-id="69f29-102">ICorDebugFunction::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="69f29-103">Získá metadata pro místní proměnné podpis funkce, která je reprezentována tuto instanci ICorDebugFunction tokenu.</span><span class="sxs-lookup"><span data-stu-id="69f29-103">Gets the metadata token for the local variable signature of the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69f29-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69f29-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVarSigToken (  
    [out] mdSignature *pmdSig  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69f29-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="69f29-105">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="69f29-106">[out] Ukazatel `mdSignature` tokenu pro místní proměnné podpis této funkce nebo `mdSignatureNil`, pokud je tato funkce nemá žádné místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="69f29-106">[out] A pointer to the `mdSignature` token for the local variable signature of this function, or `mdSignatureNil`, if this function has no local variables.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69f29-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="69f29-107">Requirements</span></span>  
 <span data-ttu-id="69f29-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69f29-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69f29-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69f29-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69f29-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69f29-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69f29-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69f29-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
