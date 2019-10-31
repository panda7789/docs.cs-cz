---
title: StrongNameHashSize – funkce
ms.date: 03/30/2017
api_name:
- StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameHashSize
helpviewer_keywords:
- StrongNameHashSize function [.NET Framework strong naming]
ms.assetid: 738c98d7-a60c-45fe-a296-220af05e6991
topic_type:
- apiref
ms.openlocfilehash: c656f73748faf8be7124be65f3ed455f2d5fd07a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73105192"
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="3463d-102">StrongNameHashSize – funkce</span><span class="sxs-lookup"><span data-stu-id="3463d-102">StrongNameHashSize Function</span></span>
<span data-ttu-id="3463d-103">Získá velikost vyrovnávací paměti vyžadované pro hodnotu hash pomocí zadaného algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="3463d-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="3463d-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="3463d-104">This function has been deprecated.</span></span> <span data-ttu-id="3463d-105">Místo toho použijte metodu [ICLRStrongName:: StrongNameHashSize –](../hosting/iclrstrongname-strongnamehashsize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3463d-105">Use the [ICLRStrongName::StrongNameHashSize](../hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3463d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3463d-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3463d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="3463d-107">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="3463d-108">pro Algoritmus hash používaný k výpočtu velikosti vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="3463d-108">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="3463d-109">mimo Vrácená velikost vyrovnávací paměti (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="3463d-109">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3463d-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3463d-110">Return Value</span></span>  
 <span data-ttu-id="3463d-111">`true` po úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="3463d-111">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3463d-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3463d-112">Remarks</span></span>  
 <span data-ttu-id="3463d-113">Pokud se funkce `StrongNameHashSize` nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="3463d-113">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3463d-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3463d-114">Requirements</span></span>  
 <span data-ttu-id="3463d-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3463d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3463d-116">**Hlavička:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="3463d-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="3463d-117">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3463d-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3463d-118">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3463d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3463d-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3463d-119">See also</span></span>

- [<span data-ttu-id="3463d-120">StrongNameHashSize – metoda</span><span class="sxs-lookup"><span data-stu-id="3463d-120">StrongNameHashSize Method</span></span>](../hosting/iclrstrongname-strongnamehashsize-method.md)
- [<span data-ttu-id="3463d-121">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3463d-121">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
