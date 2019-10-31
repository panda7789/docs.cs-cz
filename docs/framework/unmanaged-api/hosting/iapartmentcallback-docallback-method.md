---
title: IApartmentCallback::DoCallback – metoda
ms.date: 03/30/2017
api_name:
- IApartmentCallback.DoCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- DoCallback
helpviewer_keywords:
- IApartmentCallback::DoCallback method [.NET Framework hosting]
- DoCallback method [.NET Framework hosting]
ms.assetid: 8edad30c-30ff-4bee-813c-75525a82fc93
topic_type:
- apiref
ms.openlocfilehash: 9bb257a3d84d5022b9ae13c89a34572485d3033b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126949"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="69b5a-102">IApartmentCallback::DoCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="69b5a-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="69b5a-103">Spustí zadanou funkci v rámci objektu apartment.</span><span class="sxs-lookup"><span data-stu-id="69b5a-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69b5a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69b5a-104">Syntax</span></span>  
  
```cpp  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69b5a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="69b5a-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="69b5a-106">pro Ukazatel na funkci, která má být provedena v rámci objektu apartment.</span><span class="sxs-lookup"><span data-stu-id="69b5a-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="69b5a-107">pro Ukazatel na argument funkce.</span><span class="sxs-lookup"><span data-stu-id="69b5a-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69b5a-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="69b5a-108">Requirements</span></span>  
 <span data-ttu-id="69b5a-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69b5a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69b5a-110">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="69b5a-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="69b5a-111">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="69b5a-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="69b5a-112">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69b5a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69b5a-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69b5a-113">See also</span></span>

- [<span data-ttu-id="69b5a-114">IApartmentCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="69b5a-114">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)
