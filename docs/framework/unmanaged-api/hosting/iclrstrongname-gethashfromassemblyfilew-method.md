---
title: "ICLRStrongName::GetHashFromAssemblyFileW – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.GetHashFromAssemblyFileW
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::GetHashFromAssemblyFileW
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW method [.NET Framework hosting]
- GetHashFromAssemblyFileW method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5d0b44a2-5a14-44a2-9a0e-e8682fd4e106
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 14b4e6dae97777873f458018acdaf0c3f5d4f070
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="5d072-102">ICLRStrongName::GetHashFromAssemblyFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="5d072-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>
<span data-ttu-id="5d072-103">Generuje součet hash přes obsah soubor určený touto řetězec znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="5d072-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d072-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d072-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d072-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d072-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="5d072-106">[v] Cesta k souboru, který se použít algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="5d072-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="5d072-107">Tento parametr musí být řetězec znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="5d072-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="5d072-108">[ve out] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="5d072-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="5d072-109">Používejte nula pro výchozí algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="5d072-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="5d072-110">[out] Vrácená hodnota hash vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="5d072-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="5d072-111">[v] Požadovaný maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="5d072-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="5d072-112">[out] Vrácen velikost v bajtech, z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="5d072-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d072-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5d072-113">Return Value</span></span>  
 <span data-ttu-id="5d072-114">`S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="5d072-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d072-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5d072-115">Requirements</span></span>  
 <span data-ttu-id="5d072-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d072-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d072-117">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5d072-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5d072-118">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5d072-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d072-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d072-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d072-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d072-120">See Also</span></span>  
 [<span data-ttu-id="5d072-121">Gethashfromassemblyfile – metoda</span><span class="sxs-lookup"><span data-stu-id="5d072-121">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="5d072-122">Iclrstrongname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d072-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
