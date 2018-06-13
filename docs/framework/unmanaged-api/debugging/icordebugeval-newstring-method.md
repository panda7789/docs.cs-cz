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
ms.openlocfilehash: e5eb86bb80aea5fc65a7362467b78b16a59794d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412227"
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="a679e-102">ICorDebugEval::NewString – metoda</span><span class="sxs-lookup"><span data-stu-id="a679e-102">ICorDebugEval::NewString Method</span></span>
<span data-ttu-id="a679e-103">Přiděluje do nové instance řetězec s zadaný obsah.</span><span class="sxs-lookup"><span data-stu-id="a679e-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a679e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a679e-104">Syntax</span></span>  
  
```  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a679e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a679e-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="a679e-106">[v] Ukazatel na obsah pro řetězec.</span><span class="sxs-lookup"><span data-stu-id="a679e-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a679e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a679e-107">Remarks</span></span>  
 <span data-ttu-id="a679e-108">Řetězec se vždy vytvoří v doméně aplikace, ve kterém je aktuálně spuštěných vlákno.</span><span class="sxs-lookup"><span data-stu-id="a679e-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a679e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a679e-109">Requirements</span></span>  
 <span data-ttu-id="a679e-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a679e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a679e-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a679e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a679e-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a679e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a679e-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a679e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
