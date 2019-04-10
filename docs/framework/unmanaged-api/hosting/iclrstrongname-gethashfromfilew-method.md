---
title: ICLRStrongName::GetHashFromFileW – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromFileW method [.NET Framework hosting]
ms.assetid: c6ff45fc-905d-4c6e-b00c-97c6c7c55d99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1547680800b188d5b5e0032e804c22cae0547ac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227038"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="6312f-102">ICLRStrongName::GetHashFromFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="6312f-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="6312f-103">Vygeneruje hodnotu hash přes obsah souboru určeného řetězce v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="6312f-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6312f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6312f-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="6312f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6312f-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="6312f-106">[in] Kódování Unicode název souboru, který má hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="6312f-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="6312f-107">[out v] Algoritmus použitého při generování hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="6312f-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="6312f-108">Platné algoritmy jsou těmi definovanými ve Win32 rozhraní CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="6312f-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="6312f-109">Pokud `piHashAlg` je nastavena na hodnotu 0, výchozí algoritmus se používá CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="6312f-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="6312f-110">[out] Bajtové pole obsahující generované hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="6312f-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="6312f-111">[in] Maximální velikost vyrovnávací paměti, na které odkazuje `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="6312f-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="6312f-112">[out] Velikost v bajtech, z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="6312f-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6312f-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6312f-113">Return Value</span></span>  
 `S_OK` <span data-ttu-id="6312f-114">Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="6312f-114">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6312f-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6312f-115">Remarks</span></span>  
 <span data-ttu-id="6312f-116">Tato metoda je stejné jako [iclrstrongname::gethashfromfile –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) metody, s tím rozdílem, že specifikace název souboru je Unicode místo ANSI.</span><span class="sxs-lookup"><span data-stu-id="6312f-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6312f-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6312f-117">Requirements</span></span>  
 <span data-ttu-id="6312f-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6312f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6312f-119">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="6312f-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6312f-120">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6312f-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="6312f-121">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="6312f-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6312f-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6312f-122">See also</span></span>

- [<span data-ttu-id="6312f-123">GetHashFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="6312f-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="6312f-124">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6312f-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
