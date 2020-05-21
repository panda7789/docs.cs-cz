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
ms.openlocfilehash: 007de0365bf70b1f4a9a9e0f01807e7fdac19f54
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762146"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="e502f-102">ICLRStrongName::GetHashFromAssemblyFile – metoda</span><span class="sxs-lookup"><span data-stu-id="e502f-102">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>
<span data-ttu-id="e502f-103">Načte hodnotu hash zadaného souboru sestavení pomocí zadaného algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="e502f-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e502f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e502f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e502f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e502f-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="e502f-106">pro Cesta k souboru, který se má vyhodnotit</span><span class="sxs-lookup"><span data-stu-id="e502f-106">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="e502f-107">[in, out] Konstanta, která určuje algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="e502f-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="e502f-108">Pro výchozí algoritmus hash použijte nulu.</span><span class="sxs-lookup"><span data-stu-id="e502f-108">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="e502f-109">mimo Vrácená vyrovnávací paměť hash.</span><span class="sxs-lookup"><span data-stu-id="e502f-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="e502f-110">pro Požadovaná maximální velikost `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="e502f-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="e502f-111">mimo Vrácená velikost (v bajtech) `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="e502f-111">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e502f-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e502f-112">Return Value</span></span>  
 <span data-ttu-id="e502f-113">`S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="e502f-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e502f-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e502f-114">Requirements</span></span>  
 <span data-ttu-id="e502f-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e502f-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e502f-116">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="e502f-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e502f-117">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e502f-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e502f-118">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e502f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e502f-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="e502f-119">See also</span></span>

- [<span data-ttu-id="e502f-120">GetHashFromAssemblyFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="e502f-120">GetHashFromAssemblyFileW Method</span></span>](iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="e502f-121">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e502f-121">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
