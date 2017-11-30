---
title: "IDebuggerInfo::IsDebuggerAttached – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebuggerInfo.IsDebuggerAttached
api_location: mscoree.dll
api_type: COM
f1_keywords: IsDebuggerAttached
helpviewer_keywords:
- IDebuggerInfo::IsDebuggerAttached method [.NET Framework hosting]
- IsDebuggerAttached method, IDebuggerInfo interface [.NET Framework hosting]
ms.assetid: 6e21872f-602f-411a-a423-bff5cdf27000
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a6e1f11939bc4f11b1fb49dc44f129176143fbca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="46f23-102">IDebuggerInfo::IsDebuggerAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="46f23-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="46f23-103">Získá hodnotu, která určuje, zda je pro tento proces připojen spravované ladicí program.</span><span class="sxs-lookup"><span data-stu-id="46f23-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46f23-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46f23-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="46f23-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="46f23-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="46f23-106">[out] Ukazatel na hodnotu, která je `true` Pokud spravovaných ladicí program je připojené k procesu, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="46f23-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46f23-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="46f23-107">Requirements</span></span>  
 <span data-ttu-id="46f23-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46f23-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46f23-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="46f23-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="46f23-110">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="46f23-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="46f23-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46f23-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46f23-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="46f23-112">See Also</span></span>  
 [<span data-ttu-id="46f23-113">Idebuggerinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46f23-113">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)
