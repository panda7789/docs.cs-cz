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
ms.openlocfilehash: 8db3b1854e334cef4d91d21eb5f666ba2e88fc2e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135066"
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a><span data-ttu-id="eaf35-102">ICLRStrongName::StrongNameHashSize – metoda</span><span class="sxs-lookup"><span data-stu-id="eaf35-102">ICLRStrongName::StrongNameHashSize Method</span></span>
<span data-ttu-id="eaf35-103">Získá velikost vyrovnávací paměti vyžadované pro hodnotu hash pomocí zadaného algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="eaf35-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaf35-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eaf35-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eaf35-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eaf35-105">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="eaf35-106">pro Algoritmus hash používaný k výpočtu velikosti vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="eaf35-106">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="eaf35-107">mimo Vrácená velikost vyrovnávací paměti (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="eaf35-107">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eaf35-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="eaf35-108">Return Value</span></span>  
 <span data-ttu-id="eaf35-109">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="eaf35-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaf35-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eaf35-110">Requirements</span></span>  
 <span data-ttu-id="eaf35-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eaf35-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaf35-112">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="eaf35-112">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="eaf35-113">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="eaf35-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eaf35-114">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaf35-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaf35-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eaf35-115">See also</span></span>

- [<span data-ttu-id="eaf35-116">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eaf35-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
