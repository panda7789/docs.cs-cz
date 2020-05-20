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
ms.openlocfilehash: 939acc0ad47021d5fdffe7b7b71ea6a4a1635a6d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616733"
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="bdfb0-102">ComCallUnmarshal – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="bdfb0-102">ComCallUnmarshal Coclass</span></span>
<span data-ttu-id="bdfb0-103">Poskytuje rozhraní pro správu zařazování ukazatelů rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bdfb0-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdfb0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bdfb0-104">Syntax</span></span>  
  
```cpp  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="bdfb0-105">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="bdfb0-105">Interfaces</span></span>  
  
|<span data-ttu-id="bdfb0-106">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="bdfb0-106">Interface</span></span>|<span data-ttu-id="bdfb0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="bdfb0-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="bdfb0-108">Poskytuje metody pro vytváření, inicializaci a správu proxy serveru v klientském procesu.</span><span class="sxs-lookup"><span data-stu-id="bdfb0-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bdfb0-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bdfb0-109">Requirements</span></span>  
 <span data-ttu-id="bdfb0-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdfb0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdfb0-111">**Hlavička:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="bdfb0-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="bdfb0-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bdfb0-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bdfb0-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdfb0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdfb0-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="bdfb0-114">See also</span></span>

- [<span data-ttu-id="bdfb0-115">Třídy typu coclass hostování</span><span class="sxs-lookup"><span data-stu-id="bdfb0-115">Hosting Coclasses</span></span>](hosting-coclasses.md)
