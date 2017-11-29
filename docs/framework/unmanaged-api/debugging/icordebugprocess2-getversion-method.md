---
title: "ICorDebugProcess2::GetVersion – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.GetVersion
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::GetVersion
helpviewer_keywords:
- GetVersion method, ICorDebugProcess2 nterface [.NET Framework debugging]
- ICorDebugProcess2::GetVersion method [.NET Framework debugging]
ms.assetid: e11d5a75-61d9-4548-aedf-79c26079bd17
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 84db785d47f97fe058b8a66070bcf4757fa11517
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocess2getversion-method"></a><span data-ttu-id="6113d-102">ICorDebugProcess2::GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="6113d-102">ICorDebugProcess2::GetVersion Method</span></span>
<span data-ttu-id="6113d-103">Získá číslo verze common language runtime (CLR), který běží v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="6113d-103">Gets the version number of the common language runtime (CLR) that is running in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6113d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6113d-104">Syntax</span></span>  
  
```  
HRESULT GetVersion (  
    [out] COR_VERSION     *version  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6113d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6113d-105">Parameters</span></span>  
 `version`  
 <span data-ttu-id="6113d-106">[out] Ukazatel na cor_version – struktura, která ukládá číslo verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="6113d-106">[out] A pointer to a COR_VERSION structure that stores the version number of the runtime.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6113d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6113d-107">Remarks</span></span>  
 <span data-ttu-id="6113d-108">`GetVersion` Metoda vrátí kód chyby, pokud byl načten žádné runtime v procesu.</span><span class="sxs-lookup"><span data-stu-id="6113d-108">The `GetVersion` method returns an error code if no runtime has been loaded in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6113d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6113d-109">Requirements</span></span>  
 <span data-ttu-id="6113d-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6113d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6113d-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6113d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6113d-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6113d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6113d-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6113d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
