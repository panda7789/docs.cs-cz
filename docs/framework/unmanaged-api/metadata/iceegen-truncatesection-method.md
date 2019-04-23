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
ms.openlocfilehash: 1036d6080bf17eea288724c7980ce53dfa2121f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116318"
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="b5f65-102">ICeeGen::TruncateSection – metoda</span><span class="sxs-lookup"><span data-stu-id="b5f65-102">ICeeGen::TruncateSection Method</span></span>
<span data-ttu-id="b5f65-103">Zkrátí části zadaný kód pomocí zadané délky.</span><span class="sxs-lookup"><span data-stu-id="b5f65-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="b5f65-104">Tato metoda je zastaralý a neměl by se používat.</span><span class="sxs-lookup"><span data-stu-id="b5f65-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5f65-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5f65-105">Syntax</span></span>  
  
```  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5f65-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b5f65-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="b5f65-107">[in] V části došlo ke zkrácení.</span><span class="sxs-lookup"><span data-stu-id="b5f65-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="b5f65-108">[in] Délka v bajtech, podle kterého chcete zkrátit části.</span><span class="sxs-lookup"><span data-stu-id="b5f65-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5f65-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b5f65-109">Remarks</span></span>  
 <span data-ttu-id="b5f65-110">Volání `TruncateSection` pouze v případě, že máte zvláštní oddíl s požadavky, které nejsou zpracovány jinými metodami.</span><span class="sxs-lookup"><span data-stu-id="b5f65-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5f65-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b5f65-111">Requirements</span></span>  
 <span data-ttu-id="b5f65-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5f65-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5f65-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b5f65-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b5f65-114">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b5f65-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b5f65-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5f65-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5f65-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5f65-116">See also</span></span>

- [<span data-ttu-id="b5f65-117">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b5f65-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
