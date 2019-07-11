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
ms.openlocfilehash: a8f6878d714704370c3f43451c9995a7c5adb5d1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748147"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="048ff-102">ICLRStrongName::GetHashFromHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="048ff-102">ICLRStrongName::GetHashFromHandle Method</span></span>
<span data-ttu-id="048ff-103">Vygeneruje hodnotu hash přes obsah souboru, který má zadaný soubor popisovač, pomocí zadané hashovacího algoritmu.</span><span class="sxs-lookup"><span data-stu-id="048ff-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="048ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="048ff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="048ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="048ff-105">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="048ff-106">[in] Popisovač souboru, který má být mají hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="048ff-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="048ff-107">[out v] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="048ff-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="048ff-108">Použít nulu pro výchozí algoritmus.</span><span class="sxs-lookup"><span data-stu-id="048ff-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="048ff-109">[out] Vrácená hodnota hash vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="048ff-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="048ff-110">[in] Požadovaná maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="048ff-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="048ff-111">[out] Velikost v bajtech, vráceného `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="048ff-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="048ff-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="048ff-112">Return Value</span></span>  
 <span data-ttu-id="048ff-113">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="048ff-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="048ff-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="048ff-114">Requirements</span></span>  
 <span data-ttu-id="048ff-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="048ff-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="048ff-116">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="048ff-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="048ff-117">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="048ff-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="048ff-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="048ff-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="048ff-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="048ff-119">See also</span></span>

- [<span data-ttu-id="048ff-120">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="048ff-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
