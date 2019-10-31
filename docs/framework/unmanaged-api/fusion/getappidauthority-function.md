---
title: GetAppIdAuthority – funkce
ms.date: 03/30/2017
api_name:
- GetAppIdAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetAppIdAuthority
helpviewer_keywords:
- GetAppIdAuthority function [.NET Framework fusion]
ms.assetid: 9f968dad-0d09-47fb-bebc-94c39a0d16ad
topic_type:
- apiref
ms.openlocfilehash: 22a6af61251942f068676daaee2bdfa868e32a97
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134558"
---
# <a name="getappidauthority-function"></a><span data-ttu-id="55dc3-102">GetAppIdAuthority – funkce</span><span class="sxs-lookup"><span data-stu-id="55dc3-102">GetAppIdAuthority Function</span></span>
<span data-ttu-id="55dc3-103">Získá ukazatel na instanci [IAppIdAuthority –](iappidauthority-interface.md) , která spravuje klíče pro identity aplikace a odkazy.</span><span class="sxs-lookup"><span data-stu-id="55dc3-103">Gets a pointer to an [IAppIdAuthority](iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55dc3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55dc3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="55dc3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="55dc3-105">Parameters</span></span>  
 `ppIAppIdAuthority`  
 <span data-ttu-id="55dc3-106">mimo Vrácený ukazatel `IAppIdAuthority`.</span><span class="sxs-lookup"><span data-stu-id="55dc3-106">[out] The returned `IAppIdAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55dc3-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="55dc3-107">Requirements</span></span>  
 <span data-ttu-id="55dc3-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55dc3-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55dc3-109">**Hlavička:** Izolace. h</span><span class="sxs-lookup"><span data-stu-id="55dc3-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="55dc3-110">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55dc3-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55dc3-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55dc3-111">See also</span></span>

- [<span data-ttu-id="55dc3-112">IAppIdAuthority – rozhraní</span><span class="sxs-lookup"><span data-stu-id="55dc3-112">IAppIdAuthority Interface</span></span>](iappidauthority-interface.md)
- [<span data-ttu-id="55dc3-113">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="55dc3-113">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
