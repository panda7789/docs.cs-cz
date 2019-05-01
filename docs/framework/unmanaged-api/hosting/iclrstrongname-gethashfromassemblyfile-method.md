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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993106"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="beec4-102">ICLRStrongName::GetHashFromAssemblyFile – metoda</span><span class="sxs-lookup"><span data-stu-id="beec4-102">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>
<span data-ttu-id="beec4-103">Získá hodnotu hash zadaného souboru sestavení, pomocí zadané hashovacího algoritmu.</span><span class="sxs-lookup"><span data-stu-id="beec4-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beec4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="beec4-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="beec4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="beec4-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="beec4-106">[in] Cesta k souboru, který má být mají hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="beec4-106">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="beec4-107">[out v] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="beec4-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="beec4-108">Použít nulu pro výchozí hashovací algoritmus.</span><span class="sxs-lookup"><span data-stu-id="beec4-108">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="beec4-109">[out] Vrácená hodnota hash vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="beec4-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="beec4-110">[in] Požadovaná maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="beec4-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="beec4-111">[out] Velikost v bajtech, vrátil z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="beec4-111">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="beec4-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="beec4-112">Return Value</span></span>  
 <span data-ttu-id="beec4-113">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="beec4-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="beec4-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="beec4-114">Requirements</span></span>  
 <span data-ttu-id="beec4-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="beec4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="beec4-116">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="beec4-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="beec4-117">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="beec4-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="beec4-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="beec4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beec4-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="beec4-119">See also</span></span>

- [<span data-ttu-id="beec4-120">GetHashFromAssemblyFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="beec4-120">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="beec4-121">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="beec4-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
