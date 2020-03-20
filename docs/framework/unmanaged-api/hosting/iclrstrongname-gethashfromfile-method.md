---
title: ICLRStrongName::GetHashFromFile – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type:
- apiref
ms.openlocfilehash: ed735c3d7830551581df35793f3f6fdc4953dc8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178077"
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="8a1b2-102">ICLRStrongName::GetHashFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="8a1b2-102">ICLRStrongName::GetHashFromFile Method</span></span>
<span data-ttu-id="8a1b2-103">Generuje hash nad obsahem zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="8a1b2-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a1b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a1b2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a1b2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a1b2-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="8a1b2-106">[v] Název souboru hash.</span><span class="sxs-lookup"><span data-stu-id="8a1b2-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="8a1b2-107">[dovnitř, ven] Algoritmus, který se má použít při generování algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="8a1b2-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="8a1b2-108">Platné algoritmy jsou ty, které jsou definovány Win32 CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="8a1b2-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="8a1b2-109">Pokud `piHashAlg` je nastavena na hodnotu 0, použije se výchozí algoritmus CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="8a1b2-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="8a1b2-110">[out] Bajtový pole obsahující vygenerovaný hash.</span><span class="sxs-lookup"><span data-stu-id="8a1b2-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="8a1b2-111">[v] Maximální velikost vyrovnávací paměti, která `pbHash` odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="8a1b2-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="8a1b2-112">[out] Velikost vráceného bajtu v bajtech `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="8a1b2-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a1b2-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8a1b2-113">Return Value</span></span>  
 <span data-ttu-id="8a1b2-114">`S_OK`pokud byla metoda úspěšně dokončena; jinak hodnota HRESULT, která označuje selhání (viz [běžné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="8a1b2-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a1b2-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8a1b2-115">Remarks</span></span>  
 <span data-ttu-id="8a1b2-116">Tato metoda je stejná jako metoda [ICLRStrongName::GetHashFromFileW,](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) s tím rozdílem, že specifikace názvu souboru je ANSI místo Unicode.</span><span class="sxs-lookup"><span data-stu-id="8a1b2-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a1b2-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8a1b2-117">Requirements</span></span>  
 <span data-ttu-id="8a1b2-118">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a1b2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a1b2-119">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="8a1b2-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8a1b2-120">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8a1b2-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8a1b2-121">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a1b2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a1b2-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="8a1b2-122">See also</span></span>

- [<span data-ttu-id="8a1b2-123">GetHashFromFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="8a1b2-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="8a1b2-124">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8a1b2-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
