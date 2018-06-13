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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba1dc2a1ec8b0b3b5ec25036cab6362237efe98f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430753"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="79331-102">IApartmentCallback::DoCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="79331-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="79331-103">Provede zadanou funkci v rámci typu apartment.</span><span class="sxs-lookup"><span data-stu-id="79331-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79331-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79331-104">Syntax</span></span>  
  
```  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="79331-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="79331-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="79331-106">[v] Ukazatel na funkci má provádět v rámci typu apartment.</span><span class="sxs-lookup"><span data-stu-id="79331-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="79331-107">[v] Ukazatel na argument funkce.</span><span class="sxs-lookup"><span data-stu-id="79331-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79331-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="79331-108">Requirements</span></span>  
 <span data-ttu-id="79331-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79331-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79331-110">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="79331-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="79331-111">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="79331-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="79331-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79331-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79331-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="79331-113">See Also</span></span>  
 [<span data-ttu-id="79331-114">IApartmentCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="79331-114">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)
