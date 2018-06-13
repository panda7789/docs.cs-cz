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
ms.openlocfilehash: 6f5cbb7c0b4e3ce6d66d30e812008fc3419d7d7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429089"
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="be0c8-102">IAssemblyCacheItem::Commit – metoda</span><span class="sxs-lookup"><span data-stu-id="be0c8-102">IAssemblyCacheItem::Commit Method</span></span>
<span data-ttu-id="be0c8-103">Potvrdí odkaz na sestavení v mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="be0c8-103">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be0c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be0c8-104">Syntax</span></span>  
  
```  
HRESULT Commit (  
    [in] DWORD dwFlags,   
    [out, optional] ULONG *pulDisposition  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be0c8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="be0c8-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="be0c8-106">[v] Příznaky definované v Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="be0c8-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="be0c8-107">[na víc systémů, volitelné] Hodnota, která určuje výsledek operace.</span><span class="sxs-lookup"><span data-stu-id="be0c8-107">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be0c8-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="be0c8-108">Requirements</span></span>  
 <span data-ttu-id="be0c8-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be0c8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be0c8-110">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="be0c8-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="be0c8-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be0c8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be0c8-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="be0c8-112">See Also</span></span>  
 [<span data-ttu-id="be0c8-113">IAssemblyCacheItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="be0c8-113">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
