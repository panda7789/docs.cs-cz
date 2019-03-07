---
title: ICLRStrongName::GetHashFromAssemblyFileW – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW method [.NET Framework hosting]
- GetHashFromAssemblyFileW method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5d0b44a2-5a14-44a2-9a0e-e8682fd4e106
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f580d795485c5e306b4eb892c5d717346ce0c48c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57477502"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="838fb-102">ICLRStrongName::GetHashFromAssemblyFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="838fb-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>
<span data-ttu-id="838fb-103">Vygeneruje hodnotu hash přes obsah souboru určeného řetězce v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="838fb-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="838fb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="838fb-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="838fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="838fb-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="838fb-106">[in] Cesta k souboru, který má být mají hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="838fb-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="838fb-107">Tento parametr musí být řetězec s kódováním Unicode.</span><span class="sxs-lookup"><span data-stu-id="838fb-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="838fb-108">[out v] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="838fb-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="838fb-109">Použít nulu pro výchozí hashovací algoritmus.</span><span class="sxs-lookup"><span data-stu-id="838fb-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="838fb-110">[out] Vrácená hodnota hash vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="838fb-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="838fb-111">[in] Požadovaná maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="838fb-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="838fb-112">[out] Velikost v bajtech, vrátil z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="838fb-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="838fb-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="838fb-113">Return Value</span></span>  
 <span data-ttu-id="838fb-114">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="838fb-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="838fb-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="838fb-115">Requirements</span></span>  
 <span data-ttu-id="838fb-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="838fb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="838fb-117">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="838fb-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="838fb-118">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="838fb-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="838fb-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="838fb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="838fb-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="838fb-120">See also</span></span>
- [<span data-ttu-id="838fb-121">GetHashFromAssemblyFile – metoda</span><span class="sxs-lookup"><span data-stu-id="838fb-121">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="838fb-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="838fb-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
