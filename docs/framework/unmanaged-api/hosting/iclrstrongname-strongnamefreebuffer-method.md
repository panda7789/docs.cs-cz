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
ms.openlocfilehash: 0d250270d139c0e930f3270f2ca1191c9c57284b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755120"
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a><span data-ttu-id="e466e-102">ICLRStrongName::StrongNameFreeBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="e466e-102">ICLRStrongName::StrongNameFreeBuffer Method</span></span>
<span data-ttu-id="e466e-103">Uvolnění paměti, která byla přidělena s předchozí volání metody silným názvem, jako například [iclrstrongname::strongnamegetpublickey –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [iclrstrongname::strongnametokenfrompublickey –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), nebo [ Iclrstrongname::strongnamesignaturegeneration –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).</span><span class="sxs-lookup"><span data-stu-id="e466e-103">Frees memory that was allocated with a previous call to a strong name method such as [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), or [ICLRStrongName::StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e466e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e466e-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e466e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e466e-105">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="e466e-106">[in] Ukazatel na paměť uvolnit.</span><span class="sxs-lookup"><span data-stu-id="e466e-106">[in] A pointer to the memory to free.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e466e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e466e-107">Return Value</span></span>  
 <span data-ttu-id="e466e-108">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="e466e-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e466e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e466e-109">Requirements</span></span>  
 <span data-ttu-id="e466e-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e466e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e466e-111">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e466e-111">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e466e-112">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e466e-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e466e-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e466e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e466e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e466e-114">See also</span></span>

- [<span data-ttu-id="e466e-115">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e466e-115">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
