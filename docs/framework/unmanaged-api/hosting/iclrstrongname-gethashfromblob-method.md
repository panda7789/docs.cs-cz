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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34e8bcdda30c890fc40bab206bc6757afc073177
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475200"
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="c8f51-102">ICLRStrongName::GetHashFromBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="c8f51-102">ICLRStrongName::GetHashFromBlob Method</span></span>
<span data-ttu-id="c8f51-103">Získá hodnotu hash sestavení na adrese zadaná paměťová, pomocí zadané hashovacího algoritmu.</span><span class="sxs-lookup"><span data-stu-id="c8f51-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8f51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8f51-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8f51-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c8f51-105">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="c8f51-106">[in] Ukazatel na adresu blok paměti určený k hashovat.</span><span class="sxs-lookup"><span data-stu-id="c8f51-106">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="c8f51-107">[in] Délka v bajtech, bloku paměti.</span><span class="sxs-lookup"><span data-stu-id="c8f51-107">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="c8f51-108">[out v] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="c8f51-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="c8f51-109">Použít nulu pro výchozí algoritmus.</span><span class="sxs-lookup"><span data-stu-id="c8f51-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="c8f51-110">[out] Vrácená hodnota hash vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="c8f51-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="c8f51-111">[in] Požadovaná maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="c8f51-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="c8f51-112">[out] Velikost v bajtech, vráceného `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="c8f51-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8f51-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c8f51-113">Return Value</span></span>  
 <span data-ttu-id="c8f51-114">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="c8f51-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8f51-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8f51-115">Requirements</span></span>  
 <span data-ttu-id="c8f51-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8f51-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8f51-117">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="c8f51-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c8f51-118">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c8f51-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8f51-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8f51-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8f51-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8f51-120">See also</span></span>
- [<span data-ttu-id="c8f51-121">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8f51-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
