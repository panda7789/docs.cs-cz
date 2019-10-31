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
ms.openlocfilehash: 5de522c00da76e7c01369c706cb7f9e2bdad4b3b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134520"
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="df6cc-102">IAssemblyCacheItem::Commit – metoda</span><span class="sxs-lookup"><span data-stu-id="df6cc-102">IAssemblyCacheItem::Commit Method</span></span>
<span data-ttu-id="df6cc-103">Potvrdí odkaz na sestavení v mezipaměti do paměti.</span><span class="sxs-lookup"><span data-stu-id="df6cc-103">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df6cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df6cc-104">Syntax</span></span>  
  
```cpp  
HRESULT Commit (  
    [in] DWORD dwFlags,   
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df6cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="df6cc-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="df6cc-106">pro Příznaky definované v Fusion. idl</span><span class="sxs-lookup"><span data-stu-id="df6cc-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="df6cc-107">[out, volitelné] Hodnota, která určuje výsledek operace.</span><span class="sxs-lookup"><span data-stu-id="df6cc-107">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df6cc-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="df6cc-108">Requirements</span></span>  
 <span data-ttu-id="df6cc-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df6cc-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df6cc-110">**Hlavička:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="df6cc-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="df6cc-111">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df6cc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df6cc-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="df6cc-112">See also</span></span>

- [<span data-ttu-id="df6cc-113">IAssemblyCacheItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="df6cc-113">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
