---
title: "DestroyICeeFileGen – funkce"
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
- DestroyICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- DestroyICeeFileGen
helpviewer_keywords:
- DestroyICeeFileGen function [.NET Framework hosting]
ms.assetid: dc1e2235-e721-4cb2-a0b8-6b0c030d7bab
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d6c3e326aa71adc1bc9abe350cfc0528c88905cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="fbc3b-102">DestroyICeeFileGen – funkce</span><span class="sxs-lookup"><span data-stu-id="fbc3b-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="fbc3b-103">Zničí [iceefilegen –](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="fbc3b-103">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="fbc3b-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fbc3b-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbc3b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbc3b-105">Syntax</span></span>  
  
```  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fbc3b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fbc3b-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="fbc3b-107">[v] `ICeeFileGen` Objekt zrušení.</span><span class="sxs-lookup"><span data-stu-id="fbc3b-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fbc3b-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fbc3b-108">Return Value</span></span>  
 <span data-ttu-id="fbc3b-109">Tato metoda vrátí standardní kódy chyb COM.</span><span class="sxs-lookup"><span data-stu-id="fbc3b-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbc3b-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fbc3b-110">Remarks</span></span>  
 <span data-ttu-id="fbc3b-111">`DestroyICeeFileGen`zničí `ICeeFileGen` objekt vytvořený [createiceefilegen –](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="fbc3b-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbc3b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fbc3b-112">Requirements</span></span>  
 <span data-ttu-id="fbc3b-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbc3b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbc3b-114">**Záhlaví:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="fbc3b-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="fbc3b-115">**Knihovna:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="fbc3b-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="fbc3b-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbc3b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbc3b-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="fbc3b-117">See Also</span></span>  
 [<span data-ttu-id="fbc3b-118">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="fbc3b-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
