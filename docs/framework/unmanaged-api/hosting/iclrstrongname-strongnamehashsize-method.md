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
ms.openlocfilehash: 0f4fdcbdfb9db7664920a42b9406a58f9c2de0b8
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763108"
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a><span data-ttu-id="4ace0-102">ICLRStrongName::StrongNameHashSize – metoda</span><span class="sxs-lookup"><span data-stu-id="4ace0-102">ICLRStrongName::StrongNameHashSize Method</span></span>
<span data-ttu-id="4ace0-103">Získá velikost vyrovnávací paměti vyžadované pro hodnotu hash pomocí zadaného algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="4ace0-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ace0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ace0-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ace0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4ace0-105">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="4ace0-106">pro Algoritmus hash používaný k výpočtu velikosti vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4ace0-106">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="4ace0-107">mimo Vrácená velikost vyrovnávací paměti (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="4ace0-107">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ace0-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4ace0-108">Return Value</span></span>  
 <span data-ttu-id="4ace0-109">`S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="4ace0-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ace0-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4ace0-110">Requirements</span></span>  
 <span data-ttu-id="4ace0-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ace0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ace0-112">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="4ace0-112">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4ace0-113">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4ace0-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ace0-114">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ace0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ace0-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ace0-115">See also</span></span>

- [<span data-ttu-id="4ace0-116">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4ace0-116">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
