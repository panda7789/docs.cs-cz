---
title: "ITypeName::GetModifiers – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ITypeName.GetModifiers
api_location: mscoree.dll
api_type: COM
f1_keywords: GetModifiers
helpviewer_keywords:
- ITypeName::GetModifiers method [.NET Framework hosting]
- GetModifiers method [.NET Framework hosting]
ms.assetid: 75508c55-3e09-4135-80da-cc811003fa82
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a7a6bfb8a8520d390844442665e4ba5feb4dcffb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="itypenamegetmodifiers-method"></a><span data-ttu-id="59d58-102">ITypeName::GetModifiers – metoda</span><span class="sxs-lookup"><span data-stu-id="59d58-102">ITypeName::GetModifiers Method</span></span>
<span data-ttu-id="59d58-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="59d58-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59d58-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59d58-104">Syntax</span></span>  
  
```  
HRESULT GetModifiers (  
    [in] DWORD           count,  
    [out] DWORD*         rgModifiers,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="59d58-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="59d58-105">Requirements</span></span>  
 <span data-ttu-id="59d58-106">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59d58-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59d58-107">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="59d58-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="59d58-108">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="59d58-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="59d58-109">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59d58-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59d58-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="59d58-110">See Also</span></span>  
 [<span data-ttu-id="59d58-111">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="59d58-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
