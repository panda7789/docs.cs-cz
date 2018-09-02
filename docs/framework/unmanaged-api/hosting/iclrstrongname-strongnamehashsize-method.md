---
title: ICLRStrongName::StrongNameHashSize – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameHashSize
helpviewer_keywords:
- ICLRStrongName::StrongNameHashSize method [.NET Framework hosting]
- StrongNameHashSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 4a05ee56-08e4-4f3a-86a9-9b52083d5c0f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c09832d296033b0790d3e6282763a1163abdfd2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406288"
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a><span data-ttu-id="eeef5-102">ICLRStrongName::StrongNameHashSize – metoda</span><span class="sxs-lookup"><span data-stu-id="eeef5-102">ICLRStrongName::StrongNameHashSize Method</span></span>
<span data-ttu-id="eeef5-103">Získá velikost vyrovnávací paměti vyžadované pro hodnotu hash pomocí algoritmu zadanou hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="eeef5-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eeef5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eeef5-104">Syntax</span></span>  
  
```  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eeef5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eeef5-105">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="eeef5-106">[in] Hashovací algoritmus, který slouží k výpočtu velikosti vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="eeef5-106">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="eeef5-107">[out] Velikost vrácené vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="eeef5-107">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eeef5-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="eeef5-108">Return Value</span></span>  
 <span data-ttu-id="eeef5-109">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="eeef5-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eeef5-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eeef5-110">Requirements</span></span>  
 <span data-ttu-id="eeef5-111">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eeef5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eeef5-112">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="eeef5-112">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="eeef5-113">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eeef5-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eeef5-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eeef5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeef5-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="eeef5-115">See Also</span></span>  
 [<span data-ttu-id="eeef5-116">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eeef5-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
