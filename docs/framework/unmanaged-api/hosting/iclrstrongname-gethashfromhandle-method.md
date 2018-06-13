---
title: ICLRStrongName::GetHashFromHandle – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromHandle
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromHandle method [.NET Framework hosting]
ms.assetid: 3bedbb7d-3cdd-4175-b370-10ae734062db
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97d4a6bfd7a8a7aa257ad2f52d005ccc5bcd6fb6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432034"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="2e5f3-102">ICLRStrongName::GetHashFromHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="2e5f3-102">ICLRStrongName::GetHashFromHandle Method</span></span>
<span data-ttu-id="2e5f3-103">Generuje součet hash přes obsah souboru, který má zadaný soubor popisovač, pomocí zadaný algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="2e5f3-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e5f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e5f3-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2e5f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e5f3-105">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="2e5f3-106">[v] Popisovač souboru, který se použít algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="2e5f3-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="2e5f3-107">[ve out] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="2e5f3-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="2e5f3-108">Používejte nula pro výchozí algoritmus.</span><span class="sxs-lookup"><span data-stu-id="2e5f3-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="2e5f3-109">[out] Vrácená hodnota hash vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="2e5f3-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="2e5f3-110">[v] Požadovaný maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="2e5f3-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="2e5f3-111">[out] Velikost v bajtech vrácený `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="2e5f3-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e5f3-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2e5f3-112">Return Value</span></span>  
 <span data-ttu-id="2e5f3-113">`S_OK` Pokud metoda dokončena úspěšně; jinak hodnota hodnotou HRESULT označující selhání (viz [běžné hodnoty HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="2e5f3-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e5f3-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e5f3-114">Requirements</span></span>  
 <span data-ttu-id="2e5f3-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e5f3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e5f3-116">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="2e5f3-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2e5f3-117">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2e5f3-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e5f3-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e5f3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e5f3-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e5f3-119">See Also</span></span>  
 [<span data-ttu-id="2e5f3-120">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e5f3-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
