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
ms.openlocfilehash: abcae4a89dc2ee3895d6ff246fa7358a5fe2f06e
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901116"
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a><span data-ttu-id="46608-102">ICLRStrongName::StrongNameHashSize – metoda</span><span class="sxs-lookup"><span data-stu-id="46608-102">ICLRStrongName::StrongNameHashSize Method</span></span>
<span data-ttu-id="46608-103">Získá velikost vyrovnávací paměti vyžadované pro hodnotu hash pomocí zadaného algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="46608-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46608-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46608-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46608-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="46608-105">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="46608-106">pro Algoritmus hash používaný k výpočtu velikosti vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="46608-106">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="46608-107">mimo Vrácená velikost vyrovnávací paměti (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="46608-107">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46608-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="46608-108">Return Value</span></span>  
 <span data-ttu-id="46608-109">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="46608-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46608-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="46608-110">Requirements</span></span>  
 <span data-ttu-id="46608-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46608-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46608-112">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="46608-112">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="46608-113">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="46608-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="46608-114">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46608-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46608-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46608-115">See also</span></span>

- [<span data-ttu-id="46608-116">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46608-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
