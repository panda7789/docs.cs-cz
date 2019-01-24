---
title: StrongNameFreeBuffer – funkce
ms.date: 03/30/2017
api_name:
- StrongNameFreeBuffer
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer function [.NET Framework strong naming]
ms.assetid: eda21ecf-4734-4f92-aaba-9f34884385db
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 776150bdb7f7a74b6adc9a6f41bf61cae3d800ed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541011"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="ae251-102">StrongNameFreeBuffer – funkce</span><span class="sxs-lookup"><span data-stu-id="ae251-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="ae251-103">Uvolnění paměti, která byla přidělena s předchozím volání funkce silným názvem, jako například [strongnamegetpublickey –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [strongnametokenfrompublickey –](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), nebo [strongnamesignaturegeneration – ](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="ae251-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="ae251-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="ae251-104">This function has been deprecated.</span></span> <span data-ttu-id="ae251-105">Použití [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="ae251-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae251-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae251-106">Syntax</span></span>  
  
```  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae251-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae251-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="ae251-108">[in] Ukazatel na paměť uvolnit.</span><span class="sxs-lookup"><span data-stu-id="ae251-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae251-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ae251-109">Requirements</span></span>  
 <span data-ttu-id="ae251-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae251-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae251-111">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="ae251-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ae251-112">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ae251-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ae251-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae251-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae251-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae251-114">See also</span></span>
- [<span data-ttu-id="ae251-115">StrongNameFreeBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="ae251-115">StrongNameFreeBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="ae251-116">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ae251-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
