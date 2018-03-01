---
title: "ICLRStrongName::StrongNameFreeBuffer – metoda"
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
- ICLRStrongName.StrongNameFreeBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameFreeBuffer method [.NET Framework hosting]
ms.assetid: 6148c508-bd1d-4a37-85c3-06ecb09cc857
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 378847ae8bfd1640401c51f75258affbd100cb22
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a><span data-ttu-id="19f66-102">ICLRStrongName::StrongNameFreeBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="19f66-102">ICLRStrongName::StrongNameFreeBuffer Method</span></span>
<span data-ttu-id="19f66-103">Uvolní paměť, který byl přidělen s předchozí volání metody silným názvem, jako [iclrstrongname::strongnamegetpublickey –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [iclrstrongname::strongnametokenfrompublickey –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), nebo [ Iclrstrongname::strongnamesignaturegeneration –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).</span><span class="sxs-lookup"><span data-stu-id="19f66-103">Frees memory that was allocated with a previous call to a strong name method such as [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), or [ICLRStrongName::StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19f66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19f66-104">Syntax</span></span>  
  
```  
HRESULT StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="19f66-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="19f66-105">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="19f66-106">[v] Ukazatel na paměť uvolnit.</span><span class="sxs-lookup"><span data-stu-id="19f66-106">[in] A pointer to the memory to free.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19f66-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="19f66-107">Return Value</span></span>  
 <span data-ttu-id="19f66-108">`S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="19f66-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19f66-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="19f66-109">Requirements</span></span>  
 <span data-ttu-id="19f66-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19f66-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19f66-111">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="19f66-111">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="19f66-112">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="19f66-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19f66-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19f66-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19f66-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="19f66-114">See Also</span></span>  
 [<span data-ttu-id="19f66-115">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="19f66-115">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
