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
ms.openlocfilehash: 2f17a88a90905006432ae8c5dc040277124c947b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697287"
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="688f5-102">ComCallUnmarshal – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="688f5-102">ComCallUnmarshal Coclass</span></span>
<span data-ttu-id="688f5-103">Poskytuje rozhraní pro správu zařazování ukazatele rozhraní.</span><span class="sxs-lookup"><span data-stu-id="688f5-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="688f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="688f5-104">Syntax</span></span>  
  
```  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="688f5-105">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="688f5-105">Interfaces</span></span>  
  
|<span data-ttu-id="688f5-106">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="688f5-106">Interface</span></span>|<span data-ttu-id="688f5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="688f5-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="688f5-108">Poskytuje metody pro vytváření, inicializace a správy proxy serveru v procesu klienta.</span><span class="sxs-lookup"><span data-stu-id="688f5-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="688f5-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="688f5-109">Requirements</span></span>  
 <span data-ttu-id="688f5-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="688f5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="688f5-111">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="688f5-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="688f5-112">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="688f5-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="688f5-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="688f5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="688f5-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="688f5-114">See also</span></span>

- [<span data-ttu-id="688f5-115">Třídy typu coclass pro hostování</span><span class="sxs-lookup"><span data-stu-id="688f5-115">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
