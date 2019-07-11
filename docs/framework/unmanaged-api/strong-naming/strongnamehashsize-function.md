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
ms.openlocfilehash: 8093a702069e4ecd4dad761ad0a431abe81d6141
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780424"
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="40ae8-102">StrongNameHashSize – funkce</span><span class="sxs-lookup"><span data-stu-id="40ae8-102">StrongNameHashSize Function</span></span>
<span data-ttu-id="40ae8-103">Získá velikost vyrovnávací paměti vyžadované pro hodnotu hash pomocí algoritmu zadanou hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="40ae8-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="40ae8-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="40ae8-104">This function has been deprecated.</span></span> <span data-ttu-id="40ae8-105">Použití [iclrstrongname::strongnamehashsize –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="40ae8-105">Use the [ICLRStrongName::StrongNameHashSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40ae8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40ae8-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40ae8-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="40ae8-107">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="40ae8-108">[in] Hashovací algoritmus, který slouží k výpočtu velikosti vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="40ae8-108">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="40ae8-109">[out] Velikost vrácené vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="40ae8-109">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40ae8-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="40ae8-110">Return Value</span></span>  
 <span data-ttu-id="40ae8-111">`true` Při úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="40ae8-111">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40ae8-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="40ae8-112">Remarks</span></span>  
 <span data-ttu-id="40ae8-113">Pokud `StrongNameHashSize` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.</span><span class="sxs-lookup"><span data-stu-id="40ae8-113">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40ae8-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="40ae8-114">Requirements</span></span>  
 <span data-ttu-id="40ae8-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40ae8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40ae8-116">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="40ae8-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="40ae8-117">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="40ae8-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="40ae8-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40ae8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40ae8-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40ae8-119">See also</span></span>

- [<span data-ttu-id="40ae8-120">StrongNameHashSize – metoda</span><span class="sxs-lookup"><span data-stu-id="40ae8-120">StrongNameHashSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)
- [<span data-ttu-id="40ae8-121">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40ae8-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
