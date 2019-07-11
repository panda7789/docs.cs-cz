---
title: ICorDebugFrame::GetFunctionToken – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetFunctionToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunctionToken
helpviewer_keywords:
- ICorDebugFrame::GetFunctionToken method [.NET Framework debugging]
- GetFunctionToken method [.NET Framework debugging]
ms.assetid: a46925b3-3bf8-404f-9f30-a86ae41032c1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f50e5fcee3705e05aeed820cf736613c12b00e50
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754868"
---
# <a name="icordebugframegetfunctiontoken-method"></a><span data-ttu-id="68f43-102">ICorDebugFrame::GetFunctionToken – metoda</span><span class="sxs-lookup"><span data-stu-id="68f43-102">ICorDebugFrame::GetFunctionToken Method</span></span>
<span data-ttu-id="68f43-103">Získá token metadat pro funkci, která obsahuje kód spojený s rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="68f43-103">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68f43-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68f43-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionToken (  
    [out] mdMethodDef        *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68f43-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="68f43-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="68f43-106">[out] Ukazatel `mdMethodDef` token, který odkazuje na metadata pro funkci.</span><span class="sxs-lookup"><span data-stu-id="68f43-106">[out] A pointer to an `mdMethodDef` token that references the metadata for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68f43-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="68f43-107">Requirements</span></span>  
 <span data-ttu-id="68f43-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68f43-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68f43-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68f43-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68f43-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68f43-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68f43-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68f43-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
