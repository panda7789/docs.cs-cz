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
ms.openlocfilehash: acfb8910df6e20bf55ed33fdbb9b1c30d22f4684
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412049"
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="d4e4a-102">ICorDebugFunction::GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="d4e4a-102">ICorDebugFunction::GetToken Method</span></span>
<span data-ttu-id="d4e4a-103">Získá token metadata pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="d4e4a-103">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4e4a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4e4a-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4e4a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4e4a-105">Parameters</span></span>  
 `pMethodDef`  
 <span data-ttu-id="d4e4a-106">[out] Ukazatel na `mdMethodDef` token, který odkazuje na metadata pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="d4e4a-106">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4e4a-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d4e4a-107">Requirements</span></span>  
 <span data-ttu-id="d4e4a-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4e4a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4e4a-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4e4a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4e4a-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4e4a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4e4a-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4e4a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
