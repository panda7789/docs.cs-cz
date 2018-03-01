---
title: "IAssemblyCacheItem::Commit – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IAssemblyCacheItem.Commit
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::Commit
helpviewer_keywords:
- IAssemblyCacheItem::Commit method [.NET Framework fusion]
- Commit method, IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: c2321f17-f46f-4815-ae41-b28678753613
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3e1907fa3be4992573f84b4810f7504f3af78397
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="100aa-102">IAssemblyCacheItem::Commit – metoda</span><span class="sxs-lookup"><span data-stu-id="100aa-102">IAssemblyCacheItem::Commit Method</span></span>
<span data-ttu-id="100aa-103">Potvrdí odkaz na sestavení v mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="100aa-103">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="100aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="100aa-104">Syntax</span></span>  
  
```  
HRESULT Commit (  
    [in] DWORD dwFlags,   
    [out, optional] ULONG *pulDisposition  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="100aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="100aa-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="100aa-106">[v] Příznaky definované v Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="100aa-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="100aa-107">[na víc systémů, volitelné] Hodnota, která určuje výsledek operace.</span><span class="sxs-lookup"><span data-stu-id="100aa-107">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="100aa-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="100aa-108">Requirements</span></span>  
 <span data-ttu-id="100aa-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="100aa-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="100aa-110">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="100aa-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="100aa-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="100aa-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="100aa-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="100aa-112">See Also</span></span>  
 [<span data-ttu-id="100aa-113">IAssemblyCacheItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="100aa-113">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
