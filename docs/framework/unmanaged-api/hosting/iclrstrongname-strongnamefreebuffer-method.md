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
ms.openlocfilehash: a08aef367f300f7617e3bc9dc721b904f6f33626
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176354"
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a><span data-ttu-id="a68d4-102">ICLRStrongName::StrongNameFreeBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="a68d4-102">ICLRStrongName::StrongNameFreeBuffer Method</span></span>
<span data-ttu-id="a68d4-103">Uvolní paměť, která byla přidělena s předchozím voláním metody silného názvu, jako je [NAPŘÍKLAD ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)nebo [ICLRStrongName::StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).</span><span class="sxs-lookup"><span data-stu-id="a68d4-103">Frees memory that was allocated with a previous call to a strong name method such as [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), or [ICLRStrongName::StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a68d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a68d4-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a68d4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a68d4-105">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="a68d4-106">[v] Ukazatel na paměť k uvolnění.</span><span class="sxs-lookup"><span data-stu-id="a68d4-106">[in] A pointer to the memory to free.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a68d4-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a68d4-107">Return Value</span></span>  
 <span data-ttu-id="a68d4-108">`S_OK`pokud byla metoda úspěšně dokončena; jinak hodnota HRESULT, která označuje selhání (viz [běžné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="a68d4-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a68d4-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a68d4-109">Requirements</span></span>  
 <span data-ttu-id="a68d4-110">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a68d4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a68d4-111">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a68d4-111">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a68d4-112">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a68d4-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a68d4-113">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a68d4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a68d4-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="a68d4-114">See also</span></span>

- [<span data-ttu-id="a68d4-115">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a68d4-115">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
