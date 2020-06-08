---
title: ICLRStrongName::StrongNameFreeBuffer – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameFreeBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameFreeBuffer method [.NET Framework hosting]
ms.assetid: 6148c508-bd1d-4a37-85c3-06ecb09cc857
topic_type:
- apiref
ms.openlocfilehash: 7aed3e6877bfcd83754d462cdba81ccc229d002f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504001"
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a><span data-ttu-id="ade91-102">ICLRStrongName::StrongNameFreeBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="ade91-102">ICLRStrongName::StrongNameFreeBuffer Method</span></span>
<span data-ttu-id="ade91-103">Uvolní paměť, která byla přidělena předchozímu volání metody silného názvu, jako je například [ICLRStrongName:: StrongNameGetPublicKey –](iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName:: StrongNameTokenFromPublicKey –](iclrstrongname-strongnametokenfrompublickey-method.md)nebo [ICLRStrongName:: StrongNameSignatureGeneration –](iclrstrongname-strongnamesignaturegeneration-method.md).</span><span class="sxs-lookup"><span data-stu-id="ade91-103">Frees memory that was allocated with a previous call to a strong name method such as [ICLRStrongName::StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName::StrongNameTokenFromPublicKey](iclrstrongname-strongnametokenfrompublickey-method.md), or [ICLRStrongName::StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ade91-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ade91-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ade91-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ade91-105">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="ade91-106">pro Ukazatel na paměť, která má být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="ade91-106">[in] A pointer to the memory to free.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ade91-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ade91-107">Return Value</span></span>  
 <span data-ttu-id="ade91-108">`S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="ade91-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ade91-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ade91-109">Requirements</span></span>  
 <span data-ttu-id="ade91-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ade91-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ade91-111">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="ade91-111">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ade91-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ade91-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ade91-113">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ade91-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ade91-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ade91-114">See also</span></span>

- [<span data-ttu-id="ade91-115">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ade91-115">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
