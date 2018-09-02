---
title: ICLRStrongName::StrongNameFreeBuffer – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef8c1e96c12b554a89d012633d1e5c347dab6de4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398521"
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a><span data-ttu-id="db6d0-102">ICLRStrongName::StrongNameFreeBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="db6d0-102">ICLRStrongName::StrongNameFreeBuffer Method</span></span>
<span data-ttu-id="db6d0-103">Uvolnění paměti, která byla přidělena s předchozí volání metody silným názvem, jako například [iclrstrongname::strongnamegetpublickey –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [iclrstrongname::strongnametokenfrompublickey –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), nebo [ Iclrstrongname::strongnamesignaturegeneration –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).</span><span class="sxs-lookup"><span data-stu-id="db6d0-103">Frees memory that was allocated with a previous call to a strong name method such as [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), or [ICLRStrongName::StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db6d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db6d0-104">Syntax</span></span>  
  
```  
HRESULT StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db6d0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db6d0-105">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="db6d0-106">[in] Ukazatel na paměť uvolnit.</span><span class="sxs-lookup"><span data-stu-id="db6d0-106">[in] A pointer to the memory to free.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db6d0-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="db6d0-107">Return Value</span></span>  
 <span data-ttu-id="db6d0-108">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="db6d0-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db6d0-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db6d0-109">Requirements</span></span>  
 <span data-ttu-id="db6d0-110">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db6d0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db6d0-111">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="db6d0-111">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="db6d0-112">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="db6d0-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db6d0-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db6d0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db6d0-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="db6d0-114">See Also</span></span>  
 [<span data-ttu-id="db6d0-115">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db6d0-115">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
