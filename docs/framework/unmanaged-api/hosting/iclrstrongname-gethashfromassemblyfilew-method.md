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
ms.openlocfilehash: 578dd7941ad7a2cf1d39a3aeed7fa823eb7efa79
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984591"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="54f91-102">ICLRStrongName::GetHashFromAssemblyFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="54f91-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>
<span data-ttu-id="54f91-103">Vygeneruje hodnotu hash přes obsah souboru určeného řetězce v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="54f91-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54f91-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54f91-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54f91-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="54f91-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="54f91-106">[in] Cesta k souboru, který má být mají hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="54f91-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="54f91-107">Tento parametr musí být řetězec s kódováním Unicode.</span><span class="sxs-lookup"><span data-stu-id="54f91-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="54f91-108">[out v] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="54f91-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="54f91-109">Použít nulu pro výchozí hashovací algoritmus.</span><span class="sxs-lookup"><span data-stu-id="54f91-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="54f91-110">[out] Vrácená hodnota hash vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="54f91-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="54f91-111">[in] Požadovaná maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="54f91-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="54f91-112">[out] Velikost v bajtech, vrátil z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="54f91-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54f91-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="54f91-113">Return Value</span></span>  
 <span data-ttu-id="54f91-114">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="54f91-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54f91-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="54f91-115">Requirements</span></span>  
 <span data-ttu-id="54f91-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54f91-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54f91-117">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="54f91-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="54f91-118">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="54f91-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54f91-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54f91-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54f91-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="54f91-120">See also</span></span>

- [<span data-ttu-id="54f91-121">GetHashFromAssemblyFile – metoda</span><span class="sxs-lookup"><span data-stu-id="54f91-121">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="54f91-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="54f91-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
