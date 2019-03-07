---
title: ICorDebugEval::NewString – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db609bdee7975b6c067271f99529e2cf2240f720
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480179"
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="f8a6f-102">ICorDebugEval::NewString – metoda</span><span class="sxs-lookup"><span data-stu-id="f8a6f-102">ICorDebugEval::NewString Method</span></span>
<span data-ttu-id="f8a6f-103">Přidělí novou instanci řetězce se zadaným obsahem.</span><span class="sxs-lookup"><span data-stu-id="f8a6f-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8a6f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8a6f-104">Syntax</span></span>  
  
```  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8a6f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8a6f-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="f8a6f-106">[in] Ukazatel na obsah řetězce.</span><span class="sxs-lookup"><span data-stu-id="f8a6f-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8a6f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f8a6f-107">Remarks</span></span>  
 <span data-ttu-id="f8a6f-108">Řetězec se vždy vytvoří v aplikační doméně, ve které vlákno právě probíhá.</span><span class="sxs-lookup"><span data-stu-id="f8a6f-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8a6f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8a6f-109">Requirements</span></span>  
 <span data-ttu-id="f8a6f-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8a6f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8a6f-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8a6f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8a6f-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8a6f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8a6f-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8a6f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
