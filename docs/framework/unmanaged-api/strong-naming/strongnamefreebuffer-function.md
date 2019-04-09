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
ms.openlocfilehash: 9bfc6491a1d18c81a44a7d9c5084f744c9b76281
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072570"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="922b7-102">StrongNameFreeBuffer – funkce</span><span class="sxs-lookup"><span data-stu-id="922b7-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="922b7-103">Uvolnění paměti, která byla přidělena s předchozím volání funkce silným názvem, jako například [strongnamegetpublickey –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [strongnametokenfrompublickey –](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), nebo [strongnamesignaturegeneration – ](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="922b7-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="922b7-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="922b7-104">This function has been deprecated.</span></span> <span data-ttu-id="922b7-105">Použití [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="922b7-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="922b7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="922b7-106">Syntax</span></span>  
  
```  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="922b7-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="922b7-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="922b7-108">[in] Ukazatel na paměť uvolnit.</span><span class="sxs-lookup"><span data-stu-id="922b7-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="922b7-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="922b7-109">Requirements</span></span>  
 <span data-ttu-id="922b7-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="922b7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="922b7-111">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="922b7-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="922b7-112">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="922b7-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="922b7-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="922b7-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="922b7-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="922b7-114">See also</span></span>

- [<span data-ttu-id="922b7-115">StrongNameFreeBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="922b7-115">StrongNameFreeBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="922b7-116">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="922b7-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
