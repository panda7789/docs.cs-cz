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
ms.openlocfilehash: 92b9d9b5baee856f09dd24a62767aff604728997
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454079"
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="a5936-102">StrongNameHashSize – funkce</span><span class="sxs-lookup"><span data-stu-id="a5936-102">StrongNameHashSize Function</span></span>
<span data-ttu-id="a5936-103">Získá velikost vyrovnávací paměti vyžadované pro hodnotu hash, pomocí zadaný algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="a5936-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="a5936-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="a5936-104">This function has been deprecated.</span></span> <span data-ttu-id="a5936-105">Použití [iclrstrongname::strongnamehashsize –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="a5936-105">Use the [ICLRStrongName::StrongNameHashSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5936-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5936-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a5936-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5936-107">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="a5936-108">[v] Algoritmus hash, který slouží k výpočtu velikost vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a5936-108">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="a5936-109">[out] Vrácený vyrovnávací paměti velikost v bajtech.</span><span class="sxs-lookup"><span data-stu-id="a5936-109">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5936-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a5936-110">Return Value</span></span>  
 <span data-ttu-id="a5936-111">`true` Při úspěšném dokončení; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="a5936-111">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5936-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5936-112">Remarks</span></span>  
 <span data-ttu-id="a5936-113">Pokud `StrongNameHashSize` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce načíst poslední generované chyba.</span><span class="sxs-lookup"><span data-stu-id="a5936-113">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5936-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a5936-114">Requirements</span></span>  
 <span data-ttu-id="a5936-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5936-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5936-116">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="a5936-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a5936-117">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a5936-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a5936-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5936-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5936-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5936-119">See Also</span></span>  
 [<span data-ttu-id="a5936-120">StrongNameHashSize – metoda</span><span class="sxs-lookup"><span data-stu-id="a5936-120">StrongNameHashSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)  
 [<span data-ttu-id="a5936-121">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a5936-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
