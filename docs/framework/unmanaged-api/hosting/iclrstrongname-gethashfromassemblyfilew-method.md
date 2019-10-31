---
title: ICLRStrongName::GetHashFromAssemblyFileW – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW method [.NET Framework hosting]
- GetHashFromAssemblyFileW method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5d0b44a2-5a14-44a2-9a0e-e8682fd4e106
topic_type:
- apiref
ms.openlocfilehash: 43a5cd57a8eeaba70f1bb1ffb9cab5bb1a067914
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130955"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="60287-102">ICLRStrongName::GetHashFromAssemblyFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="60287-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>
<span data-ttu-id="60287-103">Vygeneruje hodnotu hash přes obsah souboru určeného řetězcem Unicode.</span><span class="sxs-lookup"><span data-stu-id="60287-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60287-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60287-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60287-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="60287-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="60287-106">pro Cesta k souboru, který se má vyhodnotit</span><span class="sxs-lookup"><span data-stu-id="60287-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="60287-107">Tento parametr musí být řetězec Unicode.</span><span class="sxs-lookup"><span data-stu-id="60287-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="60287-108">[in, out] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="60287-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="60287-109">Pro výchozí algoritmus hash použijte nulu.</span><span class="sxs-lookup"><span data-stu-id="60287-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="60287-110">mimo Vrácená vyrovnávací paměť hash.</span><span class="sxs-lookup"><span data-stu-id="60287-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="60287-111">pro Požadovaná maximální velikost `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="60287-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="60287-112">mimo Vrácená velikost (v bajtech) `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="60287-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60287-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="60287-113">Return Value</span></span>  
 <span data-ttu-id="60287-114">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="60287-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60287-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="60287-115">Requirements</span></span>  
 <span data-ttu-id="60287-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60287-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60287-117">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="60287-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="60287-118">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="60287-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="60287-119">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60287-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60287-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60287-120">See also</span></span>

- [<span data-ttu-id="60287-121">GetHashFromAssemblyFile – metoda</span><span class="sxs-lookup"><span data-stu-id="60287-121">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="60287-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="60287-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
