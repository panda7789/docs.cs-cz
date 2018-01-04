---
title: "ICLRStrongName::GetHashFromHandle – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRStrongName.GetHashFromHandle
- ICLRStrongName.StrongNameCompareAssemblies
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromHandle method [.NET Framework hosting]
ms.assetid: 3bedbb7d-3cdd-4175-b370-10ae734062db
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61e0f0cc5ba4bb48f5d54427f6e94f72ef8fbd00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="ede98-102">ICLRStrongName::GetHashFromHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="ede98-102">ICLRStrongName::GetHashFromHandle Method</span></span>
<span data-ttu-id="ede98-103">Generuje součet hash přes obsah souboru, který má zadaný soubor popisovač, pomocí zadaný algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="ede98-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ede98-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ede98-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ede98-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ede98-105">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="ede98-106">[v] Popisovač souboru, který se použít algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="ede98-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="ede98-107">[ve out] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="ede98-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="ede98-108">Používejte nula pro výchozí algoritmus.</span><span class="sxs-lookup"><span data-stu-id="ede98-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="ede98-109">[out] Vrácená hodnota hash vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ede98-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="ede98-110">[v] Požadovaný maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="ede98-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="ede98-111">[out] Velikost v bajtech vrácený `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="ede98-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ede98-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ede98-112">Return Value</span></span>  
 <span data-ttu-id="ede98-113">`S_OK`Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="ede98-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ede98-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ede98-114">Requirements</span></span>  
 <span data-ttu-id="ede98-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ede98-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ede98-116">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ede98-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ede98-117">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ede98-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ede98-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ede98-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ede98-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="ede98-119">See Also</span></span>  
 [<span data-ttu-id="ede98-120">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ede98-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
