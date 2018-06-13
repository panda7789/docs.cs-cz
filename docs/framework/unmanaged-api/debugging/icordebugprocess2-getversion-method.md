---
title: ICorDebugProcess2::GetVersion – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetVersion
helpviewer_keywords:
- GetVersion method, ICorDebugProcess2 nterface [.NET Framework debugging]
- ICorDebugProcess2::GetVersion method [.NET Framework debugging]
ms.assetid: e11d5a75-61d9-4548-aedf-79c26079bd17
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1e1f850e85099a466c497a8fcc822bce9510f69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416377"
---
# <a name="icordebugprocess2getversion-method"></a><span data-ttu-id="c238f-102">ICorDebugProcess2::GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="c238f-102">ICorDebugProcess2::GetVersion Method</span></span>
<span data-ttu-id="c238f-103">Získá číslo verze common language runtime (CLR), který běží v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="c238f-103">Gets the version number of the common language runtime (CLR) that is running in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c238f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c238f-104">Syntax</span></span>  
  
```  
HRESULT GetVersion (  
    [out] COR_VERSION     *version  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c238f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c238f-105">Parameters</span></span>  
 `version`  
 <span data-ttu-id="c238f-106">[out] Ukazatel na cor_version – struktura, která ukládá číslo verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="c238f-106">[out] A pointer to a COR_VERSION structure that stores the version number of the runtime.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c238f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c238f-107">Remarks</span></span>  
 <span data-ttu-id="c238f-108">`GetVersion` Metoda vrátí kód chyby, pokud byl načten žádné runtime v procesu.</span><span class="sxs-lookup"><span data-stu-id="c238f-108">The `GetVersion` method returns an error code if no runtime has been loaded in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c238f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c238f-109">Requirements</span></span>  
 <span data-ttu-id="c238f-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c238f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c238f-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c238f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c238f-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c238f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c238f-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c238f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
