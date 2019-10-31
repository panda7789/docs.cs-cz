---
title: ComCallUnmarshal – třída typu coclass
ms.date: 03/30/2017
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
ms.openlocfilehash: 38f3140a181deae1a86569bfc2eb7cf3cd7d1991
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131931"
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="db6c9-102">ComCallUnmarshal – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="db6c9-102">ComCallUnmarshal Coclass</span></span>
<span data-ttu-id="db6c9-103">Poskytuje rozhraní pro správu zařazování ukazatelů rozhraní.</span><span class="sxs-lookup"><span data-stu-id="db6c9-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db6c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db6c9-104">Syntax</span></span>  
  
```cpp  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="db6c9-105">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="db6c9-105">Interfaces</span></span>  
  
|<span data-ttu-id="db6c9-106">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="db6c9-106">Interface</span></span>|<span data-ttu-id="db6c9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="db6c9-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="db6c9-108">Poskytuje metody pro vytváření, inicializaci a správu proxy serveru v klientském procesu.</span><span class="sxs-lookup"><span data-stu-id="db6c9-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="db6c9-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db6c9-109">Requirements</span></span>  
 <span data-ttu-id="db6c9-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db6c9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db6c9-111">**Hlavička:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="db6c9-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="db6c9-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="db6c9-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db6c9-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db6c9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db6c9-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db6c9-114">See also</span></span>

- [<span data-ttu-id="db6c9-115">Třídy typu coclass pro hostování</span><span class="sxs-lookup"><span data-stu-id="db6c9-115">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
