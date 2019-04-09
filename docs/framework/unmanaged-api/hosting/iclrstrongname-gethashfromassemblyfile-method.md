---
title: ICLRStrongName::GetHashFromAssemblyFile – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFile method [.NET Framework hosting]
- GetHashFromAssemblyFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 0b67ea03-d474-4605-acaa-57455790250c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 714827da24b3fc0a334210fd94e61f80cb2afe49
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135749"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="85307-102">ICLRStrongName::GetHashFromAssemblyFile – metoda</span><span class="sxs-lookup"><span data-stu-id="85307-102">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>
<span data-ttu-id="85307-103">Získá hodnotu hash zadaného souboru sestavení, pomocí zadané hashovacího algoritmu.</span><span class="sxs-lookup"><span data-stu-id="85307-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85307-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85307-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85307-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="85307-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="85307-106">[in] Cesta k souboru, který má být mají hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="85307-106">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="85307-107">[out v] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="85307-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="85307-108">Použít nulu pro výchozí hashovací algoritmus.</span><span class="sxs-lookup"><span data-stu-id="85307-108">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="85307-109">[out] Vrácená hodnota hash vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="85307-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="85307-110">[in] Požadovaná maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="85307-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="85307-111">[out] Velikost v bajtech, vrátil z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="85307-111">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85307-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="85307-112">Return Value</span></span>  
 `S_OK` <span data-ttu-id="85307-113">Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="85307-113">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85307-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="85307-114">Requirements</span></span>  
 <span data-ttu-id="85307-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85307-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85307-116">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="85307-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="85307-117">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="85307-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="85307-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="85307-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="85307-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85307-119">See also</span></span>

- [<span data-ttu-id="85307-120">GetHashFromAssemblyFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="85307-120">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="85307-121">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85307-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
