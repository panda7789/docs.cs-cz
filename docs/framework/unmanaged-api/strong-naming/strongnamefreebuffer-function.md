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
ms.openlocfilehash: 639664c6ce5714b554f30bff2569a12bf48d1671
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799122"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="d65cd-102">StrongNameFreeBuffer – funkce</span><span class="sxs-lookup"><span data-stu-id="d65cd-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="d65cd-103">Uvolní paměť, která byla přidělena předchozímu volání funkce silného názvu, jako je například [StrongNameGetPublicKey –](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey –](strongnametokenfrompublickey-function.md)nebo [StrongNameSignatureGeneration –](strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="d65cd-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="d65cd-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="d65cd-104">This function has been deprecated.</span></span> <span data-ttu-id="d65cd-105">Místo toho použijte metodu [ICLRStrongName:: StrongNameFreeBuffer –](../hosting/iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d65cd-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d65cd-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d65cd-106">Syntax</span></span>  
  
```cpp  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d65cd-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d65cd-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="d65cd-108">pro Ukazatel na paměť, která má být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="d65cd-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d65cd-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d65cd-109">Requirements</span></span>  
 <span data-ttu-id="d65cd-110">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d65cd-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d65cd-111">**Hlaviček** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="d65cd-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d65cd-112">**Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d65cd-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d65cd-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d65cd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d65cd-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d65cd-114">See also</span></span>

- [<span data-ttu-id="d65cd-115">StrongNameFreeBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="d65cd-115">StrongNameFreeBuffer Method</span></span>](../hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="d65cd-116">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d65cd-116">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
