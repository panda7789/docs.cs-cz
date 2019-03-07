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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ad1f015f04b3829090417c26e8d58892ee15af4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487431"
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="6c352-102">StrongNameHashSize – funkce</span><span class="sxs-lookup"><span data-stu-id="6c352-102">StrongNameHashSize Function</span></span>
<span data-ttu-id="6c352-103">Získá velikost vyrovnávací paměti vyžadované pro hodnotu hash pomocí algoritmu zadanou hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="6c352-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="6c352-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="6c352-104">This function has been deprecated.</span></span> <span data-ttu-id="6c352-105">Použití [iclrstrongname::strongnamehashsize –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="6c352-105">Use the [ICLRStrongName::StrongNameHashSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c352-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c352-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c352-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c352-107">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="6c352-108">[in] Hashovací algoritmus, který slouží k výpočtu velikosti vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="6c352-108">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="6c352-109">[out] Velikost vrácené vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="6c352-109">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c352-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6c352-110">Return Value</span></span>  
 <span data-ttu-id="6c352-111">`true` Při úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="6c352-111">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c352-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c352-112">Remarks</span></span>  
 <span data-ttu-id="6c352-113">Pokud `StrongNameHashSize` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.</span><span class="sxs-lookup"><span data-stu-id="6c352-113">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c352-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6c352-114">Requirements</span></span>  
 <span data-ttu-id="6c352-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c352-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c352-116">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="6c352-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="6c352-117">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6c352-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6c352-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c352-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c352-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c352-119">See also</span></span>
- [<span data-ttu-id="6c352-120">StrongNameHashSize – metoda</span><span class="sxs-lookup"><span data-stu-id="6c352-120">StrongNameHashSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)
- [<span data-ttu-id="6c352-121">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c352-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
