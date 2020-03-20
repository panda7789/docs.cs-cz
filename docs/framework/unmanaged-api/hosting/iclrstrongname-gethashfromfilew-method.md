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
ms.openlocfilehash: 8f2d74531233f2ba423c39126ddc43e499cbb5d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176367"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="80557-102">ICLRStrongName::GetHashFromFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="80557-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="80557-103">Generuje hash nad obsahem souboru určeného řetězcem Unicode.</span><span class="sxs-lookup"><span data-stu-id="80557-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80557-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80557-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="80557-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80557-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="80557-106">[v] Název unicode souboru hash.</span><span class="sxs-lookup"><span data-stu-id="80557-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="80557-107">[dovnitř, ven] Algoritmus, který se má použít při generování algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="80557-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="80557-108">Platné algoritmy jsou ty, které jsou definovány Win32 CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="80557-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="80557-109">Pokud `piHashAlg` je nastavena na hodnotu 0, použije se výchozí algoritmus CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="80557-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="80557-110">[out] Bajtový pole obsahující vygenerovaný hash.</span><span class="sxs-lookup"><span data-stu-id="80557-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="80557-111">[v] Maximální velikost vyrovnávací paměti, `pbHash`na kterou se vztahuje .</span><span class="sxs-lookup"><span data-stu-id="80557-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="80557-112">[out] Velikost v bajtů `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="80557-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80557-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="80557-113">Return Value</span></span>  
 <span data-ttu-id="80557-114">`S_OK`pokud byla metoda úspěšně dokončena; jinak hodnota HRESULT, která označuje selhání (viz [běžné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="80557-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80557-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="80557-115">Remarks</span></span>  
 <span data-ttu-id="80557-116">Tato metoda je stejná jako metoda [ICLRStrongName::GetHashFromFile,](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) s tím rozdílem, že specifikace názvu souboru je Unicode místo ANSI.</span><span class="sxs-lookup"><span data-stu-id="80557-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80557-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="80557-117">Requirements</span></span>  
 <span data-ttu-id="80557-118">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80557-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80557-119">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="80557-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="80557-120">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="80557-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80557-121">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80557-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80557-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="80557-122">See also</span></span>

- [<span data-ttu-id="80557-123">GetHashFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="80557-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="80557-124">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="80557-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
