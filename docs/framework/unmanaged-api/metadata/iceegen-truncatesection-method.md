---
title: ICeeGen::TruncateSection – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.TruncateSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::TruncateSection
helpviewer_keywords:
- TruncateSection method [.NET Framework metadata]
- ICeeGen::TruncateSection method [.NET Framework metadata]
ms.assetid: 0451d752-1e5c-4c9a-8bad-6cd35b7ba3df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1ef6583587b960d74c83350b061be3c2e36fd4f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722670"
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="9f4cc-102">ICeeGen::TruncateSection – metoda</span><span class="sxs-lookup"><span data-stu-id="9f4cc-102">ICeeGen::TruncateSection Method</span></span>
<span data-ttu-id="9f4cc-103">Zkrátí části zadaný kód pomocí zadané délky.</span><span class="sxs-lookup"><span data-stu-id="9f4cc-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="9f4cc-104">Tato metoda je zastaralý a neměl by se používat.</span><span class="sxs-lookup"><span data-stu-id="9f4cc-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f4cc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f4cc-105">Syntax</span></span>  
  
```  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9f4cc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9f4cc-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="9f4cc-107">[in] V části došlo ke zkrácení.</span><span class="sxs-lookup"><span data-stu-id="9f4cc-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="9f4cc-108">[in] Délka v bajtech, podle kterého chcete zkrátit části.</span><span class="sxs-lookup"><span data-stu-id="9f4cc-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f4cc-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9f4cc-109">Remarks</span></span>  
 <span data-ttu-id="9f4cc-110">Volání `TruncateSection` pouze v případě, že máte zvláštní oddíl s požadavky, které nejsou zpracovány jinými metodami.</span><span class="sxs-lookup"><span data-stu-id="9f4cc-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f4cc-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9f4cc-111">Requirements</span></span>  
 <span data-ttu-id="9f4cc-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f4cc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f4cc-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9f4cc-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9f4cc-114">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9f4cc-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9f4cc-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f4cc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f4cc-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f4cc-116">See also</span></span>
- [<span data-ttu-id="9f4cc-117">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9f4cc-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
