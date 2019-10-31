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
ms.openlocfilehash: 4229d567fc4ced5e3b78b390ced29fb9ea60f93b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137845"
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="ad56a-102">ICorDebugFunction::GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="ad56a-102">ICorDebugFunction::GetToken Method</span></span>
<span data-ttu-id="ad56a-103">Získá token metadat pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="ad56a-103">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad56a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad56a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad56a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad56a-105">Parameters</span></span>  
 `pMethodDef`  
 <span data-ttu-id="ad56a-106">mimo Ukazatel na token `mdMethodDef`, který odkazuje na metadata této funkce.</span><span class="sxs-lookup"><span data-stu-id="ad56a-106">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad56a-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad56a-107">Requirements</span></span>  
 <span data-ttu-id="ad56a-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad56a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad56a-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ad56a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad56a-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ad56a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad56a-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad56a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
