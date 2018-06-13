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
ms.openlocfilehash: 4a489e05435ce160c65e936f448688d69b3a965f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435258"
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="9d433-102">ICLRStrongName::GetHashFromBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="9d433-102">ICLRStrongName::GetHashFromBlob Method</span></span>
<span data-ttu-id="9d433-103">Získá hodnotu hash sestavení na adrese zadaná paměťová, pomocí zadaný algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="9d433-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d433-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d433-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="9d433-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d433-105">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="9d433-106">[v] Ukazatel na adresu paměti blok, který má být použita hodnota hash.</span><span class="sxs-lookup"><span data-stu-id="9d433-106">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="9d433-107">[v] Délka v bajtech bloku paměti.</span><span class="sxs-lookup"><span data-stu-id="9d433-107">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="9d433-108">[ve out] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="9d433-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="9d433-109">Používejte nula pro výchozí algoritmus.</span><span class="sxs-lookup"><span data-stu-id="9d433-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="9d433-110">[out] Vrácená hodnota hash vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9d433-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="9d433-111">[v] Požadovaný maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="9d433-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="9d433-112">[out] Velikost v bajtech vrácený `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="9d433-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d433-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9d433-113">Return Value</span></span>  
 <span data-ttu-id="9d433-114">`S_OK` Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="9d433-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d433-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d433-115">Requirements</span></span>  
 <span data-ttu-id="9d433-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d433-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d433-117">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9d433-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9d433-118">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9d433-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d433-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d433-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d433-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d433-120">See Also</span></span>  
 [<span data-ttu-id="9d433-121">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d433-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
