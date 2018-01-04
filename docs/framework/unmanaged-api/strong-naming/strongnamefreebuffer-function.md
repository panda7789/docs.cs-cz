---
title: "StrongNameFreeBuffer – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameFreeBuffer
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: StrongNameFreeBuffer
helpviewer_keywords: StrongNameFreeBuffer function [.NET Framework strong naming]
ms.assetid: eda21ecf-4734-4f92-aaba-9f34884385db
topic_type: apiref
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f4f5bde035b0ab9df07bb0ab709a67ae1a4cff3f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="a2c01-102">StrongNameFreeBuffer – funkce</span><span class="sxs-lookup"><span data-stu-id="a2c01-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="a2c01-103">Uvolní paměť, který byl přidělen s předchozí volání funkce silným názvem, jako [strongnamegetpublickey –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [strongnametokenfrompublickey –](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), nebo [strongnamesignaturegeneration – ](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="a2c01-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="a2c01-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="a2c01-104">This function has been deprecated.</span></span> <span data-ttu-id="a2c01-105">Použití [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="a2c01-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2c01-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2c01-106">Syntax</span></span>  
  
```  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a2c01-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2c01-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="a2c01-108">[v] Ukazatel na paměť uvolnit.</span><span class="sxs-lookup"><span data-stu-id="a2c01-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2c01-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a2c01-109">Requirements</span></span>  
 <span data-ttu-id="a2c01-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2c01-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2c01-111">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="a2c01-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a2c01-112">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a2c01-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a2c01-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2c01-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2c01-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2c01-114">See Also</span></span>  
 [<span data-ttu-id="a2c01-115">StrongNameFreeBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="a2c01-115">StrongNameFreeBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)  
 [<span data-ttu-id="a2c01-116">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a2c01-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
