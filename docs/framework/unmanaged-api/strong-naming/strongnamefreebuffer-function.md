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
ms.openlocfilehash: 50e3cc6e677de45be9256a2a818ebd6ed7d8b843
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176913"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="b407b-102">StrongNameFreeBuffer – funkce</span><span class="sxs-lookup"><span data-stu-id="b407b-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="b407b-103">Uvolní paměť, která byla přidělena s předchozím voláním funkce silného názvu, jako je [například StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md)nebo [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="b407b-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="b407b-104">Tato funkce byla zastaralá.</span><span class="sxs-lookup"><span data-stu-id="b407b-104">This function has been deprecated.</span></span> <span data-ttu-id="b407b-105">Místo toho použijte metodu [ICLRStrongName::StrongNameFreeBuffer.](../hosting/iclrstrongname-strongnamefreebuffer-method.md)</span><span class="sxs-lookup"><span data-stu-id="b407b-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b407b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b407b-106">Syntax</span></span>  
  
```cpp  
VOID StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b407b-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="b407b-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="b407b-108">[v] Ukazatel na paměť k uvolnění.</span><span class="sxs-lookup"><span data-stu-id="b407b-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b407b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b407b-109">Requirements</span></span>  
 <span data-ttu-id="b407b-110">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b407b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b407b-111">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="b407b-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="b407b-112">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b407b-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b407b-113">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b407b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b407b-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="b407b-114">See also</span></span>

- [<span data-ttu-id="b407b-115">StrongNameFreeBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="b407b-115">StrongNameFreeBuffer Method</span></span>](../hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="b407b-116">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b407b-116">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
