---
title: ICLRStrongName::GetHashFromBlob – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromBlob
helpviewer_keywords:
- ICLRStrongName::GetHashFromBlob method [.NET Framework hosting]
- GetHashFromBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: f91d0f89-f356-49ac-aafb-50fad963c13d
topic_type:
- apiref
ms.openlocfilehash: b42079d138e754996470e07b884d49c1ebb625c3
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901171"
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="5a4d5-102">ICLRStrongName::GetHashFromBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="5a4d5-102">ICLRStrongName::GetHashFromBlob Method</span></span>
<span data-ttu-id="5a4d5-103">Načte hodnotu hash sestavení v zadané adrese paměti pomocí zadaného algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a4d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a4d5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a4d5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a4d5-105">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="5a4d5-106">pro Ukazatel na adresu bloku paměti, který má být použit jako hash.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-106">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="5a4d5-107">pro Délka bloku paměti (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="5a4d5-107">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="5a4d5-108">[in, out] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="5a4d5-109">Pro výchozí algoritmus použijte nulu.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="5a4d5-110">mimo Vrácená vyrovnávací paměť hash.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="5a4d5-111">pro Požadovaná maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="5a4d5-112">mimo Velikost vrácených `pbHash`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="5a4d5-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a4d5-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5a4d5-113">Return Value</span></span>  
 <span data-ttu-id="5a4d5-114">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="5a4d5-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a4d5-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5a4d5-115">Requirements</span></span>  
 <span data-ttu-id="5a4d5-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a4d5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a4d5-117">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="5a4d5-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5a4d5-118">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5a4d5-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5a4d5-119">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a4d5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a4d5-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a4d5-120">See also</span></span>

- [<span data-ttu-id="5a4d5-121">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5a4d5-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
