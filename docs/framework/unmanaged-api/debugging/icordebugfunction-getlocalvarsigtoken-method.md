---
title: ICorDebugFunction::GetLocalVarSigToken – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetLocalVarSigToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetLocalVarSigToken
helpviewer_keywords:
- ICorDebugFunction::GetLocalVarSigToken method [.NET Framework debugging]
- GetLocalVarSigToken method [.NET Framework debugging]
ms.assetid: 31e53494-bcc9-4981-91a4-f7e0f02cad48
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a682999c888a93cef94162a8179673c862dc43ce
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476643"
---
# <a name="icordebugfunctiongetlocalvarsigtoken-method"></a><span data-ttu-id="d6ff8-102">ICorDebugFunction::GetLocalVarSigToken – metoda</span><span class="sxs-lookup"><span data-stu-id="d6ff8-102">ICorDebugFunction::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="d6ff8-103">Získá metadata pro místní proměnné podpis funkce, která je reprezentovaný touto instancí ICorDebugFunction token.</span><span class="sxs-lookup"><span data-stu-id="d6ff8-103">Gets the metadata token for the local variable signature of the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6ff8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6ff8-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVarSigToken (  
    [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6ff8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6ff8-105">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="d6ff8-106">[out] Ukazatel `mdSignature` token pro místní proměnné podpis této funkce nebo `mdSignatureNil`, pokud tato funkce nemá žádné místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="d6ff8-106">[out] A pointer to the `mdSignature` token for the local variable signature of this function, or `mdSignatureNil`, if this function has no local variables.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6ff8-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6ff8-107">Requirements</span></span>  
 <span data-ttu-id="d6ff8-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6ff8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6ff8-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d6ff8-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6ff8-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6ff8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6ff8-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6ff8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
