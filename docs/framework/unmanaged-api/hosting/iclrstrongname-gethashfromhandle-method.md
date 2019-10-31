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
ms.openlocfilehash: 19d4518b7ec125df717b2f901bbd92cbd1b659bc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135168"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="ba64a-102">ICLRStrongName::GetHashFromHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="ba64a-102">ICLRStrongName::GetHashFromHandle Method</span></span>
<span data-ttu-id="ba64a-103">Vygeneruje hodnotu hash přes obsah souboru, který má zadaný popisovač souboru, pomocí zadaného algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="ba64a-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba64a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba64a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba64a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ba64a-105">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="ba64a-106">pro Popisovač souboru, který se má vyhodnotit.</span><span class="sxs-lookup"><span data-stu-id="ba64a-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="ba64a-107">[in, out] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="ba64a-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="ba64a-108">Pro výchozí algoritmus použijte nulu.</span><span class="sxs-lookup"><span data-stu-id="ba64a-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="ba64a-109">mimo Vrácená vyrovnávací paměť hash.</span><span class="sxs-lookup"><span data-stu-id="ba64a-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="ba64a-110">pro Požadovaná maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="ba64a-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="ba64a-111">mimo Velikost vrácených `pbHash`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="ba64a-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba64a-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ba64a-112">Return Value</span></span>  
 <span data-ttu-id="ba64a-113">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="ba64a-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba64a-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ba64a-114">Requirements</span></span>  
 <span data-ttu-id="ba64a-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba64a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba64a-116">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="ba64a-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ba64a-117">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ba64a-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba64a-118">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba64a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba64a-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba64a-119">See also</span></span>

- [<span data-ttu-id="ba64a-120">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba64a-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
