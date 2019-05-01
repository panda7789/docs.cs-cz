---
title: ICorDebugFunction::GetToken – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetToken
helpviewer_keywords:
- ICorDebugFunction::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: c6bbf479-062e-48e9-9c70-0f92e293e36a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e56c8eba49260eba9e3e0ca7e9ab4c7cfcd3261f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995628"
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="992d6-102">ICorDebugFunction::GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="992d6-102">ICorDebugFunction::GetToken Method</span></span>
<span data-ttu-id="992d6-103">Získá token metadat pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="992d6-103">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="992d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="992d6-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="992d6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="992d6-105">Parameters</span></span>  
 `pMethodDef`  
 <span data-ttu-id="992d6-106">[out] Ukazatel `mdMethodDef` token, který odkazuje na metadata pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="992d6-106">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="992d6-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="992d6-107">Requirements</span></span>  
 <span data-ttu-id="992d6-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="992d6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="992d6-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="992d6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="992d6-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="992d6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="992d6-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="992d6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
