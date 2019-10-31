---
title: ICLRStrongName::GetHashFromFile – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type:
- apiref
ms.openlocfilehash: 798bb0585bfe4cc29afba2fbefae818301704613
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135184"
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="0f085-102">ICLRStrongName::GetHashFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="0f085-102">ICLRStrongName::GetHashFromFile Method</span></span>
<span data-ttu-id="0f085-103">Vygeneruje hodnotu hash přes obsah zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="0f085-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f085-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f085-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f085-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0f085-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="0f085-106">pro Název souboru, na který se má vypočítat hodnota hash</span><span class="sxs-lookup"><span data-stu-id="0f085-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="0f085-107">[in, out] Algoritmus, který má být použit při generování hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="0f085-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="0f085-108">Platné algoritmy jsou definovány rozhraním Win32 CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="0f085-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="0f085-109">Je-li `piHashAlg` nastavena na hodnotu 0, je použit výchozí algoritmus CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="0f085-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="0f085-110">mimo Bajtové pole obsahující vygenerovanou hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="0f085-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="0f085-111">pro Maximální velikost vyrovnávací paměti, na kterou `pbHash` odkazuje.</span><span class="sxs-lookup"><span data-stu-id="0f085-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="0f085-112">mimo Velikost vrácených `pbHash`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="0f085-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f085-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0f085-113">Return Value</span></span>  
 <span data-ttu-id="0f085-114">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="0f085-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f085-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0f085-115">Remarks</span></span>  
 <span data-ttu-id="0f085-116">Tato metoda je stejná jako metoda [ICLRStrongName:: GetHashFromFileW –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) s tím rozdílem, že specifikace názvu souboru je ANSI namísto Unicode.</span><span class="sxs-lookup"><span data-stu-id="0f085-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f085-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0f085-117">Requirements</span></span>  
 <span data-ttu-id="0f085-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f085-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f085-119">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="0f085-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0f085-120">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0f085-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f085-121">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f085-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f085-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0f085-122">See also</span></span>

- [<span data-ttu-id="0f085-123">GetHashFromFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="0f085-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="0f085-124">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0f085-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
