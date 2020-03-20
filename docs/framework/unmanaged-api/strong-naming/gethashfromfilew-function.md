---
title: GetHashFromFileW – funkce
ms.date: 03/30/2017
api_name:
- GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type:
- apiref
ms.openlocfilehash: 9db583c7064cb910b29e84437f31143dac0d3ec9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175080"
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="72e24-102">GetHashFromFileW – funkce</span><span class="sxs-lookup"><span data-stu-id="72e24-102">GetHashFromFileW Function</span></span>
<span data-ttu-id="72e24-103">Generuje hash nad obsahem souboru určeného řetězcem Unicode.</span><span class="sxs-lookup"><span data-stu-id="72e24-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="72e24-104">Tato funkce byla zastaralá.</span><span class="sxs-lookup"><span data-stu-id="72e24-104">This function has been deprecated.</span></span> <span data-ttu-id="72e24-105">Místo toho použijte metodu [ICLRStrongName::GetHashFromFileW.](../hosting/iclrstrongname-gethashfromfilew-method.md)</span><span class="sxs-lookup"><span data-stu-id="72e24-105">Use the [ICLRStrongName::GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72e24-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72e24-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="72e24-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="72e24-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="72e24-108">[v] Název unicode souboru hash.</span><span class="sxs-lookup"><span data-stu-id="72e24-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="72e24-109">[dovnitř, ven] Algoritmus, který se má použít při generování algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="72e24-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="72e24-110">Platné algoritmy jsou ty, které jsou definovány Win32 CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="72e24-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="72e24-111">Pokud `piHashAlg` je nastavena na hodnotu 0, použije se výchozí algoritmus CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="72e24-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="72e24-112">[out] Bajtový pole obsahující vygenerovaný hash.</span><span class="sxs-lookup"><span data-stu-id="72e24-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="72e24-113">[v] Maximální velikost vyrovnávací paměti, `pbHash`na kterou se vztahuje .</span><span class="sxs-lookup"><span data-stu-id="72e24-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="72e24-114">[out] Velikost v bajtů `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="72e24-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72e24-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72e24-115">Remarks</span></span>  
 <span data-ttu-id="72e24-116">Tato funkce je stejná jako [GetHashFromFile](gethashfromfile-function.md), s tím rozdílem, že specifikace názvu souboru je Unicode místo ANSI.</span><span class="sxs-lookup"><span data-stu-id="72e24-116">This function is the same as [GetHashFromFile](gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72e24-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="72e24-117">Requirements</span></span>  
 <span data-ttu-id="72e24-118">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72e24-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72e24-119">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="72e24-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="72e24-120">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="72e24-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="72e24-121">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72e24-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72e24-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="72e24-122">See also</span></span>

- [<span data-ttu-id="72e24-123">GetHashFromFileW – metoda</span><span class="sxs-lookup"><span data-stu-id="72e24-123">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="72e24-124">GetHashFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="72e24-124">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="72e24-125">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="72e24-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
