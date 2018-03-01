---
title: "IDebuggerInfo::IsDebuggerAttached – metoda"
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
- IDebuggerInfo.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IsDebuggerAttached
helpviewer_keywords:
- IDebuggerInfo::IsDebuggerAttached method [.NET Framework hosting]
- IsDebuggerAttached method, IDebuggerInfo interface [.NET Framework hosting]
ms.assetid: 6e21872f-602f-411a-a423-bff5cdf27000
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7c241af6b71591374d8ce8cc8d1610a8dce91b2e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="b3e81-102">IDebuggerInfo::IsDebuggerAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="b3e81-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="b3e81-103">Získá hodnotu, která určuje, zda je pro tento proces připojen spravované ladicí program.</span><span class="sxs-lookup"><span data-stu-id="b3e81-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3e81-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3e81-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b3e81-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b3e81-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="b3e81-106">[out] Ukazatel na hodnotu, která je `true` Pokud spravovaných ladicí program je připojené k procesu, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="b3e81-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3e81-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b3e81-107">Requirements</span></span>  
 <span data-ttu-id="b3e81-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3e81-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3e81-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b3e81-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3e81-110">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b3e81-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3e81-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3e81-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3e81-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3e81-112">See Also</span></span>  
 [<span data-ttu-id="b3e81-113">IDebuggerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3e81-113">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)
