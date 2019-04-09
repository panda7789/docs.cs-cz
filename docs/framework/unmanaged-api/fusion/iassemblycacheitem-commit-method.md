---
title: IAssemblyCacheItem::Commit – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3757eee4c013ccf4f0f6d21ef64a92a5ffd70f19
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074310"
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="6f797-102">IAssemblyCacheItem::Commit – metoda</span><span class="sxs-lookup"><span data-stu-id="6f797-102">IAssemblyCacheItem::Commit Method</span></span>
<span data-ttu-id="6f797-103">Potvrzení odkaz na sestavení v mezipaměti na paměť.</span><span class="sxs-lookup"><span data-stu-id="6f797-103">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f797-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f797-104">Syntax</span></span>  
  
```  
HRESULT Commit (  
    [in] DWORD dwFlags,   
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f797-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f797-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="6f797-106">[in] Příznaky definované v Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="6f797-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="6f797-107">[out, volitelné] Hodnota, která určuje výsledek operace.</span><span class="sxs-lookup"><span data-stu-id="6f797-107">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f797-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6f797-108">Requirements</span></span>  
 <span data-ttu-id="6f797-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f797-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f797-110">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="6f797-110">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="6f797-111">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="6f797-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6f797-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6f797-112">See also</span></span>

- [<span data-ttu-id="6f797-113">IAssemblyCacheItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f797-113">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
