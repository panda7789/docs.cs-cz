---
title: "ICLRStrongName::GetHashFromFileW – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.GetHashFromFileW
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromFileW method [.NET Framework hosting]
ms.assetid: c6ff45fc-905d-4c6e-b00c-97c6c7c55d99
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc7589e2a977502a3e75a95b8a065f45b8805072
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="bd2e9-102">ICLRStrongName::GetHashFromFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="bd2e9-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="bd2e9-103">Generuje součet hash přes obsah soubor určený touto řetězec znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="bd2e9-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd2e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd2e9-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="bd2e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd2e9-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="bd2e9-106">[v] Unicode název souboru, který se hodnota hash.</span><span class="sxs-lookup"><span data-stu-id="bd2e9-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="bd2e9-107">[ve out] Algoritmus použitý při generování hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="bd2e9-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="bd2e9-108">Platný algoritmy jsou definované rozhraní CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="bd2e9-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="bd2e9-109">Pokud `piHashAlg` je nastaven na hodnotu 0, výchozí algoritmus se používá CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="bd2e9-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="bd2e9-110">[out] Bajtové pole obsahující generované hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="bd2e9-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="bd2e9-111">[v] Maximální velikost vyrovnávací paměti, na kterou odkazuje `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="bd2e9-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="bd2e9-112">[out] Velikost v bajtech z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="bd2e9-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd2e9-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bd2e9-113">Return Value</span></span>  
 <span data-ttu-id="bd2e9-114">`S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="bd2e9-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd2e9-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bd2e9-115">Remarks</span></span>  
 <span data-ttu-id="bd2e9-116">Tato metoda je stejná jako [iclrstrongname::gethashfromfile –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) metoda, s tím rozdílem, že soubor název specifikace je Unicode místo ANSI.</span><span class="sxs-lookup"><span data-stu-id="bd2e9-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd2e9-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bd2e9-117">Requirements</span></span>  
 <span data-ttu-id="bd2e9-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd2e9-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd2e9-119">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="bd2e9-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="bd2e9-120">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bd2e9-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bd2e9-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd2e9-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd2e9-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd2e9-122">See Also</span></span>  
 [<span data-ttu-id="bd2e9-123">Gethashfromfile – metoda</span><span class="sxs-lookup"><span data-stu-id="bd2e9-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [<span data-ttu-id="bd2e9-124">Iclrstrongname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd2e9-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
