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
ms.openlocfilehash: 553acc178bc5805b5afef5931fefc8ad74cbac39
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135178"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="c401f-102">ICLRStrongName::GetHashFromFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="c401f-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="c401f-103">Vygeneruje hodnotu hash přes obsah souboru určeného řetězcem Unicode.</span><span class="sxs-lookup"><span data-stu-id="c401f-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c401f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c401f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="c401f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c401f-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="c401f-106">pro Název Unicode souboru, na který se má vypočítat hodnota hash</span><span class="sxs-lookup"><span data-stu-id="c401f-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="c401f-107">[in, out] Algoritmus, který má být použit při generování hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="c401f-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="c401f-108">Platné algoritmy jsou definovány rozhraním Win32 CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="c401f-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="c401f-109">Je-li `piHashAlg` nastavena na hodnotu 0, je použit výchozí algoritmus CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="c401f-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="c401f-110">mimo Bajtové pole obsahující vygenerovanou hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="c401f-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="c401f-111">pro Maximální velikost vyrovnávací paměti, na kterou ukazuje `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="c401f-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="c401f-112">mimo Velikost `pbHash`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="c401f-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c401f-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c401f-113">Return Value</span></span>  
 <span data-ttu-id="c401f-114">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="c401f-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c401f-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c401f-115">Remarks</span></span>  
 <span data-ttu-id="c401f-116">Tato metoda je stejná jako metoda [ICLRStrongName:: GetHashFromFile –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) s tím rozdílem, že specifikace názvu souboru je Unicode namísto ANSI.</span><span class="sxs-lookup"><span data-stu-id="c401f-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c401f-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c401f-117">Requirements</span></span>  
 <span data-ttu-id="c401f-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c401f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c401f-119">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="c401f-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c401f-120">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c401f-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c401f-121">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c401f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c401f-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c401f-122">See also</span></span>

- [<span data-ttu-id="c401f-123">GetHashFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="c401f-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="c401f-124">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c401f-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
