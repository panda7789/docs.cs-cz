---
title: "ComCallUnmarshal – třída typu coclass"
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
- ComCallUnmarshal Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ComCallUnmarshal
helpviewer_keywords:
- ComCallUnmarshal coclass [.NET Framework hosting]
ms.assetid: 2adb5827-2268-4914-a1c6-f62b61880a45
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2cbaefd2b2c3b79a97107f4aaa394a3db2c68b33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="d0959-102">ComCallUnmarshal – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="d0959-102">ComCallUnmarshal Coclass</span></span>
<span data-ttu-id="d0959-103">Poskytuje rozhraní pro správu zařazování ukazatele rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d0959-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0959-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0959-104">Syntax</span></span>  
  
```  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="d0959-105">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0959-105">Interfaces</span></span>  
  
|<span data-ttu-id="d0959-106">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0959-106">Interface</span></span>|<span data-ttu-id="d0959-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d0959-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="d0959-108">Poskytuje metody pro vytváření, inicializace a správě proxy server v procesu klienta.</span><span class="sxs-lookup"><span data-stu-id="d0959-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d0959-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d0959-109">Requirements</span></span>  
 <span data-ttu-id="d0959-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0959-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0959-111">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="d0959-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="d0959-112">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d0959-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d0959-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0959-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0959-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0959-114">See Also</span></span>  
 [<span data-ttu-id="d0959-115">Třídy typu coclass pro hostování</span><span class="sxs-lookup"><span data-stu-id="d0959-115">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
