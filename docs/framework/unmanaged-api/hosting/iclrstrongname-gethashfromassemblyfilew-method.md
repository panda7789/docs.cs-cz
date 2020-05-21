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
ms.openlocfilehash: f44753b3e836b43bc09548a35eb68f0f22e3170f
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762133"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="c95d9-102">ICLRStrongName::GetHashFromAssemblyFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="c95d9-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>
<span data-ttu-id="c95d9-103">Vygeneruje hodnotu hash přes obsah souboru určeného řetězcem Unicode.</span><span class="sxs-lookup"><span data-stu-id="c95d9-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c95d9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c95d9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c95d9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c95d9-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="c95d9-106">pro Cesta k souboru, který se má vyhodnotit</span><span class="sxs-lookup"><span data-stu-id="c95d9-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="c95d9-107">Tento parametr musí být řetězec Unicode.</span><span class="sxs-lookup"><span data-stu-id="c95d9-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="c95d9-108">[in, out] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="c95d9-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="c95d9-109">Pro výchozí algoritmus hash použijte nulu.</span><span class="sxs-lookup"><span data-stu-id="c95d9-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="c95d9-110">mimo Vrácená vyrovnávací paměť hash.</span><span class="sxs-lookup"><span data-stu-id="c95d9-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="c95d9-111">pro Požadovaná maximální velikost `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="c95d9-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="c95d9-112">mimo Vrácená velikost (v bajtech) `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="c95d9-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c95d9-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c95d9-113">Return Value</span></span>  
 <span data-ttu-id="c95d9-114">`S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="c95d9-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c95d9-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c95d9-115">Requirements</span></span>  
 <span data-ttu-id="c95d9-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c95d9-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c95d9-117">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="c95d9-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c95d9-118">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c95d9-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c95d9-119">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c95d9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c95d9-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="c95d9-120">See also</span></span>

- [<span data-ttu-id="c95d9-121">GetHashFromAssemblyFile – metoda</span><span class="sxs-lookup"><span data-stu-id="c95d9-121">GetHashFromAssemblyFile Method</span></span>](iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="c95d9-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c95d9-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
