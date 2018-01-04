---
title: "ICLRStrongName::GetHashFromAssemblyFile – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.GetHashFromAssemblyFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::GetHashFromAssemblyFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFile method [.NET Framework hosting]
- GetHashFromAssemblyFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 0b67ea03-d474-4605-acaa-57455790250c
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6dcb0ca16c2ffdd8a928cec9cca44b628de34885
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="c1e24-102">ICLRStrongName::GetHashFromAssemblyFile – metoda</span><span class="sxs-lookup"><span data-stu-id="c1e24-102">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>
<span data-ttu-id="c1e24-103">Získá hodnotu hash souboru zadaného sestavení pomocí zadaný algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="c1e24-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1e24-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1e24-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1e24-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1e24-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="c1e24-106">[v] Cesta k souboru, který se použít algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="c1e24-106">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="c1e24-107">[ve out] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="c1e24-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="c1e24-108">Používejte nula pro výchozí algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="c1e24-108">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="c1e24-109">[out] Vrácená hodnota hash vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="c1e24-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="c1e24-110">[v] Požadovaný maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="c1e24-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="c1e24-111">[out] Vrácen velikost v bajtech, z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="c1e24-111">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1e24-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c1e24-112">Return Value</span></span>  
 <span data-ttu-id="c1e24-113">`S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="c1e24-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1e24-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c1e24-114">Requirements</span></span>  
 <span data-ttu-id="c1e24-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1e24-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1e24-116">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="c1e24-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c1e24-117">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c1e24-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1e24-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1e24-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1e24-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1e24-119">See Also</span></span>  
 [<span data-ttu-id="c1e24-120">GetHashFromAssemblyFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="c1e24-120">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [<span data-ttu-id="c1e24-121">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1e24-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
