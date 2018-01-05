---
title: "ICLRStrongName::GetHashFromBlob – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.GetHashFromBlob
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::GetHashFromBlob
helpviewer_keywords:
- ICLRStrongName::GetHashFromBlob method [.NET Framework hosting]
- GetHashFromBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: f91d0f89-f356-49ac-aafb-50fad963c13d
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1947441e395ddb9d9d0fd9c4b02e7e991b1c84a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="d806f-102">ICLRStrongName::GetHashFromBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="d806f-102">ICLRStrongName::GetHashFromBlob Method</span></span>
<span data-ttu-id="d806f-103">Získá hodnotu hash sestavení na adrese zadaná paměťová, pomocí zadaný algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="d806f-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d806f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d806f-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="d806f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d806f-105">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="d806f-106">[v] Ukazatel na adresu paměti blok, který má být použita hodnota hash.</span><span class="sxs-lookup"><span data-stu-id="d806f-106">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="d806f-107">[v] Délka v bajtech bloku paměti.</span><span class="sxs-lookup"><span data-stu-id="d806f-107">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="d806f-108">[ve out] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="d806f-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="d806f-109">Používejte nula pro výchozí algoritmus.</span><span class="sxs-lookup"><span data-stu-id="d806f-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="d806f-110">[out] Vrácená hodnota hash vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d806f-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="d806f-111">[v] Požadovaný maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="d806f-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="d806f-112">[out] Velikost v bajtech vrácený `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="d806f-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d806f-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d806f-113">Return Value</span></span>  
 <span data-ttu-id="d806f-114">`S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="d806f-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d806f-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d806f-115">Requirements</span></span>  
 <span data-ttu-id="d806f-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d806f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d806f-117">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d806f-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d806f-118">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d806f-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d806f-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d806f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d806f-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="d806f-120">See Also</span></span>  
 [<span data-ttu-id="d806f-121">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d806f-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
