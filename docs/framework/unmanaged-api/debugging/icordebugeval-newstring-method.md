---
title: "ICorDebugEval::NewString – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.NewString
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 48c1a36e32feb94e8399c46f88a98f75c81fdb6a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="930b3-102">ICorDebugEval::NewString – metoda</span><span class="sxs-lookup"><span data-stu-id="930b3-102">ICorDebugEval::NewString Method</span></span>
<span data-ttu-id="930b3-103">Přiděluje do nové instance řetězec s zadaný obsah.</span><span class="sxs-lookup"><span data-stu-id="930b3-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="930b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="930b3-104">Syntax</span></span>  
  
```  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="930b3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="930b3-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="930b3-106">[v] Ukazatel na obsah pro řetězec.</span><span class="sxs-lookup"><span data-stu-id="930b3-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="930b3-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="930b3-107">Remarks</span></span>  
 <span data-ttu-id="930b3-108">Řetězec se vždy vytvoří v doméně aplikace, ve kterém je aktuálně spuštěných vlákno.</span><span class="sxs-lookup"><span data-stu-id="930b3-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="930b3-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="930b3-109">Requirements</span></span>  
 <span data-ttu-id="930b3-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="930b3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="930b3-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="930b3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="930b3-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="930b3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="930b3-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="930b3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
