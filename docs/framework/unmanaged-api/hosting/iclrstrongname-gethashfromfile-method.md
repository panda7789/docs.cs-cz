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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 33aab5ee23a1f0d30d1f9f3079856ca30d46d2ec
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47086850"
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="97fc2-102">ICLRStrongName::GetHashFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="97fc2-102">ICLRStrongName::GetHashFromFile Method</span></span>
<span data-ttu-id="97fc2-103">Vygeneruje hodnotu hash nad obsah zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="97fc2-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97fc2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97fc2-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="97fc2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="97fc2-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="97fc2-106">[in] Název souboru, který má hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="97fc2-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="97fc2-107">[out v] Algoritmus použitého při generování hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="97fc2-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="97fc2-108">Platné algoritmy jsou těmi definovanými ve Win32 rozhraní CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="97fc2-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="97fc2-109">Pokud `piHashAlg` je nastavena na hodnotu 0, výchozí algoritmus se používá CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="97fc2-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="97fc2-110">[out] Bajtové pole obsahující generované hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="97fc2-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="97fc2-111">[in] Maximální velikost vyrovnávací paměti, která `pbHash` odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="97fc2-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="97fc2-112">[out] Velikost v bajtech, vráceného `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="97fc2-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97fc2-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="97fc2-113">Return Value</span></span>  
 <span data-ttu-id="97fc2-114">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="97fc2-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97fc2-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="97fc2-115">Remarks</span></span>  
 <span data-ttu-id="97fc2-116">Tato metoda je stejné jako [iclrstrongname::gethashfromfilew –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) metody, s tím rozdílem, že specifikace název souboru je ANSI místo Unicode.</span><span class="sxs-lookup"><span data-stu-id="97fc2-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97fc2-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="97fc2-117">Requirements</span></span>  
 <span data-ttu-id="97fc2-118">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97fc2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97fc2-119">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="97fc2-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="97fc2-120">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="97fc2-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97fc2-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97fc2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97fc2-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="97fc2-122">See Also</span></span>  
 [<span data-ttu-id="97fc2-123">GetHashFromFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="97fc2-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [<span data-ttu-id="97fc2-124">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="97fc2-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
