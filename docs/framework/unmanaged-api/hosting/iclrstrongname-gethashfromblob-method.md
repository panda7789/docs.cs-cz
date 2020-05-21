---
title: ICLRStrongName::GetHashFromBlob – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromBlob
helpviewer_keywords:
- ICLRStrongName::GetHashFromBlob method [.NET Framework hosting]
- GetHashFromBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: f91d0f89-f356-49ac-aafb-50fad963c13d
topic_type:
- apiref
ms.openlocfilehash: 081df31d1e3b1ca3345fe44b60cff6af27386953
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762120"
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="8e863-102">ICLRStrongName::GetHashFromBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="8e863-102">ICLRStrongName::GetHashFromBlob Method</span></span>
<span data-ttu-id="8e863-103">Načte hodnotu hash sestavení v zadané adrese paměti pomocí zadaného algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="8e863-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e863-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e863-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e863-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8e863-105">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="8e863-106">pro Ukazatel na adresu bloku paměti, který má být použit jako hash.</span><span class="sxs-lookup"><span data-stu-id="8e863-106">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="8e863-107">pro Délka bloku paměti (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="8e863-107">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="8e863-108">[in, out] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="8e863-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="8e863-109">Pro výchozí algoritmus použijte nulu.</span><span class="sxs-lookup"><span data-stu-id="8e863-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="8e863-110">mimo Vrácená vyrovnávací paměť hash.</span><span class="sxs-lookup"><span data-stu-id="8e863-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="8e863-111">pro Požadovaná maximální velikost `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="8e863-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="8e863-112">mimo Velikost vracené velikosti (v bajtech) `pbHash`</span><span class="sxs-lookup"><span data-stu-id="8e863-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e863-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8e863-113">Return Value</span></span>  
 <span data-ttu-id="8e863-114">`S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="8e863-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e863-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8e863-115">Requirements</span></span>  
 <span data-ttu-id="8e863-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e863-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e863-117">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="8e863-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8e863-118">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8e863-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8e863-119">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e863-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e863-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e863-120">See also</span></span>

- [<span data-ttu-id="8e863-121">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8e863-121">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
