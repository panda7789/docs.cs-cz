---
title: "ICLRStrongName::GetHashFromFile – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.GetHashFromFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bccdb01e098015f61a29ba267da1f3ec37543fcd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="263af-102">ICLRStrongName::GetHashFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="263af-102">ICLRStrongName::GetHashFromFile Method</span></span>
<span data-ttu-id="263af-103">Generuje součet hash přes obsah zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="263af-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="263af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="263af-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="263af-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="263af-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="263af-106">[v] Název souboru, který se hodnota hash.</span><span class="sxs-lookup"><span data-stu-id="263af-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="263af-107">[ve out] Algoritmus použitý při generování hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="263af-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="263af-108">Platný algoritmy jsou definované rozhraní CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="263af-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="263af-109">Pokud `piHashAlg` je nastaven na hodnotu 0, výchozí algoritmus se používá CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="263af-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="263af-110">[out] Bajtové pole obsahující generované hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="263af-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="263af-111">[v] Maximální velikost vyrovnávací paměti, `pbHash` odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="263af-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="263af-112">[out] Velikost v bajtech vrácený `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="263af-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="263af-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="263af-113">Return Value</span></span>  
 <span data-ttu-id="263af-114">`S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="263af-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="263af-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="263af-115">Remarks</span></span>  
 <span data-ttu-id="263af-116">Tato metoda je stejná jako [iclrstrongname::gethashfromfilew –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) metoda, s tím rozdílem, že soubor název specifikace je ANSI místo kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="263af-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="263af-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="263af-117">Requirements</span></span>  
 <span data-ttu-id="263af-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="263af-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="263af-119">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="263af-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="263af-120">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="263af-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="263af-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="263af-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="263af-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="263af-122">See Also</span></span>  
 [<span data-ttu-id="263af-123">Gethashfromfilew – metoda</span><span class="sxs-lookup"><span data-stu-id="263af-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [<span data-ttu-id="263af-124">Iclrstrongname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="263af-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
