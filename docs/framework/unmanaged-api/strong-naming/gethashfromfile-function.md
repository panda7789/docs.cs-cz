---
title: "GetHashFromFile – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: be7979eb0f7d32e02257cc0b3cb400263350f0bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="bcbe2-102">GetHashFromFile – funkce</span><span class="sxs-lookup"><span data-stu-id="bcbe2-102">GetHashFromFile Function</span></span>
<span data-ttu-id="bcbe2-103">Generuje součet hash přes obsah zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="bcbe2-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="bcbe2-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="bcbe2-104">This function has been deprecated.</span></span> <span data-ttu-id="bcbe2-105">Použití [iclrstrongname::gethashfromfile –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="bcbe2-105">Use the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcbe2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcbe2-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bcbe2-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="bcbe2-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="bcbe2-108">[v] Název souboru, který se hodnota hash.</span><span class="sxs-lookup"><span data-stu-id="bcbe2-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="bcbe2-109">[ve out] Algoritmus použitý při generování hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="bcbe2-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="bcbe2-110">Platný algoritmy jsou definované rozhraní CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="bcbe2-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="bcbe2-111">Pokud `piHashAlg` je nastaven na hodnotu 0, výchozí algoritmus se používá CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="bcbe2-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="bcbe2-112">[out] Bajtové pole obsahující generované hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="bcbe2-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="bcbe2-113">[v] Maximální velikost vyrovnávací paměti, `pbHash` odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="bcbe2-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="bcbe2-114">[out] Velikost v bajtech vrácený `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="bcbe2-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcbe2-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bcbe2-115">Remarks</span></span>  
 <span data-ttu-id="bcbe2-116">Tato funkce je stejný jako [gethashfromfilew –](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)kromě toho, že zadání názvu souboru je ANSI místo kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="bcbe2-116">This function is the same as [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcbe2-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bcbe2-117">Requirements</span></span>  
 <span data-ttu-id="bcbe2-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcbe2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcbe2-119">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="bcbe2-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="bcbe2-120">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bcbe2-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bcbe2-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcbe2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcbe2-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="bcbe2-122">See Also</span></span>  
 [<span data-ttu-id="bcbe2-123">GetHashFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="bcbe2-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [<span data-ttu-id="bcbe2-124">GetHashFromFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="bcbe2-124">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [<span data-ttu-id="bcbe2-125">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bcbe2-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
