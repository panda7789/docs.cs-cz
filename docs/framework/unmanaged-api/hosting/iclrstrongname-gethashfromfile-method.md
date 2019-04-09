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
ms.openlocfilehash: f410e38d846969bbd23ff5b0a6751a5202088254
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157492"
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="b7828-102">ICLRStrongName::GetHashFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="b7828-102">ICLRStrongName::GetHashFromFile Method</span></span>
<span data-ttu-id="b7828-103">Vygeneruje hodnotu hash nad obsah zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="b7828-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7828-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7828-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7828-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7828-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="b7828-106">[in] Název souboru, který má hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="b7828-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="b7828-107">[out v] Algoritmus použitého při generování hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="b7828-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="b7828-108">Platné algoritmy jsou těmi definovanými ve Win32 rozhraní CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="b7828-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="b7828-109">Pokud `piHashAlg` je nastavena na hodnotu 0, výchozí algoritmus se používá CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="b7828-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="b7828-110">[out] Bajtové pole obsahující generované hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="b7828-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="b7828-111">[in] Maximální velikost vyrovnávací paměti, která `pbHash` odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="b7828-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="b7828-112">[out] Velikost v bajtech, vráceného `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="b7828-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7828-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b7828-113">Return Value</span></span>  
 `S_OK` <span data-ttu-id="b7828-114">Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="b7828-114">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7828-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b7828-115">Remarks</span></span>  
 <span data-ttu-id="b7828-116">Tato metoda je stejné jako [iclrstrongname::gethashfromfilew –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) metody, s tím rozdílem, že specifikace název souboru je ANSI místo Unicode.</span><span class="sxs-lookup"><span data-stu-id="b7828-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7828-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7828-117">Requirements</span></span>  
 <span data-ttu-id="b7828-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7828-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7828-119">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b7828-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b7828-120">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b7828-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b7828-121">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b7828-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b7828-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7828-122">See also</span></span>

- [<span data-ttu-id="b7828-123">GetHashFromFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="b7828-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="b7828-124">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7828-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
