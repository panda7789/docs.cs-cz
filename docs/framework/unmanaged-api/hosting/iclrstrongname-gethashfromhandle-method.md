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
ms.openlocfilehash: e2d71f7c61b02273bdcaf182f6f79ca3c2a2c75f
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762070"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="e45bb-102">ICLRStrongName::GetHashFromHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="e45bb-102">ICLRStrongName::GetHashFromHandle Method</span></span>
<span data-ttu-id="e45bb-103">Vygeneruje hodnotu hash přes obsah souboru, který má zadaný popisovač souboru, pomocí zadaného algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="e45bb-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e45bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e45bb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e45bb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e45bb-105">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="e45bb-106">pro Popisovač souboru, který se má vyhodnotit.</span><span class="sxs-lookup"><span data-stu-id="e45bb-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="e45bb-107">[in, out] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="e45bb-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="e45bb-108">Pro výchozí algoritmus použijte nulu.</span><span class="sxs-lookup"><span data-stu-id="e45bb-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="e45bb-109">mimo Vrácená vyrovnávací paměť hash.</span><span class="sxs-lookup"><span data-stu-id="e45bb-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="e45bb-110">pro Požadovaná maximální velikost `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="e45bb-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="e45bb-111">mimo Velikost vracené velikosti (v bajtech) `pbHash`</span><span class="sxs-lookup"><span data-stu-id="e45bb-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e45bb-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e45bb-112">Return Value</span></span>  
 <span data-ttu-id="e45bb-113">`S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="e45bb-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e45bb-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e45bb-114">Requirements</span></span>  
 <span data-ttu-id="e45bb-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e45bb-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e45bb-116">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="e45bb-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e45bb-117">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e45bb-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e45bb-118">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e45bb-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e45bb-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="e45bb-119">See also</span></span>

- [<span data-ttu-id="e45bb-120">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e45bb-120">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
