---
title: GetHashFromFile – funkce
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f98f888280090bfa613acf6ae37bc60ab63c371e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456511"
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="6f7f4-102">GetHashFromFile – funkce</span><span class="sxs-lookup"><span data-stu-id="6f7f4-102">GetHashFromFile Function</span></span>
<span data-ttu-id="6f7f4-103">Generuje součet hash přes obsah zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="6f7f4-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="6f7f4-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="6f7f4-104">This function has been deprecated.</span></span> <span data-ttu-id="6f7f4-105">Použití [iclrstrongname::gethashfromfile –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="6f7f4-105">Use the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f7f4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f7f4-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f7f4-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f7f4-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="6f7f4-108">[v] Název souboru, který se hodnota hash.</span><span class="sxs-lookup"><span data-stu-id="6f7f4-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="6f7f4-109">[ve out] Algoritmus použitý při generování hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="6f7f4-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="6f7f4-110">Platný algoritmy jsou definované rozhraní CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="6f7f4-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="6f7f4-111">Pokud `piHashAlg` je nastaven na hodnotu 0, výchozí algoritmus se používá CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="6f7f4-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="6f7f4-112">[out] Bajtové pole obsahující generované hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="6f7f4-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="6f7f4-113">[v] Maximální velikost vyrovnávací paměti, `pbHash` odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="6f7f4-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="6f7f4-114">[out] Velikost v bajtech vrácený `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="6f7f4-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f7f4-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6f7f4-115">Remarks</span></span>  
 <span data-ttu-id="6f7f4-116">Tato funkce je stejný jako [gethashfromfilew –](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)kromě toho, že zadání názvu souboru je ANSI místo kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="6f7f4-116">This function is the same as [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f7f4-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6f7f4-117">Requirements</span></span>  
 <span data-ttu-id="6f7f4-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f7f4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f7f4-119">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="6f7f4-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="6f7f4-120">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6f7f4-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6f7f4-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f7f4-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f7f4-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f7f4-122">See Also</span></span>  
 [<span data-ttu-id="6f7f4-123">GetHashFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="6f7f4-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [<span data-ttu-id="6f7f4-124">GetHashFromFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="6f7f4-124">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [<span data-ttu-id="6f7f4-125">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f7f4-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
