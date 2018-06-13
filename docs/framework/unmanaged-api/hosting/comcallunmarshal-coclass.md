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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7884d53630ca13a30d7b4efd55d46684a9dd7d30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427639"
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="be73a-102">ComCallUnmarshal – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="be73a-102">ComCallUnmarshal Coclass</span></span>
<span data-ttu-id="be73a-103">Poskytuje rozhraní pro správu zařazování ukazatele rozhraní.</span><span class="sxs-lookup"><span data-stu-id="be73a-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be73a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be73a-104">Syntax</span></span>  
  
```  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="be73a-105">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="be73a-105">Interfaces</span></span>  
  
|<span data-ttu-id="be73a-106">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="be73a-106">Interface</span></span>|<span data-ttu-id="be73a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="be73a-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="be73a-108">Poskytuje metody pro vytváření, inicializace a správě proxy server v procesu klienta.</span><span class="sxs-lookup"><span data-stu-id="be73a-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="be73a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="be73a-109">Requirements</span></span>  
 <span data-ttu-id="be73a-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be73a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be73a-111">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="be73a-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="be73a-112">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="be73a-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="be73a-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be73a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be73a-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="be73a-114">See Also</span></span>  
 [<span data-ttu-id="be73a-115">Třídy typu coclass pro hostování</span><span class="sxs-lookup"><span data-stu-id="be73a-115">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
